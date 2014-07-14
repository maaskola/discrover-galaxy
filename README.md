This is a module for [Galaxy](http://galaxyproject.org/) that allows to run [Discrover](https://github.com/maaskola/discrover).

How to use it
=============

In the instructions below, we designate two paths by shell variables: ```$P``` stands for the path where you clone the Discrover Galaxy module's source code into, and ```$GALAXY_PATH``` is the main directory of the source code of your Galaxy instance.

0. Install [Discrover](https://github.com/maaskola/discrover).
1. Install an instance of Galaxy, following these [directions](https://wiki.galaxyproject.org/Admin/GetGalaxy).
2. Clone this repository into the main directory of your galaxy instance:

    ```sh
    cd /some/place/for/the/Discrover/Galaxy/module/source/code
    export P=`pwd`
    git clone git@github.com:maaskola/discrover-galaxy.git
    ```
3. Add a symbolic link:

    ```sh
    cd $GALAXY_PATH/tools
    ln -s $P/discrover-galaxy/tools/discrover discrover
    ```
4. Modify ```tool_conf.xml``` in the main directory of the Galaxy instance to include a section for this module.
  Find the section with 'id' equal to 'motifs' (around line 132) and add a line

    ```xml
      <tool file="discrover/discrover.xml" />
    ```

  into it, such that it looks something like this:

    ```xml
    <section id="motifs" name="Motif Tools">
      <tool file="meme/meme.xml" />
      <tool file="meme/fimo.xml" />
      <tool file="discrover/discrover.xml" />
    </section>
    ```

5. Start your Galaxy instance by executing ```cd $GALAXY_PATH && ./run.sh```. Fire up a web browser and go to http://localhost:8080. The Discrover module is available in the left side pane under the section 'Motif tools'.

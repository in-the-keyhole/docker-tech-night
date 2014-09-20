# Keyhole Software Docker Tech Night

Can't sleep at night because you haven't learned Docker yet?

***

## Homework to complete _**BEFORE**_ Tech Night

*(The payoff - you'll have Docker running on your laptop, in the safety and isolation of your own private vm.  When we go through exercises during tech night, you'll be able to follow along while gaining first-hand experience.)*

**Exercise 0**

- Prep Time: 10-15 minutes
- Cook Time: 20 minutes to 1 hour, depending on how worthless your internet provider is.  This will just be unattended download and build time.

1. Install Prerequites
  1. Git - [http://git-scm.com](http://git-scm.com)
  2. VirtualBox >= 4.3.16 - [https://www.virtualbox.org/](https://www.virtualbox.org/)
  3. Vagrant >= 1.6.5 - [https://www.vagrantup.com/](https://www.vagrantup.com/)
    - *once installed, run `vagrant version` to see version info*
2. `git clone` this repo
3. Run `vagrant up` and then wait and wait (well, hopefully, if nothing goes wrong this will take quite a while).  Here's what it looked like when I ran on my laptop - [video](https://asciinema.org/a/12321).
  ![vagrant up](http://i.imgur.com/qC2DIlK.png)
4. Open your browser to [http://192.168.169.170](http://192.168.169.170) and you should see something like this: 
  ![development environment](http://i.imgur.com/0Wi7qaI.png)
  This is just a stripped-down development environment inside our vm where we can edit files and run things from its terminal.  We won't use the 'debug', 'run', 'deploy', etc., icons.  For us, it's just a text editor and terminal.
5. Open a terminal window (*File->New Terminal*) and run 'docker version' to verify that the docker command is available.  You should see something like this.
  ![docker version](http://i.imgur.com/yErxegW.png)
  :thumbsup:
6. Go back to your laptop's terminal, where you ran 'vagrant up' earlier, and run `vagrant halt` to shutdown the vm we created

***


# Folder Structure
- /introduction - wip, blah blah blah
- /exercises - wip, blah blah blah
 
## Presenters
 * Zach Gardner
 * Luke Patterson

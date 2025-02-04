# Linux Build Guide

This is a guide to compile your version of the ShashChess Engine. 

It is GUI independent and it can work in the terminal.

### Step 1:

Download or Clone the repository, using the following command in the terminal (please make sure that you are using the command in an empty directory):

```bash
git clone https://github.com/amchess/ShashChess.git
```

### Step 2:

From the directory where you cloned the repository, navigate to the src directory, where the Makefile is located:

```bash
cd ShashChess/src/
```

### Step 3:

Run the 'make' command, specifying your preferred target.

If you don't know what targets are, please run the following command to get an explanation:

```bash
make help
```

A typical target which should work well for general purposes will be the one in the following command:

```bash
make profile-build
```

This will run for a while, creating an executable file named "shashchess"

### Step 4:

Now that you have the executable, you can run it on the terminal:

```bash
./shashchess
```

If everything went smoothly, you should now see the engine name and its authors.

# 



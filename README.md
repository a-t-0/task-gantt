
task-gantt
==========

Generating Gantt charts from Taskwarrior entries.

![`task-gantt status:pending pro:task-gantt`](doc/gantt.png)

The idea is to specify a `due` date and a `duration` (UDA) and then treat the
task as it would start at `due - duration` and end at `due` date.


Setup
-----

1.	Add `duration` as user defined attribute to your `~/.taskrc`

	```
	uda.duration.type = numeric
	```

2.	Install `Project::Gantt` perl module

	```
	cd ~
	mkdir gantt
	sudo apt-update
	sudo apt install php-imagick
	sudo apt-get install libimage-magick-perl
	sudo apt-get install perlmagick
	sudo apt-get install imagemagick
	sudo apt-get install libperl-dev
	
	wget http://www.imagemagick.org/download/ImageMagick-6.9.10-78.tar.bz2
	tar xvfz ImageMagick-6.9.2-4.tar.gz
	
	wget http://www.imagemagick.org/download/ImageMagick-6.9.10-78.7z
	apt install unzip
	
	apt install p7zip-full
	7za x ImageMagick-6.9.10-78.7z
	
	cd ImageMagick-6.9.2-4/
	./configure --with-perl
	make
	(*)
	sudo make install
	apt install cpanminus
	cpanm Project::Gantt
	```


Usage
-----

```
task-gantt [--stdout] [-d <description>] [-o <filename>] <filters> ...
```
For example, to generate a Gantt chart of all pending tasks and watch it
directly with `feh` execute
```
task-gantt --stdout status:pending | feh -
```


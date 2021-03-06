# Compiler NoC++

## Checklist
- [ ] Scanner
	- [ ] Buffer (bis 25.10.)
		- [X] Implementierung
		- [ ] Tests
	- [ ] Symboltabelle (bis 01.11.)
		- [ ] Implementierung
		- [ ] Tests
	- [ ] Automat
		- [ ] Implementierung (bis 08.11.)
		- [ ] Tests (bis 15.11.)
- [ ] Parser
	- [ ] ?

## Verwendete Software
### Diagramme
- Visual Paradigm Community Edition
- https://www.visual-paradigm.com/download/

### IDE
- CLion
- https://www.jetbrains.com/clion/

### Compiler 
- CMake (Cygwin)
- https://www.cygwin.com/setup-x86_64.exe
- gcc
- g++
- make
- Cmake
- gdb

### Compiler (Alternative)
- MingGW for windows
- http://www.mingw.org/category/wiki/download
- gcc-g++
- gcc-obj
- base
- dev-tools
- gcc-ada
- gcc-fortan
- msys-base

## Projektbeschreibung

Das Projekt wurde in 4 Teilprojekte aufgeteilt:

	- Automat
	- FileBuffer
	- Symboltabelle
	- Scanner


Jedes Teilprojekt hat die Verzeichnisstruktur:

	- src			enthaelt den Source-Code
	- includes		enthaelt die Headerfiles
	- objs			enthaelt die Objektfiles, die notwenig fuer das Gesamtprojekt sind
	- debug			enthaelt die Objektfiles und das ausfuehrbare File zum Testen  des Teilprojekts
	

Jedes Teilprojekt enthaelt ein eigenes Makefile und eine eigene Main-Klasse, um die Funktionalitaet zu testen.
	
	
Makefiles werden benoetigt, um das Compilieren und Linken automatisiert durch das Tool make ausfuehren zu lassen.
 
### Level: ohne Makefile Kenntnisse	
Im Makefile im Teilprojekt Automat sind alle Schritte zum Compilieren und Linken ausfuehrlich aufgelistet.


### Level: wenig Makefile-Kenntnisse
Im Makefile im Teilprojekt FileBuffer werden die benoetigten Verzeichnisse ueber Variablen definiert.


### Level: gute Makefile-Kenntnisse
Im Makefile im Teilprojekt Symboltable und Scanner wird auch die Liste der zu compilierenden Files ueber Variablen deklariert.


### Aufbau des Makefiles:
-	Definition der Variablen
-	Targets zum Bauen des Tests, Targets sind Sprungziele, die durch make ausgefuehrt werden können 
	
Im Terminalfenster können die targets so aufgerufen werden: make target

In der Eclipse View "Make Targets" erscheinen die Targets der einzelnen Makefiles, die dann mit einem Doppelklick ausgefuehrt werden können.


### Aufbau der Targets
- 	 target: dependencies
- 	 [tab] system_command


### Compilation commands:
classA.o: classA.cpp classA.h
    [tab] g++ -c -g classA.cpp -o classA.o

- target classA.o ist abhaengig von der Source Datei classA.cpp und classA.h
- g++ Compiler Aufruf
- das File classA.cpp wird nur compiliert (-c) und in das Outputfile (-o) classA.o geschrieben



classB.o: classB.cpp classB.h classA.h
    [tab] g++ -c -g classB.cpp -o classB.o
    
- target classB.o ist abhaengig von der Source Datei classB.cpp, classB.h und classA.h
- g++ Compiler 
- das File classB.cpp wird nur compiliert (-c) und in das Outputfile (-o) classB.o geschrieben    


### Link command:
my_program: classA.o classB.o
   [tab] g++ -g classA.o classB.o -o my_program

- target my_program ist abhaengig von den Objektdateien classA.o und classB.o
- g++ Linker 

### options:
-		-c			Kompilieren ohne zu linken. 
-		-g 			debugging infos erzeugen
-		-o file     object-file name 

http://www.gnu.org/software/make/

http://mrbook.org/blog/tutorials/make/

http://de.wikipedia.org/wiki/Make

http://www.sethi.org/classes/cet375/lab_notes/lab_04_makefile_and_compilation.html

# Ablauf

### Fetch the current scripts and JavaYacas sources

    cd yacas

    ant clean
(rm -r build)
(rm -r dist)
(rm JavaYacas/CVersion.java)

    cd JavaYacas
    svn update
    cd ../scripts
    svn update
  
**Versionsnummer** (svn) **notieren**. Git commit Nr. von Webseite holen, oder:

    svn propget git-commit --revprop -r HEAD
    

### Rebuild the jar

*build.xml*: Version (svn commit Nr.) **anpassen**!


Kontrollieren, dass in scripts diese Dateien gelöscht sind: *Makefile.am*, *maketest*

Kontrollieren, dass in JavaYacas diese Dateien gelöscht sind:
alle ausser CVersion.java.in (also auch CVersion.java löschen, wird durch ant neu generiert)

Kontrollieren, dass in JavaYacas das Verzeichnis gelöscht ist: *lib*

    cd ..

    ant
(äquivalent zu ant jar)

### Create the corresponding source archive

    cd ..
in dotar allenfalls die Versionsnummer **anpassen**!

    ./dotar
(oder
tar -czf dist/yacas-1.3.6+.tar.gz --exclude=.svn yacas/scripts yacas/JavaYacas yacas/build.xml yacas/COPYING
)

### Test

    cd dist
    rlwrap java -jar yacas.jar


# GitHub

### Commit

    git status

Version (svn commit Nr. / git commit nr) **anpassen**!

    git commit -a -m 'yacas r3216 (ba2a4f8)'
    
    git push origin master


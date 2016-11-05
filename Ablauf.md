# Ablauf

### Fetch the current scripts and jyacas sources

    cd yacas

    ant clean
(rm -r build)
(rm -r dist)
(rm jyacas/CVersion.java)

    cd jyacas
    svn update
    cd ../scripts
    svn update
  
**Versionsnummer** (svn) **notieren**. Git commit Nr. von Webseite holen, oder:

    svn propget git-commit --revprop -r HEAD
    

### Rebuild the jar

*build.xml*: Version (svn commit Nr.) **anpassen**!


Kontrollieren, dass in jyacas diese Dateien gelöscht sind:
alle ausser CVersion.java.in
(übrigens net/sf/yacas/CVersion.java wird durch ant neu generiert)

Kontrollieren, dass in jyacas das Verzeichnis gelöscht ist: *lib*

    cd ..

    ant
(äquivalent zu ant jar)

### Create the corresponding source archive

    cd ..
in dotar allenfalls die Versionsnummer **anpassen**!

    ./dotar
(oder
tar -czf dist/yacas-1.6.0.tar.gz --exclude=.svn yacas/scripts yacas/jyacas yacas/build.xml yacas/COPYING
)

### Test

    cd dist
    rlwrap java -jar yacas.jar


# GitHub

### Commit

    git status

Version (git commit nr) **anpassen**!

    git commit -a -m 'yacas 1.6.0 ()'
    
    git push origin master


title: Ruby e Ruby on Rails - Lezione 1
author: Jury Ghidinelli
copyright: Copyright © 2016 Archimedia s.r.l.

# Reperire la documentazione

  - [http://docs.ruby-doc.com/docs/ProgrammingRuby/](http://docs.ruby-doc.com/docs/ProgrammingRuby/)
  - [http://ruby-doc.org/](http://ruby-doc.org/)
  - [http://ruby-doc.org/core-2.3.1/](http://ruby-doc.org/core-2.3.1/)
  - [http://ruby-doc.org/stdlib-2.3.1/](http://ruby-doc.org/stdlib-2.3.1/)
  - [https://rubygems.org/](https://rubygems.org/)
  - [https://github.com/](https://github.com/)


# Linguaggi interpretati e compilati

Il linguaggio di programmazione è generalmente un file di testo con contenuto il codice sorgente che descrive l'algoritmo.

Per essere eseguito il codice sorgente deve essere tradotto in linguaggio macchina; la traduzione da codice sorgente a
linguaggio macchina può avvenire in due modi, con la compilazione del codice sorgente o con l'interpretazione del codice sorgente.

<% left do %>

### Linguaggi interpretati

L'interprete è il programma che si occupa di interpretare il codice sorgente per l'esecuzione

I linguaggi internpretati non hanno bisogno di compilazione, vengono eseguiti direttamente con il codice sorgente

Uno dei più grandi vantaggi è la possibilità di eseguire lo stesso codice sorgente su piattaforme diverse

Come svantaggio abbiamo una minor velocità di esecuzione rispetto ai programmi compilati

Esempio di linguaggi interpretati sono: Ruby, Perl, Php.

<% end %>

<% right do %>

### Linguaggi compilati

La compilazione è il processo con cui il compilatore (il traduttore) traduce da codice sorgente a linguaggio macchina.

Tra i vantaggi c'è la velocità di esecuzione del codice compilato, ottimizzato per l'hardware compilatore

Tra gli svantaggi c'è il fatto che un programma deve essere espressamente compilato per ogni hardware specifico.

Esempio di linguaggi compilati sono: C, C++

<% end %>

Esistono infine linguaggi di programmazione "ibridi", ovvero che vengono si compilati ma non in linguaggio macchina (ma in bytecode/P-code)
che rendono l'esecuzione indipendente dalla piattaforma: Java, .NET


# Cenni di programmazione orientata agli oggetti

La programmazione orientata agli oggetti è un [paradigma di programmazione](https://it.wikipedia.org/wiki/Paradigma_di_programmazione)
che permette di definire degli oggetti software in grado di interagire tra di loro.<br/>
Vantaggi:
* descrizione naturale degli oggeti del software rispetto al mondo reale
* più facile gestione e manutenzione di progetti di grandi dimensioni
* organizzazione del codice in classi favorisce la modularità ed il riuso

Un linguaggio di programmazione è definibile ad oggetti se implementa i seguenti meccanismi:
* incapsulamento: separazione dell'interfaccia della classe rispetto all'implenentazione della stessa
* ereditarietà: definizione di classi a partire da altre classi
* polimorfismo: utilizzo di da parte di un client di oggetti di classi diverse ma dotati delle stesse interfaccie

### Classe

La classe è la definizione di un tipo di dato (integer, string, hash, array, decimal, float) e permette la creazione di oggetti con caratteristiche definite
dalla classe stessa. <br/>
La classe è composta da:
* attributi (proprietà): variabili, costanti della classe
* metodi: procedure e funzioni che operano sugli attributi

la classe  in Ruby:<br/>

```
# commentiamo la classe Car
class Car

end
```

### Oggetto

L'oggetto è __l'istanza di una classe__, fornisce tutti i metodi e gli attributi ed agisce come fornitore di messaggi alla classe.

Inviare un messaggio ad un oggetto significa invocare un metodo sull'oggetto.

La parola chiave per indicare l'istanza di un oggetto in Ruby è `self`

Creare un'istanza significa creare un nuovo oggetto di una certa classe in Ruby:<br/>

```
alfa_romeo = Car.new
# alfa_romeo è l'istanza della classe Car
```

# Cenni di programmazione funzionale

La programmazione funzionale si basa sul concetto matematico di funzione (non informatico), cioè la funzione matematica, non esegue calcoli
ma si limita a mappare dei valori.

Rispetto alla programmazione ad oggetti, la programazione funzionale non ragiona appunto come oggetto ma come funzione, di conseguenza
non esiste il concetto di variabile o di stato del programma in un dato momento.

Ruby non è un linguaggio funzionale, ma adotta alcune tecniche relative alla programmazione funzionale (Proc e lambda )

```
foo = [1,2,3,4,5]
foo.map({|bar| puts bar + 1})
```
La funzione `map` è una funzione che ha come parametro un'altra funzione. In Ruby il codice racchiuso tra `{}` è una funzione anonima.

La traduzione della funzione map è _per ogni elemento dell'array, stampa il valore dell'elemento aggiungendo 1_

Questo tipo di funzioni si chiamano _high-order functions_

Ruby per quanto riguarda la programmazione funzionale implementa anche le "closures" attraverso le funzioni anonime Proc e lambda

Esempio di implementazione in Ruby

```
def moltiplicazione(moltiplicatore)
    return lambda {|n| n*moltiplicatore }
end

per3 = moltiplicazione(3)
per8 = moltiplicazione(8)

puts per3.call(3)               #=> 9
puts per3.call(per8.call(2))    #=> 48
```

# Ruby, Rails, Ruby On Rails

Ruby è un linguaggio di scripting interpretato completamente ad oggetti nato nel 1995. Grazie al framework MVC Ruby on Rails
ha avuto negli ultimi anni una rapida diffusione a livello mondiale.

Ruby prende spunto da linguaggi preesistenti :

* Smaltalk:  quanto riguarda lo sviluppo orientato agli oggetti
* Lisp: per le sue caratteristiche di __programmazione funzionale__
* Perl: per sintassi ed espressioni

Ruby si è diffuso enormemente negli ultimi anni anche per la sua versatilità. Oltre al framework per il web Ruby on Rails,
ci sono anche numerosi progetti che si basano su linguaggio Ruby:

* Ruby on Rails: framework MVC per il web
* Metasploit: framework per la sicurezza informatica
* Adeharsion: framework applicazioni voice
* sonic-pi: sintetizzatore musicale da scripting
* chef: deployer per cloud e sistemi server
* slideshow: queste slide sono fatte con slideshow
* Vagrant
* Chef

numerosissimi inoltre sono i progetti web sviluppati in Ruby e Ruby on Rails:

* Solidus/Spree: framework per il commercio elettronico
* Shopify
* Airbnb
* Stripe
* Twitter
* Github
* Groupon


# Setup di Ruby su Linux

L'interprete Ruby è disponibile per i maggiori sistemi operativi: Linux, Windows, MacOS, ed altri.

Per l'installazione in ambiente Linux generalmente utilizziamo [R.V.M.](https://rvm.io/)

Rvm è un'utility command line che permette di gestire contemporaneamente più ambienti diversi di versioni diverse
di Ruby ed il relativo set di Gemme.

per l'installazione:

Da utente NON root eseguire `$ \curl -sSL https://get.rvm.io | sudo bash -s stable`

Aggiungere gli utenti che devono usare rvm al gruppo rvm che ha creato l'installazione.

A questo punto abbiamo installato RVM, di conseguenza possiamo:

avere un elenco di versioni di Ruby installate `rvm list`, oppure `rvm list known` avere un elenco di versioni di Ruby installabili ed infine `rvm install 2.3`
installare una versione di Ruby oppure utilizzare una certa versione di Ruby installata `rvm use 2.3`


# Interactive Ruby Shell (irb)

Con l'installazione di Ruby abbiamo a disposizione la shell interattiva di Ruby. Con la shell interattiva abbiamo a disposizione un ambiente
dove possiamo scrivere comandi ruby.

```
$ irb
2.3.0:001>puts "Ciao Ruby"
Ciao Ruby
2.3.0:002>
```

attraverso irb è possibile eseguire qualsiasi comando Ruby.


# Ruby Gems, Bundle

__Ruby Gems__

Ruby gems è il package manager di Ruby. Per gestore di pacchetti si intende il software che permette di installare, aggiornare, gestire i pacchetti
Ruby (gems - gemme).

Il repository ufficiale delle gemme di Ruby è [Ruby Gems](https://www.rubygems.org/).

Le gemme sono di fatto delle librerie che vengono installate a livello di sistema o a livello applicativo.

Le gemme sono versionate, quindi può essere indicata precisamente la versione della gemma da utilizzare nel sistema

I comandi  principali sono:

* gem list
* gem install <nome della gemma> --version
* gem update <nome della gemma>
* gem help commands

Il comando gem viene installato con l'installazione di ruby

__Bundle__

[Bundler](http://bundler.io) è un gestore di dipendenze appplicative. Per gestore di dipendenze applicative si intende un "file di configurazione"
(Gemfile e Gemfile.lock) dove vengono gestite le gemme necessarie al progetto che si sta sviluppando con la relativa versione.

Bundler è a sua volta una gemma, quindi per l'installazione si deve usare gem : `gem install bundler`

Per inizializzare il progetto Ruby all'utilizzo di bundler : `bundler init` che crea il file Gemfile.

Il file Gemfile è il file di configurazione di qualsiasi applicazione Ruby (più avanti vedremo quindi anche di Rails) dove vengono elencate le gemme
necessarie all'applicazione.

Editando il file Gemfile:

```
source "https://rubygems.org"
# gem "rails"
```

Proviamo ad installare la gemma [Colorize](https://rubygems.org/gems/colorize)

Modificare il file aggiungendo la gemma  `gem "colorize"` e togliendo la gemma rails (commentata)

Eseguiamo il comando `bundle install`

Proviamo ad usare la gemma con irb

```
irb

>require 'colorize'
>String.colors      
>puts "testo colorato".colorize(:red)
>puts "This is red on blue and underline".colorize(:red).on_blue.underline
```
Oltre al file Gemfile, il comando bundle installa crea anche il file Gemfile.lock che descrive l'elenco delle gemme necessarie al progetto
con la relativa versione


# Strumenti di sviluppo

__Editor__

Per sviluppare in Ruby è sufficiente un editor di testo qualsiasi di base (vi,nano)

Ci sono editor un pò più evoluti e graficamente più gradevoli per esempio: [Atom](https://atom.io/)

Ci sono IDE molto evoluti e completi

* [Ruby Mine](https://www.jetbrains.com/ruby/)
* [Rad Rails](http://www.aptana.com/products/radrails.html)

__Versionamento del codice (git)__

Git è un sistema di versionamento dei progetti software.

Git è utile per piccoli progetti, necessario per gruppi di sviluppatori, indispendabile per grandi progetti

Git si compone di un server (dove viene mantenuto il repository del sorgente) e di un client (che serve per gestire il progetto)

Una guida introduttiva e veloce a git [http://rogerdudler.github.io/git-guide/index.it.html](http://rogerdudler.github.io/git-guide/index.it.html)


# Q&A

* Cosa è un linguaggio interpretato?
* In cosa può essermi d'aiuto Ruby?
* Come installo Ruby?
* Ruby e JAVA => RJB (collegamento AS/400 DB2)

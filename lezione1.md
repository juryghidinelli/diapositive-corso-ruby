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

numerosissimi infine sono i progetti web sviluppati in Ruby e Ruby on Rails:

* Solidus/Spree: framework per il commercio elettronico
* Shopify
* Airbnb
* Stripe
* Twitter
* github
* groupon


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


# Gems, Bundle





[http://bundler.io/](http://bundler.io/)

# Q&A

Domande e risposte

title: Ruby e Ruby on Rails - Lezione 3
author: Jury Ghidinelli
copyright: Copyright © 2016 Archimedia s.r.l.

# La classe

In Ruby ogni cosa è un oggetto . La programmazione orientata agli oggetti modella e descrive
in un modo più simile alla realtà un software. Infatti un oggetto in Ruby ha determinate
caratteristiche e proprietà come potrebbe averlo un'automobile nel mondo reale (marca, modello)
e fa determinate funzioni (si accende, sterza a destra, sterza a sinistra).

In Ruby quindi per creare un oggetto è necessario definire un __Classe__ al quale interno
sono definiti metodi e attributi; praticamente una classe è la definizione di un oggetto
(la classe Car è la definizioe dell'oggetto alfa_romeo o ferrari)

La definizione delle classi in Ruby è descritta in questo modo:

```
def Car
  def initialize #il metodo initialize viene eseguito nel momento in cui viene creata la classe
    puts "Sono un'automobile"
  end
end

automobile = Car.new #creazione della classe
Sono un'automobile #output a console del risultato

```

`initialize` è ile metodo costruttore della classe e viene invocato al momento
della creazione dell'oggetto della classe


# L'oggetto: istanza di una classe

L'oggetto è l'istanza di una classe, e viene creata nel momento in cui si instanzia una nuova classe.


```
automobile = Car.new(10,5)
```

la variabile automobile è l'istanza della classe Car



# Accessors: getters e setters

Gli attributi accessori sono delle "scorciatoie" alla creazione di metodi setter e getter.

```
attr_accessor :litri_carburante, :posti_a_sedere #imposta il

#attr_reader :litri_carburante #attributo in sola lettura
#attr_writer :litri_carburante #attributo in sola scrittura

#attr :litri_carburante, true #attributo che può essere anche scrivibile (true)
#attr :litri_carburante, true #attributo che può essere anche scrivibile (true)
```

# Metodi di classe e metodi di istanza

Esempio della classe Car con implementazione metodo di classe
``calcolo_litri_al_km`` e metodo di istanza ``litri_al_km``


```
def Car
  attr_accessor :litri_carburante, :posti_a_sedere, :km_percorsi  

  def initialize(litri_carburante, posti_a_sedere)
    self.litri_carburante = litri_carburante
    self.posti_a_sedere = posti_a_sedere
  end

  def Car.calcolo_litri_al_km(litri,km)
    (litri_carburante/km_percorsi).to_i
  end

  def litri_al_km
    Car.calcolo_litri_al_km(litri,km)
  end
end

automobile = Car.new(10,5)
puts automobile.litri_carburante
puts automobile.posti_a_sedere
puts litri_al_km
puts Car.calcolo_litri_al_km(50,400)

```


# Relazioni tra classi

```
def Car
  attr_accessor :litri_carburante, :posti_a_sedere, :km_percorsi
  attr_accessor :passeggeri

  def initialize(litri_carburante, posti_a_sedere)
    self.litri_carburante = litri_carburante
    self.posti_a_sedere = posti_a_sedere
    self.passeggeri = []
  end

  def Car.calcolo_litri_al_km(litri,km)
    (litri_carburante/km_percorsi).to_i
  end

  def litri_al_km
    Car.calcolo_litri_al_km(litri,km)
  end

  def stampa_passeggeri
    self.passeggeri.each do |p|
      puts p.nome_cognome
    end
  end

end


def Passenger
  attr_accessor :nome, :cognome

  def initialize(nome,cognome)
    self.nome = nome
    self.cognome = cognome
  end

  def nome_cognome
    "#{nome} #{cognome}"
  end

end

```

# Oggetti unici

Un esempio di un oggetto unico implementato con una classe è il seguente,

```
class Logger

  private_class_method :new #si ridefinisce medoto new privato

  @@logger = nil
  def Logger.create
    @@logger = new unless @@logger
    @@logger
  end
end

puts Logger.create.id
puts Logger.create.id
puts Logger.create.id

```

``@@logger`` è una variabile di classe vuol dire che è comune per tutte le classi (non solo le istanze)

In particolare questo esempio è l'implementazione di un singleton.


# Ereditarietà

L'ereditarietà è un meccanismo della programmazione orientata agli oggetti che partendo da una classe
iniziale di base, raffine a specializza una sottoclasse.
Esempio:

```
class Vehicle
  attr_accessor :ruote

  def initialize(ruote)
    self.ruote=ruote
  end

end


class Car < Vehicle
  attr_accessor :potenza, :tipo_carburante

  def initialize(potenza, tipo_carburante, ruote)
    super(ruote)
    self.potenza = potenza
    self.tipo_carburante = tipo_carburante
  end
end

class Bicycle < Vehicle

  def initialize(ruote)
    super(ruote)
  end
end


car = Car.new(15, "Benzina", 4)
bicycle = Bicycle.new(2)


```

Ruby è un linguaggio ad ereditarietà singola (una classe può ereditare da una
sola classe e non da più classi).


# Override di un metodo

```
class Vehicle
  attr_accessor :ruote

  def initialize(ruote)
    self.ruote=ruote
  end

  def tipo_veicolo
    "Veicolo Generico"
  end

end


class Car < Vehicle
  attr_accessor :potenza, :tipo_carburante

  def initialize(potenza, tipo_carburante, ruote)
    super(ruote)
    self.potenza = potenza
    self.tipo_carburante = tipo_carburante
  end

  def tipo_veicolo
    "Automobile"
  end
end
```


# Metodi polimorfici

Il poliformismo in Ruby viene gestito attraverso la tecnica [Duck Typing](https://it.wikipedia.org/wiki/Duck_typing)


```
class Vehicle
  attr_accessor :ruote

  def initialize(ruote)
    self.ruote=ruote
  end

  def tipo_veicolo
    "Veicolo Generico"
  end

  def to_s
    "sono un veicolo"
  end

end


class Car < Vehicle
  attr_accessor :potenza, :tipo_carburante

  def initialize(potenza, tipo_carburante, ruote)
    super(ruote)
    self.potenza = potenza
    self.tipo_carburante = tipo_carburante
  end

  def tipo_veicolo
    "Automobile"
  end

  def to_s
    "sono un automobile"
  end
end

class Animal
  attr_accessor :classificazione

  def initialize(classificazione)
    self.classificazione = classificazione
  end

  def to_s
    "io sono un animale #{classificazione}"
  end
end

puts Animal.new.to_s
puts Car.new.to_s
puts Vehicle.new.to_s

```




# Q&A

Domande e risposte

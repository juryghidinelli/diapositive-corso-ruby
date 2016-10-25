title: Ruby e Ruby on Rails - Lezione 2
author: Jury Ghidinelli
copyright: Copyright © 2016 Archimedia s.r.l.

# Creare programmi in Ruby

Creazione del file script.rb

`bundle init` che crea il file Gemfile

editare il file con l'editor o l'ide

# Stringhe

Le stringhe sono sequenze di caratteri racchuse tra "" oppure ''. Le stringhe
sono classi di tipo String. Alla sequenza dei caratteri compresi nelle stringhe
si può accedere con i caratteri [] come se fosse un array.

```
stringa = "Ciao Ruby"
stringa.class
stringa[0]
stringa[0].chr
stringa[0..3]
stringa[0...3] #estremo escluso
stringa[0,2] #lunghezza 4
stringa[-6..-1] #si parte dal fondo
stringa[4]="prova"
```

```
"Stringa 1" * 2

"Stringa 1" + "Stringa 2"
```

Metodi legati alla classe stringa

```
"stringa".capitalize
"stringa".upcase
"stringa".downcase
"StringA".swapcase #Inversione di maiuscole e minuscole
"stringa".chop #elimina l'ultimo carattere dalla stringa
"stringa,".chomp(",") #elimina l'ultimo carattere separatore della stringa
"stringa, prova, dest".gsub(/ov/,"*")
"stringa, prova, dest".sub(/ov/,"*")
"uno,due,tre".split(",")
"uno,due,tre".tr("due","due!!!")
"stringa".center(20)
"stringa".ljust(20)
"     stringa    ".lstrip
"     stringa    ".rstrip
"     stringa    ".strip
```

# Numeri e tipi numerici

I tipi di dato numerici in Ruby sono Fixnum, Bignum, Float


```
numero_fixnum = 4
numero_fixnum.class
numero_bignum = 21239399232991233323232323232
numero_bignum.class
numero_float = 3.2
numero_float.class

#Provare a cercare nella documentazione di ruby la differenza tra Fixnum e Bignum

#Operatori aritmetici +, -, *, /, %

-1977.abs #valore assoluta
100.size  #dimensione in byte

2.to_f
2.3233.to_i
"2.3".to_f
"2.4".to_i

3.class.superclass.superclass.superclass.superclass

```

In ruby qualsiasi classe alla fine è un oggetto quindi:
```
"prova prova due".object_id #id dell'oggetto stringa in memoria
"prova prova due".object_id

:symbolo.object_id #l'object id di un simbolo è sempre lo stesso

```

Il symbol `:abc` oppure `"prova".to_sym` è un modo per dire "qualche cosa che si chiama così"


# Metodi e loro chiamata

I metodi di classe in ruby possono essere immplementati nei seguenti modi

```
def method_name [( [arg [= default]]...[, * arg [, &expr ]])]

end
```

Esempio:

```
def method_name
def method_name (var1, var2)
def method_name (var1=value1, var2=value2)

return
return 12
return 1,2,3 #ritorna 3 variabili

def test
  return 1,2,3
end

a,b,c = test

```

```
def prova(*test)
  puts test.length
  puts test.inspect
end

prova("prvoa","test","cinque")

```

__Metodi di classe__

```
class Classe
  def metodo_di_istanza
  end

  def Classe.metodo_di_classe
  end

  def self.metodo_di_classe
  end

end
```

# Date e calcoli sulle date

I tipi di variabili per la gestione di date sono Date, DateTime, Time

[https://ruby-doc.org/stdlib-2.3.1/libdoc/date/rdoc/Date.html](https://ruby-doc.org/stdlib-2.3.1/libdoc/date/rdoc/Date.html)



# Array

Un array è una lista di oggetti non necessariamente dello stesso tipo.

```
arr = Array.new

arr = []

arr = [1, 2, "abc", "prova"]

arr = Array.new(6)

arr = Array.new(2,"prova")

arr[0]
arr[2]

arr = [1, 2, 3, 4, 5]
arr[1,2]

arr.join(",")



```

[https://ruby-doc.org/core-2.2.0/Array.html](https://ruby-doc.org/core-2.2.0/Array.html)


# Blocchi

Un blocco è una porzione di codice compresa tra parole chiave `do  end` e `{}`

```
stringa = "Stringa di prova"

stringa.each_byte {|c| puts c.chr}

arr.each do |a|
  puts a
end

arr = [1, 2, 3, 4, 5]

arr.each_with_index do |a,index|
  arr[index]==a
end

```

I blocchi possono essere chiamati all'interno di un metodo, questa metodologia è utilizzata parecchio
in software scritti in Ruby.

```
def metodo
    puts "stampo nel metodo"
    yield
end

metodo {
  puts "Stampon nel blocco"
}

```

la parola chiave `yield` esegue di fatto il codice contenuto nel blocco passato al metodo

```
def metodo
    yield
    puts "stampo nel metodo"
    yield

    yield("testo")
end

metodo { |valore|
  puts "Stampon nel blocco il valore #{valore}"
}

metodo do |valore|
  puts "Stampon nel blocco il valore #{valore}"
end

```


# Test di una condizione: if ... then Unless

```
def test(n=1)
  if n == 1 then
      puts "N = uno"
  elsif n == 2 then
      puts "N = due"
  else
      puts "N non vale ne uno ne due"
  end
end
```

All'opposto di if in ruby è presente Unless


```
def test(n=1)
  unless n > 10
    puts "N<=10"
  else
    puts "N>10"
  end
end
```


# Case

In molti casi potrebbe essere più comodo ed utile utilizzare il costrutto `case` invece che
if else. Per esempio:

```
case variabile
  when "valore1"
    puts "valore1"
  when "valore2"
    puts "valore2"
  when "valore3","valore4","valore5"
    puts "valore3 o 4 o 5"
  eslse
    puts "altri valori"
end

```

# classe range

https://ruby-doc.org/core-2.2.0/Range.html

I ranges rappresentao un set di dato con un inizio ed una fine, un intervallo di dati.
Per definire i range si possono descrivere in questo modo.

```
(0..2).to_a



```

# Cicli for

La gestione dei flussi con i clicli può avvenire con vari costrutti:
il ciclo for è uno dei costrutti.

```
for n in "a".."z"
  puts n
end

for n in "a".."z"
  puts n
end


```

# Cicli while

To be _completed_


# Modificatori while

To be _completed_


# Cicli until

To be _completed_

# Q&A

Domande e risposte

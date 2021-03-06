# ErlsomTutorial

Instalacja erlsom:

Pobrać:
```
https://github.com/willemdj/erlsom
https://github.com/kkcm/ErlsomTutorial
```
Krok po kroku:  
```
whereis(erlang)
cd ...
cd lib
mkdir erlsom-1.2.1
cd erlsom-1.2.1
mkdir ebin
mkdir src
```
pliki z pobranego repo skopiować do folderu erlsom-1.2.1/src  
odpalić make  
przenieść wszystkie pliki beam z erlsom-1.2.1/src/ebin do erlsom-1.2.1/ebin  
o powinno działać


SAX PARSE:

Wyświetlanie wszystkich eventów:
```
erlsom_tutorial:print_events("pollution_1.xml"). 
```

Przykładowe zastosowanie -> zliczenie wszystkich pomiarów (czyli wystąpień tagu measurement):
```
erlsom_tutorial:count_measurements("pollution.xml"). 
```
Reagowanie na dany event w odmienny sposób (funkcja callback(event, state)):
```
erlsom_tutorial:react_for_events("pollution_1.xml").
```
DOM PARSE:

Zamiana pliku xml na formę obiektową:
```
DOM = erlsom_tutorial:dom("pollution_1.xml").
```
Result = {ok, Element, Tail}  
Element = {Tag, Attributes, Content}  
Tag is a string  
Attributes = [{AttributeName, Value}]  
Content is a list of Elements and/or strings.  
  
Przykładowe sparsowanie danych:
```
erlsom_tutorial:parse_from_dom(DOM). 
```
DATA BINDER

Kompilowanie modelu oraz sparsowanie do struktury modelu opisanej w xsd:
```
BIND = erlsom_tutorial:bind("pollution_1.xml", "pollution.xsd").
```

Informacyjnie:
```
erlsom:compile_xsd_file(Model_file),
erlsom:scan(Xml, Model),
```

Stworzenie pliku nagłówkowego by móc odwoływać się do rekordów w module:
```
erlsom:write_xsd_hrl_file("pollution.xsd", "head.hrl"). 
```

Dodanie nagłówka:
```
-include("head.hrl").
```

Pokazanie listy sparsowanych pomiarów:
```
erlsom_tutorial:bind_test(BIND).
```

Pokazanie dostępu do pomiarów:
```
erlsom_tutorial:bind_test2(BIND).
```

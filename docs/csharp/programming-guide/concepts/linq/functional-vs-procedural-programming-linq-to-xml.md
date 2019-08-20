---
title: Programowanie funkcjonalne a Programowanie proceduralne (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594248"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Programowanie funkcjonalne a Programowanie proceduralne (LINQ to XML)C#()
Istnieją różne typy aplikacji XML:  
  
- Niektóre aplikacje pobierają źródłowe dokumenty XML i generują nowe dokumenty XML, które znajdują się w innym kształcie niż dokumenty źródłowe.  
  
- Niektóre aplikacje pobierają źródłowe dokumenty XML i generują dokumenty z wynikami całkowicie różnymi formularzami, takimi jak pliki tekstowe HTML lub CSV.  
  
- Niektóre aplikacje pobierają źródłowe dokumenty XML i wstawiają rekordy do bazy danych.  
  
- Niektóre aplikacje pobierają dane z innego źródła, takiego jak baza danych, i tworzy z niego dokumenty XML.  
  
 Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów funkcji, które programista XML musi zaimplementować.  
  
 W przypadku wszystkich typów aplikacji istnieją dwie podejścia z kontrastem, które może podjąć Deweloper:  
  
- Funkcjonalne konstruowanie przy użyciu podejścia deklaratywnego.  
  
- Modyfikowanie drzewa XML w pamięci przy użyciu kodu proceduralnego.  
  
 LINQ to XML obsługuje oba podejścia.  
  
 Korzystając z podejścia funkcjonalnego, należy napisać przekształcenia, które pobierają dokumenty źródłowe i generować zupełnie nowe dokumenty wynikowe z żądanym kształtem.  
  
 Podczas modyfikowania drzewa XML w miejscu należy napisać kod, który przechodzi przez węzły w drzewie XML w pamięci, wstawiając, usuwając i modyfikując węzły, w razie potrzeby.  
  
 Możesz użyć LINQ to XML z dowolnego podejścia. Używasz tych samych klas, a w niektórych przypadkach te same metody. Jednak struktura i cele dwóch metod są bardzo różne. Na przykład w różnych sytuacjach jedno lub inne podejście często ma lepszą wydajność i będzie używać więcej lub mniej pamięci. Ponadto jedno lub inne podejście będzie łatwiejsze do pisania i uzyskania bardziej możliwego do utrzymania kodu.  
  
 Aby wyświetlić dwa podejścia z kontrastem, zobacz [modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalna (LINQ to XML)C#(](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)).  
  
 Aby zapoznać się z samouczkiem dotyczącym pisania przekształceń funkcjonalnych, zobacz [czyste działania transformacji XMLC#()](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programowania LINQ to XML (C#)](./linq-to-xml-overview.md)

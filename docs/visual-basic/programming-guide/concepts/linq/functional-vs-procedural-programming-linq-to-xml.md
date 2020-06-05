---
title: Programowanie funkcjonalne a proceduralne (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
ms.openlocfilehash: 0b525f13298e7402369b890516434cec47e01542
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398438"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>Programowanie funkcjonalne a proceduralne (LINQ to XML) (Visual Basic)
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
  
 Aby wyświetlić dwa podejścia z kontrastem, zobacz [Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)](in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 Aby zapoznać się z samouczkiem dotyczącym pisania przekształceń funkcjonalnych, zobacz [czyste działania transformacji XML (Visual Basic)](pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ to XML (Visual Basic)](linq-to-xml-programming-overview.md)

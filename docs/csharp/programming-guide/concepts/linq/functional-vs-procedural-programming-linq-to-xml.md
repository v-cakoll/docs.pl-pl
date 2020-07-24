---
title: Programowanie funkcjonalne a proceduralne (LINQ to XML) (C#)
description: W przypadku przetwarzania XML LINQ to XML obsługuje zarówno modyfikacje drzewa XML w pamięci, jak i konstrukcja funkcjonalna, która używa podejścia deklaracyjnego.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e19f9311c56f4fe2c5e7e5f228aca6c03c6fe04d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103651"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Programowanie funkcjonalne a proceduralne (LINQ to XML) (C#)
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
  
 Aby wyświetlić dwa podejścia z kontrastem, zobacz [Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Aby zapoznać się z samouczkiem dotyczącym pisania przekształceń funkcjonalnych, zobacz [czyste działania transformacji XML (C#)](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ to XML (C#)](./linq-to-xml-overview.md)

---
title: Programowanie funkcjonalne a programowanie proceduralne (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594248"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Programowanie funkcjonalne a programowanie proceduralne (LINQ do XML) (C#)
Istnieją różne rodzaje aplikacji XML:  
  
- Niektóre aplikacje przyjmują źródłowe dokumenty XML i tworzą nowe dokumenty XML, które mają inny kształt niż dokumenty źródłowe.  
  
- Niektóre aplikacje przyjmują źródłowe dokumenty XML i tworzą dokumenty wyników w zupełnie innej formie, takiej jak pliki tekstowe HTML lub CSV.  
  
- Niektóre aplikacje przyjmują źródłowe dokumenty XML i wstawiają rekordy do bazy danych.  
  
- Niektóre aplikacje przyjmują dane z innego źródła, takiego jak baza danych, i tworzą z niej dokumenty XML.  
  
 Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów funkcji, które programista XML musi zaimplementować.  
  
 W przypadku wszystkich tych typów aplikacji istnieją dwa kontrastujące podejścia, które deweloper może podjąć:  
  
- Funkcjonalna konstrukcja przy użyciu podejścia deklaratywnego.  
  
- Modyfikacja drzewa XML w pamięci przy użyciu kodu proceduralnego.  
  
 LINQ do XML obsługuje oba podejścia.  
  
 Korzystając z podejścia funkcjonalnego, piszesz przekształcenia, które przyjmują dokumenty źródłowe i generują całkowicie nowe dokumenty wynikowe o pożądanym kształcie.  
  
 Podczas modyfikowania drzewa XML w miejscu, należy napisać kod, który przechodzi i porusza się po węzłach w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów w razie potrzeby.  
  
 Linq można użyć do XML z obu podejść. Używasz tych samych klas, a w niektórych przypadkach te same metody. Jednak struktura i cele obu podejść są bardzo różne. Na przykład w różnych sytuacjach jedno lub drugie podejście często mają lepszą wydajność i używać więcej lub mniej pamięci. Ponadto jedno lub drugie podejście będzie łatwiejsze do napisania i przynieść więcej kodu do konserwacji.  
  
 Aby zobaczyć dwa podejścia skontrastowane, zobacz [Modyfikacja drzewa XML w pamięci vs. Konstrukcja funkcjonalna (LINQ do XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Aby zapoznać się z samouczkiem na temat pisania przekształceń funkcjonalnych, zobacz [Czyste transformacje funkcjonalne języka XML (C#).](./introduction-to-pure-functional-transformations.md)  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie programowania LINQ do XML (C#)](./linq-to-xml-overview.md)

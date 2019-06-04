---
title: Programowanie funkcjonalne a Proceduralne (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 1f713e54cefed5b1fcf8c29cd88aa7587a737327
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486949"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Programowanie funkcjonalne a Proceduralne (LINQ to XML) (C#)
Istnieją różne rodzaje aplikacji XML:  
  
- Niektóre aplikacje źródła dokumentów XML i tworzące nowe dokumenty XML znajdujących się w innym kształcie niż dokumentów źródłowych.  
  
- Niektóre aplikacje źródła dokumentów XML i tworzące dokumenty wynik w postaci zupełnie innego, takich jak pliki tekst HTML lub CSV.  
  
- Niektóre aplikacje zająć dokumentów XML źródła i wstawiania rekordów do bazy danych.  
  
- Niektóre aplikacje pobierają dane z innego źródła, takich jak bazy danych i tworzenie dokumentów XML z niego.  
  
 Nie są to wszystkie typy aplikacji XML, ale są to reprezentatywny zestaw typów, funkcji, który musi zaimplementować programista XML.  
  
 W przypadku wszystkich tych rodzajów aplikacji istnieją dwie metody kontrastujące deweloper może potrwać:  
  
- Konstrukcja funkcjonalna przy użyciu podejścia deklaratywnego.  
  
- Za pomocą kod proceduralny modyfikowanie drzewa XML w pamięci.  
  
 LINQ to XML obsługuje oba podejścia.  
  
 Korzystając z podejścia funkcjonalności, można napisać przekształcenia używające dokumentów źródłowych i generować zupełnie nowe dokumenty wyniku żądanego kształtu.  
  
 Podczas modyfikowania drzewa XML w miejscu, pisania kodu, który przechodzi przez i przechodzi przez węzły w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów, zgodnie z potrzebami.  
  
 Za pomocą LINQ to XML każda z tych metod. Użyj tych samych klas, a w niektórych przypadkach te same metody. Struktury i celów dwie metody są jednak bardzo różnią się. Na przykład w różnych sytuacjach co najmniej inne podejście będzie często mają lepszą wydajność i używać więcej lub mniej pamięci. Ponadto co najmniej inne podejście będzie można łatwiej napisać i uzyskanie więcej kodu łatwego w utrzymaniu.  
  
 Aby wyświetlić dwa podejścia porównanie, zobacz [vs modyfikowanie drzewa XML w pamięci. Konstrukcja funkcjonalna (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Samouczek na temat pisania przekształceń funkcjonalnych, zobacz [czystego funkcjonalności przekształcenia XML (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML — przegląd programowania (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)

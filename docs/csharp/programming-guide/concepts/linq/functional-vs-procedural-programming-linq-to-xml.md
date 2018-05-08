---
title: Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 16d78e967fd5379940ac93c82e3bb59c60941e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)
Istnieją różne typy aplikacji XML:  
  
-   Niektóre aplikacje zająć dokumentów XML źródła i utworzyć nowe dokumenty XML, znajdujących się w kształcie innego niż dokumenty źródła.  
  
-   Niektóre aplikacje zająć dokumentów XML źródła i tworzenie dokumentów wynik w postaci zupełnie innego, takich jak pliki tekstowe HTML lub CSV.  
  
-   Niektóre aplikacje zająć dokumentów XML źródła i Wstaw rekordy w bazie danych.  
  
-   Niektóre aplikacje pobierają dane z innego źródła, na przykład w bazie danych i tworzenie dokumentów XML z niego.  
  
 Nie są one wszystkich typów aplikacji XML, ale są one reprezentatywny zestaw typów funkcji, aby zaimplementować programisty XML.  
  
 Wszystkie aplikacje tego typu istnieją dwie metody kontrastujące deweloper może zająć:  
  
-   Budowa funkcjonalności deklaratywne podejście.  
  
-   Przy użyciu kodu procedurach modyfikacji drzewa XML w pamięci.  
  
 LINQ do XML obsługuje obu podejść.  
  
 Korzystając z funkcjonalności podejście, należy napisać przekształcenia, które podejmują dokumentów źródłowych i generowanie całkowicie nowych dokumentów wynik żądanego kształtu.  
  
 Podczas modyfikowania drzewo XML w miejscu, pisania kodu, który jest przesyłany i nawiguje węzłów w drzewie XML w pamięci, wstawianie, usuwanie i modyfikowanie węzłów w razie potrzeby.  
  
 LINQ do XML można użyć obu metod. Użyj tej samej klasy, a w niektórych przypadkach te same metody. Jednak struktury i celów dwa podejścia są bardzo różnią się. Na przykład w różnych sytuacjach co najmniej inne podejścia będzie często mają lepszą wydajność i użyj bardziej lub mniej pamięci. Ponadto jedna lub innej metody będzie łatwiejszy do zapisu i uzyskanie kodu za więcej.  
  
 Aby wyświetlić dwa podejścia odróżniające, zobacz [vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 Samouczek dotyczący zapisywania przekształcenia funkcjonalności, zobacz [czysty funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML-przegląd programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

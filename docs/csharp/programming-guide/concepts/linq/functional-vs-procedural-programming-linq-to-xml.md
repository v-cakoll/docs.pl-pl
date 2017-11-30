---
title: "Vs funkcjonalności. Programowanie procedurach (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b6aa8ce45afdb68f7ff544b8c8f2f5e1e4a79533
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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

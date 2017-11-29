---
title: "Zastosowanie transformacji funkcjonalności (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7196e128a6d61b2b28e955a79561db2b9a5e51b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="applicability-of-functional-transformation-c"></a>Zastosowanie transformacji funkcjonalności (C#)
Czysty przekształcenia funkcjonalności mają zastosowanie w różnych sytuacjach.  
  
 Metoda przekształcania funkcjonalności doskonale nadaje się do badania i manipulowania nimi danych strukturalnych; w związku z tym mieścił się prawidłowo w technologii LINQ. Jednak funkcjonalności przekształcania ma znacznie większą zastosowania niż LINQ. Żaden proces, w którym głównego skoncentrować się na przekształcenia danych z jednej formy prawdopodobnie należy traktować jako potencjalny funkcjonalności transformacji.  
  
 Takie podejście ma zastosowanie do wiele problemów, które nie mogą być wyświetlane na pierwszy rzut oka jako kandydata. Używane w połączeniu ze LINQ, lub oddzielnie, przekształcania funkcjonalności należy rozważyć obejmujące następujące zagadnienia:  
  
-   Dokumenty opartych na języku XML. Poprawnie sformułowanych danych dowolnego dialekt XML może manipulować łatwo za pomocą przekształcania funkcjonalności. Aby uzyskać więcej informacji, zobacz [funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Inne formaty plików strukturalnych. Z plików Windows.ini do dokumentów w formacie zwykłego tekstu większość plików ma niektórych strukturę, która pozwala na analizy i przekształcania.  
  
-   Dane protokołów przesyłania strumieniowego. Dane kodowania i dekodowania danych z protokołów komunikacyjnych często może być reprezentowany przez prosty przekształcenia funkcjonalności.  
  
-   RDBMS i OODBMS dane. Relacyjnych i zorientowanym obiektowo baz danych, podobnie jak XML, są powszechnie używane dane strukturalne źródeł.  
  
-   Mathematic, statystyki i naukowe rozwiązania. Zwykle tych pól do manipulowania dużych zestawów danych ułatwiających użytkownika wizualizacji, szacowanie lub faktycznie Rozwiązywanie problemów z systemem innym niż prosta.  
  
 Zgodnie z opisem w [refaktoryzacji do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), przy użyciu czystych funkcji jest przykładem programowanie funkcjonalne. W dodatkowych do ich natychmiastowe korzyści przy użyciu czystych funkcji zapewnia przydatna w myślenia o problemach z punktu widzenia funkcjonalności transformacji. Takie podejście również może mieć istotny wpływ na projekt programu i klasy. Jest to szczególnie istotne, gdy problem pozwala na rozwiązanie przekształcania danych zgodnie z powyższym opisem.  
  
 Chociaż są one poza zakres tego samouczka, projekty, które wpływało funkcjonalności transformacja perspektywy mają tendencję do środka na procesy więcej niż na obiekty jako złośliwych użytkowników i wynikowa rozwiązania zwykle wdrażane jako serię na dużą skalę przekształcenia w odróżnieniu od zmian stanu pojedynczego obiektu.  
  
 Ponownie należy pamiętać, że C# obsługuje zarówno nadrzędnych, jak i funkcjonalności podejścia, dlatego najlepiej projekt aplikacji może uwzględniać oba elementy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności Pure (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
 [Refaktoryzacja do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

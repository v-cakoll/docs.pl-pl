---
title: Zastosowanie przekształcania funkcjonalnego (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: baa3866c8c2c148a3080522d7c02e28e9d0fd945
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47231536"
---
# <a name="applicability-of-functional-transformation-c"></a>Zastosowanie przekształcania funkcjonalnego (C#)
Czyste Przekształcanie funkcjonalne mają zastosowanie w wielu różnych sytuacjach.  
  
 Przekształcanie funkcjonalne podejście idealnie nadaje się do wykonywania zapytań i manipulowania ustrukturyzowanych danych; w związku z tym dopasowuje również przy użyciu technologii LINQ. Przekształcanie funkcjonalne ma jednak znacznie szerszy stosowania niż korzystanie z LINQ. Prawdopodobnie należy rozważyć żaden proces, której głównym celem jest przekształcania danych z jednego formularza jako kandydat do Przekształcanie funkcjonalne.  
  
 Takie podejście stosuje się do wielu problemów, które nie mogą być wyświetlane na pierwszy rzut oka jako kandydata. Używany w połączeniu z LINQ, lub oddzielnie, przekształcanie funkcjonalne mają być uwzględniane w następujących obszarach:  
  
-   Oparte na języku XML dokumenty. Poprawnie sformułowanych danych dowolnego dialekt XML można łatwo modyfikować poprzez przekształcanie funkcjonalne. Aby uzyskać więcej informacji, zobacz [funkcjonalności transformacji XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Inne formaty plików ze strukturą. Z plików Windows.ini do dokumentów w formacie zwykłego tekstu większość plików mają pewne struktury, która pozwala na analizy i przekształcania.  
  
-   Protokołów przesyłania strumieniowego danych. Dane kodowania i dekodowania danych z protokołów komunikacyjnych często może być reprezentowany przez proste przekształcanie funkcjonalne.  
  
-   System RDBMS i OODBMS dane. Relacyjne i zorientowane obiektowo baz danych, tak jak XML, są powszechnie używane danych strukturalnych źródeł.  
  
-   Rozwiązania matematycznych, statystyk i analizy. Te pola są zwykle do manipulowania dużych zestawów danych, aby pomóc użytkownikowi w wizualizacji, szacowanie lub faktycznie Rozwiązywanie problemów z nietrywialnymi.  
  
 Zgodnie z opisem w [Refaktoryzacja do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), przy użyciu czystej funkcji znajduje się przykład programowania funkcjonalnego. W dodatkowej ich natychmiastowe korzyści przy użyciu czystej funkcji udostępnia cenne doświadczenie w myśleć o problemach z punktu widzenia Przekształcanie funkcjonalne. Takie podejście może mieć istotny wpływ na program i klasy projektu. Jest to szczególnie istotne w przypadku, gdy problem jest przydatna w rozwiązaniu przekształcania danych zgodnie z powyższym opisem.  
  
 Mimo że są one poza zakres tego samouczka, projekty, które wpływało perspektywy Przekształcanie funkcjonalne mają tendencję do Centrum na więcej niż na obiekty aktorów procesy, a wynikowy rozwiązania zwykle można zaimplementować jako serię na dużą skalę przekształcenia, a nie pojedynczego obiektu po zmianie stanu.  
  
 Ponownie należy pamiętać, że języka C# obsługuje podejścia imperatywnego i funkcjonalności, dzięki czemu najlepsze projekt aplikacji może uwzględniać oba elementy.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przekształceń funkcjonalnych (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [Przekształcanie funkcjonalne kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)  
- [Refaktoryzacja do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

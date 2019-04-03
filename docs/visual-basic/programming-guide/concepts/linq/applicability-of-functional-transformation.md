---
title: Zastosowanie przekształcania funkcjonalnego (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: 7efeab82dafc284f64a950eb7f5e4a6ee3f2e73d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827617"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Zastosowanie przekształcania funkcjonalnego (Visual Basic)
Czyste Przekształcanie funkcjonalne mają zastosowanie w wielu różnych sytuacjach.  
  
 Przekształcanie funkcjonalne podejście idealnie nadaje się do wykonywania zapytań i manipulowania ustrukturyzowanych danych; w związku z tym dopasowuje również przy użyciu technologii LINQ. Przekształcanie funkcjonalne ma jednak znacznie szerszy stosowania niż korzystanie z LINQ. Prawdopodobnie należy rozważyć żaden proces, której głównym celem jest przekształcania danych z jednego formularza jako kandydat do Przekształcanie funkcjonalne.  
  
 Takie podejście stosuje się do wielu problemów, które nie mogą być wyświetlane na pierwszy rzut oka jako kandydata. Używany w połączeniu z LINQ, lub oddzielnie, przekształcanie funkcjonalne mają być uwzględniane w następujących obszarach:  
  
-   Oparte na języku XML dokumenty. Poprawnie sformułowanych danych dowolnego dialekt XML można łatwo modyfikować poprzez przekształcanie funkcjonalne. Aby uzyskać więcej informacji, zobacz [funkcjonalności transformacji XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
-   Inne formaty plików ze strukturą. Z plików Windows.ini do dokumentów w formacie zwykłego tekstu większość plików mają pewne struktury, która pozwala na analizy i przekształcania.  
  
-   Protokołów przesyłania strumieniowego danych. Dane kodowania i dekodowania danych z protokołów komunikacyjnych często może być reprezentowany przez proste przekształcanie funkcjonalne.  
  
-   System RDBMS i OODBMS dane. Relacyjne i zorientowane obiektowo baz danych, tak jak XML, są powszechnie używane danych strukturalnych źródeł.  
  
-   Rozwiązania matematycznych, statystyk i analizy. Te pola są zwykle do manipulowania dużych zestawów danych, aby pomóc użytkownikowi w wizualizacji, szacowanie lub faktycznie Rozwiązywanie problemów z nietrywialnymi.  
  
 Zgodnie z opisem w [Refaktoryzacja do czystych funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md), przy użyciu czystej funkcji znajduje się przykład programowania funkcjonalnego. W dodatkowej ich natychmiastowe korzyści przy użyciu czystej funkcji udostępnia cenne doświadczenie w myśleć o problemach z punktu widzenia Przekształcanie funkcjonalne. Takie podejście może mieć istotny wpływ na program i klasy projektu. Jest to szczególnie istotne w przypadku, gdy problem jest przydatna w rozwiązaniu przekształcania danych zgodnie z powyższym opisem.  
  
 Mimo że są one poza zakres tego samouczka, projekty, które wpływało perspektywy Przekształcanie funkcjonalne mają tendencję do Centrum na więcej niż na obiekty aktorów procesy, a wynikowy rozwiązania zwykle można zaimplementować jako serię na dużą skalę przekształcenia, a nie pojedynczego obiektu po zmianie stanu.  
  
 Ponownie należy pamiętać, że Visual Basic obsługuje podejścia imperatywnego i funkcjonalności, dzięki czemu najlepsze projekt aplikacji może uwzględniać oba elementy.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Przekształcanie funkcjonalne kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)
- [Refaktoryzacja do czystych funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

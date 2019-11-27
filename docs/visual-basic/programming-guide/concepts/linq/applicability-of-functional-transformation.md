---
title: Zastosowanie przekształcania funkcjonalnego
ms.date: 07/20/2015
ms.assetid: 3b74e134-e19b-44bc-8d06-e26c48305040
ms.openlocfilehash: 292201f4964142126d428939807cb20f354a7d2f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345770"
---
# <a name="applicability-of-functional-transformation-visual-basic"></a>Możliwość zastosowania transformacji funkcjonalnej (Visual Basic)
Czyste przekształcenia funkcjonalne mają zastosowanie w wielu różnych sytuacjach.  
  
 Podejście do transformacji funkcjonalnej idealnie nadaje się do wykonywania zapytań i manipulowania danymi strukturalnymi; w związku z tym dobrze pasuje do technologii LINQ. Jednak przekształcanie funkcjonalne ma znacznie szersze możliwości zastosowania niż w przypadku LINQ. Każdy proces, w którym głównym fokusem jest Przekształcanie danych z jednego formularza do innego powinien być uznany za kandydata na potrzeby transformacji funkcjonalnej.  
  
 Takie podejście dotyczy wielu problemów, które mogą nie pojawiać się w pierwszej kolejności jako kandydata. W połączeniu z lub niezależnie od LINQ, należy wziąć pod uwagę transformację funkcjonalną dla następujących obszarów:  
  
- Dokumenty oparte na języku XML. Poprawnie sformułowane dane dowolnego dialektu XML mogą być łatwo przetwarzane przez funkcję transformacji funkcjonalnej. Aby uzyskać więcej informacji, zobacz [funkcjonalne Przekształcanie kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md).  
  
- Inne formaty plików ze strukturą. Z plików Windows. ini do dokumentów w formacie zwykłego tekstu większość plików ma pewną strukturę, która pozwala na analizę i transformację.  
  
- Protokoły przesyłania strumieniowego danych. Kodowanie danych do i dekodowanie danych z protokołów komunikacyjnych może być często reprezentowane przez prostą transformację funkcjonalną.  
  
- Dane RDBMS i OODBMS. Relacyjne i zorientowane na obiekty bazy danych, podobnie jak XML, są szeroko używanymi źródłami danych.  
  
- Rozwiązania matematyczne, statystyczne i naukowe. Te pola umożliwiają manipulowanie dużymi zestawami danych w celu ułatwienia użytkownikowi wizualizacji, szacowania lub rozwiązywania nieuproszczonych problemów.  
  
 Zgodnie z opisem w temacie [Refaktoryzacja do czystych funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)korzystanie z funkcji czystych jest przykładem programowania funkcjonalnego. W celu uzyskania natychmiastowych korzyści korzystanie z funkcji czystych zapewnia cenne środowisko w przypadku problemów z perspektywą transformacji funkcjonalnej. Takie podejście może również mieć istotny wpływ na projekt programu i klasy. Jest to szczególnie prawdziwe, gdy problem nadaje się do rozwiązania do przekształcania danych, jak opisano powyżej.  
  
 Chociaż wykraczają poza zakres tego samouczka, projekty, na które ma wpływ perspektywa transformacji funkcjonalnej, przeprowadzą do centrów procesów więcej niż w przypadku obiektów jako aktorów, a uzyskane rozwiązanie ma być implementowane jako seria dużej skali przekształcenia, a nie zmiany stanu poszczególnych obiektów.  
  
 Należy pamiętać, że Visual Basic obsługuje zarówno podejścia bezwzględne, jak i funkcjonalne, dzięki czemu najlepszym rozwiązaniem dla aplikacji mogą być elementy obu tych elementów.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Przekształcanie funkcjonalne kodu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)
- [Refaktoryzacja do czystych funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

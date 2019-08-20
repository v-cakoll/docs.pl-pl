---
title: Możliwość zastosowania transformacji funkcjonalnejC#()
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594874"
---
# <a name="applicability-of-functional-transformation-c"></a>Możliwość zastosowania transformacji funkcjonalnejC#()
Czyste przekształcenia funkcjonalne mają zastosowanie w wielu różnych sytuacjach.  
  
 Podejście do transformacji funkcjonalnej idealnie nadaje się do wykonywania zapytań i manipulowania danymi strukturalnymi; w związku z tym dobrze pasuje do technologii LINQ. Jednak przekształcanie funkcjonalne ma znacznie szersze możliwości zastosowania niż w przypadku LINQ. Każdy proces, w którym głównym fokusem jest Przekształcanie danych z jednego formularza do innego powinien być uznany za kandydata na potrzeby transformacji funkcjonalnej.  
  
 Takie podejście dotyczy wielu problemów, które mogą nie pojawiać się w pierwszej kolejności jako kandydata. W połączeniu z lub niezależnie od LINQ, należy wziąć pod uwagę transformację funkcjonalną dla następujących obszarów:  
  
- Dokumenty oparte na języku XML. Poprawnie sformułowane dane dowolnego dialektu XML mogą być łatwo przetwarzane przez funkcję transformacji funkcjonalnej. Aby uzyskać więcej informacji, zobacz [funkcjonalne Przekształcanie koduC#XML ()](./functional-transformation-of-xml.md).  
  
- Inne formaty plików ze strukturą. Z plików Windows. ini do dokumentów w formacie zwykłego tekstu większość plików ma pewną strukturę, która pozwala na analizę i transformację.  
  
- Protokoły przesyłania strumieniowego danych. Kodowanie danych do i dekodowanie danych z protokołów komunikacyjnych może być często reprezentowane przez prostą transformację funkcjonalną.  
  
- Dane RDBMS i OODBMS. Relacyjne i zorientowane na obiekty bazy danych, podobnie jak XML, są szeroko używanymi źródłami danych.  
  
- Rozwiązania matematyczne, statystyczne i naukowe. Te pola umożliwiają manipulowanie dużymi zestawami danych w celu ułatwienia użytkownikowi wizualizacji, szacowania lub rozwiązywania nieuproszczonych problemów.  
  
 Zgodnie z opisem w temacie [Refaktoryzacja do czystychC#funkcji ()](./refactoring-into-pure-functions.md)użycie czystych funkcji jest przykładem programowania funkcjonalnego. W celu uzyskania natychmiastowych korzyści korzystanie z funkcji czystych zapewnia cenne środowisko w przypadku problemów z perspektywą transformacji funkcjonalnej. Takie podejście może również mieć istotny wpływ na projekt programu i klasy. Jest to szczególnie prawdziwe, gdy problem nadaje się do rozwiązania do przekształcania danych, jak opisano powyżej.  
  
 Chociaż wykraczają poza zakres tego samouczka, projekty, na które ma wpływ perspektywa transformacji funkcjonalnej, przeprowadzą do centrów procesów więcej niż w przypadku obiektów jako aktorów, a uzyskane rozwiązanie ma być implementowane jako seria dużej skali przekształcenia, a nie zmiany stanu poszczególnych obiektów.  
  
 Należy pamiętać, że C# program obsługuje zarówno podejścia bezwzględne, jak i funkcjonalne, dzięki czemu najlepszym rozwiązaniem dla aplikacji mogą być elementy obu tych elementów.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Przekształcenie funkcjonalne XML (C#)](./functional-transformation-of-xml.md)
- [Refaktoryzacja do czystych funkcji (C#)](./refactoring-into-pure-functions.md)

---
title: Zastosowanie transformacji funkcjonalnej (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594874"
---
# <a name="applicability-of-functional-transformation-c"></a>Zastosowanie transformacji funkcjonalnej (C#)
Czyste przemiany funkcjonalne mają zastosowanie w wielu różnych sytuacjach.  
  
 Podejście do transformacji funkcjonalnej idealnie nadaje się do wykonywania zapytań i manipulowania danymi strukturalnymi; dlatego dobrze pasuje do technologii LINQ. Jednak transformacja funkcjonalna ma znacznie szersze zastosowanie niż użycie z LINQ. Każdy proces, w którym główny nacisk kładzie się na przekształcanie danych z jednego formularza do drugiego, powinien być prawdopodobnie uważany za kandydata do transformacji funkcjonalnej.  
  
 Takie podejście ma zastosowanie do wielu problemów, które mogą nie pojawić się na pierwszy rzut oka jako kandydat. Używane w połączeniu z linq lub oddzielnie od LINQ, transformacja funkcjonalna powinna być brana pod uwagę dla następujących obszarów:  
  
- dokumentów opartych na xml. Dobrze sformułowane dane dowolnego dialektu XML można łatwo manipulować poprzez transformację funkcjonalną. Aby uzyskać więcej informacji, zobacz [Transformacja funkcjonalna języka XML (C#)](./functional-transformation-of-xml.md).  
  
- Inne formaty plików strukturalnych. Od plików Windows.ini do dokumentów tekstowych, większość plików ma pewną strukturę, która nadaje się do analizy i transformacji.  
  
- Protokoły przesyłania strumieniowego danych. Kodowanie danych i dekodowanie danych z protokołów komunikacyjnych często może być reprezentowane przez prostą transformację funkcjonalną.  
  
- RDBMS i OODBMS. Relacyjne i obiektowe bazy danych, podobnie jak XML, są szeroko stosowanymi ustrukturyzowanymi źródłami danych.  
  
- Matematyka, statystyka i rozwiązania naukowe. Te pola mają tendencję do manipulowania dużymi zestawami danych, aby pomóc użytkownikowi w wizualizowaniu, szacowaniu lub rozwiązywaniu nietrywialnych problemów.  
  
 Jak opisano w [Refaktoryzacja do czystych funkcji (C#)](./refactoring-into-pure-functions.md), przy użyciu czystych funkcji jest przykładem programowania funkcjonalnego. Oprócz ich natychmiastowych korzyści, korzystanie z czystych funkcji zapewnia cenne doświadczenie w myśleniu o problemach z perspektywy transformacji funkcjonalnej. Takie podejście może mieć również duży wpływ na projekt programu i klasy. Jest to szczególnie ważne, gdy problem nadaje się do rozwiązania transformacji danych, jak opisano powyżej.  
  
 Mimo, że wykraczają one poza zakres tego samouczka, projekty, które są pod wpływem perspektywy transformacji funkcjonalnej mają tendencję do wyśrodkowania na procesach więcej niż na obiektach jako aktorów, a wynikowe rozwiązanie wydaje się być realizowane jako seria na dużą skalę transformacje, a nie zmiany stanu obiektu.  
  
 Ponownie należy pamiętać, że C# obsługuje podejścia imperatywne i funkcjonalne, więc najlepszy projekt dla aplikacji może zawierać elementy obu.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przemian funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Transformacja funkcjonalna języka XML (C#)](./functional-transformation-of-xml.md)
- [Refaktoryzacja do czystych funkcji (C#)](./refactoring-into-pure-functions.md)

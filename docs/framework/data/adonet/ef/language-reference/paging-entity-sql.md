---
title: Stronicowanie (Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: 25d52734c30e087629be9923a43e720f94c96d04
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249575"
---
# <a name="paging-entity-sql"></a>Stronicowanie (Entity SQL)
Stronicowanie fizyczne można wykonać za pomocą podklauzul [Skip](skip-entity-sql.md) i [Limit](limit-entity-sql.md) w klauzuli [order by](order-by-entity-sql.md) . Aby dokonać niejednoznacznego stronicowania, należy użyć SKIP i LIMIT. Jeśli chcesz tylko ograniczyć liczbę wierszy w wyniku w sposób niedeterministyczny, należy użyć [klauzuli TOP](top-entity-sql.md). Wartość TOP i SKIP/LIMIT wykluczają się wzajemnie.  
  
## <a name="top-overview"></a>Najważniejsze Omówienie  
 Klauzula SELECT może mieć opcjonalną podklauzulę TOP, która znajduje się po opcjonalnym modyfikatorze ALL/DISTINCT. Podklauzula TOP określa, że tylko pierwszy zestaw wierszy zostanie zwrócony z wyniku zapytania. Aby uzyskać więcej informacji, zobacz [Top](top-entity-sql.md).  
  
## <a name="skip-and-limit-overview"></a>Przegląd POMIJAnia i OGRANICZAnia  
 SKIP i LIMIT są częścią klauzuli ORDER BY. Jeśli Podklauzula POMIJAnia wyrażenia jest obecna w klauzuli ORDER BY, wyniki zostaną posortowane zgodnie z specyfikacją sortowania, a zestaw wyników będzie zawierać wiersze zaczynające się od następnego wiersza bezpośrednio po wyrażeniu SKIP. Na przykład Pomiń 5 spowoduje pominięcie pierwszych pięciu wierszy i zwrócenie od szóstego wiersza do przodu. Jeśli Podklauzula wyrażenia limitu jest obecna w klauzuli ORDER BY, zapytanie zostanie posortowane zgodnie z specyfikacją sortowania, a wynikowa liczba wierszy zostanie ograniczona przez wyrażenie limitu. Na przykład LIMIT 5 ograniczy wynik do pięciu wystąpień lub wierszy. Nie trzeba używać jednocześnie pominięcia i limitu; Możesz użyć tylko pominięcia lub wystarczy ograniczyć z klauzulą ORDER BY. Więcej informacji znajduje się w następujących tematach:  
  
- [SKIP](skip-entity-sql.md)  
  
- [LIMIT](limit-entity-sql.md)  
  
- [ORDER BY](order-by-entity-sql.md)  
  
## <a name="see-also"></a>Zobacz także

- [Odwołanie do jednostki SQL](entity-sql-reference.md)
- [Omówienie jednostki SQL](entity-sql-overview.md)
- [Instrukcje: Strona za poorednictwem wyników zapytania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))

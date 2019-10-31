---
title: Harmonogram wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106228"
---
# <a name="scheduling-threads"></a>Harmonogram wątków

Każdy wątek ma przypisany priorytet wątku. Wątki utworzone w środowisku uruchomieniowym języka wspólnego mają początkowo przypisany priorytet <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Wątki utworzone poza środowiskiem uruchomieniowym zachowują priorytet, który miał przed wprowadzeniem środowiska zarządzanego. Można pobrać lub ustawić priorytet dowolnego wątku za pomocą właściwości <xref:System.Threading.Thread.Priority?displayProperty=nameWithType>.  
  
 Wątki są zaplanowane do wykonania na podstawie ich priorytetu. Chociaż wątki są wykonywane w czasie wykonywania, wszystkie wątki są przypisanymi wycinkami czasu procesora przez system operacyjny. Szczegóły algorytmu planowania używane do określenia kolejności, w której wątki są wykonywane, różnią się w zależności od systemu operacyjnego. W niektórych systemach operacyjnych wątek o najwyższym priorytecie (z tych wątków, które mogą być wykonywane) jest zawsze zaplanowany do uruchomienia w pierwszej kolejności. Jeśli wszystkie wątki o takim samym priorytecie są dostępne, harmonogram przechodzi przez wątki w tym priorytecie, co oznacza, że każdy wątek jest stałym wycinkem czasu, który ma zostać wykonany. Tak długo, jak wątek o wyższym priorytecie jest dostępny do uruchomienia, wątki o niższym priorytecie nie są wykonywane. Gdy nie ma więcej możliwy do uruchomienia wątków o danym priorytecie, harmonogram przechodzi do następnego niższego priorytetu i planuje wątki w tym priorytecie do wykonania. Jeśli wątek o wyższym priorytecie zostanie możliwy do uruchomienia, wątek o niższym priorytecie zostanie przeniesiona, a wątek o wyższym priorytecie będzie można wykonać raz ponownie. Na wszystkich tych systemach system operacyjny może również dynamicznie dostosować priorytety wątków, ponieważ interfejs użytkownika aplikacji jest przenoszony między pierwszym i tłem. Inne systemy operacyjne mogą korzystać z innego algorytmu planowania.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)
- [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)

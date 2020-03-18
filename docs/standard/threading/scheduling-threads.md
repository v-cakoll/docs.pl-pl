---
title: Harmonogram wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106228"
---
# <a name="scheduling-threads"></a>Harmonogram wątków

Każdy wątek ma przypisany priorytet wątku. Wątkom utworzonym w czasie wykonywania języka wspólnego początkowo <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>przypisywany jest priorytet . Wątki utworzone poza środowiskiem uruchomieniowym zachowują priorytet, który mieli przed wejściem do środowiska zarządzanego. Można uzyskać lub ustawić priorytet dowolnego <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> wątku z właściwością.  
  
 Wątki są zaplanowane do wykonania na podstawie ich priorytetu. Mimo że wątki są wykonywane w czasie wykonywania, wszystkie wątki są przypisane wycinki czasu procesora przez system operacyjny. Szczegóły algorytmu planowania używane go do określenia kolejności wykonywania wątków różnią się w zależności od systemu operacyjnego. W niektórych systemach operacyjnych wątek o najwyższym priorytecie (z tych wątków, które mogą być wykonywane) jest zawsze zaplanowane do uruchomienia jako pierwszy. Jeśli dostępnych jest wiele wątków o tym samym priorytecie, harmonogram przechodzi przez wątki na tym priorytecie, nadając każdemu wątkowi stały wycinek czasu, w którym ma zostać wykonany. Tak długo, jak wątek o wyższym priorytecie jest dostępny do uruchomienia, wątki o niższym priorytecie nie są wykonywane. Gdy nie ma więcej wątków runnable na danym priorytecie, harmonogram przenosi się do następnego niższego priorytetu i planuje wątki na ten priorytet do wykonania. Jeśli wątek o wyższym priorytecie staje się uruchamiany, wątek o niższym priorytecie jest wywłaszczony, a wątek o wyższym priorytecie może zostać wykonany ponownie. Oprócz tego system operacyjny może również dynamicznie dostosowywać priorytety wątków, ponieważ interfejs użytkownika aplikacji jest przenoszony między pierwszym planem a tłem. Inne systemy operacyjne mogą zdecydować się na użycie innego algorytmu planowania.  
  
## <a name="see-also"></a>Zobacz też

- [Korzystanie z wątków i wątków](../../../docs/standard/threading/using-threads-and-threading.md)
- [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)

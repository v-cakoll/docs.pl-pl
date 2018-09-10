---
title: Harmonogram wątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 811a75c9f0350eefc98c32181e859b7583ff74ef
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186295"
---
# <a name="scheduling-threads"></a>Harmonogram wątków

Każdy wątek ma przypisany priorytet wątku. Utworzone w ramach środowiska uruchomieniowego języka wspólnego wątki są początkowo przypisana priorytet <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Wątki utworzony poza środowisko uruchomieniowe zachować priorytet, który wcześniej one umieszczone w środowisku zarządzanym. Można uzyskać lub ustawić priorytet z żadnym z wątków <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> właściwości.  
  
 Wątki są zaplanowane do wykonania na podstawie ich priorytetu. Mimo że wątki są wykonywane w ramach środowiska uruchomieniowego, wszystkie wątki są przypisywane przedziały czasu procesora przez system operacyjny. Szczegółowe informacje o harmonogramie algorytm używany do określenia kolejność wykonywania wątków zależy od każdego systemu operacyjnego. W niektórych systemach operacyjnych wątku z najwyższym priorytetem (z wątków, które mogą być wykonywane) zawsze jest zaplanowana do uruchomienia jako pierwsza. Jeśli wiele wątków, z tym samym priorytecie są wszystkie dostępne cykli harmonogramu za pomocą wątków tego priorytetem, dzięki czemu każdy wątek wycinek stały czas, w której chcesz wykonać. Tak długo, jak wątek o wyższym priorytecie jest dostępna do uruchamiania, nie otrzymują niższy priorytet wątków do wykonania. Gdy istnieją wątki nie ma już możliwy do uruchomienia w danym priorytecie, harmonogram przechodzi do następnego niższy priorytet i planuje wątków, w tym priorytet dla wykonywania. Jeśli wątek wyższy priorytet staje się możliwy do uruchomienia, niższy priorytet wątku jest przerywane i wyższy priorytet wątku można wykonać ponownie. Na podstawie wszystkich, systemu operacyjnego można również dostosować priorytety wątku dynamicznie zgodnie z interfejsu użytkownika aplikacji jest przenoszone między pierwszego planu i tła. Inne systemy operacyjne, warto używać innego algorytmu planowania.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
- [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)

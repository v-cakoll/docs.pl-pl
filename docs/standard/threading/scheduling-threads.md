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
ms.openlocfilehash: 794dfe3dc8e8cded9f7008300351598bbd1dee07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582811"
---
# <a name="scheduling-threads"></a>Harmonogram wątków
Każdy wątek ma priorytet wątku przypisane do niej. Utworzone w ramach środowisko uruchomieniowe języka wspólnego wątki są początkowo przypisana priorytet **ThreadPriority.Normal**. Wątki utworzony poza środowisko uruchomieniowe zachować priorytet, który wcześniej one umieszczone w zarządzanym środowisku. Można pobrać lub ustawić priorytet którymkolwiek wątku z **Thread.Priority** właściwości.  
  
 Wątki są zaplanowane do uruchomienia, na podstawie ich priorytetu. Mimo że wątki są wykonywane w ramach środowiska uruchomieniowego, wszystkie wątki są przypisywane przedziały czasu procesora przez system operacyjny. Szczegółowe informacje o harmonogramie algorytm używany do określenia kolejności wykonywania wątków zależy od każdego systemu operacyjnego. W niektórych systemach operacyjnych wątku najwyższy priorytet (wątki, które mogą być wykonywane) zawsze jest zaplanowane do uruchomienia pierwszy. Jeśli wiele wątków z takim samym priorytecie będą dostępne, cykle harmonogramu przez wątki tego priorytetem, podając każdy wątek wycinek stały czas, w którym ma być wykonane. Tak długo, jak wątku z wyższym priorytetem jest dostępna do uruchamiania, niższy priorytet wątków nie może korzystać do wykonania. Jeśli nie ma już do uruchomienia wątków w danym priorytecie, harmonogram przechodzi do następnego niższy priorytet i harmonogramy wątków w tym priorytet dla wykonywania. W przypadku wyższy priorytet wątku do uruchomienia, niższy priorytet wątku jest przeniesiona i wyższy priorytet wątku można wykonać ponownie. U góry wszystko systemu operacyjnego można również dostosować priorytety wątku dynamicznie jako interfejsu użytkownika aplikacji są przenoszone między pierwszego planu i tła. Innych systemów operacyjnych można użyć innego algorytmu planowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie wątków i wątkowości](../../../docs/standard/threading/using-threads-and-threading.md)  
 [Zarządzana i niezarządzana wątkowość w systemie Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)

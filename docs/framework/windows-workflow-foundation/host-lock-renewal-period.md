---
title: Okres odnawiania blokady hosta
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 91d83259c766120f7e3ffc9e49f1cf1b18c32a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513721"
---
# <a name="host-lock-renewal-period"></a>Okres odnawiania blokady hosta
**Okres odnawiania blokady hosta** właściwość w magazynie wystąpień przepływu pracy SQL pozwala określić okres czasu, w którym host odnawia jego blokadę wystąpienia przepływu pracy. Blokada pozostaje ważny na okres odnawiania blokady hosta + 30 sekund. Jeśli host nie może odnowić blokady (innymi słowy, przedłużyć dzierżawę) w tym okresie, blokady wygaśnie, a dostawca trwałości odblokowuje wystąpienie. Wartość tej właściwości jest typu TimeSpan w postaci "hh: mm:". Minimalna dozwolona wartość to "00: 00:01" (1 sekunda). Wartość domyślna tej właściwości to "00: 00:30" (30 sekund).  
  
 Ta właściwość jest istotna w scenariuszach, w którym hosta usługi przepływu pracy nie powiedzie się, zanim można odblokować wystąpienie usługi przepływu pracy, który jest właścicielem. W tym scenariuszu blokady dla wystąpienia usługi przepływu pracy w bazie danych trwałości usunięciu dostawca trwałości po wygaśnięciu blokady, dzięki czemu mogą uzyskiwać innego hosta usługi przepływu pracy uruchomionych na tym samym komputerze lub inny komputer w farmie serwerów Zablokuj i załadować wystąpienia przepływu pracy usługi do pamięci, aby wznowić działania z jej ostatniego utrwalonego stanu.  
  
 Ustawienie wyższej wartości dla tej właściwości powoduje wystąpienie usługi do zablokowania w bazie danych trwałości dłużej przepływu pracy i w związku z tym opóźnienia odzyskiwania wystąpienia z ostatniego punktu trwałości. Ustawienie przez krótki czas dla tej właściwości spowoduje, że nowe wystąpienie hosta usługi przepływu pracy, aby pobrać wystąpienia usługi przepływu pracy nie powiodło się szybko, ale powoduje wzrost obciążenia pracą hosta usługi przepływu pracy oraz bazy danych programu SQL Server.  
  
 W magazynie wystąpień przepływu pracy SQL działa wewnętrzny zadanie, które okresowo budzi i wykrywa wystąpienia z wygasłych blokad na nich. Po znalezieniu wystąpień z wygasłych blokad, umieszcza wystąpienia w tabeli RunnableInstances tak, aby hosta przepływu pracy może odbierać i Uruchom te wystąpienia.

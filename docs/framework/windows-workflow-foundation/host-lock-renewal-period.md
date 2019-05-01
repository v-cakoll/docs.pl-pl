---
title: Okres odnowienia blokady hosta
ms.date: 03/30/2017
ms.assetid: f8ba94fc-27e0-4d8e-8f85-50a6d2a3cd43
ms.openlocfilehash: 91d83259c766120f7e3ffc9e49f1cf1b18c32a18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945616"
---
# <a name="host-lock-renewal-period"></a>Okres odnowienia blokady hosta
**Okres odnowienia blokady hosta** właściwość Store wystąpienia przepływu pracy SQL pozwala określić okres czasu, w którym hosta odnawia blokady w wystąpieniu przepływu pracy. Blokada pozostaje ważny na okres odnowienia blokady hosta + 30 sekund. Jeśli host nie odnowić blokady (innymi słowy, przedłużyć dzierżawę) w tym przedziale czasu wygaśnięcia blokady i dostawcy stanów trwałych odblokowuje wystąpienia. Wartość tej właściwości jest typu TimeSpan format "gg". Minimalna dozwolona wartość to "00: 00:01" (1 sekunda). Wartość domyślna tej właściwości to "00: 00:30" (30 sekund).  
  
 Ta właściwość ma istotne znaczenie w scenariuszach, w którym hosta usługi przepływu pracy nie powiedzie się, zanim go odblokować wystąpienie usługi przepływu pracy, który jest właścicielem. W tym scenariuszu blokady w wystąpieniu usługi przepływu pracy w bazie danych trwałości zostanie usunięty przez dostawcę trwałości po wygaśnięciu blokady, dzięki czemu mogą uzyskiwać innego hosta usługi przepływu pracy uruchomionej na tym samym komputerze lub inny komputer w farmie serwerów Blokowanie i załadować wystąpienia usługi przepływu pracy do pamięci, aby wznowić jego wykonywanie z jej ostatniego utrwalonego stanu.  
  
 Ustawienie wyższej wartości dla tej właściwości powoduje, że przepływ pracy wystąpień usługi zostanie zablokowane w bazie danych trwałości przez dłuższy czas i w związku z tym opóźnia odzyskiwania wystąpienie z ostatniego punktu stanu trwałego. Ustawienie krótkiego interwału dla tej właściwości powoduje, że nowe wystąpienie hosta usługi przepływu pracy, aby pobrać wystąpienie usługi przepływu pracy nie powiodło się szybko, ale powoduje wzrost obciążenia hosta usługi przepływu pracy oraz bazy danych programu SQL Server.  
  
 Store wystąpienia przepływu pracy SQL uruchamia zadania wewnętrzne, która okresowo budzi wykryje wystąpienia z wygasłych blokadami na nich. Po znalezieniu wystąpień z wygasłych blokad, umieszcza wystąpienia w tabeli RunnableInstances tak, aby hosta przepływu pracy może odbierać i Uruchom te wystąpienia.

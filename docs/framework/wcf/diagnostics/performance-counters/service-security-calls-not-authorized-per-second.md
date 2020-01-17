---
title: 'Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163881"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę
Nazwa licznika: wywołania zabezpieczeń bez autoryzacji na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wiadomości przychodzących w jednej sekund, które są od prawidłowego użytkownika i są chronione prawidłowo, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.  
  
 Licznik jest zwiększany, gdy metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> zwraca `false`.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)

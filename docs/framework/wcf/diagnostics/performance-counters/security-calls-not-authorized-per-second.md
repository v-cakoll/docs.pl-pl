---
title: Nieautoryzowane wywołania zabezpieczeń na sekundę
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163933"
---
# <a name="security-calls-not-authorized-per-second"></a>Nieautoryzowane wywołania zabezpieczeń na sekundę
Nazwa licznika: wywołania zabezpieczeń nie są autoryzowane na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, których autoryzacja zakończyła się niepowodzeniem w ramach tej operacji w drugim.  
  
 Licznik jest zwiększany, gdy metoda <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> zwraca `false`. Wskazuje on, że komunikat przychodzący jest prawidłowym użytkownikiem i chroniony prawidłowo, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)

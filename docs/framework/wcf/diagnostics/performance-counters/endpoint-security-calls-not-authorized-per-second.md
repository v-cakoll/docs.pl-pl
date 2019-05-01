---
title: 'Punkt końcowy: Nieautoryzowane wywołania zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: c62bec570daf8b107ca0540871eb6eac43ca2d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951117"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a>Punkt końcowy: Nieautoryzowane wywołania zabezpieczeń na sekundę
Nazwa komputera: Wywołania zabezpieczeń bez autoryzacji na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba komunikatów przychodzących na sekundę, które pochodzą z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.  
  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

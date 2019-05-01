---
title: 'Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 523e5182ca661e170e5cba01d5221b5c38251959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773412"
---
# <a name="service-security-calls-not-authorized-per-second"></a>Usługa: Nieautoryzowane wywołania zabezpieczeń na sekundę
Nazwa komputera: Nieautoryzowane wywołania zabezpieczeń na sekundę  
  
## <a name="description"></a>Opis  
 Liczba komunikatów przychodzących w jednej sekundy, które pochodzą z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.  
  
 Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkId=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

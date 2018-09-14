---
title: Błędne sesje komunikacji niezawodnej na sekundę
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45514875"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>Błędne sesje komunikacji niezawodnej na sekundę
Nazwa licznika: Błędne sesje komunikacji niezawodnej na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba sesje niezawodnej obsługi komunikatów, które są umieszczone w tej usłudze na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

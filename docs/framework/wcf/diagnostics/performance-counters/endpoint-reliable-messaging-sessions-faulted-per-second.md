---
title: 'Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: f6b48ec4c37c28588dd874a5bfa94a01a2f43b0c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190822"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Punkt końcowy: Błędne sesje komunikacji niezawodnej na sekundę
Nazwa licznika: Błędne sesje komunikacji niezawodnej na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba sesje niezawodnej obsługi komunikatów, które są umieszczone w tym punkcie końcowym na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

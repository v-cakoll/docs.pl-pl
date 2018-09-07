---
title: Porzucone komunikaty niezawodnej obsługi komunikatów na sekundę
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075387"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Porzucone komunikaty niezawodnej obsługi komunikatów na sekundę
Nazwa licznika: Sesje niezawodnej obsługi komunikatów na sekundę porzuconych.  
  
## <a name="description"></a>Opis  
 Całkowita liczba komunikaty niezawodnej obsługi komunikatów, które zostały usunięte w tej usłudze na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

---
title: Porzucone komunikaty komunikacji niezawodnej na sekundę
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 946e0408b8b6602bba7824b45e4d6cb91cdaa4eb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163959"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Porzucone komunikaty komunikacji niezawodnej na sekundę
Nazwa licznika: porzucone sesje niezawodnej obsługi komunikatów na sekundę.  
  
## <a name="description"></a>Opis  
 Całkowita liczba komunikatów komunikacji niezawodnej, które zostały usunięte w tej usłudze w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)

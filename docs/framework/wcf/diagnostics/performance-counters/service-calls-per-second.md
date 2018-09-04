---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499890"
---
# <a name="service-calls-per-second"></a>Usługa: Wywołania na sekundę
Nazwa licznika: Wywołania na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 -D 0) / F) gdzie licznika (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje mianownik (D), liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania, a F to częstotliwość to znaczniki osi.

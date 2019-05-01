---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773367"
---
# <a name="service-calls-per-second"></a>Usługa: Wywołania na sekundę
Nazwa komputera: Wywołania na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 -D 0) / F) gdzie licznika (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje mianownik (D), liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania, a F to częstotliwość to znaczniki osi.

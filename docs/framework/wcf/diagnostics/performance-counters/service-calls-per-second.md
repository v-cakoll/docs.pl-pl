---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: c23456f49eb867d5b6f66b4386a83615d95e07da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473931"
---
# <a name="service-calls-per-second"></a>Usługa: Wywołania na sekundę
Nazwa licznika: Wywołania na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 -D 0) / F) gdy licznik (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje denominator (D) liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania i F jest częstotliwość to znaczniki osi.

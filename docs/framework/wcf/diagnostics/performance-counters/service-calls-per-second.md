---
title: "Usługa: Wywołania na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0880ce3674f41367c46f4d0268a5391cfda210ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-calls-per-second"></a>Usługa: Wywołania na sekundę
Nazwa licznika: Wywołania na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 -D 0) / F) gdy licznik (N) reprezentuje liczbę operacji wykonywanych podczas ostatniego interwału próbkowania reprezentuje denominator (D) liczbę znaczników, który upłynął podczas ostatniego interwału próbkowania i F jest częstotliwość to znaczniki osi.

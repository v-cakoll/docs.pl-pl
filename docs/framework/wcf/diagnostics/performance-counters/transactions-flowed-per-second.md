---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: a71095b9fdd16d7e220be8a0aeb0a746bb50527e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transactions-flowed-per-second"></a>Przepływ transakcji na sekundę
Nazwa licznika: Przekazane transakcje na sekundę  
  
## <a name="description"></a>Opis  
 Liczba transakcji skierowana do tej operacji na sekundę. Ten licznik jest zwiększany za każdym razem, który zawiera identyfikator transakcji znajduje się w komunikat, który jest wysyłany do operacji.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)

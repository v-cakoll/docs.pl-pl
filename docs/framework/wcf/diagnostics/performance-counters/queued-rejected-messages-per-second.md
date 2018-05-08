---
title: Zakolejkowane komunikaty odrzucone na sekundę
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 31091c6c9dd04ecd7294f69f9611f25e401df724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="queued-rejected-messages-per-second"></a>Zakolejkowane komunikaty odrzucone na sekundę
Nazwa licznika: Zakolejkowane komunikaty odrzucone na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba komunikatów, które zostały odrzucone przez transport z kolejką w tej usługi na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)

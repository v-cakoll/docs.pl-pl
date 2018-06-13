---
title: Wywołania na sekundę
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 04eb5deaf8e6eb09be4e0bf404bec11b8ce84427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472622"
---
# <a name="calls-per-second"></a>Wywołania na sekundę
Nazwa licznika: Wywołania na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej operacji na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)

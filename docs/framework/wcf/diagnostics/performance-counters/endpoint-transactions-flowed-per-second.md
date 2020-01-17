---
title: 'Punkt końcowy: Przekazane transakcje na sekundę'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163556"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Punkt końcowy: Przekazane transakcje na sekundę
Nazwa licznika: przepływające na sekundę transakcje.  
  
## <a name="description"></a>Opis  
 Liczba transakcji przepływających do operacji w tym punkcie końcowym w drugim. Ten licznik jest zwiększany za każdym razem, gdy w komunikacie wysyłanym do punktu końcowego jest obecny identyfikator transakcji.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)

---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: 8b6077af3f98f7a205772b4883dc122374083e00
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163829"
---
# <a name="transactions-flowed-per-second"></a>Przepływ transakcji na sekundę
Nazwa licznika: przepływające transakcje na sekundę  
  
## <a name="description"></a>Opis  
 Liczba transakcji przepływających do tej operacji w drugim. Ten licznik jest zwiększany za każdym razem, gdy w komunikacie wysyłanym do operacji jest obecny identyfikator transakcji.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F)

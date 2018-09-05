---
title: Zatwierdzone operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564014"
---
# <a name="transacted-operations-committed-per-second"></a>Zatwierdzone operacje transakcyjne na sekundę
Nazwa licznika: Zatwierdzone Operacje transakcyjne na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba operacji transakcyjnych, które miały miejsce w tej usługi na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

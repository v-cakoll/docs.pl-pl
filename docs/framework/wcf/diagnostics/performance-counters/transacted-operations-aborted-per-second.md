---
title: Przerwane operacje transakcyjne na sekundę
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417485"
---
# <a name="transacted-operations-aborted-per-second"></a>Przerwane operacje transakcyjne na sekundę
Nazwa licznika: Transacted przerwane operacje na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba operacji transakcyjnych, które zostało przerwane w tej usłudze na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

---
title: Zakolejkowane komunikaty porzucone na sekundę
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916165"
---
# <a name="queue-dropped-messages-per-second"></a>Zakolejkowane komunikaty porzucone na sekundę
Nazwa komputera: Porzucone komunikaty w kolejce na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wiadomości, które są porzucane w kolejce transportu na tę usługę na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

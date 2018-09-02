---
title: Zakolejkowane komunikaty porzucone na sekundę
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418251"
---
# <a name="queue-dropped-messages-per-second"></a>Zakolejkowane komunikaty porzucone na sekundę
Nazwa licznika: Zakolejkowane komunikaty porzucone na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wiadomości, które są porzucane w kolejce transportu na tę usługę na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

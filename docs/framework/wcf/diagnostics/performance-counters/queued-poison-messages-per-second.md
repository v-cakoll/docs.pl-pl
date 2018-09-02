---
title: Zakolejkowane komunikaty zanieczyszczone na sekundę
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420692"
---
# <a name="queued-poison-messages-per-second"></a>Zakolejkowane komunikaty zanieczyszczone na sekundę
Nazwa licznika: Zakolejkowane komunikaty zanieczyszczone na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wiadomości, które są oznaczone uszkodzone przez umieszczonych w kolejce transportu na tę usługę z kolejką na sekundę.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

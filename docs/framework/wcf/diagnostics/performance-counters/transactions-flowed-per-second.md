---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392939"
---
# <a name="transactions-flowed-per-second"></a>Przepływ transakcji na sekundę
Nazwa licznika: Przekazane transakcje na sekundę  
  
## <a name="description"></a>Opis  
 Liczba transakcji przekazane do tej operacji na sekundę. Ten licznik jest zwiększany ilekroć dowolny identyfikator transakcji znajduje się w wiadomości, które są wysyłane do operacji.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N: 1 - N 0) / ((D 1 - D 0) / F)

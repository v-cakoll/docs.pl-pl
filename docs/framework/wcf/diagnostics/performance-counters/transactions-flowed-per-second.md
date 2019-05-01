---
title: Przepływ transakcji na sekundę
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927195"
---
# <a name="transactions-flowed-per-second"></a>Przepływ transakcji na sekundę
Nazwa komputera:  Przepływ transakcji na sekundę  
  
## <a name="description"></a>Opis  
 Liczba transakcji przekazane do tej operacji na sekundę. Ten licznik jest zwiększany ilekroć dowolny identyfikator transakcji znajduje się w wiadomości, które są wysyłane do operacji.  
  
 Ten licznik jest typ licznika wydajności [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)

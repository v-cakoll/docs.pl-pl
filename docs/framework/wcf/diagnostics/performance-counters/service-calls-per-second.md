---
title: 'Usługa: Wywołania na sekundę'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163907"
---
# <a name="service-calls-per-second"></a>Usługa: Wywołania na sekundę
Nazwa licznika: wywołania na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań tej usługi w drugim.  
  
 Ten licznik jest typem licznika wydajności [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1-N 0)/((D 1-D 0)/F) gdzie licznik (N) reprezentuje liczbę operacji wykonanych w ciągu ostatniego interwału próbkowania, mianownik (D) reprezentuje liczbę taktów, które upłynęły podczas ostatniego interwału próbkowania, a F jest częstotliwością taktów.

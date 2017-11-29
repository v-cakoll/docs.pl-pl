---
title: "Wywołania zakończone niepowodzeniami na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 504470a7338a22d058f6ae1f99192e9665b4d968
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="calls-failed-per-second"></a>Wywołania zakończone niepowodzeniami na sekundę
Nazwa licznika: Wywołania zakończone niepowodzeniami na sekundę  
  
## <a name="description"></a>Opis  
 Liczba wywołań z nieobsługiwanymi wyjątkami w tej operacji na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)  
  
 Ten licznik jest zwiększany zawsze, gdy jest nieobsługiwany w tej operacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

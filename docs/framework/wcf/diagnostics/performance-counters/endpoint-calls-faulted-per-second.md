---
title: "Punkt końcowy: Wywołania zwracające błędy na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842270d6e570767c25c414307be941f24b01dd07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-calls-faulted-per-second"></a>Punkt końcowy: Wywołania zwracające błędy na sekundę
Nazwa licznika: Wywołania zwracające błędy na sekundę.  
  
## <a name="description"></a>Opis  
 Liczba wywołań, które zwrócone błędy na ten punkt końcowy na sekundę.  
  
 Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)  
  
 W [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] komunikacji metody usług aplikacji, przetwarzania przy użyciu protokołu SOAP komunikatów "fault" informacje o błędzie. Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne. Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)

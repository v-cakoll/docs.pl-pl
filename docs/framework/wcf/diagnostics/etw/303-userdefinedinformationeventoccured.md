---
title: "303 — UserDefinedInformationEventOccured"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bd4d94d457793eb036f037cc6dc22bff6d26ee2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="303---userdefinedinformationeventoccured"></a>303 — UserDefinedInformationEventOccured
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|303|  
|Słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany z kodu użytkownika. Deweloperzy mogą emituje to zdarzenie po wystąpieniu zdarzenia informacyjną niestandardowy w usłudze ich. Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: '%1' dla odwołania: "%2", ładunku: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Nazwa użytkownika zdarzenia|  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

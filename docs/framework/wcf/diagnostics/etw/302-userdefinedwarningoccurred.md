---
title: 302 — UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a>302 — UserDefinedWarningOccurred
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|302|  
|Słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany z kodu użytkownika. Deweloperzy mogą emituje to zdarzenie, gdy wystąpi zdarzenie ostrzeżenia niestandardowy w usłudze ich. Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: '%1' dla odwołania: "%2", ładunku: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Zdefiniowane przez użytkownika nazwa zdarzenia.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

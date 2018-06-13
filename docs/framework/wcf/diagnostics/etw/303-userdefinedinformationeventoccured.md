---
title: 303 — UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459143"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 — UserDefinedInformationEventOccured
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|303|  
|Słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany z kodu użytkownika. Deweloperzy mogą emituje to zdarzenie po wystąpieniu zdarzenia informacyjną niestandardowy w usłudze ich. Można to zrobić przy użyciu <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykład WCF, który opakowuje tego interfejsu API i pokazuje, jak poprawnie Emituj to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: '%1' dla odwołania: "%2", ładunku: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Nazwa użytkownika zdarzenia|  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

---
title: 303 — UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595782"
---
# <a name="303---userdefinedinformationeventoccured"></a>303 — UserDefinedInformationEventOccured
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|303|  
|słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez kod użytkownika. Deweloperzy może emitować to zdarzenie, gdy wystąpi zdarzenie informacyjne niestandardowy w ich usługi. Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: "%1" dla odwołania: "%2", ładunek: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Zdefiniowana przez użytkownika nazwa zdarzenia|  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

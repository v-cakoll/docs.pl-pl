---
title: 301 — UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596482"
---
# <a name="301---userdefinederroroccurred"></a>301 — UserDefinedErrorOccurred
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|301|  
|słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Błąd|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez kod użytkownika. Deweloperzy może emitować to zdarzenie, gdy wystąpi błąd niestandardowy w ich usługi. Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: "%1" dla odwołania: "%2", ładunek: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Zdefiniowana przez użytkownika nazwa zdarzenia.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

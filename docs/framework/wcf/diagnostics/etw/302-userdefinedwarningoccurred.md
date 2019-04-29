---
title: 302 — UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596755"
---
# <a name="302---userdefinedwarningoccurred"></a>302 — UserDefinedWarningOccurred
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|302|  
|słowa kluczowe|Rozwiązywanie problemów, HealthMonitoring UserEvents, ServiceModel, EndToEndMonitoring|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane przez kod użytkownika. Deweloperzy może emitować to zdarzenie, gdy wystąpi zdarzenie ostrzeżenia niestandardowy w ich usługi. Można to zrobić za pomocą <xref:System.Diagnostics.Eventing> interfejsów API. Ponadto jest przykładowy WCF, otacza tego interfejsu API, który pokazuje, jak prawidłowo emisji to zdarzenie.  
  
## <a name="message"></a>Komunikat  
 Nazwa: "%1" dla odwołania: "%2", ładunek: %3  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa|`xs:string`|Zdefiniowana przez użytkownika nazwa zdarzenia.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|ładunek|`xs:string`|Zdefiniowane przez użytkownika ładunek zdarzenia.|

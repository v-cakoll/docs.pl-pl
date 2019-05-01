---
title: 213 — ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781826"
---
# <a name="213---servicehoststarted"></a>213 — ServiceHostStarted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|Identyfikator|213|  
|słowa kluczowe|EndToEndMonitoring HealthMonitoring, rozwiązywania problemów, ServiceHost|  
|Poziom|LogAlways|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowane, podczas uruchamiania hosta usługi hostowanej w sieci Web. Dzieje się tak zazwyczaj, gdy usługa została aktywowana przez komunikat. Również zdarzyć, gdy usługa jest skonfigurowana do automatycznego uruchomienia.  
  
## <a name="message"></a>Komunikat  
 ServiceHost pracy: "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa typu usługi|`xs:string`|Pełna nazwa CLR typu implementacji usługi.|  
|HostReference|`xs:string`|Dla usług sieci Web hostowanych w tym polu jednoznacznie identyfikuje usługę w hierarchii w sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżka wirtualna usługi&#124;ServiceName". Przykład: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.|  
|AppDomain|`xs:string`|Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.|

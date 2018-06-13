---
title: 499 — TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469511"
---
# <a name="499---transferemitted"></a>499 — TransferEmitted
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|499|  
|Słowa kluczowe|Rozwiązywanie problemów, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking ServiceHost, WCFMessageLogging|  
|Poziom|LogAlways|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po wystąpieniu zdarzenia transferu.  
  
## <a name="message"></a>Komunikat  
 Zdarzenia transferu wysyłanego.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|

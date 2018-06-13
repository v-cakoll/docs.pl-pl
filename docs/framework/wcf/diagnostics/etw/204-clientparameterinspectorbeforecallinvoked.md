---
title: 204 — ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458588"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a>204 — ClientParameterInspectorBeforeCallInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|204|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeCall` metoda inspektora parametru klienta.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wywołał metodę "BeforeCall" w obiekcie ClientParameterInspector typu "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Element FullName CLR typu inspector wywołana.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web&#124;ścieżki wirtualnej usługi&#124;ServiceName". Przykład: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|

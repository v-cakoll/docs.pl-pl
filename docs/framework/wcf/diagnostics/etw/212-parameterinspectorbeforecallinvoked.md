---
title: "212 — ParameterInspectorBeforeCallInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c428c9057e1538cfadb2b02bd05e2d61b4566399
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a>212 — ParameterInspectorBeforeCallInvoked
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|212|  
|Słowa kluczowe|Rozwiązywanie problemów, ServiceModel|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji Server aplikacje/analityczne|  
  
## <a name="description"></a>Opis  
 To zdarzenie jest emitowany po modelu usługi został wywołany `BeforeCall` metoda `ParameterInspector`.  
  
## <a name="message"></a>Komunikat  
 Dyspozytor wywołał metodę "BeforeCall" w obiekcie ParameterInspector typu "%1".  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|TypeName|`xs:string`|Element FullName CLR typu inspector wywołana.|  
|HostReference|`xs:string`|W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web. Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ". Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".|  
|Domeny aplikacji|`xs:string`|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|

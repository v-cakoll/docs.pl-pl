---
title: 1124 - InvokeMethodIsStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8db91ad18548ac67a1ad2942fb7f57048e272df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1124---invokemethodisstatic"></a>1124 - InvokeMethodIsStatic
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1124|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku CacheMetadata działanie InvokeMethod wskazuje, że jest statyczna metoda do wywołania.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" — metoda jest statyczna.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana InvokeMethod działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|

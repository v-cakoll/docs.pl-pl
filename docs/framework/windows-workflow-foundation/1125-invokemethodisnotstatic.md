---
title: 1125 - InvokeMethodIsNotStatic
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8b5e255e9a753c6476a070609b0cbda189d37a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="1125---invokemethodisnotstatic"></a>1125 - InvokeMethodIsNotStatic
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1125|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Informacje|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Podczas wykonywania kroku CacheMetadata działanie InvokeMethod wskazuje, że wywoływanej metody nie jest statyczne.  
  
## <a name="message"></a>Komunikat  
 InvokeMethod "%1" — metoda nie jest statyczna.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:String|Nazwa wyświetlana InvokeMethod działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|

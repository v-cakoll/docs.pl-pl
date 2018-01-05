---
title: '&lt;synchronousReceive&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt;, element
Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta. Nie ma żadnych atrybutów ani elementów podrzędnych.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<endpointBehaviors >  
\<zachowanie >  
\<synchronousReceive >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="remarks"></a>Uwagi  
 Umożliwia to zachowanie poinstruować odbiornik kanału do użycia synchronicznego odbierania zamiast domyślnego, asynchroniczne. [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]wystawia nowego wątku pompa dla poszczególnych zaakceptowanych kanałów. Jeśli istnieje wiele kanałów, istnieje możliwość wyczerpaniu wątków.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

---
title: '&lt;synchronousReceive&gt;, element'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: af1ca2ee1fe3c03c33f05e0c30c7b843b3720a36
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753264"
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt;, element
Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta. Nie ma żadnych atrybutów ani elementów podrzędnych.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
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
 Umożliwia to zachowanie poinstruować odbiornik kanału do użycia synchronicznego odbierania zamiast domyślnego, asynchroniczne. Windows Communication Foundation (WCF) wystawia nowego wątku pompa dla poszczególnych zaakceptowanych kanałów. Jeśli istnieje wiele kanałów, istnieje możliwość wyczerpaniu wątków.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

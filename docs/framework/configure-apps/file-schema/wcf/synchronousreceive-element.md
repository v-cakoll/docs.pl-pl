---
title: '&lt;synchronousReceive&gt;, element'
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: dedbe156dea79c78f05acdb3a044c9080665675a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598898"
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt;, element
Ten element konfiguracji służy do określania zachowania w czasie wykonywania do odbierania wiadomości w aplikacji usługi lub klienta. Nie ma żadnych atrybutów lub elementów podrzędnych.  
  
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
 Użyj tego zachowania, aby nakazać odbiornik kanału do użycia przez synchroniczny otrzymywać zamiast domyślnej, asynchronicznego. Windows Communication Foundation (WCF) wystawia nowy wątek pompy dla każdego kanału akceptowane. W przypadku wielu kanałów, istnieje możliwość korzystającym z wątków.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>

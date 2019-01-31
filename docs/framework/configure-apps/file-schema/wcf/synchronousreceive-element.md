---
title: <synchronousReceive> — element
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: f4a8868304ebae9a7ed5e6afbfb14fb2116afc49
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278480"
---
# <a name="synchronousreceive-element"></a>\<synchronousReceive > element
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

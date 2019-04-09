---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: dc8dea0ddd1ea074c08952e3e2ebfef2d12f7183
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099290"
---
# <a name="persistenceprovider"></a>\<persistenceProvider>
Określa typ implementacji dostawcy stanów stałych do użycia, jak również limit czasu na potrzeby operacji trwałości.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<persistenceProvider>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|persistenceOperationTimeout|A <xref:System.TimeSpan> wartość, która określa limit czasu użyty dla operacji utrwalania. Wartość domyślna to "00: 00:30".|  
|— typ|Ciąg, który określa typ fabryki dostawcy trwałości do użycia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa dostawcy stanów trwałych, który ma być używany do serializacji stanu usługi WCF. Należy używać razem z `wsHttpContextBinding` który przekazuje informacje o stanie w nagłówkach HTTP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>

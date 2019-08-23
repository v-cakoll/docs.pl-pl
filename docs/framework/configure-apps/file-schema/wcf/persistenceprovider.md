---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934139"
---
# <a name="persistenceprovider"></a>\<persistenceProvider>
Określa typ implementacji dostawcy trwałości, a także limit czasu na potrzeby operacji trwałości.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
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
|persistenceOperationTimeout|<xref:System.TimeSpan> Wartość określająca limit czasu używany na potrzeby operacji trwałości. Wartość domyślna to "00:00:30".|  
|— typ|Ciąg określający typ fabryki dostawcy trwałości do użycia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element określa dostawcę trwałości, który ma być używany do serializacji stanu usługi WCF. Powinna być używana razem z `wsHttpContextBinding` informacjami o stanie, które przechodzą w nagłówkach HTTP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>

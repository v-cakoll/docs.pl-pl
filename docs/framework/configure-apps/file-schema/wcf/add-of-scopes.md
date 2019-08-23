---
title: <add> dla <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926627"
---
# <a name="add-of-scopes"></a>\<Dodaj > \<zakresów >
Dodaje niestandardowy identyfikator URI zakresu, którego można użyć do filtrowania punktów końcowych usługi podczas zapytania.  
  
\<system.ServiceModel>  
\<> zachowań  
\<endpointBehaviors>  
\<> zachowania  
\<endpointDiscovery>  
\<zakresy >  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|zakres|Identyfikator URI zawierający zakres informacji dla punktu końcowego, który może być używany w kryterium dopasowywania do znajdowania usług.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zakresy >](scopes.md)|Zawiera kolekcję elementów konfiguracji, które określają niestandardowe identyfikatory URI, których można użyć do filtrowania punktów końcowych usługi podczas zapytania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>

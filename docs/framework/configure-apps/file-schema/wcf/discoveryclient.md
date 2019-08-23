---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919275"
---
# <a name="discoveryclient"></a>\<discoveryClient>
Element konfiguracji do tworzenia niestandardowego powiązania, które umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.  
  
\<system.serviceModel>  
\<> powiązań  
\<customBinding>  
\<> powiązania  
\<discoveryClient>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|discoveryEndpoint|Ciąg zawierający nazwę punktu końcowego odnajdywania, który umożliwia aplikacji klienckiej automatyczne wyszukiwanie usługi wykrywalnej i znajdowanie jej adresu w czasie wykonywania.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<standardEndpoints >](standardendpoints.md)|Element konfiguracji, który dostarcza zestaw kryteriów używanych przez aplikację kliencką do wyszukiwania usługi odnajdywania. Kryteria mogą być pogrupowane w kryteria wyszukiwania (określające, które usługi są szukane) i znajdować kryteria zakończenia (jak długo wyszukiwanie powinno trwać).|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> powiązania](../../../misc/binding.md)|Definiuje wszystkie możliwości powiązań niestandardowego powiązania.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>

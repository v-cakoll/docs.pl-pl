---
title: <extensions> Sekcja
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268291"
---
# <a name="extensions-section"></a>\<Rozszerzenia > sekcji
Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.  
  
\<system.ServiceModel>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Ta sekcja zawiera elementy podrzędne, które określają zachowanie rozszerzeń, które umożliwiają użytkownikowi dostosowywanie zachowania usługi lub punktu końcowego.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Ta sekcja umożliwia zastosowanie elementu niestandardowego powiązania z maszyny lub pliku konfiguracji aplikacji.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Ta sekcja zawiera elementy podrzędne, określających rozszerzeń powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.ServiceModel|Element główny wszystkich elementów konfiguracji programu WCF.|

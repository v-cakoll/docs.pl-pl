---
title: "&lt;extensions&gt; — sekcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04905ae0f40a1f9ca88b4a04d4e49b0ce895ca56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltextensionsgt-section"></a>&lt;extensions&gt; — sekcja
Ta sekcja konfiguracji zawiera Kolekcja rozszerzeń, które umożliwiają użytkownikowi utworzenie powiązań zdefiniowanych przez użytkownika, zachowania i inne aspekty rozszerzeń.  
  
\<System. ServiceModel >  
  
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
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Ta sekcja zawiera elementy podrzędne, które Określ rozszerzenia powiązania, które umożliwiają użytkownikowi dostosowywanie powiązania.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Ta sekcja zawiera elementy podrzędne, które rejestruje standardowych punktów końcowych.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.ServiceModel|Element główny wszystkich elementów konfiguracji usługi WCF.|

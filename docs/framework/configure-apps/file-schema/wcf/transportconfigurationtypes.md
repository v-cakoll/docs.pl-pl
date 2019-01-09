---
title: '&lt;transportConfigurationTypes&gt;'
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: 5a51450d198ea395098f8a6a38d9104d0fe8538b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145474"
---
# <a name="lttransportconfigurationtypesgt"></a>&lt;transportConfigurationTypes&gt;
Reprezentuje kolekcję elementów konfiguracji, które identyfikują typ danego transportu. Może to służyć do dodawania niestandardowych protokołów WAS.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
\<transportConfigurationTypes >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Nazwa transportu|  
|transportConfigurationType|Typ, który implementuje transportu|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|Dodaje element konfiguracji, który identyfikuje typ danego transportu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)

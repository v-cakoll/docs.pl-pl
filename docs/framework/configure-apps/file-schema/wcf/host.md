---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 3d1f7774f61060880a5c3b0327bdd6c2cc4dd74e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103002"
---
# <a name="host"></a>\<host>
Określa ustawienia dla usługi hosta.  
  
 \<system.ServiceModel>  
\<services>  
\<service>  
\<host>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddresses>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekcja `baseAddress` elementy, które określa adres podstawowy, używany przez hosta usługi.|  
|[\<timeOuts>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|Element konfiguracji, który określa przedział czasu dozwolony usługi hosta na otwarcie lub zamknięcie.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<service>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|Określa ustawienia usługi Windows Communication Foundation (WCF).|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)

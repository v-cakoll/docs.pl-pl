---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: dc4b31e729f9037da101bdf3e6cde28e91b1a070
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277020"
---
# <a name="baseaddresses"></a>\<baseAddresses>
Reprezentuje kolekcję `baseAddress` elementy, które są adresami podstawowymi dla usługi hosta w środowisku. Jeśli adres podstawowy jest obecny, można skonfigurować punkty końcowe z adresami określany względem adresu podstawowego.  
  
 \<system.ServiceModel>  
\<client>  
\<punkt końcowy >  
\<host>  
\<baseAddresses>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
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
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|Element konfiguracji określający adres podstawowy, używany przez hosta usługi.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<host>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|Element konfiguracji, który określa ustawienia dla usługi hosta.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)

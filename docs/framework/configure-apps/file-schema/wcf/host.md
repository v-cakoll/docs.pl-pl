---
title: '&lt;host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 1fb35058d407d0fbae78092bb4ccd45b0aaa40e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702031"
---
# <a name="lthostgt"></a>&lt;host&gt;
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

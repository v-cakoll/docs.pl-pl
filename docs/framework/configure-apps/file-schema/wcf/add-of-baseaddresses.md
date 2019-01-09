---
title: '&lt;add&gt; w &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149088"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a>&lt;add&gt; w &lt;baseAddresses&gt;
Reprezentuje element konfiguracji określający adres podstawowy, używany przez hosta usługi.  
  
 \<system.ServiceModel>  
\<Klient >  
\<punkt końcowy >  
\<host >  
\<baseAddresses >  
\<baseAddress >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`baseAddress`|Ciąg, który określa adres bazowy używany przez hosta usługi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|Kolekcja `baseAddress` elementów.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [Hosting](../../../../../docs/framework/wcf/feature-details/hosting.md)

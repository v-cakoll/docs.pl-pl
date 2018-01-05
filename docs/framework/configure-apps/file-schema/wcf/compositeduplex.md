---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80c8f3954cccbce8e93ab9d8c516fdfd6c7bff10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<compositeDuplex >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|ClientBaseAddress|Identyfikator URI, który ustawia adres kanału powrotnego w trybie duplex. Usługa używa ten adres, aby upewnić się, skontaktuj się z pomocą i nawiązania połączenia z klientem.<br /><br /> Jeśli ten atrybut nie jest ustawiona, domyślny adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany. Wartość domyślna to `null`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używany z transportu, które nie zezwalają na komunikacji dupleksowej natywnie, na przykład HTTP. TCP, natomiast natywnie umożliwia komunikacji dupleksowej i nie wymaga użycia tego elementu powiązania dla usługi wysłać wiadomości zwrotnie do klienta.  
  
 Klient musi ujawniać adres usługi upewnić się, skontaktuj się z pomocą i nawiązania połączenia. Ten adres klienta jest zapewniana przez `clientBaseAddress` atrybutu. Należy pamiętać, że Windows Communication Foundation (WCF) auto generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.  
  
## <a name="example"></a>Przykład  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

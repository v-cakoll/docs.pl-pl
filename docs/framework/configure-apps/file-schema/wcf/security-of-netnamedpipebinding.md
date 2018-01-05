---
title: '&lt;security&gt; w &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fb5d1d3a767a9f4034473baad271c40677cedca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a>&lt;security&gt; w &lt;netNamedPipeBinding&gt;
Definiuje ustawienia zabezpieczeń dla powiązania.  
  
 \<System. ServiceModel >  
\<powiązania >  
\<netNamedPipeBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|tryb|Określa typ zabezpieczeń, która jest stosowana do tego powiązania. Prawidłowe wartości są następujące:<br /><br /> -Brak: Powoduje wyłączenie zabezpieczeń.<br />-Transport: Zabezpieczenia za pomocą zabezpieczeń transportu na podstawie podstawowej. Jest możliwe kontrolowanie poziomu ochrony, w tym trybie.<br />— Wartość domyślna to transportu. Ten atrybut jest typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|transport|Definiuje ustawienia zabezpieczeń dla transportu. Ten element jest typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|powiązanie|Element powiązania [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Wybieranie typu poświadczeń](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)

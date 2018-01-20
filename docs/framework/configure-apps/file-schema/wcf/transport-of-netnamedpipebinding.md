---
title: '&lt;transport&gt; w &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84811c70f2f3608c10d8886900169f804a8c9b62
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a>&lt;transport&gt; w &lt;netNamedPipeBinding&gt;
Definiuje ustawienia zabezpieczeń transportu nazwanego potoku.  
  
 \<system.ServiceModel>  
\<powiązania >  
\<netNamedPipeBinding>  
\<Powiązanie >  
\<security>  
\<transport>  
  
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
|protectionLevel|Określa poziom ochrony nazwanego potoku. Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane. Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak ochrony.<br />-Znak: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.<br /><br /> Wartość domyślna to EncryptAndSign.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|Definiuje ustawienia zabezpieczeń dla powiązania.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)

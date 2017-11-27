---
title: '&lt;Obiekt windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a>&lt;Obiekt windowsStreamSecurity&gt;
Określ ustawienia zabezpieczenia strumienia systemu Windows niestandardowego powiązania.  
  
 \<system.serviceModel >  
\<powiązania >  
\<customBinding >  
\<Powiązanie >  
\<Obiekt windowsStreamSecurity >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|protectionLevel|Definiuje zabezpieczenia na poziomie wiadomości. Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane. Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak ochrony.<br />-Znak: Komunikaty są podpisane.<br />-EncryptAndSign: Komunikaty są podpisane i zaszyfrowane.<br /><br /> Wartość domyślna to EncryptAndSign.<br /><br /> Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Powiązanie >](../../../../../docs/framework/misc/binding.md)|Definiuje wszystkie możliwości powiązania niestandardowego powiązania.|  
  
## <a name="remarks"></a>Uwagi  
 Transporty Użyj protokołu zorientowanych strumieniowo np. TCP i nazwane potoki obsługują uaktualnienia transportu na podstawie strumienia. W szczególności WCF udostępnia aktualizacje zabezpieczeń. Konfiguracja zabezpieczeń transportu jest hermetyzowany przez ten element konfiguracji za pomocą [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), które można konfigurować i dodane do powiązania niestandardowego  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

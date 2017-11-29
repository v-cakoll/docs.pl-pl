---
title: '&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0fb9ff476812b6b889750e8eb7b80efce801f041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a>&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;
Określa ustawienia dla usługi bezpiecznej konwersacji.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<serviceCredentials >  
\<secureConversationAuthentication >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`securityStateEncoderType`|Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> do użycia.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu konfiguracji, aby określić listę znanych oświadczenia dla serializacji plików cookie Token kontekstu zabezpieczeń (SCT), a także kodera do kodowania i ochronę plików cookie. Aby uzyskać więcej informacji dotyczących SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

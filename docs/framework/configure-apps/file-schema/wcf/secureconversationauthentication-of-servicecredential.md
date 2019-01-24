---
title: '&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 11ce6dcd2f075606cf808992edb99328daec3fba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696417"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a>&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;
Określa ustawienia dla usługi bezpiecznej konwersacji.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceCredentials>  
\<secureConversationAuthentication>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`securityStateEncoderType`|Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> ma być używany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji umożliwia określenie listy znanych oświadczenia dla tokenu kontekstu zabezpieczeń (SCT) serializacji plików cookie, a także koder do zakodowania i ochronę informacji z plików cookie. Aby uzyskać więcej informacji na temat SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

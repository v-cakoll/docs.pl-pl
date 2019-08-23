---
title: <secureConversationAuthentication> dla <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935838"
---
# <a name="secureconversationauthentication-of-servicecredential"></a>\<secureConversationAuthentication > \<> servicecredential
Określa ustawienia usługi bezpiecznej konwersacji.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
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
|`securityStateEncoderType`|Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , który ma być używany.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj tego elementu konfiguracji, aby określić listę znanych typów roszczeń dla serializacji plików cookie kontekstu zabezpieczeń (SCT), a także kodera do kodowania i zabezpieczania informacji plików cookie. Aby uzyskać więcej informacji na temat SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

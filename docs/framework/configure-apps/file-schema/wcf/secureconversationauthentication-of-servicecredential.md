---
title: <secureConversationAuthentication> dla <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399943"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="5f69f-102">\<secureConversationAuthentication> dla \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="5f69f-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="5f69f-103">Określa ustawienia usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="5f69f-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="5f69f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f69f-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f69f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5f69f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5f69f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f69f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f69f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5f69f-107">Attributes</span></span>  
  
|<span data-ttu-id="5f69f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5f69f-108">Attribute</span></span>|<span data-ttu-id="5f69f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5f69f-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="5f69f-110">Ciąg określający typ, który <xref:System.ServiceModel.Security.SecurityStateEncoder> ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5f69f-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f69f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5f69f-111">Child Elements</span></span>  
 <span data-ttu-id="5f69f-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="5f69f-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f69f-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5f69f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5f69f-114">Element</span><span class="sxs-lookup"><span data-stu-id="5f69f-114">Element</span></span>|<span data-ttu-id="5f69f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5f69f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="5f69f-116">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="5f69f-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f69f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f69f-117">Remarks</span></span>  
 <span data-ttu-id="5f69f-118">Użyj tego elementu konfiguracji, aby określić listę znanych typów roszczeń dla serializacji plików cookie kontekstu zabezpieczeń (SCT), a także kodera do kodowania i zabezpieczania informacji plików cookie.</span><span class="sxs-lookup"><span data-stu-id="5f69f-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="5f69f-119">Aby uzyskać więcej informacji na temat SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential> .</span><span class="sxs-lookup"><span data-stu-id="5f69f-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f69f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f69f-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

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
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="5db99-102">\<secureConversationAuthentication > \<> servicecredential</span><span class="sxs-lookup"><span data-stu-id="5db99-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="5db99-103">Określa ustawienia usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="5db99-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="5db99-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5db99-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5db99-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="5db99-105">\<behaviors></span></span>  
<span data-ttu-id="5db99-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5db99-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5db99-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="5db99-107">\<behavior></span></span>  
<span data-ttu-id="5db99-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="5db99-108">\<serviceCredentials></span></span>  
<span data-ttu-id="5db99-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="5db99-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db99-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5db99-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5db99-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5db99-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5db99-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5db99-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5db99-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5db99-113">Attributes</span></span>  
  
|<span data-ttu-id="5db99-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5db99-114">Attribute</span></span>|<span data-ttu-id="5db99-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5db99-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="5db99-116">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="5db99-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5db99-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5db99-117">Child Elements</span></span>  
 <span data-ttu-id="5db99-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="5db99-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5db99-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5db99-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5db99-120">Element</span><span class="sxs-lookup"><span data-stu-id="5db99-120">Element</span></span>|<span data-ttu-id="5db99-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5db99-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5db99-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="5db99-122">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="5db99-123">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="5db99-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5db99-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5db99-124">Remarks</span></span>  
 <span data-ttu-id="5db99-125">Użyj tego elementu konfiguracji, aby określić listę znanych typów roszczeń dla serializacji plików cookie kontekstu zabezpieczeń (SCT), a także kodera do kodowania i zabezpieczania informacji plików cookie.</span><span class="sxs-lookup"><span data-stu-id="5db99-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="5db99-126">Aby uzyskać więcej informacji na temat SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="5db99-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db99-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5db99-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

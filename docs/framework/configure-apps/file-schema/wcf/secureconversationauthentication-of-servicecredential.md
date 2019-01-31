---
title: <secureConversationAuthentication> z <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 13e9312e4c4eade003fec77909a743009aa9bca7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278528"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="3fa83-102">\<secureConversationAuthentication > z \<serviceCredential ></span><span class="sxs-lookup"><span data-stu-id="3fa83-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="3fa83-103">Określa ustawienia dla usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="3fa83-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="3fa83-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3fa83-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3fa83-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="3fa83-105">\<behaviors></span></span>  
<span data-ttu-id="3fa83-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3fa83-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3fa83-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="3fa83-107">\<behavior></span></span>  
<span data-ttu-id="3fa83-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3fa83-108">\<serviceCredentials></span></span>  
<span data-ttu-id="3fa83-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="3fa83-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fa83-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fa83-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3fa83-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3fa83-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3fa83-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3fa83-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3fa83-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3fa83-113">Attributes</span></span>  
  
|<span data-ttu-id="3fa83-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3fa83-114">Attribute</span></span>|<span data-ttu-id="3fa83-115">Opis</span><span class="sxs-lookup"><span data-stu-id="3fa83-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="3fa83-116">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> ma być używany.</span><span class="sxs-lookup"><span data-stu-id="3fa83-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3fa83-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3fa83-117">Child Elements</span></span>  
 <span data-ttu-id="3fa83-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="3fa83-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3fa83-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3fa83-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3fa83-120">Element</span><span class="sxs-lookup"><span data-stu-id="3fa83-120">Element</span></span>|<span data-ttu-id="3fa83-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3fa83-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3fa83-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3fa83-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="3fa83-123">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="3fa83-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fa83-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fa83-124">Remarks</span></span>  
 <span data-ttu-id="3fa83-125">Ten element konfiguracji umożliwia określenie listy znanych oświadczenia dla tokenu kontekstu zabezpieczeń (SCT) serializacji plików cookie, a także koder do zakodowania i ochronę informacji z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3fa83-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="3fa83-126">Aby uzyskać więcej informacji na temat SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="3fa83-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fa83-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fa83-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

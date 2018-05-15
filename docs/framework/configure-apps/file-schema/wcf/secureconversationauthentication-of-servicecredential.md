---
title: '&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7b56d12793ad35e6f951638465e77b92a66a6fd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="b98f7-102">&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="b98f7-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="b98f7-103">Określa ustawienia dla usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="b98f7-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="b98f7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b98f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b98f7-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b98f7-105">\<behaviors></span></span>  
<span data-ttu-id="b98f7-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b98f7-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b98f7-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b98f7-107">\<behavior></span></span>  
<span data-ttu-id="b98f7-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b98f7-108">\<serviceCredentials></span></span>  
<span data-ttu-id="b98f7-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b98f7-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b98f7-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b98f7-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b98f7-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b98f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b98f7-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b98f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b98f7-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b98f7-113">Attributes</span></span>  
  
|<span data-ttu-id="b98f7-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b98f7-114">Attribute</span></span>|<span data-ttu-id="b98f7-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b98f7-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="b98f7-116">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> do użycia.</span><span class="sxs-lookup"><span data-stu-id="b98f7-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b98f7-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b98f7-117">Child Elements</span></span>  
 <span data-ttu-id="b98f7-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b98f7-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b98f7-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b98f7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b98f7-120">Element</span><span class="sxs-lookup"><span data-stu-id="b98f7-120">Element</span></span>|<span data-ttu-id="b98f7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b98f7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b98f7-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b98f7-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="b98f7-123">Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="b98f7-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b98f7-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b98f7-124">Remarks</span></span>  
 <span data-ttu-id="b98f7-125">Użyj tego elementu konfiguracji, aby określić listę znanych oświadczenia dla serializacji plików cookie Token kontekstu zabezpieczeń (SCT), a także kodera do kodowania i ochronę plików cookie.</span><span class="sxs-lookup"><span data-stu-id="b98f7-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="b98f7-126">Aby uzyskać więcej informacji dotyczących SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="b98f7-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b98f7-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b98f7-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

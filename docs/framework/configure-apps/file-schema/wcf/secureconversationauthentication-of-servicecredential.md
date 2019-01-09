---
title: '&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 2c8479c4d8a321c822d49bdc24f359ffad5500e9
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147190"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="9c8b8-102">&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="9c8b8-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="9c8b8-103">Określa ustawienia dla usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="9c8b8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9c8b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9c8b8-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="9c8b8-105">\<behaviors></span></span>  
<span data-ttu-id="9c8b8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9c8b8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9c8b8-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="9c8b8-107">\<behavior></span></span>  
<span data-ttu-id="9c8b8-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9c8b8-108">\<serviceCredentials></span></span>  
<span data-ttu-id="9c8b8-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="9c8b8-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c8b8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c8b8-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c8b8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c8b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9c8b8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c8b8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c8b8-113">Attributes</span></span>  
  
|<span data-ttu-id="9c8b8-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9c8b8-114">Attribute</span></span>|<span data-ttu-id="9c8b8-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9c8b8-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="9c8b8-116">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c8b8-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c8b8-117">Child Elements</span></span>  
 <span data-ttu-id="9c8b8-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c8b8-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c8b8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9c8b8-120">Element</span><span class="sxs-lookup"><span data-stu-id="9c8b8-120">Element</span></span>|<span data-ttu-id="9c8b8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9c8b8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c8b8-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9c8b8-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="9c8b8-123">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c8b8-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c8b8-124">Remarks</span></span>  
 <span data-ttu-id="9c8b8-125">Ten element konfiguracji umożliwia określenie listy znanych oświadczenia dla tokenu kontekstu zabezpieczeń (SCT) serializacji plików cookie, a także koder do zakodowania i ochronę informacji z plików cookie.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="9c8b8-126">Aby uzyskać więcej informacji na temat SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="9c8b8-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8b8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c8b8-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

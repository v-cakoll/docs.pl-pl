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
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="d6120-102">&lt;secureConversationAuthentication&gt; w &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="d6120-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="d6120-103">Określa ustawienia dla usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="d6120-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="d6120-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d6120-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d6120-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d6120-105">\<behaviors></span></span>  
<span data-ttu-id="d6120-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d6120-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d6120-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d6120-107">\<behavior></span></span>  
<span data-ttu-id="d6120-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d6120-108">\<serviceCredentials></span></span>  
<span data-ttu-id="d6120-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d6120-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6120-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6120-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6120-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d6120-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6120-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d6120-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6120-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d6120-113">Attributes</span></span>  
  
|<span data-ttu-id="d6120-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d6120-114">Attribute</span></span>|<span data-ttu-id="d6120-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d6120-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="d6120-116">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> do użycia.</span><span class="sxs-lookup"><span data-stu-id="d6120-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6120-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d6120-117">Child Elements</span></span>  
 <span data-ttu-id="d6120-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="d6120-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6120-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d6120-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d6120-120">Element</span><span class="sxs-lookup"><span data-stu-id="d6120-120">Element</span></span>|<span data-ttu-id="d6120-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d6120-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6120-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d6120-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="d6120-123">Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="d6120-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6120-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6120-124">Remarks</span></span>  
 <span data-ttu-id="d6120-125">Użyj tego elementu konfiguracji, aby określić listę znanych oświadczenia dla serializacji plików cookie Token kontekstu zabezpieczeń (SCT), a także kodera do kodowania i ochronę plików cookie.</span><span class="sxs-lookup"><span data-stu-id="d6120-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="d6120-126">Aby uzyskać więcej informacji dotyczących SCT, zobacz <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="d6120-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6120-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6120-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

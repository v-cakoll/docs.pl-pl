---
title: <secureConversationAuthentication> dla <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399943"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="3ea10-102">\<secureConversationAuthentication > \<> servicecredential</span><span class="sxs-lookup"><span data-stu-id="3ea10-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="3ea10-103">Określa ustawienia usługi bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="3ea10-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="3ea10-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3ea10-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3ea10-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="3ea10-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="3ea10-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="3ea10-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="3ea10-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="3ea10-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<secureConversationAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="3ea10-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea10-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ea10-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea10-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ea10-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea10-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ea10-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea10-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ea10-114">Attributes</span></span>  
  
|<span data-ttu-id="3ea10-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ea10-115">Attribute</span></span>|<span data-ttu-id="3ea10-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3ea10-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="3ea10-117">Ciąg określający typ <xref:System.ServiceModel.Security.SecurityStateEncoder> , który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="3ea10-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea10-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ea10-118">Child Elements</span></span>  
 <span data-ttu-id="3ea10-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ea10-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea10-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ea10-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea10-121">Element</span><span class="sxs-lookup"><span data-stu-id="3ea10-121">Element</span></span>|<span data-ttu-id="3ea10-122">Opis</span><span class="sxs-lookup"><span data-stu-id="3ea10-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ea10-123">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3ea10-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="3ea10-124">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="3ea10-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea10-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ea10-125">Remarks</span></span>  
 <span data-ttu-id="3ea10-126">Użyj tego elementu konfiguracji, aby określić listę znanych typów roszczeń dla serializacji plików cookie kontekstu zabezpieczeń (SCT), a także kodera do kodowania i zabezpieczania informacji plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3ea10-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="3ea10-127">Aby uzyskać więcej informacji na temat SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="3ea10-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea10-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ea10-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>

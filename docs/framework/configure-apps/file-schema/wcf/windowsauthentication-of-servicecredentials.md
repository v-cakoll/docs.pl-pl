---
title: <windowsAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ded04f6e87fce2e12dac8f681ba2d4178f8fd204
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399112"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="73df4-102">\<WindowsAuthentication > z \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="73df4-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="73df4-103">Określa ustawienia poświadczenia usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="73df4-103">Specifies the settings of a Windows service credential.</span></span>  
  
<span data-ttu-id="73df4-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="73df4-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="73df4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="73df4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="73df4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="73df4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> ServiceCredentials**](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="73df4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="73df4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="73df4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73df4-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="73df4-111">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73df4-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73df4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="73df4-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73df4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73df4-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73df4-114">Attributes</span></span>  
  
|<span data-ttu-id="73df4-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="73df4-115">Attribute</span></span>|<span data-ttu-id="73df4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="73df4-116">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="73df4-117">Opcjonalny atrybut logiczny, który określa, czy system zawiera grupy systemu Windows w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="73df4-117">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="73df4-118">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="73df4-118">The default is `true`.</span></span><br /><br /> <span data-ttu-id="73df4-119">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy.</span><span class="sxs-lookup"><span data-stu-id="73df4-119">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="73df4-120">Ustaw ten atrybut na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="73df4-120">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="73df4-121">Opcjonalny atrybut logiczny, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania.</span><span class="sxs-lookup"><span data-stu-id="73df4-121">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="73df4-122">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="73df4-122">The default is `false`.</span></span><br /><br /> <span data-ttu-id="73df4-123">Gdy atrybut powiązania jest ustawiony na `Windows`, system nie zezwala na anonimowe wywołania. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="73df4-123">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="73df4-124">Oznacza to, że w celu uzyskania dostępu do systemu są dozwolone tylko uwierzytelnione wywołania domeny lub grupy roboczej.</span><span class="sxs-lookup"><span data-stu-id="73df4-124">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="73df4-125">To zachowanie można zastąpić za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="73df4-125">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="73df4-126">Użyj tego ustawienia z największą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="73df4-126">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73df4-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73df4-127">Child Elements</span></span>  
 <span data-ttu-id="73df4-128">Brak.</span><span class="sxs-lookup"><span data-stu-id="73df4-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73df4-129">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73df4-129">Parent Elements</span></span>  
  
|<span data-ttu-id="73df4-130">Element</span><span class="sxs-lookup"><span data-stu-id="73df4-130">Element</span></span>|<span data-ttu-id="73df4-131">Opis</span><span class="sxs-lookup"><span data-stu-id="73df4-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73df4-132">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="73df4-132">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="73df4-133">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="73df4-133">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73df4-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73df4-134">Remarks</span></span>  
 <span data-ttu-id="73df4-135">Użyj tego elementu, aby określić, `allowAnonymousLogons` czy zezwolić na dostęp anonimowym użytkownikom systemu Windows przez ustawienie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="73df4-135">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="73df4-136">Można również określić, `includeWindowsGroups` czy mają zostać dołączone informacje o grupie, do których użytkownicy należą do AuthorizationContext przez ustawienie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="73df4-136">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="73df4-137">Jeśli jest ustawiona na `true` (ustawienie domyślne), usługa może określić grupy systemu Windows, do których należy klient.</span><span class="sxs-lookup"><span data-stu-id="73df4-137">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73df4-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73df4-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>

---
title: <windowsAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 81793b0d58a95166bc23f98d46ce94a5f1e1d018
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940291"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="9aeac-102">\<WindowsAuthentication > z \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="9aeac-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="9aeac-103">Określa ustawienia poświadczenia usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9aeac-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="9aeac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9aeac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9aeac-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="9aeac-105">\<behaviors></span></span>  
<span data-ttu-id="9aeac-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9aeac-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9aeac-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="9aeac-107">\<behavior></span></span>  
<span data-ttu-id="9aeac-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9aeac-108">\<serviceCredentials></span></span>  
<span data-ttu-id="9aeac-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="9aeac-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aeac-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9aeac-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9aeac-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9aeac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9aeac-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9aeac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9aeac-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9aeac-113">Attributes</span></span>  
  
|<span data-ttu-id="9aeac-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9aeac-114">Attribute</span></span>|<span data-ttu-id="9aeac-115">Opis</span><span class="sxs-lookup"><span data-stu-id="9aeac-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="9aeac-116">Opcjonalny atrybut logiczny, który określa, czy system zawiera grupy systemu Windows w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9aeac-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="9aeac-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9aeac-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="9aeac-118">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ skutkuje rozwinięciem całej grupy.</span><span class="sxs-lookup"><span data-stu-id="9aeac-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="9aeac-119">Ustaw ten atrybut na `false` , jeśli nie ma potrzeby ustanawiania listy grup, do których należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="9aeac-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="9aeac-120">Opcjonalny atrybut logiczny, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania.</span><span class="sxs-lookup"><span data-stu-id="9aeac-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="9aeac-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9aeac-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="9aeac-122">Gdy atrybut powiązania jest ustawiony na `Windows`, system nie zezwala na anonimowe wywołania. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="9aeac-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="9aeac-123">Oznacza to, że w celu uzyskania dostępu do systemu są dozwolone tylko uwierzytelnione wywołania domeny lub grupy roboczej.</span><span class="sxs-lookup"><span data-stu-id="9aeac-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="9aeac-124">To zachowanie można zastąpić za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9aeac-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="9aeac-125">Użyj tego ustawienia z największą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="9aeac-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9aeac-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9aeac-126">Child Elements</span></span>  
 <span data-ttu-id="9aeac-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="9aeac-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9aeac-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9aeac-128">Parent Elements</span></span>  
  
|<span data-ttu-id="9aeac-129">Element</span><span class="sxs-lookup"><span data-stu-id="9aeac-129">Element</span></span>|<span data-ttu-id="9aeac-130">Opis</span><span class="sxs-lookup"><span data-stu-id="9aeac-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9aeac-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9aeac-131">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="9aeac-132">Określa poświadczenie, które ma być używane w uwierzytelnianiu usługi i ustawień związanych z walidacją poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="9aeac-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aeac-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9aeac-133">Remarks</span></span>  
 <span data-ttu-id="9aeac-134">Użyj tego elementu, aby określić, `allowAnonymousLogons` czy zezwolić na dostęp anonimowym użytkownikom systemu Windows przez ustawienie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9aeac-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="9aeac-135">Można również określić, `includeWindowsGroups` czy mają zostać dołączone informacje o grupie, do których użytkownicy należą do AuthorizationContext przez ustawienie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9aeac-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="9aeac-136">Jeśli jest ustawiona na `true` (ustawienie domyślne), usługa może określić grupy systemu Windows, do których należy klient.</span><span class="sxs-lookup"><span data-stu-id="9aeac-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aeac-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aeac-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>

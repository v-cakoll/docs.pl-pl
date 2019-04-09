---
title: <windowsAuthentication> z <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ffddbae7effabcdafdc2638d588bbbf3e42d2c2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200392"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="2af19-102">\<windowsAuthentication > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2af19-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="2af19-103">Określa ustawienia poświadczenia usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="2af19-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="2af19-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2af19-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2af19-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2af19-105">\<behaviors></span></span>  
<span data-ttu-id="2af19-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2af19-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2af19-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2af19-107">\<behavior></span></span>  
<span data-ttu-id="2af19-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2af19-108">\<serviceCredentials></span></span>  
<span data-ttu-id="2af19-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="2af19-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af19-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="2af19-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2af19-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2af19-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2af19-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2af19-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2af19-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2af19-113">Attributes</span></span>  
  
|<span data-ttu-id="2af19-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2af19-114">Attribute</span></span>|<span data-ttu-id="2af19-115">Opis</span><span class="sxs-lookup"><span data-stu-id="2af19-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="2af19-116">Opcjonalny logiczny atrybut, który określa, czy system zawiera grupy Windows w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2af19-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="2af19-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2af19-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="2af19-118">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="2af19-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="2af19-119">Ustaw ten atrybut na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="2af19-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="2af19-120">Opcjonalny logiczny atrybut, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania.</span><span class="sxs-lookup"><span data-stu-id="2af19-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="2af19-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2af19-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="2af19-122">Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `Windows`, system nie zezwala na dostęp anonimowy wywołań.</span><span class="sxs-lookup"><span data-stu-id="2af19-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="2af19-123">Oznacza to, tym tylko domeny lub grupy roboczej uwierzytelniony obiekty wywołujące mogą uzyskać dostęp do systemu.</span><span class="sxs-lookup"><span data-stu-id="2af19-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="2af19-124">To zachowanie można zastąpić za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2af19-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="2af19-125">Użyj tego ustawienia z najwyższą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="2af19-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2af19-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2af19-126">Child Elements</span></span>  
 <span data-ttu-id="2af19-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="2af19-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2af19-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2af19-128">Parent Elements</span></span>  
  
|<span data-ttu-id="2af19-129">Element</span><span class="sxs-lookup"><span data-stu-id="2af19-129">Element</span></span>|<span data-ttu-id="2af19-130">Opis</span><span class="sxs-lookup"><span data-stu-id="2af19-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2af19-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2af19-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="2af19-132">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="2af19-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2af19-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2af19-133">Remarks</span></span>  
 <span data-ttu-id="2af19-134">Użyj tego elementu, aby określić, czy chcesz zezwolić anonimowym użytkownikom Windows dostępu przez ustawienie `allowAnonymousLogons` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2af19-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="2af19-135">Można również określić, czy do uwzględnienia informacji o grupie, do której należą użytkownicy w autoryzacji, ustawiając `includeWindowsGroups` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2af19-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="2af19-136">Jeśli jest równa `true` (ustawienie domyślne), ta usługa może określić grupy Windows, do której należy dany klient.</span><span class="sxs-lookup"><span data-stu-id="2af19-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af19-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2af19-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>

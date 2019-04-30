---
title: <windowsAuthentication> dla <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: ffddbae7effabcdafdc2638d588bbbf3e42d2c2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769697"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="56736-102">\<windowsAuthentication > z \<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="56736-102">\<windowsAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="56736-103">Określa ustawienia poświadczenia usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="56736-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="56736-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56736-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="56736-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="56736-105">\<behaviors></span></span>  
<span data-ttu-id="56736-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="56736-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="56736-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="56736-107">\<behavior></span></span>  
<span data-ttu-id="56736-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="56736-108">\<serviceCredentials></span></span>  
<span data-ttu-id="56736-109">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="56736-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56736-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="56736-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56736-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="56736-111">Attributes and Elements</span></span>  
 <span data-ttu-id="56736-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="56736-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56736-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="56736-113">Attributes</span></span>  
  
|<span data-ttu-id="56736-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="56736-114">Attribute</span></span>|<span data-ttu-id="56736-115">Opis</span><span class="sxs-lookup"><span data-stu-id="56736-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="56736-116">Opcjonalny logiczny atrybut, który określa, czy system zawiera grupy Windows w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="56736-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="56736-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="56736-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="56736-118">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ powoduje ona wystąpił błąd rozszerzania grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="56736-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="56736-119">Ustaw ten atrybut na `false` Jeśli potrzebujesz nawiązać listy grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="56736-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="56736-120">Opcjonalny logiczny atrybut, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania.</span><span class="sxs-lookup"><span data-stu-id="56736-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="56736-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="56736-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="56736-122">Gdy `clientCredentialType` ma ustawioną wartość atrybutu powiązania `Windows`, system nie zezwala na dostęp anonimowy wywołań.</span><span class="sxs-lookup"><span data-stu-id="56736-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="56736-123">Oznacza to, tym tylko domeny lub grupy roboczej uwierzytelniony obiekty wywołujące mogą uzyskać dostęp do systemu.</span><span class="sxs-lookup"><span data-stu-id="56736-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="56736-124">To zachowanie można zastąpić za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56736-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="56736-125">Użyj tego ustawienia z najwyższą ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="56736-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56736-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="56736-126">Child Elements</span></span>  
 <span data-ttu-id="56736-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="56736-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56736-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="56736-128">Parent Elements</span></span>  
  
|<span data-ttu-id="56736-129">Element</span><span class="sxs-lookup"><span data-stu-id="56736-129">Element</span></span>|<span data-ttu-id="56736-130">Opis</span><span class="sxs-lookup"><span data-stu-id="56736-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56736-131">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="56736-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="56736-132">Określa poświadczenie do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="56736-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56736-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56736-133">Remarks</span></span>  
 <span data-ttu-id="56736-134">Użyj tego elementu, aby określić, czy chcesz zezwolić anonimowym użytkownikom Windows dostępu przez ustawienie `allowAnonymousLogons` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56736-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="56736-135">Można również określić, czy do uwzględnienia informacji o grupie, do której należą użytkownicy w autoryzacji, ustawiając `includeWindowsGroups` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="56736-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="56736-136">Jeśli jest równa `true` (ustawienie domyślne), ta usługa może określić grupy Windows, do której należy dany klient.</span><span class="sxs-lookup"><span data-stu-id="56736-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56736-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56736-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>

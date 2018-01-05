---
title: '&lt;windowsAuthentication&gt; w &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b6043b35ea9dbed1e1e6e170035436038334b34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltwindowsauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="5da28-102">&lt;windowsAuthentication&gt; w &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="5da28-102">&lt;windowsAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="5da28-103">Określa ustawienia poświadczenia usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5da28-103">Specifies the settings of a Windows service credential.</span></span>  
  
 <span data-ttu-id="5da28-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5da28-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5da28-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5da28-105">\<behaviors></span></span>  
<span data-ttu-id="5da28-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5da28-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5da28-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5da28-107">\<behavior></span></span>  
<span data-ttu-id="5da28-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5da28-108">\<serviceCredentials></span></span>  
<span data-ttu-id="5da28-109">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5da28-109">\<windowsAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da28-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5da28-110">Syntax</span></span>  
  
```xml  
<windowsAuthentication  
      allowAnonymousLogons="Boolean"  
      includeWindowsGroups="Boolean" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5da28-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5da28-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5da28-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5da28-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5da28-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5da28-113">Attributes</span></span>  
  
|<span data-ttu-id="5da28-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5da28-114">Attribute</span></span>|<span data-ttu-id="5da28-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5da28-115">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="5da28-116">Opcjonalny logiczny atrybut, który określa, czy system zawiera grupy systemu Windows w kontekście zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5da28-116">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="5da28-117">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="5da28-117">The default is `true`.</span></span><br /><br /> <span data-ttu-id="5da28-118">Ustawienie tego atrybutu na `true` ma wpływ na wydajność, ponieważ jej wynikiem rozszerzenia grupy pełnej.</span><span class="sxs-lookup"><span data-stu-id="5da28-118">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="5da28-119">Ten atrybut na `false` Jeśli nie musisz ustanowić listę grup należy użytkownik.</span><span class="sxs-lookup"><span data-stu-id="5da28-119">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="5da28-120">Opcjonalny logiczny atrybut, który określa, czy są dozwolone anonimowe, nieuwierzytelnione wywoływania.</span><span class="sxs-lookup"><span data-stu-id="5da28-120">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="5da28-121">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="5da28-121">The default is `false`.</span></span><br /><br /> <span data-ttu-id="5da28-122">Gdy `clientCredentialType` ustawiono atrybut powiązania `Windows`, systemu nie zezwala na anonimowe obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="5da28-122">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="5da28-123">Oznacza to, że tylko domeny lub grupy roboczej uwierzytelniony elementy wywołujące mogą uzyskać dostępu do systemu.</span><span class="sxs-lookup"><span data-stu-id="5da28-123">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="5da28-124">Aby zmienić to zachowanie, należy za pomocą tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5da28-124">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="5da28-125">Użyj tego ustawienia z najwyższą ostrożność.</span><span class="sxs-lookup"><span data-stu-id="5da28-125">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5da28-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5da28-126">Child Elements</span></span>  
 <span data-ttu-id="5da28-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="5da28-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5da28-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5da28-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5da28-129">Element</span><span class="sxs-lookup"><span data-stu-id="5da28-129">Element</span></span>|<span data-ttu-id="5da28-130">Opis</span><span class="sxs-lookup"><span data-stu-id="5da28-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5da28-131">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5da28-131">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="5da28-132">Określa poświadczenia do użycia w uwierzytelnianiu usługi i ustawień dotyczących walidacji poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="5da28-132">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5da28-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5da28-133">Remarks</span></span>  
 <span data-ttu-id="5da28-134">Użyj tego elementu, aby określić, czy zezwolić na dostęp do anonimowych użytkowników systemu Windows przez ustawienie `allowAnonymousLogons` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5da28-134">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="5da28-135">Można również określić, czy do uwzględnienia informacji o grupie, do której należą użytkowników w elementu AuthorizationContext przez ustawienie `includeWindowsGroups` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="5da28-135">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="5da28-136">Jeśli wartość jest ustawiona na `true` (ustawienie domyślne), ta usługa może określić grupy systemu Windows, do której należy dany klient.</span><span class="sxs-lookup"><span data-stu-id="5da28-136">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da28-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5da28-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WindowsServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>

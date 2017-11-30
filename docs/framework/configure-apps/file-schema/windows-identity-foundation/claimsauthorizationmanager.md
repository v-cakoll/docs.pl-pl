---
title: '&lt;claimsAuthorizationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4b4d86204d5f7225f167be125ce017488c851e98
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimsauthorizationmanagergt"></a><span data-ttu-id="5f090-102">&lt;claimsAuthorizationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="5f090-102">&lt;claimsAuthorizationManager&gt;</span></span>
<span data-ttu-id="5f090-103">Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="5f090-103">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="5f090-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="5f090-104">\<system.identityModel></span></span>  
<span data-ttu-id="5f090-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5f090-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5f090-106">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="5f090-106">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f090-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f090-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f090-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5f090-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5f090-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5f090-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f090-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5f090-110">Attributes</span></span>  
  
|<span data-ttu-id="5f090-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5f090-111">Attribute</span></span>|<span data-ttu-id="5f090-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5f090-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5f090-113">— typ</span><span class="sxs-lookup"><span data-stu-id="5f090-113">type</span></span>|<span data-ttu-id="5f090-114">Typ niestandardowy, która jest pochodną <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="5f090-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="5f090-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f090-115">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5f090-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5f090-116">Child Elements</span></span>  
 <span data-ttu-id="5f090-117">W przypadku nie `type` atrybutu, lub jeśli `type` atrybut odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych; jednak klasy wyprowadzone z <xref:System.Security.Claims.ClaimsAuthorizationManager> można zdefiniować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5f090-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5f090-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5f090-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5f090-119">Element</span><span class="sxs-lookup"><span data-stu-id="5f090-119">Element</span></span>|<span data-ttu-id="5f090-120">Opis</span><span class="sxs-lookup"><span data-stu-id="5f090-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f090-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="5f090-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="5f090-122">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="5f090-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f090-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f090-123">Remarks</span></span>  
 <span data-ttu-id="5f090-124">Domyślne zachowanie realizowane za pośrednictwem <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy zawsze autoryzuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="5f090-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="5f090-125">Jeśli nie `type` jest określony atrybut lub, jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5f090-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="5f090-126">Można określić `type` atrybut, aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy do zaimplementowania niestandardowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="5f090-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="5f090-127">Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementy podrzędne `<claimsAuthorizationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="5f090-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="5f090-128">Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="5f090-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5f090-129">Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, konfiguracja tożsamości, który odwołuje się do niego `<federationConfiguration>` element konfiguruje Menedżera autoryzacji oświadczeń i zasad, które jest używane do obliczania decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="5f090-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="5f090-130">Dotyczy to przypadków, nawet w przypadku scenariuszy, które nie są pasywnym scenariusze sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5f090-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="5f090-131">Jeśli aplikacja nie jest pasywny aplikacji sieci Web, `<claimsAuthorizationManager>` — element (i jego zasady elementów podrzędnych, a jeśli istnieje) konfiguracji przywoływanego tożsamości są tylko ustawienia zastosowane.</span><span class="sxs-lookup"><span data-stu-id="5f090-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="5f090-132">Wszystkie inne ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="5f090-132">All other settings are ignored.</span></span> <span data-ttu-id="5f090-133">Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="5f090-133">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="5f090-134">Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5f090-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f090-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f090-135">Example</span></span>  
 <span data-ttu-id="5f090-136">Następujący kod XML przedstawia konfigurację do autoryzacji oświadczeń manager, który implementuje zasad składa się z pary Akcja zasobu, z których każdy określa logiczna kombinacje oświadczeń, których obiekt żądający musi posiadać można wykonać akcji dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="5f090-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="5f090-137">Kod, który implementuje Menedżera autoryzacji oświadczeń możliwość korzystania z tych zasad można znaleźć w `ClaimsBasedAuthorization` próbki.</span><span class="sxs-lookup"><span data-stu-id="5f090-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```

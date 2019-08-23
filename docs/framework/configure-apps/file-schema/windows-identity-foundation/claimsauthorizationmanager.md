---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942890"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="3418e-101">\<Składnika ClaimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="3418e-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="3418e-102">Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="3418e-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="3418e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3418e-103">\<system.identityModel></span></span>  
<span data-ttu-id="3418e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3418e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3418e-105">\<Składnika ClaimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="3418e-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3418e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3418e-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3418e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3418e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3418e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3418e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3418e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3418e-109">Attributes</span></span>  
  
|<span data-ttu-id="3418e-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3418e-110">Attribute</span></span>|<span data-ttu-id="3418e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3418e-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3418e-112">— typ</span><span class="sxs-lookup"><span data-stu-id="3418e-112">type</span></span>|<span data-ttu-id="3418e-113">Typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="3418e-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="3418e-114">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3418e-114">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3418e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3418e-115">Child Elements</span></span>  
 <span data-ttu-id="3418e-116">Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthorizationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthorizationManager> mogą definiować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3418e-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3418e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3418e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3418e-118">Element</span><span class="sxs-lookup"><span data-stu-id="3418e-118">Element</span></span>|<span data-ttu-id="3418e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3418e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3418e-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3418e-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="3418e-121">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="3418e-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3418e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3418e-122">Remarks</span></span>  
 <span data-ttu-id="3418e-123">Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę zawsze autoryzuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="3418e-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="3418e-124">Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthorizationManager>` określa <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę, element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3418e-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="3418e-125">Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthorizationManager> aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="3418e-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="3418e-126">Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthorizationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="3418e-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="3418e-127">Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.</span><span class="sxs-lookup"><span data-stu-id="3418e-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3418e-128">W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości `<federationConfiguration>` , do której odwołuje się element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane do wykonania decyzje dotyczące autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3418e-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="3418e-129">Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3418e-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="3418e-130">Jeśli aplikacja nie jest pasywną aplikacją sieci Web, `<claimsAuthorizationManager>` element (i jego elementy zasad podrzędnych, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="3418e-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="3418e-131">Wszystkie inne ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="3418e-131">All other settings are ignored.</span></span> <span data-ttu-id="3418e-132">Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3418e-132">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="3418e-133">Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="3418e-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3418e-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="3418e-134">Example</span></span>  
 <span data-ttu-id="3418e-135">W poniższym kodzie XML przedstawiono konfigurację Menedżera autoryzacji oświadczeń, który implementuje zasady składające się z par akcji zasobów, z których każda określa logiczne kombinacje oświadczeń, które obiekt żądający musi dysponować, aby wykonać akcję dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="3418e-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="3418e-136">Kod implementujący Menedżera autoryzacji oświadczeń, który może korzystać z tych zasad, `ClaimsBasedAuthorization` można znaleźć w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3418e-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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

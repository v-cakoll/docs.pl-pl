---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268106"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="36684-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="36684-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="36684-102">Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="36684-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="36684-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="36684-103">\<system.identityModel></span></span>  
<span data-ttu-id="36684-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="36684-104">\<identityConfiguration></span></span>  
<span data-ttu-id="36684-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="36684-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36684-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="36684-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36684-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="36684-107">Attributes and Elements</span></span>  
 <span data-ttu-id="36684-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="36684-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36684-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="36684-109">Attributes</span></span>  
  
|<span data-ttu-id="36684-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="36684-110">Attribute</span></span>|<span data-ttu-id="36684-111">Opis</span><span class="sxs-lookup"><span data-stu-id="36684-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36684-112">— typ</span><span class="sxs-lookup"><span data-stu-id="36684-112">type</span></span>|<span data-ttu-id="36684-113">Typ niestandardowy, który pochodzi od klasy <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="36684-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="36684-114">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="36684-114">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36684-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="36684-115">Child Elements</span></span>  
 <span data-ttu-id="36684-116">W przypadku nie `type` atrybut, lub jeśli `type` atrybutu odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych; jednak klasy pochodne klasy <xref:System.Security.Claims.ClaimsAuthorizationManager> można zdefiniować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="36684-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36684-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="36684-117">Parent Elements</span></span>  
  
|<span data-ttu-id="36684-118">Element</span><span class="sxs-lookup"><span data-stu-id="36684-118">Element</span></span>|<span data-ttu-id="36684-119">Opis</span><span class="sxs-lookup"><span data-stu-id="36684-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36684-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="36684-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="36684-121">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="36684-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36684-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="36684-122">Remarks</span></span>  
 <span data-ttu-id="36684-123">Domyślne zachowanie, dostępne za pośrednictwem <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy zawsze autoryzuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="36684-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="36684-124">Jeśli nie `type` atrybut jest określony lub jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy `<claimsAuthorizationManager>` element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="36684-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="36684-125">Można określić `type` pochodną klasy atrybutu, aby zarejestrować typ <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę, aby wdrożyć niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="36684-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="36684-126">Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementów podrzędnych `<claimsAuthorizationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metodę obsługującą te elementy.</span><span class="sxs-lookup"><span data-stu-id="36684-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="36684-127">Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="36684-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="36684-128">Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach, w kodzie, konfiguracja tożsamości, która odwołuje się do niej `<federationConfiguration>` element konfiguruje Menedżera autoryzacji oświadczeń i zasady, które jest używane do utworzenia decyzji dotyczących autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="36684-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="36684-129">Ta zasada obowiązuje, nawet w scenariuszach, które nie są pasywnym scenariusze sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web.</span><span class="sxs-lookup"><span data-stu-id="36684-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="36684-130">Jeśli aplikacja nie jest pasywnym aplikacji sieci Web, `<claimsAuthorizationManager>` — element (i jego zasady elementów podrzędnych, a jeśli jest obecna) konfiguracji odwołania tożsamości są tylko ustawienia zastosowane.</span><span class="sxs-lookup"><span data-stu-id="36684-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="36684-131">Wszystkie inne ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="36684-131">All other settings are ignored.</span></span> <span data-ttu-id="36684-132">Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="36684-132">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="36684-133">Element ten ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="36684-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36684-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="36684-134">Example</span></span>  
 <span data-ttu-id="36684-135">Następujący kod XML przedstawia konfigurację do autoryzacji oświadczeń manager, który implementuje zasady składa się z pary Akcja zasobu, z których każdy Określa logiczną kombinacji oświadczeń, których obiekt żądający musi posiadać do wykonania akcji w zasobie.</span><span class="sxs-lookup"><span data-stu-id="36684-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="36684-136">Kod, który implementuje Menedżera autoryzacji oświadczeń stanie przy użyciu tych zasad można znaleźć w `ClaimsBasedAuthorization` próbki.</span><span class="sxs-lookup"><span data-stu-id="36684-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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

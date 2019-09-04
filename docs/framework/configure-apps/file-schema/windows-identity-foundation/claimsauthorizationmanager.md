---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252086"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="20a96-101">\<Składnika ClaimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="20a96-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="20a96-102">Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="20a96-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
<span data-ttu-id="20a96-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="20a96-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="20a96-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="20a96-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="20a96-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="20a96-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="20a96-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Składnika ClaimsAuthorizationManager >**</span><span class="sxs-lookup"><span data-stu-id="20a96-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a96-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="20a96-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20a96-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="20a96-108">Attributes and Elements</span></span>  
 <span data-ttu-id="20a96-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="20a96-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20a96-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="20a96-110">Attributes</span></span>  
  
|<span data-ttu-id="20a96-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="20a96-111">Attribute</span></span>|<span data-ttu-id="20a96-112">Opis</span><span class="sxs-lookup"><span data-stu-id="20a96-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20a96-113">— typ</span><span class="sxs-lookup"><span data-stu-id="20a96-113">type</span></span>|<span data-ttu-id="20a96-114">Typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthorizationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="20a96-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="20a96-115">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="20a96-115">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20a96-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="20a96-116">Child Elements</span></span>  
 <span data-ttu-id="20a96-117">Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthorizationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthorizationManager> mogą definiować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="20a96-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20a96-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="20a96-118">Parent Elements</span></span>  
  
|<span data-ttu-id="20a96-119">Element</span><span class="sxs-lookup"><span data-stu-id="20a96-119">Element</span></span>|<span data-ttu-id="20a96-120">Opis</span><span class="sxs-lookup"><span data-stu-id="20a96-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20a96-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="20a96-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="20a96-122">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="20a96-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20a96-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20a96-123">Remarks</span></span>  
 <span data-ttu-id="20a96-124">Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę zawsze autoryzuje oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="20a96-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="20a96-125">Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthorizationManager>` określa <xref:System.Security.Claims.ClaimsAuthorizationManager> klasę, element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="20a96-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="20a96-126">Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthorizationManager> aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="20a96-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="20a96-127">Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthorizationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="20a96-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="20a96-128">Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.</span><span class="sxs-lookup"><span data-stu-id="20a96-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20a96-129">W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości `<federationConfiguration>` , do której odwołuje się element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane do wykonania decyzje dotyczące autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="20a96-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="20a96-130">Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web.</span><span class="sxs-lookup"><span data-stu-id="20a96-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="20a96-131">Jeśli aplikacja nie jest pasywną aplikacją sieci Web, `<claimsAuthorizationManager>` element (i jego elementy zasad podrzędnych, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami.</span><span class="sxs-lookup"><span data-stu-id="20a96-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="20a96-132">Wszystkie inne ustawienia są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="20a96-132">All other settings are ignored.</span></span> <span data-ttu-id="20a96-133">Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="20a96-133">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="20a96-134">Ten element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="20a96-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20a96-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="20a96-135">Example</span></span>  
 <span data-ttu-id="20a96-136">W poniższym kodzie XML przedstawiono konfigurację Menedżera autoryzacji oświadczeń, który implementuje zasady składające się z par akcji zasobów, z których każda określa logiczne kombinacje oświadczeń, które obiekt żądający musi dysponować, aby wykonać akcję dla zasobu.</span><span class="sxs-lookup"><span data-stu-id="20a96-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="20a96-137">Kod implementujący Menedżera autoryzacji oświadczeń, który może korzystać z tych zasad, `ClaimsBasedAuthorization` można znaleźć w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="20a96-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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

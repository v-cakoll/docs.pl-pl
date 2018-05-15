---
title: '&lt;claimsAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4a91e0ed1f437089e26e5902515f73a15d94a8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="e5d4c-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="e5d4c-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="e5d4c-103">Rejestruje Menedżer uwierzytelniania oświadczeń oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="e5d4c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e5d4c-104">\<system.identityModel></span></span>  
<span data-ttu-id="e5d4c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e5d4c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e5d4c-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="e5d4c-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5d4c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5d4c-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5d4c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e5d4c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e5d4c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5d4c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e5d4c-110">Attributes</span></span>  
  
|<span data-ttu-id="e5d4c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e5d4c-111">Attribute</span></span>|<span data-ttu-id="e5d4c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e5d4c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5d4c-113">— typ</span><span class="sxs-lookup"><span data-stu-id="e5d4c-113">type</span></span>|<span data-ttu-id="e5d4c-114">Określa typ niestandardowy, która jest pochodną <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="e5d4c-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołania do typu niestandardowego].</span><span class="sxs-lookup"><span data-stu-id="e5d4c-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5d4c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e5d4c-116">Child Elements</span></span>  
 <span data-ttu-id="e5d4c-117">W przypadku nie `type` atrybutu, lub jeśli `type` atrybut odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych; jednak klasy wyprowadzone z <xref:System.Security.Claims.ClaimsAuthenticationManager> można zdefiniować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5d4c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e5d4c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e5d4c-119">Element</span><span class="sxs-lookup"><span data-stu-id="e5d4c-119">Element</span></span>|<span data-ttu-id="e5d4c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e5d4c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5d4c-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e5d4c-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="e5d4c-122">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5d4c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5d4c-123">Remarks</span></span>  
 <span data-ttu-id="e5d4c-124">Domyślne zachowanie realizowane za pośrednictwem <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy echa oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="e5d4c-125">Jeśli nie `type` jest określony atrybut lub, jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="e5d4c-126">Można określić `type` atrybut, aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy do zaimplementowania niestandardowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="e5d4c-127">Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementy podrzędne `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="e5d4c-128">Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="e5d4c-129">`<claimsAuthenticationManager>` Ustawia element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5d4c-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5d4c-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5d4c-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```

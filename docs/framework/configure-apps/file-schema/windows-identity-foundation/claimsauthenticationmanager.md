---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b7d68c2fe89b5ca56319df2f24fadd51f329f5ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a><span data-ttu-id="fc016-102">&lt;claimsAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="fc016-102">&lt;claimsAuthenticationManager&gt;</span></span>
<span data-ttu-id="fc016-103">Rejestruje Menedżer uwierzytelniania oświadczeń oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="fc016-103">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="fc016-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="fc016-104">\<system.identityModel></span></span>  
<span data-ttu-id="fc016-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fc016-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fc016-106">\<claimsAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="fc016-106">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc016-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc016-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc016-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fc016-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fc016-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fc016-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc016-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fc016-110">Attributes</span></span>  
  
|<span data-ttu-id="fc016-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fc016-111">Attribute</span></span>|<span data-ttu-id="fc016-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fc016-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc016-113">— typ</span><span class="sxs-lookup"><span data-stu-id="fc016-113">type</span></span>|<span data-ttu-id="fc016-114">Określa typ niestandardowy, która jest pochodną <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="fc016-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="fc016-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołania do typu niestandardowego].</span><span class="sxs-lookup"><span data-stu-id="fc016-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc016-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fc016-116">Child Elements</span></span>  
 <span data-ttu-id="fc016-117">W przypadku nie `type` atrybutu, lub jeśli `type` atrybut odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych; jednak klasy wyprowadzone z <xref:System.Security.Claims.ClaimsAuthenticationManager> można zdefiniować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fc016-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc016-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fc016-118">Parent Elements</span></span>  
  
|<span data-ttu-id="fc016-119">Element</span><span class="sxs-lookup"><span data-stu-id="fc016-119">Element</span></span>|<span data-ttu-id="fc016-120">Opis</span><span class="sxs-lookup"><span data-stu-id="fc016-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc016-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="fc016-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="fc016-122">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="fc016-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc016-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc016-123">Remarks</span></span>  
 <span data-ttu-id="fc016-124">Domyślne zachowanie realizowane za pośrednictwem <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy echa oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="fc016-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="fc016-125">Jeśli nie `type` jest określony atrybut lub, jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fc016-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="fc016-126">Można określić `type` atrybut, aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy do zaimplementowania niestandardowego zachowania.</span><span class="sxs-lookup"><span data-stu-id="fc016-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="fc016-127">Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementy podrzędne `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="fc016-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="fc016-128">Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="fc016-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="fc016-129">`<claimsAuthenticationManager>` Ustawia element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fc016-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc016-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc016-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```

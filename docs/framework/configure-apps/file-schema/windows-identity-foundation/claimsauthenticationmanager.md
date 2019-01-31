---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: ecf26263bf47e8b4609e7adc208f0a59a2fa795b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255188"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="7a5b9-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="7a5b9-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="7a5b9-102">Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="7a5b9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7a5b9-103">\<system.identityModel></span></span>  
<span data-ttu-id="7a5b9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7a5b9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7a5b9-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="7a5b9-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a5b9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a5b9-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a5b9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a5b9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7a5b9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a5b9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a5b9-109">Attributes</span></span>  
  
|<span data-ttu-id="7a5b9-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a5b9-110">Attribute</span></span>|<span data-ttu-id="7a5b9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="7a5b9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a5b9-112">— typ</span><span class="sxs-lookup"><span data-stu-id="7a5b9-112">type</span></span>|<span data-ttu-id="7a5b9-113">Określa typ niestandardowy, który pochodzi od klasy <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="7a5b9-114">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="7a5b9-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a5b9-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a5b9-115">Child Elements</span></span>  
 <span data-ttu-id="7a5b9-116">W przypadku nie `type` atrybut, lub jeśli `type` atrybutu odwołania <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych; jednak klasy pochodne klasy <xref:System.Security.Claims.ClaimsAuthenticationManager> można zdefiniować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a5b9-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a5b9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7a5b9-118">Element</span><span class="sxs-lookup"><span data-stu-id="7a5b9-118">Element</span></span>|<span data-ttu-id="7a5b9-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7a5b9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a5b9-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7a5b9-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="7a5b9-121">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a5b9-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a5b9-122">Remarks</span></span>  
 <span data-ttu-id="7a5b9-123">Domyślne zachowanie, dostępne za pośrednictwem <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy funkcją oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="7a5b9-124">Jeśli nie `type` atrybut jest określony lub jeśli `type` Określa atrybut <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy `<claimsAuthenticationManager>` element nie ma elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="7a5b9-125">Można określić `type` pochodną klasy atrybutu, aby zarejestrować typ <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, aby wdrożyć niestandardowe zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="7a5b9-126">Klasy pochodne mogą obsługiwać konfiguracji za pomocą elementów podrzędnych `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodę obsługującą te elementy.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="7a5b9-127">Projektant klasy zależy od schematu zdefiniowane dla elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="7a5b9-128">`<claimsAuthenticationManager>` Ustawia element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a5b9-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a5b9-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a5b9-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```

---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 3602a4805e86833ba6070d801cef6758aaee8a5c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941830"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="0637b-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0637b-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="0637b-102">Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="0637b-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="0637b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0637b-103">\<system.identityModel></span></span>  
<span data-ttu-id="0637b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0637b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="0637b-105">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0637b-105">\<claimsAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0637b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="0637b-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0637b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0637b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0637b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0637b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0637b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0637b-109">Attributes</span></span>  
  
|<span data-ttu-id="0637b-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0637b-110">Attribute</span></span>|<span data-ttu-id="0637b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0637b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0637b-112">— typ</span><span class="sxs-lookup"><span data-stu-id="0637b-112">type</span></span>|<span data-ttu-id="0637b-113">Określa typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="0637b-113">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="0637b-114">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="0637b-114">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0637b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0637b-115">Child Elements</span></span>  
 <span data-ttu-id="0637b-116">Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthenticationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthenticationManager> mogą definiować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0637b-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0637b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0637b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0637b-118">Element</span><span class="sxs-lookup"><span data-stu-id="0637b-118">Element</span></span>|<span data-ttu-id="0637b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="0637b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0637b-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0637b-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="0637b-121">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="0637b-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0637b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0637b-122">Remarks</span></span>  
 <span data-ttu-id="0637b-123">Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę zwraca oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="0637b-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="0637b-124">Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthenticationManager>` określa <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0637b-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="0637b-125">Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthenticationManager> aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="0637b-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="0637b-126">Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthenticationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="0637b-126">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="0637b-127">Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.</span><span class="sxs-lookup"><span data-stu-id="0637b-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="0637b-128">`<claimsAuthenticationManager>` Element<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ustawia właściwość.</span><span class="sxs-lookup"><span data-stu-id="0637b-128">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0637b-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="0637b-129">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```

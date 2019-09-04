---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: c901daf4d442a206345301795c7a4bdc076329cd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252088"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="11b10-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="11b10-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="11b10-102">Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="11b10-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="11b10-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="11b10-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="11b10-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="11b10-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="11b10-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="11b10-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="11b10-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="11b10-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b10-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="11b10-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11b10-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11b10-108">Attributes and Elements</span></span>  
 <span data-ttu-id="11b10-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11b10-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11b10-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11b10-110">Attributes</span></span>  
  
|<span data-ttu-id="11b10-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="11b10-111">Attribute</span></span>|<span data-ttu-id="11b10-112">Opis</span><span class="sxs-lookup"><span data-stu-id="11b10-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11b10-113">— typ</span><span class="sxs-lookup"><span data-stu-id="11b10-113">type</span></span>|<span data-ttu-id="11b10-114">Określa typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="11b10-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="11b10-115">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="11b10-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11b10-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11b10-116">Child Elements</span></span>  
 <span data-ttu-id="11b10-117">Jeśli `type` nie ma atrybutu lub <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Jeśli atrybut `<claimsAuthenticationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthenticationManager> mogą definiować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="11b10-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11b10-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11b10-118">Parent Elements</span></span>  
  
|<span data-ttu-id="11b10-119">Element</span><span class="sxs-lookup"><span data-stu-id="11b10-119">Element</span></span>|<span data-ttu-id="11b10-120">Opis</span><span class="sxs-lookup"><span data-stu-id="11b10-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11b10-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="11b10-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="11b10-122">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="11b10-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b10-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11b10-123">Remarks</span></span>  
 <span data-ttu-id="11b10-124">Domyślne zachowanie udostępniane przez <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę zwraca oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="11b10-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="11b10-125">Jeśli nie `type` określono atrybutu lub `type` Jeśli atrybut `<claimsAuthenticationManager>` określa <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="11b10-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="11b10-126">Możesz określić atrybut, `type` aby zarejestrować typ pochodny klasy, <xref:System.Security.Claims.ClaimsAuthenticationManager> aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="11b10-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="11b10-127">Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów `<claimsAuthenticationManager>` podrzędnych elementu przez <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> zastąpienie metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="11b10-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="11b10-128">Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.</span><span class="sxs-lookup"><span data-stu-id="11b10-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="11b10-129">`<claimsAuthenticationManager>` Element<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> ustawia właściwość.</span><span class="sxs-lookup"><span data-stu-id="11b10-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b10-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="11b10-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</system.identityModel>  
```

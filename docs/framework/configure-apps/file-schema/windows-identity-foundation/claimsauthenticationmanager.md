---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152752"
---
# <a name="claimsauthenticationmanager"></a><span data-ttu-id="e40ad-101">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="e40ad-101">\<claimsAuthenticationManager></span></span>
<span data-ttu-id="e40ad-102">Rejestruje menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e40ad-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
<span data-ttu-id="e40ad-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e40ad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e40ad-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e40ad-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e40ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e40ad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e40ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span><span class="sxs-lookup"><span data-stu-id="e40ad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e40ad-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e40ad-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e40ad-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e40ad-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e40ad-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e40ad-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e40ad-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e40ad-110">Attributes</span></span>  
  
|<span data-ttu-id="e40ad-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e40ad-111">Attribute</span></span>|<span data-ttu-id="e40ad-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e40ad-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e40ad-113">type</span><span class="sxs-lookup"><span data-stu-id="e40ad-113">type</span></span>|<span data-ttu-id="e40ad-114">Określa typ niestandardowy, który <xref:System.Security.Claims.ClaimsAuthenticationManager> pochodzi z klasy.</span><span class="sxs-lookup"><span data-stu-id="e40ad-114">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="e40ad-115">Aby uzyskać więcej informacji `type` na temat określania atrybutu, zobacz [Odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="e40ad-115">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e40ad-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e40ad-116">Child Elements</span></span>  
 <span data-ttu-id="e40ad-117">Jeśli nie `type` ma żadnego atrybutu `type` lub jeśli <xref:System.Security.Claims.ClaimsAuthenticationManager> atrybut `<claimsAuthenticationManager>` odwołuje się do klasy, element nie przyjmuje elementów podrzędnych; jednak klasy uzyskane <xref:System.Security.Claims.ClaimsAuthenticationManager> z można zdefiniować elementy konfiguracji podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e40ad-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e40ad-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e40ad-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e40ad-119">Element</span><span class="sxs-lookup"><span data-stu-id="e40ad-119">Element</span></span>|<span data-ttu-id="e40ad-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e40ad-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e40ad-121">\<>konfiguracji tożsamości</span><span class="sxs-lookup"><span data-stu-id="e40ad-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="e40ad-122">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="e40ad-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e40ad-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e40ad-123">Remarks</span></span>  
 <span data-ttu-id="e40ad-124">Domyślne zachowanie dostarczone <xref:System.Security.Claims.ClaimsAuthenticationManager> za pośrednictwem klasy odzwierciedla oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="e40ad-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="e40ad-125">Jeśli `type` nie atrybut jest określony `type` lub jeśli <xref:System.Security.Claims.ClaimsAuthenticationManager> atrybut określa `<claimsAuthenticationManager>` klasę, element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e40ad-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="e40ad-126">Można określić `type` atrybut, aby zarejestrować typ <xref:System.Security.Claims.ClaimsAuthenticationManager> pochodzący z klasy, aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="e40ad-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="e40ad-127">Klasy pochodne mogą obsługiwać konfigurację za pośrednictwem elementów podrzędnych `<claimsAuthenticationManager>` elementu, zastępując <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metodę obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="e40ad-127">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="e40ad-128">Schemat zdefiniowany dla elementów podrzędnych jest do projektanta klasy.</span><span class="sxs-lookup"><span data-stu-id="e40ad-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="e40ad-129">Element `<claimsAuthenticationManager>` ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="e40ad-129">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e40ad-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e40ad-130">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```

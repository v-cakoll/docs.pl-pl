---
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: a54fc2cea84bb9d08a9725d846fe38efd7b5475a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152752"
---
# \<claimsAuthenticationManager>
<span data-ttu-id="6ec1d-101">Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-101">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="6ec1d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ec1d-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ec1d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6ec1d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6ec1d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ec1d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ec1d-105">Attributes</span></span>  
  
|<span data-ttu-id="6ec1d-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6ec1d-106">Attribute</span></span>|<span data-ttu-id="6ec1d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ec1d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ec1d-108">typ</span><span class="sxs-lookup"><span data-stu-id="6ec1d-108">type</span></span>|<span data-ttu-id="6ec1d-109">Określa typ niestandardowy, który pochodzi od <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-109">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="6ec1d-110">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="6ec1d-110">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ec1d-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6ec1d-111">Child Elements</span></span>  
 <span data-ttu-id="6ec1d-112">Jeśli nie ma `type` atrybutu lub jeśli `type` atrybut odwołuje się do <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy, element nie `<claimsAuthenticationManager>` przyjmuje elementów podrzędnych, jednak klasy pochodne <xref:System.Security.Claims.ClaimsAuthenticationManager> mogą definiować podrzędne elementy konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ec1d-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6ec1d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="6ec1d-114">Element</span><span class="sxs-lookup"><span data-stu-id="6ec1d-114">Element</span></span>|<span data-ttu-id="6ec1d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6ec1d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="6ec1d-116">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ec1d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ec1d-117">Remarks</span></span>  
 <span data-ttu-id="6ec1d-118">Domyślne zachowanie udostępniane przez klasę zwraca <xref:System.Security.Claims.ClaimsAuthenticationManager> oświadczenia przychodzące.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="6ec1d-119">Jeśli nie `type` określono atrybutu lub jeśli `type` atrybut określa <xref:System.Security.Claims.ClaimsAuthenticationManager> klasę, `<claimsAuthenticationManager>` element nie przyjmuje elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="6ec1d-120">Możesz określić atrybut, `type` Aby zarejestrować typ pochodny <xref:System.Security.Claims.ClaimsAuthenticationManager> klasy, aby zaimplementować zachowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="6ec1d-121">Klasy pochodne mogą obsługiwać konfigurację za pomocą elementów podrzędnych `<claimsAuthenticationManager>` elementu przez zastąpienie <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> metody do obsługi tych elementów.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-121">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="6ec1d-122">Schemat zdefiniowany dla elementów podrzędnych jest projektantem klasy.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="6ec1d-123">`<claimsAuthenticationManager>`Element ustawia <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="6ec1d-123">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec1d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ec1d-124">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```

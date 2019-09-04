---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252017"
---
# <a name="customcookiehandler"></a><span data-ttu-id="f570b-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="f570b-101">\<customCookieHandler></span></span>
<span data-ttu-id="f570b-102">Ustawia niestandardowy typ procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="f570b-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="f570b-103">Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="f570b-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="f570b-104">Typ niestandardowy musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="f570b-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="f570b-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f570b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f570b-106">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="f570b-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="f570b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f570b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="f570b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="f570b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="f570b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="f570b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f570b-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="f570b-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f570b-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f570b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f570b-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f570b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f570b-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f570b-113">Attributes</span></span>  
  
|<span data-ttu-id="f570b-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f570b-114">Attribute</span></span>|<span data-ttu-id="f570b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="f570b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f570b-116">— typ</span><span class="sxs-lookup"><span data-stu-id="f570b-116">type</span></span>|<span data-ttu-id="f570b-117">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="f570b-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="f570b-118">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f570b-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f570b-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f570b-119">Child Elements</span></span>  
 <span data-ttu-id="f570b-120">Brak</span><span class="sxs-lookup"><span data-stu-id="f570b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f570b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f570b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f570b-122">Element</span><span class="sxs-lookup"><span data-stu-id="f570b-122">Element</span></span>|<span data-ttu-id="f570b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f570b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f570b-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="f570b-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="f570b-125">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , czy program używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="f570b-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f570b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f570b-126">Remarks</span></span>  
 <span data-ttu-id="f570b-127">W przypadku określenia niestandardowego programu obsługi plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ niestandardowej obsługi `<customCookieHandler>` plików cookie, dołączając element podrzędny, który odwołuje się do typu procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="f570b-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="f570b-128">Nie można określić tego elementu, `mode` gdy atrybut ma wartość "fragmentaryczne" lub "domyślne".</span><span class="sxs-lookup"><span data-stu-id="f570b-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="f570b-129">Niestandardowe programy obsługi plików cookie muszą pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="f570b-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="f570b-130">Element jest reprezentowany <xref:System.IdentityModel.Configuration.CustomTypeElement> przez klasę. `<customCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="f570b-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f570b-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="f570b-131">Example</span></span>  
 <span data-ttu-id="f570b-132">Poniższy przykład konfiguruje SAM do korzystania z niestandardowej procedury obsługi plików cookie typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="f570b-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f570b-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f570b-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>

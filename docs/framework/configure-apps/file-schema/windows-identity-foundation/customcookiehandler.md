---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 0129c63fe17b63889a77ea1a56c0d7e657def859
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224054"
---
# <a name="customcookiehandler"></a><span data-ttu-id="5a9b8-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="5a9b8-101">\<customCookieHandler></span></span>
<span data-ttu-id="5a9b8-102">Ustawia typ procedury obsługi niestandardowego pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="5a9b8-103">Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element jest "Niestandardowy".</span><span class="sxs-lookup"><span data-stu-id="5a9b8-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="5a9b8-104">Niestandardowy typ musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="5a9b8-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="5a9b8-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="5a9b8-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="5a9b8-106">\<federationConfiguration></span></span>  
<span data-ttu-id="5a9b8-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="5a9b8-107">\<cookieHandler></span></span>  
<span data-ttu-id="5a9b8-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="5a9b8-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a9b8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a9b8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a9b8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a9b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a9b8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a9b8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a9b8-112">Attributes</span></span>  
  
|<span data-ttu-id="5a9b8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a9b8-113">Attribute</span></span>|<span data-ttu-id="5a9b8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5a9b8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a9b8-115">— typ</span><span class="sxs-lookup"><span data-stu-id="5a9b8-115">type</span></span>|<span data-ttu-id="5a9b8-116">Określa typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="5a9b8-117">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a9b8-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a9b8-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a9b8-118">Child Elements</span></span>  
 <span data-ttu-id="5a9b8-119">Brak</span><span class="sxs-lookup"><span data-stu-id="5a9b8-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a9b8-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a9b8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5a9b8-121">Element</span><span class="sxs-lookup"><span data-stu-id="5a9b8-121">Element</span></span>|<span data-ttu-id="5a9b8-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5a9b8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a9b8-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="5a9b8-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="5a9b8-124">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa na odczytywanie i zapisywanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a9b8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a9b8-125">Remarks</span></span>  
 <span data-ttu-id="5a9b8-126">Po określeniu obsługi niestandardowych plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` element na "Niestandardowe", należy określić typ obsługi niestandardowych plików cookie, umieszczając `<customCookieHandler>` elementu podrzędnego, który odwołuje się typ procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="5a9b8-127">Ten element nie może być określony, gdy `mode` atrybut jest ustawiony na "Fragmentaryczne" lub "Default".</span><span class="sxs-lookup"><span data-stu-id="5a9b8-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="5a9b8-128">Programy obsługi niestandardowych plików cookie musi pochodzić od klasy <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="5a9b8-129">`<customCookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.CustomTypeElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a9b8-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a9b8-130">Example</span></span>  
 <span data-ttu-id="5a9b8-131">Poniższy przykład umożliwia skonfigurowanie tego Zabronić używania obsługi niestandardowych plików cookie, typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="5a9b8-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a9b8-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a9b8-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>

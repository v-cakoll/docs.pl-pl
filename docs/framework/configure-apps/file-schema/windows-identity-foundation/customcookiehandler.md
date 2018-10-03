---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 51ca91de5c77727f5f5506118461d19354f12c14
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029089"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="95475-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="95475-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="95475-103">Ustawia typ procedury obsługi niestandardowego pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="95475-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="95475-104">Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element jest "Niestandardowy".</span><span class="sxs-lookup"><span data-stu-id="95475-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="95475-105">Niestandardowy typ musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="95475-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="95475-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="95475-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="95475-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="95475-107">\<federationConfiguration></span></span>  
<span data-ttu-id="95475-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="95475-108">\<cookieHandler></span></span>  
<span data-ttu-id="95475-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="95475-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95475-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="95475-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95475-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95475-111">Attributes and Elements</span></span>  
 <span data-ttu-id="95475-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95475-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95475-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95475-113">Attributes</span></span>  
  
|<span data-ttu-id="95475-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95475-114">Attribute</span></span>|<span data-ttu-id="95475-115">Opis</span><span class="sxs-lookup"><span data-stu-id="95475-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95475-116">— typ</span><span class="sxs-lookup"><span data-stu-id="95475-116">type</span></span>|<span data-ttu-id="95475-117">Określa typ niestandardowy, który pochodzi od klasy <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="95475-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="95475-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="95475-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95475-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95475-119">Child Elements</span></span>  
 <span data-ttu-id="95475-120">Brak</span><span class="sxs-lookup"><span data-stu-id="95475-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95475-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95475-121">Parent Elements</span></span>  
  
|<span data-ttu-id="95475-122">Element</span><span class="sxs-lookup"><span data-stu-id="95475-122">Element</span></span>|<span data-ttu-id="95475-123">Opis</span><span class="sxs-lookup"><span data-stu-id="95475-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95475-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="95475-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="95475-125">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa na odczytywanie i zapisywanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="95475-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95475-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95475-126">Remarks</span></span>  
 <span data-ttu-id="95475-127">Po określeniu obsługi niestandardowych plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` element na "Niestandardowe", należy określić typ obsługi niestandardowych plików cookie, umieszczając `<customCookieHandler>` elementu podrzędnego, który odwołuje się typ procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="95475-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="95475-128">Ten element nie może być określony, gdy `mode` atrybut jest ustawiony na "Fragmentaryczne" lub "Default".</span><span class="sxs-lookup"><span data-stu-id="95475-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="95475-129">Programy obsługi niestandardowych plików cookie musi pochodzić od klasy <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="95475-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="95475-130">`<customCookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.CustomTypeElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="95475-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95475-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="95475-131">Example</span></span>  
 <span data-ttu-id="95475-132">Poniższy przykład umożliwia skonfigurowanie tego Zabronić używania obsługi niestandardowych plików cookie, typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="95475-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95475-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95475-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>

---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b974767aa86801bff234e200e1fce021bfc422c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755607"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="06bd5-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="06bd5-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="06bd5-103">Ustawia typ obsługi niestandardowego pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="06bd5-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="06bd5-104">Ten element tylko mogą występować Jeśli `mode` atrybutu `<cookieHandler>` element jest "Custom".</span><span class="sxs-lookup"><span data-stu-id="06bd5-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="06bd5-105">Niestandardowy typ musi pochodzić z <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="06bd5-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="06bd5-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="06bd5-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="06bd5-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="06bd5-107">\<federationConfiguration></span></span>  
<span data-ttu-id="06bd5-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="06bd5-108">\<cookieHandler></span></span>  
<span data-ttu-id="06bd5-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="06bd5-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bd5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="06bd5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06bd5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06bd5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06bd5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06bd5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06bd5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06bd5-113">Attributes</span></span>  
  
|<span data-ttu-id="06bd5-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="06bd5-114">Attribute</span></span>|<span data-ttu-id="06bd5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="06bd5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06bd5-116">— typ</span><span class="sxs-lookup"><span data-stu-id="06bd5-116">type</span></span>|<span data-ttu-id="06bd5-117">Określa typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="06bd5-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="06bd5-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="06bd5-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06bd5-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06bd5-119">Child Elements</span></span>  
 <span data-ttu-id="06bd5-120">Brak</span><span class="sxs-lookup"><span data-stu-id="06bd5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06bd5-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06bd5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="06bd5-122">Element</span><span class="sxs-lookup"><span data-stu-id="06bd5-122">Element</span></span>|<span data-ttu-id="06bd5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="06bd5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06bd5-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="06bd5-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="06bd5-125">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="06bd5-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06bd5-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06bd5-126">Remarks</span></span>  
 <span data-ttu-id="06bd5-127">Po określeniu obsługi niestandardowych plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ obsługi niestandardowych plików cookie przez dołączenie `<customCookieHandler>` elementu podrzędnego, który odwołuje się do typu obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="06bd5-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="06bd5-128">Ten element nie może być określona gdy `mode` ustawiono atrybut "Fragmentaryczne" lub "Default".</span><span class="sxs-lookup"><span data-stu-id="06bd5-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="06bd5-129">Programy obsługi niestandardowego pliku cookie musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="06bd5-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="06bd5-130">`<customCookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.CustomTypeElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="06bd5-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06bd5-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="06bd5-131">Example</span></span>  
 <span data-ttu-id="06bd5-132">Poniższy przykład konfiguruje się SAM do użycia niestandardowego pliku cookie obsługi typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="06bd5-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="06bd5-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06bd5-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>

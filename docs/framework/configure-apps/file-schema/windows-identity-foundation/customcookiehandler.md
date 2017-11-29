---
title: '&lt;customCookieHandler&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: df95e8d47d6a19e4fd488fa14bc771bc2c2b56b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="34e70-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="34e70-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="34e70-103">Ustawia typ obsługi niestandardowego pliku cookie.</span><span class="sxs-lookup"><span data-stu-id="34e70-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="34e70-104">Ten element tylko mogą występować Jeśli `mode` atrybutu `<cookieHandler>` element jest "Custom".</span><span class="sxs-lookup"><span data-stu-id="34e70-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="34e70-105">Niestandardowy typ musi pochodzić z <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="34e70-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="34e70-106">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="34e70-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="34e70-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="34e70-107">\<federationConfiguration></span></span>  
<span data-ttu-id="34e70-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="34e70-108">\<cookieHandler></span></span>  
<span data-ttu-id="34e70-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="34e70-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34e70-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="34e70-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34e70-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34e70-111">Attributes and Elements</span></span>  
 <span data-ttu-id="34e70-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34e70-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34e70-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34e70-113">Attributes</span></span>  
  
|<span data-ttu-id="34e70-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34e70-114">Attribute</span></span>|<span data-ttu-id="34e70-115">Opis</span><span class="sxs-lookup"><span data-stu-id="34e70-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34e70-116">— typ</span><span class="sxs-lookup"><span data-stu-id="34e70-116">type</span></span>|<span data-ttu-id="34e70-117">Określa typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="34e70-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="34e70-118">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="34e70-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34e70-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34e70-119">Child Elements</span></span>  
 <span data-ttu-id="34e70-120">Brak</span><span class="sxs-lookup"><span data-stu-id="34e70-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34e70-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34e70-121">Parent Elements</span></span>  
  
|<span data-ttu-id="34e70-122">Element</span><span class="sxs-lookup"><span data-stu-id="34e70-122">Element</span></span>|<span data-ttu-id="34e70-123">Opis</span><span class="sxs-lookup"><span data-stu-id="34e70-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34e70-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="34e70-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="34e70-125">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="34e70-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34e70-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34e70-126">Remarks</span></span>  
 <span data-ttu-id="34e70-127">Po określeniu obsługi niestandardowych plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ obsługi niestandardowych plików cookie przez dołączenie `<customCookieHandler>` elementu podrzędnego, który odwołuje się do typu obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="34e70-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="34e70-128">Ten element nie może być określona gdy `mode` ustawiono atrybut "Fragmentaryczne" lub "Default".</span><span class="sxs-lookup"><span data-stu-id="34e70-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="34e70-129">Programy obsługi niestandardowego pliku cookie musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="34e70-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="34e70-130">`<customCookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.CustomTypeElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="34e70-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e70-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="34e70-131">Example</span></span>  
 <span data-ttu-id="34e70-132">Poniższy przykład konfiguruje się SAM do użycia niestandardowego pliku cookie obsługi typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="34e70-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34e70-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34e70-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>

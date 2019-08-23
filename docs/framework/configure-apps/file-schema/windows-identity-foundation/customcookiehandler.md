---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942786"
---
# <a name="customcookiehandler"></a><span data-ttu-id="23b5b-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="23b5b-101">\<customCookieHandler></span></span>
<span data-ttu-id="23b5b-102">Ustawia niestandardowy typ procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="23b5b-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="23b5b-103">Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="23b5b-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="23b5b-104">Typ niestandardowy musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="23b5b-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="23b5b-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="23b5b-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="23b5b-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="23b5b-106">\<federationConfiguration></span></span>  
<span data-ttu-id="23b5b-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="23b5b-107">\<cookieHandler></span></span>  
<span data-ttu-id="23b5b-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="23b5b-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b5b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="23b5b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23b5b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23b5b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="23b5b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23b5b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23b5b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23b5b-112">Attributes</span></span>  
  
|<span data-ttu-id="23b5b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23b5b-113">Attribute</span></span>|<span data-ttu-id="23b5b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="23b5b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23b5b-115">— typ</span><span class="sxs-lookup"><span data-stu-id="23b5b-115">type</span></span>|<span data-ttu-id="23b5b-116">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="23b5b-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="23b5b-117">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="23b5b-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23b5b-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23b5b-118">Child Elements</span></span>  
 <span data-ttu-id="23b5b-119">Brak</span><span class="sxs-lookup"><span data-stu-id="23b5b-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23b5b-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23b5b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="23b5b-121">Element</span><span class="sxs-lookup"><span data-stu-id="23b5b-121">Element</span></span>|<span data-ttu-id="23b5b-122">Opis</span><span class="sxs-lookup"><span data-stu-id="23b5b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23b5b-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="23b5b-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="23b5b-124">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , czy program używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="23b5b-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23b5b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23b5b-125">Remarks</span></span>  
 <span data-ttu-id="23b5b-126">W przypadku określenia niestandardowego programu obsługi plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ niestandardowej obsługi `<customCookieHandler>` plików cookie, dołączając element podrzędny, który odwołuje się do typu procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="23b5b-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="23b5b-127">Nie można określić tego elementu, `mode` gdy atrybut ma wartość "fragmentaryczne" lub "domyślne".</span><span class="sxs-lookup"><span data-stu-id="23b5b-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="23b5b-128">Niestandardowe programy obsługi plików cookie muszą pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="23b5b-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="23b5b-129">Element jest reprezentowany <xref:System.IdentityModel.Configuration.CustomTypeElement> przez klasę. `<customCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="23b5b-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23b5b-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="23b5b-130">Example</span></span>  
 <span data-ttu-id="23b5b-131">Poniższy przykład konfiguruje SAM do korzystania z niestandardowej procedury obsługi plików cookie typu `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="23b5b-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="23b5b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23b5b-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>

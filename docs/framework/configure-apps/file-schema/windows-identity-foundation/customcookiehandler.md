---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252017"
---
# \<customCookieHandler>
<span data-ttu-id="3a9ac-101">Ustawia niestandardowy typ procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="3a9ac-102">Ten element może być obecny tylko wtedy, gdy `mode` atrybut `<cookieHandler>` elementu ma wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="3a9ac-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="3a9ac-103">Typ niestandardowy musi pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="3a9ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a9ac-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a9ac-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a9ac-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3a9ac-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a9ac-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a9ac-107">Attributes</span></span>  
  
|<span data-ttu-id="3a9ac-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a9ac-108">Attribute</span></span>|<span data-ttu-id="3a9ac-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9ac-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a9ac-110">typ</span><span class="sxs-lookup"><span data-stu-id="3a9ac-110">type</span></span>|<span data-ttu-id="3a9ac-111">Określa typ niestandardowy, który pochodzi od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="3a9ac-112">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3a9ac-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a9ac-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a9ac-113">Child Elements</span></span>  
 <span data-ttu-id="3a9ac-114">Brak</span><span class="sxs-lookup"><span data-stu-id="3a9ac-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a9ac-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a9ac-115">Parent Elements</span></span>  
  
|<span data-ttu-id="3a9ac-116">Element</span><span class="sxs-lookup"><span data-stu-id="3a9ac-116">Element</span></span>|<span data-ttu-id="3a9ac-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3a9ac-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="3a9ac-118">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , czy program <xref:System.IdentityModel.Services.SessionAuthenticationModule> używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a9ac-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a9ac-119">Remarks</span></span>  
 <span data-ttu-id="3a9ac-120">W przypadku określenia niestandardowego programu obsługi plików cookie przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "Custom", należy określić typ niestandardowej obsługi plików cookie, dołączając `<customCookieHandler>` element podrzędny, który odwołuje się do typu procedury obsługi plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="3a9ac-121">Nie można określić tego elementu, gdy `mode` atrybut ma wartość "fragmentaryczne" lub "domyślne".</span><span class="sxs-lookup"><span data-stu-id="3a9ac-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="3a9ac-122">Niestandardowe programy obsługi plików cookie muszą pochodzić od <xref:System.IdentityModel.Services.CookieHandler> klasy.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="3a9ac-123">`<customCookieHandler>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.CustomTypeElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="3a9ac-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a9ac-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a9ac-124">Example</span></span>  
 <span data-ttu-id="3a9ac-125">Poniższy przykład konfiguruje SAM do korzystania z niestandardowej procedury obsługi plików cookie typu `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="3a9ac-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a9ac-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a9ac-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>

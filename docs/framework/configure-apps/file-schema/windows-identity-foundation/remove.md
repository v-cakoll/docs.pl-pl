---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: cfdfbb3aabde253ad17b221801b20c1ac9a45c2d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251928"
---
# <a name="remove"></a><span data-ttu-id="f0e8c-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="f0e8c-101">\<remove></span></span>
<span data-ttu-id="f0e8c-102">Usuwa określony program obsługi tokenów zabezpieczających z kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
<span data-ttu-id="f0e8c-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0e8c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0e8c-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f0e8c-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f0e8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f0e8c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f0e8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f0e8c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f0e8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Usuń >**</span><span class="sxs-lookup"><span data-stu-id="f0e8c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e8c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0e8c-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0e8c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0e8c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f0e8c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0e8c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0e8c-111">Attributes</span></span>  
  
|<span data-ttu-id="f0e8c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f0e8c-112">Attribute</span></span>|<span data-ttu-id="f0e8c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f0e8c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0e8c-114">— typ</span><span class="sxs-lookup"><span data-stu-id="f0e8c-114">type</span></span>|<span data-ttu-id="f0e8c-115">Nazwa typu CLR programu obsługi tokenów, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="f0e8c-116">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="f0e8c-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="f0e8c-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0e8c-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0e8c-118">Child Elements</span></span>  
 <span data-ttu-id="f0e8c-119">Brak</span><span class="sxs-lookup"><span data-stu-id="f0e8c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0e8c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0e8c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f0e8c-121">Element</span><span class="sxs-lookup"><span data-stu-id="f0e8c-121">Element</span></span>|<span data-ttu-id="f0e8c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f0e8c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0e8c-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f0e8c-123">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="f0e8c-124">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0e8c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0e8c-125">Example</span></span>  
 <span data-ttu-id="f0e8c-126">Poniższy kod XML pokazuje użycie `<add>` elementów i `<remove>` , aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="f0e8c-127">Kod XML jest pobierany z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="f0e8c-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

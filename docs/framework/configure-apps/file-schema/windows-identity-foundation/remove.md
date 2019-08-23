---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 11aeed0277fc13cbd9a65232311bd575a4a81ff7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942581"
---
# <a name="remove"></a><span data-ttu-id="5aa82-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="5aa82-101">\<remove></span></span>
<span data-ttu-id="5aa82-102">Usuwa określony program obsługi tokenów zabezpieczających z kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="5aa82-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="5aa82-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5aa82-103">\<system.identityModel></span></span>  
<span data-ttu-id="5aa82-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5aa82-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5aa82-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5aa82-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5aa82-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="5aa82-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aa82-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5aa82-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa82-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5aa82-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5aa82-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5aa82-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa82-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5aa82-110">Attributes</span></span>  
  
|<span data-ttu-id="5aa82-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5aa82-111">Attribute</span></span>|<span data-ttu-id="5aa82-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5aa82-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5aa82-113">— typ</span><span class="sxs-lookup"><span data-stu-id="5aa82-113">type</span></span>|<span data-ttu-id="5aa82-114">Nazwa typu CLR programu obsługi tokenów, który ma zostać usunięty.</span><span class="sxs-lookup"><span data-stu-id="5aa82-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="5aa82-115">Aby uzyskać więcej informacji na temat sposobu określania `type` atrybutu, zobacz [odwołania do typów niestandardowych](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="5aa82-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="5aa82-116">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="5aa82-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa82-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5aa82-117">Child Elements</span></span>  
 <span data-ttu-id="5aa82-118">Brak</span><span class="sxs-lookup"><span data-stu-id="5aa82-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5aa82-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5aa82-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5aa82-120">Element</span><span class="sxs-lookup"><span data-stu-id="5aa82-120">Element</span></span>|<span data-ttu-id="5aa82-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5aa82-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5aa82-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5aa82-122">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="5aa82-123">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="5aa82-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5aa82-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5aa82-124">Example</span></span>  
 <span data-ttu-id="5aa82-125">Poniższy kod XML pokazuje użycie `<add>` elementów i `<remove>` , aby zastąpić domyślną procedurę obsługi tokena sesji za pomocą procedury obsługi niestandardowego tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="5aa82-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="5aa82-126">Kod XML jest pobierany z `ClaimsAwareWebFarm` przykładu.</span><span class="sxs-lookup"><span data-stu-id="5aa82-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

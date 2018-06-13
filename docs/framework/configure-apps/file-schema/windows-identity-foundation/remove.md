---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dfea0b0eb4b133308f10b523a659cc00f87252b8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755080"
---
# <a name="ltremovegt"></a><span data-ttu-id="e1cc4-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="e1cc4-102">&lt;remove&gt;</span></span>
<span data-ttu-id="e1cc4-103">Usuwa określony zabezpieczenia programu obsługi tokenów z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="e1cc4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e1cc4-104">\<system.identityModel></span></span>  
<span data-ttu-id="e1cc4-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e1cc4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e1cc4-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e1cc4-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e1cc4-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="e1cc4-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1cc4-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1cc4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1cc4-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1cc4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1cc4-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1cc4-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1cc4-111">Attributes</span></span>  
  
|<span data-ttu-id="e1cc4-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1cc4-112">Attribute</span></span>|<span data-ttu-id="e1cc4-113">Opis</span><span class="sxs-lookup"><span data-stu-id="e1cc4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1cc4-114">— typ</span><span class="sxs-lookup"><span data-stu-id="e1cc4-114">type</span></span>|<span data-ttu-id="e1cc4-115">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="e1cc4-116">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="e1cc4-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="e1cc4-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1cc4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1cc4-118">Child Elements</span></span>  
 <span data-ttu-id="e1cc4-119">Brak</span><span class="sxs-lookup"><span data-stu-id="e1cc4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1cc4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1cc4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1cc4-121">Element</span><span class="sxs-lookup"><span data-stu-id="e1cc4-121">Element</span></span>|<span data-ttu-id="e1cc4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e1cc4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1cc4-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e1cc4-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="e1cc4-124">Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1cc4-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1cc4-125">Example</span></span>  
 <span data-ttu-id="e1cc4-126">Następujący kod XML pokazano sposób użycia `<add>` i `<remove>` elementy, aby zastąpić domyślny sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="e1cc4-127">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="e1cc4-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

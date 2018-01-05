---
title: '&lt;remove&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 15c2561487eecb44cf3542768de0a77d1dd6713d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt"></a><span data-ttu-id="136a7-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="136a7-102">&lt;remove&gt;</span></span>
<span data-ttu-id="136a7-103">Usuwa określony zabezpieczenia programu obsługi tokenów z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="136a7-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="136a7-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="136a7-104">\<system.identityModel></span></span>  
<span data-ttu-id="136a7-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="136a7-105">\<identityConfiguration></span></span>  
<span data-ttu-id="136a7-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="136a7-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="136a7-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="136a7-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136a7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="136a7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="136a7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="136a7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="136a7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="136a7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="136a7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="136a7-111">Attributes</span></span>  
  
|<span data-ttu-id="136a7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="136a7-112">Attribute</span></span>|<span data-ttu-id="136a7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="136a7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="136a7-114">— typ</span><span class="sxs-lookup"><span data-stu-id="136a7-114">type</span></span>|<span data-ttu-id="136a7-115">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="136a7-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="136a7-116">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołuje się do niestandardowego typu](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="136a7-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/en-us/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="136a7-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="136a7-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="136a7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="136a7-118">Child Elements</span></span>  
 <span data-ttu-id="136a7-119">Brak</span><span class="sxs-lookup"><span data-stu-id="136a7-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="136a7-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="136a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="136a7-121">Element</span><span class="sxs-lookup"><span data-stu-id="136a7-121">Element</span></span>|<span data-ttu-id="136a7-122">Opis</span><span class="sxs-lookup"><span data-stu-id="136a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="136a7-123">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="136a7-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="136a7-124">Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="136a7-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="136a7-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="136a7-125">Example</span></span>  
 <span data-ttu-id="136a7-126">Następujący kod XML pokazano sposób użycia `<add>` i `<remove>` elementy, aby zastąpić domyślny sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="136a7-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="136a7-127">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="136a7-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

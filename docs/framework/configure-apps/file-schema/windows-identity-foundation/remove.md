---
title: '&lt;remove&gt;'
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 410fef1a43f9202d56c4957b1162c53ee056ae3f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074917"
---
# <a name="ltremovegt"></a><span data-ttu-id="fcd71-102">&lt;remove&gt;</span><span class="sxs-lookup"><span data-stu-id="fcd71-102">&lt;remove&gt;</span></span>
<span data-ttu-id="fcd71-103">Usuwa programu obsługi tokenów zabezpieczeń określone z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="fcd71-103">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="fcd71-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="fcd71-104">\<system.identityModel></span></span>  
<span data-ttu-id="fcd71-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="fcd71-105">\<identityConfiguration></span></span>  
<span data-ttu-id="fcd71-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fcd71-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="fcd71-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="fcd71-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcd71-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fcd71-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd71-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fcd71-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fcd71-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fcd71-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd71-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fcd71-111">Attributes</span></span>  
  
|<span data-ttu-id="fcd71-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fcd71-112">Attribute</span></span>|<span data-ttu-id="fcd71-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fcd71-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcd71-114">— typ</span><span class="sxs-lookup"><span data-stu-id="fcd71-114">type</span></span>|<span data-ttu-id="fcd71-115">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="fcd71-115">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="fcd71-116">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="fcd71-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="fcd71-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="fcd71-117">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcd71-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fcd71-118">Child Elements</span></span>  
 <span data-ttu-id="fcd71-119">Brak</span><span class="sxs-lookup"><span data-stu-id="fcd71-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd71-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fcd71-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd71-121">Element</span><span class="sxs-lookup"><span data-stu-id="fcd71-121">Element</span></span>|<span data-ttu-id="fcd71-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fcd71-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcd71-123">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="fcd71-123">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="fcd71-124">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="fcd71-124">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fcd71-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="fcd71-125">Example</span></span>  
 <span data-ttu-id="fcd71-126">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="fcd71-126">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="fcd71-127">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="fcd71-127">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

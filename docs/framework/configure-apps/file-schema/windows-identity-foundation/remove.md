---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: a54957458311e2d5941d1aa1c2486a2f66994d9b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288135"
---
# <a name="remove"></a><span data-ttu-id="bb126-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="bb126-101">\<remove></span></span>
<span data-ttu-id="bb126-102">Usuwa programu obsługi tokenów zabezpieczeń określone z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="bb126-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="bb126-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bb126-103">\<system.identityModel></span></span>  
<span data-ttu-id="bb126-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bb126-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bb126-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="bb126-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bb126-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="bb126-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb126-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb126-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb126-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bb126-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bb126-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bb126-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb126-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bb126-110">Attributes</span></span>  
  
|<span data-ttu-id="bb126-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bb126-111">Attribute</span></span>|<span data-ttu-id="bb126-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bb126-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bb126-113">— typ</span><span class="sxs-lookup"><span data-stu-id="bb126-113">type</span></span>|<span data-ttu-id="bb126-114">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="bb126-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="bb126-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="bb126-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span> <span data-ttu-id="bb126-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="bb126-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb126-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bb126-117">Child Elements</span></span>  
 <span data-ttu-id="bb126-118">Brak</span><span class="sxs-lookup"><span data-stu-id="bb126-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb126-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bb126-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bb126-120">Element</span><span class="sxs-lookup"><span data-stu-id="bb126-120">Element</span></span>|<span data-ttu-id="bb126-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bb126-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb126-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="bb126-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="bb126-123">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="bb126-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bb126-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb126-124">Example</span></span>  
 <span data-ttu-id="bb126-125">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="bb126-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="bb126-126">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="bb126-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

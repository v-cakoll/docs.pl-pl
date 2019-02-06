---
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 17c4d4289cf90b66d52986c054d4807ecff2b3d8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758420"
---
# <a name="remove"></a><span data-ttu-id="82631-101">\<remove></span><span class="sxs-lookup"><span data-stu-id="82631-101">\<remove></span></span>
<span data-ttu-id="82631-102">Usuwa programu obsługi tokenów zabezpieczeń określone z kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="82631-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
 <span data-ttu-id="82631-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="82631-103">\<system.identityModel></span></span>  
<span data-ttu-id="82631-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="82631-104">\<identityConfiguration></span></span>  
<span data-ttu-id="82631-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="82631-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="82631-106">\<remove></span><span class="sxs-lookup"><span data-stu-id="82631-106">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82631-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="82631-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82631-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82631-108">Attributes and Elements</span></span>  
 <span data-ttu-id="82631-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82631-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82631-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82631-110">Attributes</span></span>  
  
|<span data-ttu-id="82631-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="82631-111">Attribute</span></span>|<span data-ttu-id="82631-112">Opis</span><span class="sxs-lookup"><span data-stu-id="82631-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82631-113">— typ</span><span class="sxs-lookup"><span data-stu-id="82631-113">type</span></span>|<span data-ttu-id="82631-114">Nazwa typu CLR programu obsługi tokenów do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="82631-114">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="82631-115">Aby uzyskać więcej informacji o sposobie określania `type` atrybutów, zobacz [odwołań do typu niestandardowego](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="82631-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="82631-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="82631-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82631-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82631-117">Child Elements</span></span>  
 <span data-ttu-id="82631-118">Brak</span><span class="sxs-lookup"><span data-stu-id="82631-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82631-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82631-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82631-120">Element</span><span class="sxs-lookup"><span data-stu-id="82631-120">Element</span></span>|<span data-ttu-id="82631-121">Opis</span><span class="sxs-lookup"><span data-stu-id="82631-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82631-122">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="82631-122">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="82631-123">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="82631-123">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="82631-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="82631-124">Example</span></span>  
 <span data-ttu-id="82631-125">Następujący kody XML pokazuje użycie `<add>` i `<remove>` elementów, aby zastąpić domyślne sesji programu obsługi tokenów niestandardową sesję programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="82631-125">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="82631-126">Kod XML jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="82631-126">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```

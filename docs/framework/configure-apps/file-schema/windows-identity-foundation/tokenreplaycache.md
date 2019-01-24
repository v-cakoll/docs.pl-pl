---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1e89afc5764dbdb86e87d2307425299dff57c686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525174"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="f4245-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="f4245-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="f4245-103">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f4245-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="f4245-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f4245-104">\<system.identityModel></span></span>  
<span data-ttu-id="f4245-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f4245-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f4245-106">\<caches></span><span class="sxs-lookup"><span data-stu-id="f4245-106">\<caches></span></span>  
<span data-ttu-id="f4245-107">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="f4245-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4245-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4245-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4245-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f4245-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f4245-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f4245-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4245-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4245-111">Attributes</span></span>  
  
|<span data-ttu-id="f4245-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f4245-112">Attribute</span></span>|<span data-ttu-id="f4245-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f4245-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f4245-114">— typ</span><span class="sxs-lookup"><span data-stu-id="f4245-114">type</span></span>|<span data-ttu-id="f4245-115">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="f4245-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="f4245-116">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="f4245-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="f4245-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f4245-117">Child Elements</span></span>  
 <span data-ttu-id="f4245-118">Brak</span><span class="sxs-lookup"><span data-stu-id="f4245-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4245-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f4245-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f4245-120">Element</span><span class="sxs-lookup"><span data-stu-id="f4245-120">Element</span></span>|<span data-ttu-id="f4245-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f4245-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4245-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="f4245-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="f4245-123">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f4245-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4245-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f4245-124">Remarks</span></span>  
 <span data-ttu-id="f4245-125">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4245-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="f4245-126">Wykrywanie powtórzeń tokenów jest włączane przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który określa również czas wygaśnięcia maksymalna tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4245-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4245-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4245-127">Example</span></span>  
 <span data-ttu-id="f4245-128">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="f4245-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4245-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4245-129">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="f4245-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="f4245-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)

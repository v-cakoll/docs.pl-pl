---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: d21a819f789b5be4bdf7ebf57b37a072e1d213ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206224"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="2c2c3-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="2c2c3-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="2c2c3-103">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="2c2c3-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2c2c3-104">\<system.identityModel></span></span>  
<span data-ttu-id="2c2c3-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2c2c3-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2c2c3-106">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="2c2c3-106">\<caches></span></span>  
<span data-ttu-id="2c2c3-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="2c2c3-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c2c3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c2c3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c2c3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c2c3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2c2c3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c2c3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c2c3-111">Attributes</span></span>  
  
|<span data-ttu-id="2c2c3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2c2c3-112">Attribute</span></span>|<span data-ttu-id="2c2c3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="2c2c3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c2c3-114">— typ</span><span class="sxs-lookup"><span data-stu-id="2c2c3-114">type</span></span>|<span data-ttu-id="2c2c3-115">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="2c2c3-116">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="2c2c3-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="2c2c3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c2c3-117">Child Elements</span></span>  
 <span data-ttu-id="2c2c3-118">Brak</span><span class="sxs-lookup"><span data-stu-id="2c2c3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c2c3-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c2c3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c2c3-120">Element</span><span class="sxs-lookup"><span data-stu-id="2c2c3-120">Element</span></span>|<span data-ttu-id="2c2c3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2c2c3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c2c3-122">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="2c2c3-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="2c2c3-123">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c2c3-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c2c3-124">Remarks</span></span>  
 <span data-ttu-id="2c2c3-125">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="2c2c3-126">Wykrywanie powtórzeń tokenów jest włączane przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który określa również czas wygaśnięcia maksymalna tokenów.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c2c3-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c2c3-127">Example</span></span>  
 <span data-ttu-id="2c2c3-128">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="2c2c3-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c2c3-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c2c3-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="2c2c3-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="2c2c3-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)

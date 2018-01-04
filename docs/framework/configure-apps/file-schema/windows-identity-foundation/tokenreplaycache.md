---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f388369d4dc2e590473ad98189ade70b77551b10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="213a7-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="213a7-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="213a7-103">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="213a7-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="213a7-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="213a7-104">\<system.identityModel></span></span>  
<span data-ttu-id="213a7-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="213a7-105">\<identityConfiguration></span></span>  
<span data-ttu-id="213a7-106">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="213a7-106">\<caches></span></span>  
<span data-ttu-id="213a7-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="213a7-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213a7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="213a7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="213a7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="213a7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="213a7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="213a7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="213a7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="213a7-111">Attributes</span></span>  
  
|<span data-ttu-id="213a7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="213a7-112">Attribute</span></span>|<span data-ttu-id="213a7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="213a7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="213a7-114">— typ</span><span class="sxs-lookup"><span data-stu-id="213a7-114">type</span></span>|<span data-ttu-id="213a7-115">Typ, który pochodzi z <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="213a7-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="213a7-116">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołania do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="213a7-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="213a7-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="213a7-117">Child Elements</span></span>  
 <span data-ttu-id="213a7-118">Brak</span><span class="sxs-lookup"><span data-stu-id="213a7-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="213a7-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="213a7-119">Parent Elements</span></span>  
  
|<span data-ttu-id="213a7-120">Element</span><span class="sxs-lookup"><span data-stu-id="213a7-120">Element</span></span>|<span data-ttu-id="213a7-121">Opis</span><span class="sxs-lookup"><span data-stu-id="213a7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="213a7-122">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="213a7-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="213a7-123">Rejestruje pamięci podręcznych, używany przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="213a7-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="213a7-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="213a7-124">Remarks</span></span>  
 <span data-ttu-id="213a7-125">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania tokeny powtórzony.</span><span class="sxs-lookup"><span data-stu-id="213a7-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="213a7-126">Wykrywanie powtórzeń tokenów jest włączana przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który również określa czas maksymalny wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="213a7-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="213a7-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="213a7-127">Example</span></span>  
 <span data-ttu-id="213a7-128">Następujący kod XML zawiera konfiguracji niestandardowej pamięci podręcznej wykrywania tokeny powtórzony.</span><span class="sxs-lookup"><span data-stu-id="213a7-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="213a7-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="213a7-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="213a7-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="213a7-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)

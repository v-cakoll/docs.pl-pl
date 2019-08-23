---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5747a4cfa93118dd41292904b168bbef02fec415
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944078"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="bbbb8-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="bbbb8-101">\<tokenReplayCache></span></span>
<span data-ttu-id="bbbb8-102">Rejestruje pamięć podręczną powtarzania tokenów za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="bbbb8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bbbb8-103">\<system.identityModel></span></span>  
<span data-ttu-id="bbbb8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bbbb8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bbbb8-105">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="bbbb8-105">\<caches></span></span>  
<span data-ttu-id="bbbb8-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="bbbb8-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbb8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbbb8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbbb8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bbbb8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bbbb8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbbb8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bbbb8-110">Attributes</span></span>  
  
|<span data-ttu-id="bbbb8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bbbb8-111">Attribute</span></span>|<span data-ttu-id="bbbb8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bbbb8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bbbb8-113">— typ</span><span class="sxs-lookup"><span data-stu-id="bbbb8-113">type</span></span>|<span data-ttu-id="bbbb8-114">Typ, który pochodzi od <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="bbbb8-115">Aby uzyskać więcej informacji na temat sposobu określania niestandardowego `type`, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="bbbb8-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bbbb8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bbbb8-116">Child Elements</span></span>  
 <span data-ttu-id="bbbb8-117">Brak</span><span class="sxs-lookup"><span data-stu-id="bbbb8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbbb8-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bbbb8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bbbb8-119">Element</span><span class="sxs-lookup"><span data-stu-id="bbbb8-119">Element</span></span>|<span data-ttu-id="bbbb8-120">Opis</span><span class="sxs-lookup"><span data-stu-id="bbbb8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bbbb8-121">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="bbbb8-121">\<caches></span></span>](caches.md)|<span data-ttu-id="bbbb8-122">Rejestruje pamięci podręczne używane przez usługę lub kolekcję programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbbb8-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbbb8-123">Remarks</span></span>  
 <span data-ttu-id="bbbb8-124">Pamięć podręczna powtarzania tokenów służy do wykrywania powtórzonych tokenów.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="bbbb8-125">Wykrywanie powtarzania tokenów jest włączane przez [ \<element > tokenReplayDetection](tokenreplaydetection.md) , który określa również maksymalny czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-125">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbbb8-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbbb8-126">Example</span></span>  
 <span data-ttu-id="bbbb8-127">Poniższy kod XML przedstawia konfigurację niestandardowej pamięci podręcznej na potrzeby wykrywania ponownie odtwarzanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="bbbb8-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbbb8-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bbbb8-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="bbbb8-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="bbbb8-129">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)

---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251784"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="7f8ff-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="7f8ff-101">\<tokenReplayCache></span></span>
<span data-ttu-id="7f8ff-102">Rejestruje pamięć podręczną powtarzania tokenów za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="7f8ff-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7f8ff-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7f8ff-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="7f8ff-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="7f8ff-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7f8ff-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="7f8ff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<pamięć podręczna >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="7f8ff-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="7f8ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**</span><span class="sxs-lookup"><span data-stu-id="7f8ff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f8ff-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f8ff-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f8ff-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f8ff-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7f8ff-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f8ff-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f8ff-111">Attributes</span></span>  
  
|<span data-ttu-id="7f8ff-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f8ff-112">Attribute</span></span>|<span data-ttu-id="7f8ff-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7f8ff-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f8ff-114">— typ</span><span class="sxs-lookup"><span data-stu-id="7f8ff-114">type</span></span>|<span data-ttu-id="7f8ff-115">Typ, który pochodzi od <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="7f8ff-116">Aby uzyskać więcej informacji na temat sposobu określania niestandardowego `type`, zobacz [odwołania do typów niestandardowych].</span><span class="sxs-lookup"><span data-stu-id="7f8ff-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="7f8ff-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f8ff-117">Child Elements</span></span>  
 <span data-ttu-id="7f8ff-118">Brak</span><span class="sxs-lookup"><span data-stu-id="7f8ff-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f8ff-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f8ff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7f8ff-120">Element</span><span class="sxs-lookup"><span data-stu-id="7f8ff-120">Element</span></span>|<span data-ttu-id="7f8ff-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7f8ff-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f8ff-122">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="7f8ff-122">\<caches></span></span>](caches.md)|<span data-ttu-id="7f8ff-123">Rejestruje pamięci podręczne używane przez usługę lub kolekcję programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f8ff-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f8ff-124">Remarks</span></span>  
 <span data-ttu-id="7f8ff-125">Pamięć podręczna powtarzania tokenów służy do wykrywania powtórzonych tokenów.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="7f8ff-126">Wykrywanie powtarzania tokenów jest włączane przez [ \<element > tokenReplayDetection](tokenreplaydetection.md) , który określa również maksymalny czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f8ff-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f8ff-127">Example</span></span>  
 <span data-ttu-id="7f8ff-128">Poniższy kod XML przedstawia konfigurację niestandardowej pamięci podręcznej na potrzeby wykrywania ponownie odtwarzanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="7f8ff-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f8ff-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f8ff-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="7f8ff-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="7f8ff-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)

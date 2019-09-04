---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251768"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="69b72-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="69b72-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="69b72-102">Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="69b72-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="69b72-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69b72-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69b72-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="69b72-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="69b72-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="69b72-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="69b72-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**</span><span class="sxs-lookup"><span data-stu-id="69b72-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b72-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="69b72-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="69b72-108">Typ</span><span class="sxs-lookup"><span data-stu-id="69b72-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69b72-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69b72-109">Attributes and Elements</span></span>  
 <span data-ttu-id="69b72-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69b72-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69b72-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69b72-111">Attributes</span></span>  
  
|<span data-ttu-id="69b72-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69b72-112">Attribute</span></span>|<span data-ttu-id="69b72-113">Opis</span><span class="sxs-lookup"><span data-stu-id="69b72-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69b72-114">dostępny</span><span class="sxs-lookup"><span data-stu-id="69b72-114">enabled</span></span>|<span data-ttu-id="69b72-115">Wartość określająca, czy jest włączone wykrywanie powtarzania tokenów; wartość "true" w celu włączenia wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="69b72-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="69b72-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="69b72-116">expirationPeriod</span></span>|<span data-ttu-id="69b72-117">A <xref:System.TimeSpan> , która określa maksymalny czas, po upływie którego element zostanie uznany za wygasły i usunięty z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="69b72-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="69b72-118">Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="69b72-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69b72-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69b72-119">Child Elements</span></span>  
 <span data-ttu-id="69b72-120">Brak</span><span class="sxs-lookup"><span data-stu-id="69b72-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69b72-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69b72-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69b72-122">Element</span><span class="sxs-lookup"><span data-stu-id="69b72-122">Element</span></span>|<span data-ttu-id="69b72-123">Opis</span><span class="sxs-lookup"><span data-stu-id="69b72-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69b72-124">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="69b72-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="69b72-125">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="69b72-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="69b72-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="69b72-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="69b72-127">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="69b72-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69b72-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69b72-128">Remarks</span></span>  
 <span data-ttu-id="69b72-129">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="69b72-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="69b72-130">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="69b72-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="69b72-131">Typ pamięci podręcznej powtarzania tokenów jest określany przez [ \<element > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="69b72-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>

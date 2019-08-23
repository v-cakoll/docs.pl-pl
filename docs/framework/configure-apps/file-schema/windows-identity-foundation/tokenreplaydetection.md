---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944296"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="13371-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="13371-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="13371-102">Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="13371-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="13371-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="13371-103">\<system.identityModel></span></span>  
<span data-ttu-id="13371-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13371-104">\<identityConfiguration></span></span>  
<span data-ttu-id="13371-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="13371-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13371-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="13371-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="13371-107">Typ</span><span class="sxs-lookup"><span data-stu-id="13371-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13371-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13371-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13371-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13371-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13371-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13371-110">Attributes</span></span>  
  
|<span data-ttu-id="13371-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13371-111">Attribute</span></span>|<span data-ttu-id="13371-112">Opis</span><span class="sxs-lookup"><span data-stu-id="13371-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13371-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="13371-113">enabled</span></span>|<span data-ttu-id="13371-114">Wartość określająca, czy jest włączone wykrywanie powtarzania tokenów; wartość "true" w celu włączenia wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="13371-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="13371-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="13371-115">expirationPeriod</span></span>|<span data-ttu-id="13371-116">A <xref:System.TimeSpan> , która określa maksymalny czas, po upływie którego element zostanie uznany za wygasły i usunięty z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="13371-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="13371-117">Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="13371-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13371-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13371-118">Child Elements</span></span>  
 <span data-ttu-id="13371-119">Brak</span><span class="sxs-lookup"><span data-stu-id="13371-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13371-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13371-120">Parent Elements</span></span>  
  
|<span data-ttu-id="13371-121">Element</span><span class="sxs-lookup"><span data-stu-id="13371-121">Element</span></span>|<span data-ttu-id="13371-122">Opis</span><span class="sxs-lookup"><span data-stu-id="13371-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13371-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13371-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="13371-124">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="13371-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="13371-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="13371-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="13371-126">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="13371-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13371-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13371-127">Remarks</span></span>  
 <span data-ttu-id="13371-128">Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="13371-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="13371-129">Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="13371-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="13371-130">Typ pamięci podręcznej powtarzania tokenów jest określany przez [ \<element > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="13371-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>

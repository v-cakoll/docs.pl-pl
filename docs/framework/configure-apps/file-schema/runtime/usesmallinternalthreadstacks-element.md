---
title: "&lt;Usesmallinternalthreadstacks —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="d49c4-102">&lt;Usesmallinternalthreadstacks —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="d49c4-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="d49c4-103">Użyj żądania, że środowisko uruchomieniowe języka wspólnego (CLR) Zmniejsz pamięci, określając rozmiary jawne stosu podczas tworzenia niektórych wątków, które jest używana wewnętrznie, zamiast domyślny rozmiar stosu dla tych wątków.</span><span class="sxs-lookup"><span data-stu-id="d49c4-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="d49c4-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="d49c4-104">\<configuration> Element</span></span>  
<span data-ttu-id="d49c4-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="d49c4-105">\<runtime> Element</span></span>  
<span data-ttu-id="d49c4-106">\<Usesmallinternalthreadstacks — > — Element</span><span class="sxs-lookup"><span data-stu-id="d49c4-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d49c4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d49c4-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d49c4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d49c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d49c4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d49c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d49c4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d49c4-110">Attributes</span></span>  
  
|<span data-ttu-id="d49c4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d49c4-111">Attribute</span></span>|<span data-ttu-id="d49c4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d49c4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d49c4-113">włączone</span><span class="sxs-lookup"><span data-stu-id="d49c4-113">enabled</span></span>|<span data-ttu-id="d49c4-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d49c4-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d49c4-115">Określa, czy żądanie rozmiary CLR Użyj jawnego stosu zamiast domyślny rozmiar stosu podczas tworzenia niektórych wątków, które jest używana wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d49c4-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="d49c4-116">Rozmiar stosu jawne są mniejsze niż domyślny rozmiar stosu 1 MB.</span><span class="sxs-lookup"><span data-stu-id="d49c4-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d49c4-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d49c4-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="d49c4-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="d49c4-118">Value</span></span>|<span data-ttu-id="d49c4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d49c4-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d49c4-120">true</span><span class="sxs-lookup"><span data-stu-id="d49c4-120">true</span></span>|<span data-ttu-id="d49c4-121">Żądanie rozmiary jawne stosu.</span><span class="sxs-lookup"><span data-stu-id="d49c4-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="d49c4-122">false</span><span class="sxs-lookup"><span data-stu-id="d49c4-122">false</span></span>|<span data-ttu-id="d49c4-123">Użyj domyślnego rozmiaru stosu.</span><span class="sxs-lookup"><span data-stu-id="d49c4-123">Use the default stack size.</span></span> <span data-ttu-id="d49c4-124">Jest to wartość domyślna dla [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d49c4-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d49c4-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d49c4-125">Child Elements</span></span>  
 <span data-ttu-id="d49c4-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="d49c4-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d49c4-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d49c4-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d49c4-128">Element</span><span class="sxs-lookup"><span data-stu-id="d49c4-128">Element</span></span>|<span data-ttu-id="d49c4-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d49c4-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d49c4-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d49c4-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d49c4-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d49c4-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d49c4-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d49c4-132">Remarks</span></span>  
 <span data-ttu-id="d49c4-133">Ten element konfiguracji jest używane do żądania użyj ograniczoną ilość pamięci wirtualnej w ramach procesu, ponieważ rozmiary jawne wątku, używane przez środowisko CLR do wewnętrznego wątków, jeśli żądanie jest honorowane, są mniejsze niż domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d49c4-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d49c4-134">Ten element konfiguracji jest to żądanie do środowiska CLR, zamiast być bezwzględnie spełniony.</span><span class="sxs-lookup"><span data-stu-id="d49c4-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="d49c4-135">W [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], żądanie jest honorowane tylko w przypadku x86 architektury.</span><span class="sxs-lookup"><span data-stu-id="d49c4-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="d49c4-136">Ten element może być całkowicie ignorowane w przyszłych wersjach środowiska CLR lub zastępuje rozmiary jawne stosu, które są zawsze używane dla wybranych wątków wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="d49c4-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="d49c4-137">Określanie, czy ten element konfiguracji zamienia niezawodności mniejsze zużycie pamięci wirtualnej Jeśli środowisko CLR będzie honorować żądania, ponieważ stos mniejszych może sprawić stosu najprawdopodobniej przepełnienie.</span><span class="sxs-lookup"><span data-stu-id="d49c4-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d49c4-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d49c4-138">Example</span></span>  
 <span data-ttu-id="d49c4-139">Poniższy przykład pokazuje, jak żądania CLR stosu jawne użyj rozmiarów niektórych wątków, które jest używana wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d49c4-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d49c4-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d49c4-140">See Also</span></span>  
 [<span data-ttu-id="d49c4-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d49c4-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d49c4-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d49c4-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

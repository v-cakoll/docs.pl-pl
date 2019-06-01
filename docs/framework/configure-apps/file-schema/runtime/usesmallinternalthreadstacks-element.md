---
title: <UseSmallInternalThreadStacks>, element
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f098065cc005c59ec558ffa1f95202715624e7d
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456114"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="d8a46-102">\<UseSmallInternalThreadStacks> Element</span><span class="sxs-lookup"><span data-stu-id="d8a46-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="d8a46-103">Użyj żądania, że środowisko uruchomieniowe języka wspólnego (CLR), zmniejszyć pamięci, określając stosu jawnych rozmiarów, podczas tworzenia niektórych wątków, które używa wewnętrznie, zamiast korzystać z domyślnego rozmiaru stosu dla tych wątków.</span><span class="sxs-lookup"><span data-stu-id="d8a46-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="d8a46-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="d8a46-104">\<configuration> Element</span></span>  
<span data-ttu-id="d8a46-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="d8a46-105">\<runtime> Element</span></span>  
<span data-ttu-id="d8a46-106">\<UseSmallInternalThreadStacks> Element</span><span class="sxs-lookup"><span data-stu-id="d8a46-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a46-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8a46-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8a46-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d8a46-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d8a46-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d8a46-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8a46-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d8a46-110">Attributes</span></span>  
  
|<span data-ttu-id="d8a46-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d8a46-111">Attribute</span></span>|<span data-ttu-id="d8a46-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d8a46-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8a46-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="d8a46-113">enabled</span></span>|<span data-ttu-id="d8a46-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d8a46-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d8a46-115">Określa, czy żądanie rozmiary CLR Użyj jawnego stosu zamiast domyślnego rozmiaru stosu podczas tworzenia niektórych wątków, które używa wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d8a46-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="d8a46-116">Rozmiary jawne stosu są mniejsze niż domyślny rozmiar stosu 1 MB.</span><span class="sxs-lookup"><span data-stu-id="d8a46-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d8a46-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d8a46-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="d8a46-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="d8a46-118">Value</span></span>|<span data-ttu-id="d8a46-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d8a46-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d8a46-120">true</span><span class="sxs-lookup"><span data-stu-id="d8a46-120">true</span></span>|<span data-ttu-id="d8a46-121">Żądanie stosu jawnych rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="d8a46-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="d8a46-122">false</span><span class="sxs-lookup"><span data-stu-id="d8a46-122">false</span></span>|<span data-ttu-id="d8a46-123">Użyj domyślnego rozmiaru stosu.</span><span class="sxs-lookup"><span data-stu-id="d8a46-123">Use the default stack size.</span></span> <span data-ttu-id="d8a46-124">Jest to flaga domyślna dla [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d8a46-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8a46-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d8a46-125">Child Elements</span></span>  
 <span data-ttu-id="d8a46-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8a46-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8a46-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d8a46-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d8a46-128">Element</span><span class="sxs-lookup"><span data-stu-id="d8a46-128">Element</span></span>|<span data-ttu-id="d8a46-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d8a46-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d8a46-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8a46-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d8a46-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d8a46-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8a46-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8a46-132">Remarks</span></span>  
 <span data-ttu-id="d8a46-133">Ten element konfiguracji służy do żądania użyj ograniczoną ilość pamięci wirtualnej w procesie, ponieważ rozmiary jawne wątków, które środowisko CLR używa wewnętrznego wątków, jeśli żądanie zostanie uznane, są mniejsze niż domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d8a46-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d8a46-134">Ten element konfiguracji to żądanie do środowiska CLR zamiast bezwzględnie.</span><span class="sxs-lookup"><span data-stu-id="d8a46-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="d8a46-135">W programie .NET Framework 4, żądanie zostanie uznane tylko w przypadku x86 architektury.</span><span class="sxs-lookup"><span data-stu-id="d8a46-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="d8a46-136">Ten element może być całkowicie ignorowane w przyszłych wersjach środowiska CLR lub zastępuje rozmiary jawne stosu, które są zawsze używane dla wybranych wątków wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="d8a46-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="d8a46-137">Określanie, czy ten element konfiguracji zamienia niezawodność mniejsze użycie pamięci wirtualnej, jeśli środowisko CLR honoruje żądania, ponieważ mniejsze rozmiary stos może sprawić stosu najprawdopodobniej przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="d8a46-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8a46-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8a46-138">Example</span></span>  
 <span data-ttu-id="d8a46-139">Poniższy przykład pokazuje, jak żądanie stosu jawnego użycia CLR rozmiarów dla niektórych wątków, które używa wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d8a46-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8a46-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8a46-140">See also</span></span>

- [<span data-ttu-id="d8a46-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d8a46-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d8a46-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d8a46-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)

---
title: <UseSmallInternalThreadStacks>, element
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74678089bb1b19295983064eb7ad54fbf0a1e361
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663387"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="d34f5-102">\<UseSmallInternalThreadStacks, element ></span><span class="sxs-lookup"><span data-stu-id="d34f5-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="d34f5-103">Żądania, które zmniejszają użycie pamięci przez środowisko uruchomieniowe języka wspólnego (CLR) przez określenie jawnych rozmiarów stosu podczas tworzenia niektórych wątków, które używają wewnętrznie, zamiast używania domyślnego rozmiaru stosu dla tych wątków.</span><span class="sxs-lookup"><span data-stu-id="d34f5-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="d34f5-104">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d34f5-104">\<configuration> Element</span></span>  
<span data-ttu-id="d34f5-105">\<Element > środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d34f5-105">\<runtime> Element</span></span>  
<span data-ttu-id="d34f5-106">\<UseSmallInternalThreadStacks, element ></span><span class="sxs-lookup"><span data-stu-id="d34f5-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34f5-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d34f5-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d34f5-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d34f5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d34f5-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d34f5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d34f5-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d34f5-110">Attributes</span></span>  
  
|<span data-ttu-id="d34f5-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d34f5-111">Attribute</span></span>|<span data-ttu-id="d34f5-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d34f5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d34f5-113">dostępny</span><span class="sxs-lookup"><span data-stu-id="d34f5-113">enabled</span></span>|<span data-ttu-id="d34f5-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d34f5-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d34f5-115">Określa, czy należy zażądać, aby środowisko CLR używało jawnych rozmiarów stosu zamiast domyślnego rozmiaru stosu, gdy tworzy pewne wątki używane wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d34f5-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="d34f5-116">Jawne rozmiary stosu są mniejsze niż domyślny rozmiar stosu wynoszący 1 MB.</span><span class="sxs-lookup"><span data-stu-id="d34f5-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d34f5-117">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d34f5-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="d34f5-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="d34f5-118">Value</span></span>|<span data-ttu-id="d34f5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="d34f5-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d34f5-120">true</span><span class="sxs-lookup"><span data-stu-id="d34f5-120">true</span></span>|<span data-ttu-id="d34f5-121">Żądaj jawnych rozmiarów stosu.</span><span class="sxs-lookup"><span data-stu-id="d34f5-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="d34f5-122">false</span><span class="sxs-lookup"><span data-stu-id="d34f5-122">false</span></span>|<span data-ttu-id="d34f5-123">Użyj domyślnego rozmiaru stosu.</span><span class="sxs-lookup"><span data-stu-id="d34f5-123">Use the default stack size.</span></span> <span data-ttu-id="d34f5-124">Jest to wartość domyślna dla .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d34f5-124">This is the default for the .NET Framework 4.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d34f5-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d34f5-125">Child Elements</span></span>  
 <span data-ttu-id="d34f5-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="d34f5-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d34f5-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d34f5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d34f5-128">Element</span><span class="sxs-lookup"><span data-stu-id="d34f5-128">Element</span></span>|<span data-ttu-id="d34f5-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d34f5-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d34f5-130">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d34f5-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d34f5-131">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d34f5-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d34f5-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d34f5-132">Remarks</span></span>  
 <span data-ttu-id="d34f5-133">Ten element konfiguracji jest używany do żądania zredukowania użycia pamięci wirtualnej w procesie, ponieważ jawne rozmiary wątków używane przez środowisko CLR dla wewnętrznych wątków, jeśli żądanie jest honorowane, są mniejsze niż rozmiar domyślny.</span><span class="sxs-lookup"><span data-stu-id="d34f5-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d34f5-134">Ten element konfiguracji jest żądaniem do środowiska CLR, a nie bezwzględnym wymaganiem.</span><span class="sxs-lookup"><span data-stu-id="d34f5-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="d34f5-135">W .NET Framework 4 żądanie jest uznawane za tylko dla architektury x86.</span><span class="sxs-lookup"><span data-stu-id="d34f5-135">In the .NET Framework 4, the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="d34f5-136">Ten element może zostać całkowicie zignorowany w przyszłych wersjach środowiska CLR lub zastąpiony przez jawne rozmiary stosu, które są zawsze używane dla wybranych wewnętrznych wątków.</span><span class="sxs-lookup"><span data-stu-id="d34f5-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="d34f5-137">Określenie tego elementu konfiguracji zapewnia niezawodność dla mniejszej ilości pamięci wirtualnej, jeśli środowisko CLR honoruje żądanie, ponieważ mniejsze rozmiary stosu mogą potencjalnie spowodować przepełnienie stosu.</span><span class="sxs-lookup"><span data-stu-id="d34f5-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d34f5-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="d34f5-138">Example</span></span>  
 <span data-ttu-id="d34f5-139">Poniższy przykład pokazuje, jak zażądać, aby środowisko CLR używało jawnych rozmiarów stosu dla niektórych wątków używanych wewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="d34f5-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d34f5-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d34f5-140">See also</span></span>

- [<span data-ttu-id="d34f5-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d34f5-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d34f5-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d34f5-142">Configuration File Schema</span></span>](../index.md)

---
title: <performanceCounters> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697151"
---
# <a name="performancecounters-element"></a><span data-ttu-id="7d2e6-102">\<performanceCounters > elementu</span><span class="sxs-lookup"><span data-stu-id="7d2e6-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="7d2e6-103">Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-103">Specifies the size of the global memory shared by performance counters.</span></span>

[<span data-ttu-id="7d2e6-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="7d2e6-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7d2e6-105">&nbsp; @ no__t-1[ **\<system. Diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d2e6-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="7d2e6-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="7d2e6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7d2e6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d2e6-107">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d2e6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d2e6-108">Attributes and Elements</span></span>

<span data-ttu-id="7d2e6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d2e6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d2e6-110">Attributes</span></span>

|<span data-ttu-id="7d2e6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d2e6-111">Attribute</span></span>|<span data-ttu-id="7d2e6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d2e6-112">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7d2e6-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="7d2e6-113">filemappingsize</span></span>|<span data-ttu-id="7d2e6-114">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7d2e6-115">Określa rozmiar pamięci globalnej udostępnionej przez liczniki wydajności w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="7d2e6-116">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-116">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7d2e6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d2e6-117">Child Elements</span></span>

<span data-ttu-id="7d2e6-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7d2e6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d2e6-119">Parent Elements</span></span>

|<span data-ttu-id="7d2e6-120">Element</span><span class="sxs-lookup"><span data-stu-id="7d2e6-120">Element</span></span>|<span data-ttu-id="7d2e6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7d2e6-121">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="7d2e6-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="7d2e6-123">Określa element główny dla sekcji konfiguracji ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-123">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d2e6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d2e6-124">Remarks</span></span>

<span data-ttu-id="7d2e6-125">Liczniki wydajności używają pliku mapowanego na pamięć lub pamięci współdzielonej do publikowania danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="7d2e6-126">Rozmiar pamięci współdzielonej określa, ile wystąpień może być używanych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="7d2e6-127">Istnieją dwa typy pamięci współdzielonej: globalna pamięć udostępniona i oddzielna pamięć współdzielona.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="7d2e6-128">Globalna pamięć współdzielona jest używana przez wszystkie kategorie liczników wydajności zainstalowane z .NET Framework wersjami 1,0 lub 1,1.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="7d2e6-129">Kategorie liczników wydajności zainstalowane z .NET Framework w wersji 2,0 używają oddzielnej pamięci współdzielonej, z każdą kategorią licznika wydajności mającą własną pamięć.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="7d2e6-130">Rozmiar globalnej pamięci współdzielonej można ustawić tylko przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="7d2e6-131">Domyślny rozmiar to 524 288 bTak, maksymalny rozmiar to 33 554 432 bajtów, a minimalny rozmiar to 32 768 bajtów.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="7d2e6-132">Ponieważ globalna pamięć udostępniona jest współdzielona przez wszystkie procesy i kategorie, pierwszy twórca określa rozmiar.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="7d2e6-133">W przypadku zdefiniowania rozmiaru w pliku konfiguracyjnym aplikacji ten rozmiar jest używany tylko wtedy, gdy aplikacja jest pierwszą aplikacją, która powoduje wykonanie liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="7d2e6-134">W związku z tym poprawną lokalizacją określającą wartość `filemappingsize` jest plik Machine. config.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="7d2e6-135">Pamięć w globalnej pamięci współdzielonej nie może zostać wydana przez poszczególne liczniki wydajności, więc ostatecznie globalna pamięć udostępniona jest wyczerpana, jeśli utworzono dużą liczbę wystąpień liczników wydajności o różnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="7d2e6-136">W przypadku rozmiaru oddzielnej pamięci współdzielonej wartość DWORD FileMappingSize w kluczu rejestru HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services @ no__t-0 *\<category name >* \Performance jest przywoływana jako pierwsza, a następnie wartość określony dla globalnej pamięci współdzielonej w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="7d2e6-137">Jeśli wartość FileMappingSize nie istnieje, oddzielny rozmiar pamięci współdzielonej jest ustawiany na jeden czwarty (1/4) ustawienia globalne w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7d2e6-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d2e6-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d2e6-138">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>

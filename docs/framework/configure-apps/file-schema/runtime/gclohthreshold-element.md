---
title: GCLOHThreshold, element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451221"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="de131-102">GCLOHThreshold, element</span><span class="sxs-lookup"><span data-stu-id="de131-102">GCLOHThreshold element</span></span>

<span data-ttu-id="de131-103">Określa rozmiar progu (w bajtach), który powoduje, że moduł wyrzucania elementów bezużytecznych umieszcza obiekty na stercie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="de131-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="de131-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de131-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="de131-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de131-105">Attributes</span></span>

|<span data-ttu-id="de131-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="de131-106">Attribute</span></span>|<span data-ttu-id="de131-107">Opis</span><span class="sxs-lookup"><span data-stu-id="de131-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="de131-108">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="de131-108">Required attribute.</span></span><br /><br /><span data-ttu-id="de131-109">Określa rozmiar progu, który powoduje, że obiekty przechodzą na stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="de131-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="de131-110">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="de131-110">enabled attribute</span></span>

|<span data-ttu-id="de131-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="de131-111">Value</span></span>|<span data-ttu-id="de131-112">Opis</span><span class="sxs-lookup"><span data-stu-id="de131-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="de131-113">Rozmiar progu, w bajtach, który powoduje, że obiekty przechodzą na stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="de131-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="de131-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de131-114">Child elements</span></span>

<span data-ttu-id="de131-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="de131-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="de131-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de131-116">Parent elements</span></span>

|<span data-ttu-id="de131-117">Element</span><span class="sxs-lookup"><span data-stu-id="de131-117">Element</span></span>|<span data-ttu-id="de131-118">Opis</span><span class="sxs-lookup"><span data-stu-id="de131-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="de131-119">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="de131-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="de131-120">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="de131-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="de131-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de131-121">Remarks</span></span>

<span data-ttu-id="de131-122">To ustawienie zostało wprowadzone w .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="de131-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="de131-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de131-123">See also</span></span>

- [<span data-ttu-id="de131-124">Schemat ustawień czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="de131-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="de131-125">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="de131-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="de131-126">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="de131-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="de131-127">Podstawowe opcje konfiguracji sieci w czasie wykonywania dla usługi GC</span><span class="sxs-lookup"><span data-stu-id="de131-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)

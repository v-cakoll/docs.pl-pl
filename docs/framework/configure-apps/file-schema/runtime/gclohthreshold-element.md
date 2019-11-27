---
title: GCLOHThreshold, element
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451221"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="b203a-102">GCLOHThreshold, element</span><span class="sxs-lookup"><span data-stu-id="b203a-102">GCLOHThreshold element</span></span>

<span data-ttu-id="b203a-103">Określa rozmiar progu (w bajtach), który powoduje, że moduł wyrzucania elementów bezużytecznych umieszcza obiekty na stercie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="b203a-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="b203a-104">[\<> konfiguracji](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b203a-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="b203a-105">&nbsp;&nbsp;[\<środowiska uruchomieniowego >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b203a-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="b203a-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold ></span><span class="sxs-lookup"><span data-stu-id="b203a-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="b203a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b203a-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="b203a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b203a-108">Attributes</span></span>

|<span data-ttu-id="b203a-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b203a-109">Attribute</span></span>|<span data-ttu-id="b203a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b203a-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b203a-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="b203a-111">Required attribute.</span></span><br /><br /><span data-ttu-id="b203a-112">Określa rozmiar progu, który powoduje, że obiekty przechodzą na stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b203a-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="b203a-113">włączony atrybut</span><span class="sxs-lookup"><span data-stu-id="b203a-113">enabled attribute</span></span>

|<span data-ttu-id="b203a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="b203a-114">Value</span></span>|<span data-ttu-id="b203a-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b203a-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="b203a-116">Rozmiar progu, w bajtach, który powoduje, że obiekty przechodzą na stertę dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b203a-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="b203a-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b203a-117">Child elements</span></span>

<span data-ttu-id="b203a-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b203a-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="b203a-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b203a-119">Parent elements</span></span>

|<span data-ttu-id="b203a-120">Element</span><span class="sxs-lookup"><span data-stu-id="b203a-120">Element</span></span>|<span data-ttu-id="b203a-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b203a-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b203a-122">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b203a-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b203a-123">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b203a-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b203a-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b203a-124">Remarks</span></span>

<span data-ttu-id="b203a-125">To ustawienie zostało wprowadzone w .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="b203a-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="b203a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b203a-126">See also</span></span>

- [<span data-ttu-id="b203a-127">Schemat ustawień czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="b203a-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="b203a-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b203a-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="b203a-129">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="b203a-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="b203a-130">Podstawowe opcje konfiguracji sieci w czasie wykonywania dla usługi GC</span><span class="sxs-lookup"><span data-stu-id="b203a-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)

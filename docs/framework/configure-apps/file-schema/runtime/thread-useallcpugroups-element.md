---
title: <Thread_UseAllCpuGroups> Element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663424"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="0936b-102">\<Thread_UseAllCpuGroups> Element</span><span class="sxs-lookup"><span data-stu-id="0936b-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="0936b-103">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="0936b-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="0936b-104">\<> konfiguracji </span><span class="sxs-lookup"><span data-stu-id="0936b-104">\<configuration></span></span>\
<span data-ttu-id="0936b-105">\<> środowiska uruchomieniowego </span><span class="sxs-lookup"><span data-stu-id="0936b-105">\<runtime></span></span>\
<span data-ttu-id="0936b-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="0936b-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="0936b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0936b-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0936b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0936b-108">Attributes and Elements</span></span>

<span data-ttu-id="0936b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0936b-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0936b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0936b-110">Attributes</span></span>

|<span data-ttu-id="0936b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0936b-111">Attribute</span></span>|<span data-ttu-id="0936b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="0936b-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0936b-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="0936b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0936b-114">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="0936b-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="0936b-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="0936b-115">enabled Attribute</span></span>

|<span data-ttu-id="0936b-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="0936b-116">Value</span></span>|<span data-ttu-id="0936b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0936b-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0936b-118">Środowisko uruchomieniowe nie dystrybuuje zarządzanych wątków w wielu grupach procesorów.</span><span class="sxs-lookup"><span data-stu-id="0936b-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="0936b-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="0936b-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="0936b-120">Środowisko uruchomieniowe dystrybuuje wątki zarządzane między wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<GCCpuGroup element >](gccpugroup-element.md) jest włączony.</span><span class="sxs-lookup"><span data-stu-id="0936b-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0936b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0936b-121">Child Elements</span></span>

<span data-ttu-id="0936b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="0936b-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0936b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0936b-123">Parent Elements</span></span>

|<span data-ttu-id="0936b-124">Element</span><span class="sxs-lookup"><span data-stu-id="0936b-124">Element</span></span>|<span data-ttu-id="0936b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="0936b-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0936b-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0936b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0936b-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0936b-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0936b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0936b-128">Remarks</span></span>

<span data-ttu-id="0936b-129">Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="0936b-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="0936b-130">Aby użyć tej funkcji, należy również włączyć [ \<GCCpuGroup >](gccpugroup-element.md) , który rozszerza odzyskiwanie pamięci do wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="0936b-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="0936b-131">Włączenie elementu > [ GCCpuGroupwymagawłączeniaelementugcServer>.\<](gcserver-element.md) [ \<](gccpugroup-element.md)</span><span class="sxs-lookup"><span data-stu-id="0936b-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="0936b-132">Jeśli te elementy nie są włączone, włączenie `<Thread_UseAllCpuGroups>` elementu nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="0936b-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="0936b-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="0936b-133">Example</span></span>

<span data-ttu-id="0936b-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="0936b-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0936b-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0936b-135">See also</span></span>

- [<span data-ttu-id="0936b-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="0936b-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0936b-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0936b-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0936b-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="0936b-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)

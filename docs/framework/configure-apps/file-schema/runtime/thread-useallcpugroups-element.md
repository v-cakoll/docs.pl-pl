---
title: <Thread_UseAllCpuGroups>, element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115408"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="13ae6-102">\<element > Thread_UseAllCpuGroups</span><span class="sxs-lookup"><span data-stu-id="13ae6-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="13ae6-103">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="13ae6-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="13ae6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="13ae6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13ae6-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="13ae6-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="13ae6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="13ae6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="13ae6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="13ae6-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13ae6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13ae6-108">Attributes and Elements</span></span>

<span data-ttu-id="13ae6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13ae6-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="13ae6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13ae6-110">Attributes</span></span>

|<span data-ttu-id="13ae6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="13ae6-111">Attribute</span></span>|<span data-ttu-id="13ae6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="13ae6-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="13ae6-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="13ae6-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="13ae6-114">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="13ae6-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="13ae6-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="13ae6-115">enabled Attribute</span></span>

|<span data-ttu-id="13ae6-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="13ae6-116">Value</span></span>|<span data-ttu-id="13ae6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="13ae6-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="13ae6-118">Środowisko uruchomieniowe nie dystrybuuje zarządzanych wątków w wielu grupach procesorów.</span><span class="sxs-lookup"><span data-stu-id="13ae6-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="13ae6-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="13ae6-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="13ae6-120">Środowisko uruchomieniowe dystrybuuje wątki zarządzane do wielu grup procesorów, jeśli komputer ma wiele grup CPU i jest włączony [\<GCCpuGroup >](gccpugroup-element.md) .</span><span class="sxs-lookup"><span data-stu-id="13ae6-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="13ae6-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13ae6-121">Child Elements</span></span>

<span data-ttu-id="13ae6-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="13ae6-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="13ae6-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13ae6-123">Parent Elements</span></span>

|<span data-ttu-id="13ae6-124">Element</span><span class="sxs-lookup"><span data-stu-id="13ae6-124">Element</span></span>|<span data-ttu-id="13ae6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="13ae6-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="13ae6-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13ae6-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="13ae6-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="13ae6-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13ae6-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13ae6-128">Remarks</span></span>

<span data-ttu-id="13ae6-129">Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="13ae6-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="13ae6-130">Aby użyć tej funkcji, należy również włączyć [\<GCCpuGroup >](gccpugroup-element.md) elementu, który rozszerza odzyskiwanie pamięci do wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="13ae6-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="13ae6-131">Włączenie elementu [\<GCCpuGroup >](gccpugroup-element.md) wymaga włączenia [\<gcServer >](gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="13ae6-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="13ae6-132">Jeśli te elementy nie są włączone, włączenie elementu `<Thread_UseAllCpuGroups>` nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="13ae6-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="13ae6-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ae6-133">Example</span></span>

<span data-ttu-id="13ae6-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="13ae6-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="13ae6-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13ae6-135">See also</span></span>

- [<span data-ttu-id="13ae6-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="13ae6-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="13ae6-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="13ae6-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="13ae6-138">\<element > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="13ae6-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)

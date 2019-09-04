---
title: <Thread_UseAllCpuGroups> Element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e964f1b2861926803b0449be06cbfd9567ac74a3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252273"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="8bb35-102">\<Thread_UseAllCpuGroups> Element</span><span class="sxs-lookup"><span data-stu-id="8bb35-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="8bb35-103">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="8bb35-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="8bb35-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bb35-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8bb35-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bb35-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8bb35-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="8bb35-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="8bb35-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bb35-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8bb35-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8bb35-108">Attributes and Elements</span></span>

<span data-ttu-id="8bb35-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8bb35-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8bb35-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8bb35-110">Attributes</span></span>

|<span data-ttu-id="8bb35-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8bb35-111">Attribute</span></span>|<span data-ttu-id="8bb35-112">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb35-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="8bb35-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb35-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8bb35-114">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="8bb35-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="8bb35-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="8bb35-115">enabled Attribute</span></span>

|<span data-ttu-id="8bb35-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="8bb35-116">Value</span></span>|<span data-ttu-id="8bb35-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb35-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="8bb35-118">Środowisko uruchomieniowe nie dystrybuuje zarządzanych wątków w wielu grupach procesorów.</span><span class="sxs-lookup"><span data-stu-id="8bb35-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="8bb35-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="8bb35-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="8bb35-120">Środowisko uruchomieniowe dystrybuuje wątki zarządzane między wiele grup CPU, jeśli komputer ma wiele grup CPU i [ \<GCCpuGroup element >](gccpugroup-element.md) jest włączony.</span><span class="sxs-lookup"><span data-stu-id="8bb35-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="8bb35-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8bb35-121">Child Elements</span></span>

<span data-ttu-id="8bb35-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="8bb35-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8bb35-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8bb35-123">Parent Elements</span></span>

|<span data-ttu-id="8bb35-124">Element</span><span class="sxs-lookup"><span data-stu-id="8bb35-124">Element</span></span>|<span data-ttu-id="8bb35-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb35-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="8bb35-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bb35-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="8bb35-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="8bb35-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8bb35-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bb35-128">Remarks</span></span>

<span data-ttu-id="8bb35-129">Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="8bb35-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="8bb35-130">Aby użyć tej funkcji, należy również włączyć [ \<GCCpuGroup >](gccpugroup-element.md) , który rozszerza odzyskiwanie pamięci do wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="8bb35-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="8bb35-131">Włączenie elementu > [ GCCpuGroupwymagawłączeniaelementugcServer>.\<](gcserver-element.md) [ \<](gccpugroup-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bb35-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="8bb35-132">Jeśli te elementy nie są włączone, włączenie `<Thread_UseAllCpuGroups>` elementu nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="8bb35-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="8bb35-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb35-133">Example</span></span>

<span data-ttu-id="8bb35-134">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="8bb35-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="8bb35-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bb35-135">See also</span></span>

- [<span data-ttu-id="8bb35-136">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="8bb35-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8bb35-137">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8bb35-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8bb35-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="8bb35-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)

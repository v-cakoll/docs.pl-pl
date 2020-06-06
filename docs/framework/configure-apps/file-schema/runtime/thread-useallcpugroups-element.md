---
title: <Thread_UseAllCpuGroups>, element
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115408"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="82c4f-102">\<Thread_UseAllCpuGroups> Element</span><span class="sxs-lookup"><span data-stu-id="82c4f-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="82c4f-103">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="82c4f-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="82c4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82c4f-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82c4f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82c4f-105">Attributes and Elements</span></span>

<span data-ttu-id="82c4f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82c4f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="82c4f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82c4f-107">Attributes</span></span>

|<span data-ttu-id="82c4f-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="82c4f-108">Attribute</span></span>|<span data-ttu-id="82c4f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="82c4f-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="82c4f-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="82c4f-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="82c4f-111">Określa, czy środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="82c4f-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="82c4f-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="82c4f-112">enabled Attribute</span></span>

|<span data-ttu-id="82c4f-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="82c4f-113">Value</span></span>|<span data-ttu-id="82c4f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="82c4f-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="82c4f-115">Środowisko uruchomieniowe nie dystrybuuje zarządzanych wątków w wielu grupach procesorów.</span><span class="sxs-lookup"><span data-stu-id="82c4f-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="82c4f-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="82c4f-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="82c4f-117">Środowisko uruchomieniowe dystrybuuje wątki zarządzane do wielu grup procesorów, jeśli komputer ma wiele grup CPU, a [\<GCCpuGroup>](gccpugroup-element.md) element jest włączony.</span><span class="sxs-lookup"><span data-stu-id="82c4f-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="82c4f-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82c4f-118">Child Elements</span></span>

<span data-ttu-id="82c4f-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="82c4f-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="82c4f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82c4f-120">Parent Elements</span></span>

|<span data-ttu-id="82c4f-121">Element</span><span class="sxs-lookup"><span data-stu-id="82c4f-121">Element</span></span>|<span data-ttu-id="82c4f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="82c4f-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="82c4f-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82c4f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="82c4f-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82c4f-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82c4f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82c4f-125">Remarks</span></span>

<span data-ttu-id="82c4f-126">Gdy komputer ma wiele grup CPU, włączenie tego elementu powoduje, że środowisko uruchomieniowe dystrybuuje wątki zarządzane we wszystkich grupach procesora.</span><span class="sxs-lookup"><span data-stu-id="82c4f-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="82c4f-127">Aby użyć tej funkcji, należy również włączyć [\<GCCpuGroup>](gccpugroup-element.md) element, który rozszerza wyrzucanie elementów bezużytecznych do wszystkich grup CPU i pobiera wszystkie rdzenie do konta podczas tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="82c4f-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="82c4f-128">Włączenie [\<GCCpuGroup>](gccpugroup-element.md) elementu wymaga włączenia [\<gcServer>](gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="82c4f-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="82c4f-129">Jeśli te elementy nie są włączone, włączenie `<Thread_UseAllCpuGroups>` elementu nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="82c4f-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="82c4f-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="82c4f-130">Example</span></span>

<span data-ttu-id="82c4f-131">Poniższy przykład pokazuje, jak włączyć obsługę wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="82c4f-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="82c4f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82c4f-132">See also</span></span>

- [<span data-ttu-id="82c4f-133">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="82c4f-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="82c4f-134">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="82c4f-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="82c4f-135">\<GCCpuGroup>Postaci</span><span class="sxs-lookup"><span data-stu-id="82c4f-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)

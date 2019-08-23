---
title: <GCCpuGroup>, element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56b23b6d5fca6d0527d509c9b6a6fc6dd82336
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920779"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="d777c-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="d777c-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="d777c-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="d777c-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="d777c-104">\<> konfiguracji </span><span class="sxs-lookup"><span data-stu-id="d777c-104">\<configuration></span></span>\
<span data-ttu-id="d777c-105">\<> środowiska uruchomieniowego </span><span class="sxs-lookup"><span data-stu-id="d777c-105">\<runtime></span></span>\
<span data-ttu-id="d777c-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="d777c-106">\<GCCpuGroup></span></span>

## <a name="syntax"></a><span data-ttu-id="d777c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="d777c-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d777c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d777c-108">Attributes and Elements</span></span>

<span data-ttu-id="d777c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d777c-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d777c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d777c-110">Attributes</span></span>

|<span data-ttu-id="d777c-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d777c-111">Attribute</span></span>|<span data-ttu-id="d777c-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d777c-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d777c-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="d777c-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d777c-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="d777c-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="d777c-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="d777c-115">enabled Attribute</span></span>

|<span data-ttu-id="d777c-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="d777c-116">Value</span></span>|<span data-ttu-id="d777c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d777c-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="d777c-118">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="d777c-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="d777c-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="d777c-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="d777c-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów, jeśli jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="d777c-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d777c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d777c-121">Child Elements</span></span>

<span data-ttu-id="d777c-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d777c-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d777c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d777c-123">Parent Elements</span></span>

|<span data-ttu-id="d777c-124">Element</span><span class="sxs-lookup"><span data-stu-id="d777c-124">Element</span></span>|<span data-ttu-id="d777c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d777c-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d777c-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d777c-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d777c-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d777c-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d777c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d777c-128">Remarks</span></span>

<span data-ttu-id="d777c-129">Jeśli na komputerze jest włączona wiele grup CPU i wyrzucanie elementów bezużytecznych serwera (zobacz [ \<gcServer >](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU i pobiera wszystkie rdzenie podczas tworzenia i Zrównoważ sterty.</span><span class="sxs-lookup"><span data-stu-id="d777c-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="d777c-130">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d777c-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="d777c-131">Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [ \<element > Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d777c-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="d777c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="d777c-132">Example</span></span>

<span data-ttu-id="d777c-133">Poniższy przykład pokazuje, jak włączyć odzyskiwanie pamięci dla wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="d777c-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d777c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d777c-134">See also</span></span>

- [<span data-ttu-id="d777c-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="d777c-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d777c-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d777c-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d777c-137">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="d777c-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="d777c-138">Stacja robocza i odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="d777c-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)

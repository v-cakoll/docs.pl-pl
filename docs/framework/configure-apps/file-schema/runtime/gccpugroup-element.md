---
title: <GCCpuGroup>, element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ff646f13c5619b0bfca1b61c86013a981c274e3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252563"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="5e047-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="5e047-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="5e047-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="5e047-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="5e047-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e047-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5e047-105">&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="5e047-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="5e047-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="5e047-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="5e047-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e047-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e047-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5e047-108">Attributes and Elements</span></span>

<span data-ttu-id="5e047-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5e047-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5e047-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e047-110">Attributes</span></span>

|<span data-ttu-id="5e047-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5e047-111">Attribute</span></span>|<span data-ttu-id="5e047-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5e047-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5e047-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="5e047-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5e047-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="5e047-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="5e047-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="5e047-115">enabled Attribute</span></span>

|<span data-ttu-id="5e047-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="5e047-116">Value</span></span>|<span data-ttu-id="5e047-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5e047-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="5e047-118">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="5e047-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="5e047-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="5e047-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="5e047-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów, jeśli jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="5e047-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="5e047-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5e047-121">Child Elements</span></span>

<span data-ttu-id="5e047-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="5e047-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5e047-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5e047-123">Parent Elements</span></span>

|<span data-ttu-id="5e047-124">Element</span><span class="sxs-lookup"><span data-stu-id="5e047-124">Element</span></span>|<span data-ttu-id="5e047-125">Opis</span><span class="sxs-lookup"><span data-stu-id="5e047-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5e047-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e047-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5e047-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5e047-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5e047-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e047-128">Remarks</span></span>

<span data-ttu-id="5e047-129">Jeśli na komputerze jest włączona wiele grup CPU i wyrzucanie elementów bezużytecznych serwera (zobacz [ \<gcServer >](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU i pobiera wszystkie rdzenie podczas tworzenia i Zrównoważ sterty.</span><span class="sxs-lookup"><span data-stu-id="5e047-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="5e047-130">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="5e047-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="5e047-131">Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [ \<element > Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5e047-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="5e047-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e047-132">Example</span></span>

<span data-ttu-id="5e047-133">Poniższy przykład pokazuje, jak włączyć odzyskiwanie pamięci dla wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="5e047-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5e047-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e047-134">See also</span></span>

- [<span data-ttu-id="5e047-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5e047-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5e047-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5e047-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="5e047-137">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="5e047-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="5e047-138">Stacja robocza i odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="5e047-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)

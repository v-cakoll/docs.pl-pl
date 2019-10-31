---
title: <GCCpuGroup> Element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116833"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="72d2e-102">\<element > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="72d2e-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="72d2e-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="72d2e-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="72d2e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="72d2e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="72d2e-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="72d2e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="72d2e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**</span><span class="sxs-lookup"><span data-stu-id="72d2e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="72d2e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="72d2e-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="72d2e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="72d2e-108">Attributes and Elements</span></span>

<span data-ttu-id="72d2e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="72d2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="72d2e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="72d2e-110">Attributes</span></span>

|<span data-ttu-id="72d2e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="72d2e-111">Attribute</span></span>|<span data-ttu-id="72d2e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="72d2e-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="72d2e-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="72d2e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="72d2e-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="72d2e-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="72d2e-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="72d2e-115">enabled Attribute</span></span>

|<span data-ttu-id="72d2e-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="72d2e-116">Value</span></span>|<span data-ttu-id="72d2e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="72d2e-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="72d2e-118">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="72d2e-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="72d2e-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="72d2e-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="72d2e-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów, jeśli jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="72d2e-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="72d2e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="72d2e-121">Child Elements</span></span>

<span data-ttu-id="72d2e-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="72d2e-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="72d2e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="72d2e-123">Parent Elements</span></span>

|<span data-ttu-id="72d2e-124">Element</span><span class="sxs-lookup"><span data-stu-id="72d2e-124">Element</span></span>|<span data-ttu-id="72d2e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="72d2e-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="72d2e-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72d2e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="72d2e-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="72d2e-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="72d2e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72d2e-128">Remarks</span></span>

<span data-ttu-id="72d2e-129">Gdy komputer ma wiele grup CPU i jest włączone odzyskiwanie pamięci serwera (zobacz [\<gcServer >](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora i pobiera wszystkie rdzenie do konta podczas tworzenia i Zrównoważ sterty.</span><span class="sxs-lookup"><span data-stu-id="72d2e-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="72d2e-130">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="72d2e-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="72d2e-131">Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="72d2e-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="72d2e-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="72d2e-132">Example</span></span>

<span data-ttu-id="72d2e-133">Poniższy przykład pokazuje, jak włączyć odzyskiwanie pamięci dla wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="72d2e-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="72d2e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72d2e-134">See also</span></span>

- [<span data-ttu-id="72d2e-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="72d2e-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="72d2e-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d2e-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="72d2e-137">Aby wyłączyć współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="72d2e-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="72d2e-138">Stacja robocza i odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="72d2e-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)

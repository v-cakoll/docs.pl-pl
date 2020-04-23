---
title: <GCCpuGroup>, element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102895"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="43b1d-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="43b1d-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="43b1d-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="43b1d-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="43b1d-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43b1d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43b1d-105">&nbsp;&nbsp;[**\<>czasu wykonywania**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="43b1d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="43b1d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>GCCpuGroup**</span><span class="sxs-lookup"><span data-stu-id="43b1d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="43b1d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b1d-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43b1d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43b1d-108">Attributes and Elements</span></span>

<span data-ttu-id="43b1d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43b1d-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="43b1d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43b1d-110">Attributes</span></span>

|<span data-ttu-id="43b1d-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="43b1d-111">Attribute</span></span>|<span data-ttu-id="43b1d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="43b1d-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="43b1d-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="43b1d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="43b1d-114">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="43b1d-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="43b1d-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="43b1d-115">enabled Attribute</span></span>

|<span data-ttu-id="43b1d-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="43b1d-116">Value</span></span>|<span data-ttu-id="43b1d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="43b1d-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="43b1d-118">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="43b1d-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="43b1d-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="43b1d-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="43b1d-120">Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesora CPU, jeśli jest włączone wyrzucanie elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="43b1d-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="43b1d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43b1d-121">Child Elements</span></span>

<span data-ttu-id="43b1d-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="43b1d-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43b1d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43b1d-123">Parent Elements</span></span>

|<span data-ttu-id="43b1d-124">Element</span><span class="sxs-lookup"><span data-stu-id="43b1d-124">Element</span></span>|<span data-ttu-id="43b1d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="43b1d-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="43b1d-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43b1d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="43b1d-127">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43b1d-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43b1d-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b1d-128">Remarks</span></span>

<span data-ttu-id="43b1d-129">Gdy komputer ma wiele grup procesora CPU i jest włączone wyrzucanie elementów bezużytecznych serwera (zobacz [ \<gcServer>](gcserver-element.md) element), włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU i uwzględnia wszystkie rdzenie podczas tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="43b1d-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="43b1d-130">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="43b1d-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="43b1d-131">Aby włączyć środowisko uruchomieniowe do dystrybucji wątków użytkownika we wszystkich grupach procesora CPU, należy również włączyć [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="43b1d-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="43b1d-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="43b1d-132">Example</span></span>

<span data-ttu-id="43b1d-133">W poniższym przykładzie pokazano, jak włączyć wyrzucanie elementów bezużytecznych dla wielu grup procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="43b1d-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="43b1d-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43b1d-134">See also</span></span>

- [<span data-ttu-id="43b1d-135">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="43b1d-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43b1d-136">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43b1d-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="43b1d-137">Wyłącz równoczesne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="43b1d-137">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="43b1d-138">Wyrzucanie elementów bezużytecznych stacji roboczych i serwera</span><span class="sxs-lookup"><span data-stu-id="43b1d-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)

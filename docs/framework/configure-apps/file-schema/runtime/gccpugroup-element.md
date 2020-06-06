---
title: <GCCpuGroup> Element
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102895"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="348dd-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="348dd-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="348dd-103">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="348dd-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="348dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="348dd-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="348dd-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="348dd-105">Attributes and Elements</span></span>

<span data-ttu-id="348dd-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="348dd-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="348dd-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="348dd-107">Attributes</span></span>

|<span data-ttu-id="348dd-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="348dd-108">Attribute</span></span>|<span data-ttu-id="348dd-109">Opis</span><span class="sxs-lookup"><span data-stu-id="348dd-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="348dd-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="348dd-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="348dd-111">Określa, czy wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="348dd-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="348dd-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="348dd-112">enabled Attribute</span></span>

|<span data-ttu-id="348dd-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="348dd-113">Value</span></span>|<span data-ttu-id="348dd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="348dd-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="348dd-115">Wyrzucanie elementów bezużytecznych nie obsługuje wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="348dd-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="348dd-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="348dd-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="348dd-117">Wyrzucanie elementów bezużytecznych obsługuje wiele grup procesorów, jeśli jest włączone odzyskiwanie pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="348dd-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="348dd-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="348dd-118">Child Elements</span></span>

<span data-ttu-id="348dd-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="348dd-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="348dd-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="348dd-120">Parent Elements</span></span>

|<span data-ttu-id="348dd-121">Element</span><span class="sxs-lookup"><span data-stu-id="348dd-121">Element</span></span>|<span data-ttu-id="348dd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="348dd-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="348dd-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="348dd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="348dd-124">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="348dd-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="348dd-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="348dd-125">Remarks</span></span>

<span data-ttu-id="348dd-126">Gdy komputer ma wiele grup CPU i jest włączone odzyskiwanie pamięci serwera (zobacz [\<gcServer>](gcserver-element.md) element), włączenie tego elementu rozszerza odzyskiwanie pamięci dla wszystkich grup CPU i pobiera wszystkie rdzenie w przypadku tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="348dd-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="348dd-127">Ten element ma zastosowanie tylko do wątków wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="348dd-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="348dd-128">Aby umożliwić środowisko uruchomieniowe dystrybuowanie wątków użytkownika między wszystkimi grupami CPU, należy również włączyć [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="348dd-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="348dd-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="348dd-129">Example</span></span>

<span data-ttu-id="348dd-130">Poniższy przykład pokazuje, jak włączyć odzyskiwanie pamięci dla wielu grup procesorów.</span><span class="sxs-lookup"><span data-stu-id="348dd-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="348dd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="348dd-131">See also</span></span>

- [<span data-ttu-id="348dd-132">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="348dd-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="348dd-133">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="348dd-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="348dd-134">Wyłącz współbieżne wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="348dd-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="348dd-135">Stacja robocza i odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="348dd-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)

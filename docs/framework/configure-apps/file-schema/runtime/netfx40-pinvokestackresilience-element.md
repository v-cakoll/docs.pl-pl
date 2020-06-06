---
title: <NetFx40_PInvokeStackResilience>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116157"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="2b2a9-102">\<NetFx40_PInvokeStackResilience> Element</span><span class="sxs-lookup"><span data-stu-id="2b2a9-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="2b2a9-103">Określa, czy środowisko uruchomieniowe automatycznie naprawia nieprawidłowe deklaracje wywołania platformy w czasie wykonywania, kosztem wolniejszych przejść między zarządzanym i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="2b2a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b2a9-104">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b2a9-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2b2a9-105">Attributes and Elements</span></span>

<span data-ttu-id="2b2a9-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b2a9-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2b2a9-107">Attributes</span></span>

|<span data-ttu-id="2b2a9-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2b2a9-108">Attribute</span></span>|<span data-ttu-id="2b2a9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2b2a9-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2b2a9-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b2a9-111">Określa, czy środowisko uruchomieniowe wykrywa nieprawidłowe deklaracje wywołania platformy i automatycznie naprawia stos w czasie wykonywania na platformach 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-111">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2b2a9-112">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="2b2a9-112">enabled Attribute</span></span>

|<span data-ttu-id="2b2a9-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="2b2a9-113">Value</span></span>|<span data-ttu-id="2b2a9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2b2a9-114">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="2b2a9-115">Środowisko uruchomieniowe używa szybszej architektury organizowania międzyoperacyjnego wprowadzonej w .NET Framework 4, która nie wykrywa i nie naprawia niepoprawnych deklaracji wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-115">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="2b2a9-116">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-116">This is the default.</span></span>|
|`1`|<span data-ttu-id="2b2a9-117">Środowisko uruchomieniowe używa wolniejszych przejść, które wykrywają i rozwiązują nieprawidłowe deklaracje wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-117">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2b2a9-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2b2a9-118">Child Elements</span></span>

<span data-ttu-id="2b2a9-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b2a9-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2b2a9-120">Parent Elements</span></span>

|<span data-ttu-id="2b2a9-121">Element</span><span class="sxs-lookup"><span data-stu-id="2b2a9-121">Element</span></span>|<span data-ttu-id="2b2a9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2b2a9-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2b2a9-123">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2b2a9-124">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-124">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b2a9-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b2a9-125">Remarks</span></span>

<span data-ttu-id="2b2a9-126">Ten element umożliwia wymianę między nieprawidłowymi deklaracjami wywołania platformy w celu uzyskania odporności w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-126">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="2b2a9-127">Począwszy od .NET Framework 4, ulepszona architektura organizowania międzyoperacyjności zapewnia znaczącą poprawę wydajności dla przejść z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-127">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="2b2a9-128">We wcześniejszych wersjach .NET Framework warstwa marshaler wykryła nieprawidłowe deklaracje wywołania platformy na 32-bitowych platformach i automatycznie naprawi stos.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-128">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="2b2a9-129">Nowa architektura organizowania eliminuje ten krok.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-129">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="2b2a9-130">W związku z tym przejścia są bardzo szybkie, ale nieprawidłowa deklaracja wywołania platformy może spowodować błąd programu.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-130">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="2b2a9-131">Aby ułatwić wykrywanie niepoprawnych deklaracji podczas opracowywania, udoskonalono środowisko debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-131">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="2b2a9-132">Asystent debugowania zarządzanego [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) (MDA) powiadamia o nieprawidłowej deklaracji wywołania platformy, gdy aplikacja jest uruchomiona z dołączonym debugerem.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-132">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="2b2a9-133">Aby rozwiązać scenariusze, w których aplikacja używa składników, których nie można ponownie skompilować, i które mają nieprawidłowe deklaracje wywołania platformy, można użyć `NetFx40_PInvokeStackResilience` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-133">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="2b2a9-134">Dodanie tego elementu do pliku konfiguracji aplikacji z opcją załączanie `enabled="1"` do trybu zgodności z zachowaniem wcześniejszych wersji .NET Framework, kosztem wolniejszych przejść.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-134">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="2b2a9-135">Zestawy, które zostały skompilowane pod kątem wcześniejszych wersji .NET Framework są automatycznie zaznaczane w tym trybie zgodności i nie potrzebują tego elementu.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-135">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="2b2a9-136">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b2a9-136">Configuration File</span></span>

<span data-ttu-id="2b2a9-137">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-137">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="2b2a9-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b2a9-138">Example</span></span>

<span data-ttu-id="2b2a9-139">Poniższy przykład pokazuje, jak zrezygnować z zwiększonej elastyczności względem nieprawidłowych deklaracji wywołania platformy dla aplikacji, kosztem wolniejszych przejść między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="2b2a9-139">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2b2a9-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b2a9-140">See also</span></span>

- [<span data-ttu-id="2b2a9-141">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2b2a9-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b2a9-142">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b2a9-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b2a9-143">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="2b2a9-143">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)

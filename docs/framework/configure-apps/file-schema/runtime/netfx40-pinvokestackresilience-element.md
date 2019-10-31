---
title: <NetFx40_PInvokeStackResilience>, element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 86f50aafe0b21d5080288e09ac7118ca1e4c939a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116157"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="069c7-102">\<element > NetFx40_PInvokeStackResilience</span><span class="sxs-lookup"><span data-stu-id="069c7-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="069c7-103">Określa, czy środowisko uruchomieniowe automatycznie naprawia nieprawidłowe deklaracje wywołania platformy w czasie wykonywania, kosztem wolniejszych przejść między zarządzanym i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="069c7-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="069c7-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="069c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="069c7-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="069c7-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="069c7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<NetFx40_PInvokeStackResilience >**</span><span class="sxs-lookup"><span data-stu-id="069c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="069c7-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="069c7-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="069c7-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="069c7-108">Attributes and Elements</span></span>

<span data-ttu-id="069c7-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="069c7-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="069c7-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="069c7-110">Attributes</span></span>

|<span data-ttu-id="069c7-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="069c7-111">Attribute</span></span>|<span data-ttu-id="069c7-112">Opis</span><span class="sxs-lookup"><span data-stu-id="069c7-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="069c7-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="069c7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="069c7-114">Określa, czy środowisko uruchomieniowe wykrywa nieprawidłowe deklaracje wywołania platformy i automatycznie naprawia stos w czasie wykonywania na platformach 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="069c7-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="069c7-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="069c7-115">enabled Attribute</span></span>

|<span data-ttu-id="069c7-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="069c7-116">Value</span></span>|<span data-ttu-id="069c7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="069c7-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="069c7-118">Środowisko uruchomieniowe używa szybszej architektury organizowania międzyoperacyjnego wprowadzonej w .NET Framework 4, która nie wykrywa i nie naprawia niepoprawnych deklaracji wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="069c7-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="069c7-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="069c7-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="069c7-120">Środowisko uruchomieniowe używa wolniejszych przejść, które wykrywają i rozwiązują nieprawidłowe deklaracje wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="069c7-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="069c7-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="069c7-121">Child Elements</span></span>

<span data-ttu-id="069c7-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="069c7-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="069c7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="069c7-123">Parent Elements</span></span>

|<span data-ttu-id="069c7-124">Element</span><span class="sxs-lookup"><span data-stu-id="069c7-124">Element</span></span>|<span data-ttu-id="069c7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="069c7-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="069c7-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="069c7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="069c7-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="069c7-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="069c7-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="069c7-128">Remarks</span></span>

<span data-ttu-id="069c7-129">Ten element umożliwia wymianę między nieprawidłowymi deklaracjami wywołania platformy w celu uzyskania odporności w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="069c7-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="069c7-130">Począwszy od .NET Framework 4, ulepszona architektura organizowania międzyoperacyjności zapewnia znaczącą poprawę wydajności dla przejść z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="069c7-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="069c7-131">We wcześniejszych wersjach .NET Framework warstwa marshaler wykryła nieprawidłowe deklaracje wywołania platformy na 32-bitowych platformach i automatycznie naprawi stos.</span><span class="sxs-lookup"><span data-stu-id="069c7-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="069c7-132">Nowa architektura organizowania eliminuje ten krok.</span><span class="sxs-lookup"><span data-stu-id="069c7-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="069c7-133">W związku z tym przejścia są bardzo szybkie, ale nieprawidłowa deklaracja wywołania platformy może spowodować błąd programu.</span><span class="sxs-lookup"><span data-stu-id="069c7-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="069c7-134">Aby ułatwić wykrywanie niepoprawnych deklaracji podczas opracowywania, udoskonalono środowisko debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="069c7-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="069c7-135">Asystent debugowania zarządzanego [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) (MDA) powiadamia o nieprawidłowej deklaracji wywołania platformy, gdy aplikacja jest uruchomiona z dołączonym debugerem.</span><span class="sxs-lookup"><span data-stu-id="069c7-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="069c7-136">Aby rozwiązać scenariusze, w których aplikacja używa składników, których nie można ponownie skompilować, i które mają nieprawidłowe deklaracje wywołania platformy, można użyć elementu `NetFx40_PInvokeStackResilience`.</span><span class="sxs-lookup"><span data-stu-id="069c7-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="069c7-137">Dodanie tego elementu do pliku konfiguracji aplikacji przy użyciu funkcji `enabled="1"` powoduje przejście do trybu zgodności z zachowaniem wcześniejszych wersji .NET Framework, kosztem wolniejszych przejść.</span><span class="sxs-lookup"><span data-stu-id="069c7-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="069c7-138">Zestawy, które zostały skompilowane pod kątem wcześniejszych wersji .NET Framework są automatycznie zaznaczane w tym trybie zgodności i nie potrzebują tego elementu.</span><span class="sxs-lookup"><span data-stu-id="069c7-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="069c7-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="069c7-139">Configuration File</span></span>

<span data-ttu-id="069c7-140">Tego elementu można używać tylko w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="069c7-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="069c7-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="069c7-141">Example</span></span>

<span data-ttu-id="069c7-142">Poniższy przykład pokazuje, jak zrezygnować z zwiększonej elastyczności względem nieprawidłowych deklaracji wywołania platformy dla aplikacji, kosztem wolniejszych przejść między kodem zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="069c7-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="069c7-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="069c7-143">See also</span></span>

- [<span data-ttu-id="069c7-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="069c7-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="069c7-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="069c7-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="069c7-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="069c7-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)

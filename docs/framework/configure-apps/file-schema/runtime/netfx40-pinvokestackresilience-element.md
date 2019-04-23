---
title: <NetFx40_PInvokeStackResilience> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725bd715f6e70dff08929e58d588a3d8561d5011
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224237"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="af2e0-102">\<NetFx40_PInvokeStackResilience> Element</span><span class="sxs-lookup"><span data-stu-id="af2e0-102">\<NetFx40_PInvokeStackResilience> Element</span></span>
<span data-ttu-id="af2e0-103">Określa, czy środowisko wykonawcze automatycznie poprawki nieprawidłowa platforma wywołania deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między zarządzane, a kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="af2e0-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="af2e0-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="af2e0-104">\<configuration></span></span>  
<span data-ttu-id="af2e0-105">\<runtime></span><span class="sxs-lookup"><span data-stu-id="af2e0-105">\<runtime></span></span>  
<span data-ttu-id="af2e0-106"><NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="af2e0-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af2e0-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="af2e0-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af2e0-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="af2e0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="af2e0-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="af2e0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af2e0-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="af2e0-110">Attributes</span></span>  
  
|<span data-ttu-id="af2e0-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="af2e0-111">Attribute</span></span>|<span data-ttu-id="af2e0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="af2e0-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="af2e0-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="af2e0-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="af2e0-114">Określa, czy środowisko uruchomieniowe wykryje nieprawidłowa platforma wywołuje deklaracje i automatycznie naprawia stosu w czasie wykonywania na platformach 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="af2e0-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="af2e0-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="af2e0-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="af2e0-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="af2e0-116">Value</span></span>|<span data-ttu-id="af2e0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="af2e0-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="af2e0-118">Środowisko wykonawcze używa szybciej międzyoperacyjnego marshaling architektury wprowadzona w [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], który nie może wykryć, i wywołanie platformy niepoprawne poprawki deklaracji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="af2e0-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="af2e0-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="af2e0-120">Przejść wolniejsze używa środowiska uruchomieniowego, Wykryj i napraw nieprawidłowe platformy, które wywołuje deklaracji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af2e0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="af2e0-121">Child Elements</span></span>  
 <span data-ttu-id="af2e0-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="af2e0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af2e0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="af2e0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="af2e0-124">Element</span><span class="sxs-lookup"><span data-stu-id="af2e0-124">Element</span></span>|<span data-ttu-id="af2e0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="af2e0-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="af2e0-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af2e0-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="af2e0-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="af2e0-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af2e0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af2e0-128">Remarks</span></span>  
 <span data-ttu-id="af2e0-129">Ten element pozwala na szybsze marshaling międzyoperacyjny dla odporności na błędy czasu wykonywania względem platformy nieprawidłowe wywołanie deklaracji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="af2e0-130">Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], usprawnione współdziałania, organizowanie architektura zapewnia zwiększenie wydajności istotne dla przejścia z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="af2e0-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="af2e0-131">We wcześniejszych wersjach programu .NET Framework organizowania warstwy wykrył nieprawidłowe wywołania deklaracje na platformach 32-bitowych i platformy automatycznie naprawić stosu.</span><span class="sxs-lookup"><span data-stu-id="af2e0-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="af2e0-132">Nowa architektura organizowania eliminuje ten krok.</span><span class="sxs-lookup"><span data-stu-id="af2e0-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="af2e0-133">W wyniku przejścia są bardzo szybko, ale platforma nieprawidłowe wywołanie deklaracji może spowodować awarię programu.</span><span class="sxs-lookup"><span data-stu-id="af2e0-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="af2e0-134">Aby ułatwić wykrywanie nieprawidłowe deklaracje podczas tworzenia środowiska debugowania programu Visual Studio została ulepszona.</span><span class="sxs-lookup"><span data-stu-id="af2e0-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="af2e0-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) zarządzanego Asystenta debugowania (MDA) powiadamia o niepoprawne platformy deklaracji wywołania, gdy aplikacja jest uruchomiona w debugerze.</span><span class="sxs-lookup"><span data-stu-id="af2e0-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="af2e0-136">Dla których aplikacja używa składników, że nie można ponownie skompilować i że ma nieprawidłowe wywołanie platformy deklaracji, można użyć scenariuszy `NetFx40_PInvokeStackResilience` elementu.</span><span class="sxs-lookup"><span data-stu-id="af2e0-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="af2e0-137">Dodanie tego elementu do pliku konfiguracyjnego aplikacji za pomocą `enabled="1"` zdecyduje się w trybie zgodności z zachowaniem wcześniejszych wersjach programu .NET Framework, kosztem wolniejsze przejścia.</span><span class="sxs-lookup"><span data-stu-id="af2e0-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="af2e0-138">Zestawy, które zostały skompilowane dla wcześniejszych wersji programu .NET Framework są automatycznie wyłączony w tym trybie zgodności, a ten element nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="af2e0-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="af2e0-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="af2e0-139">Configuration File</span></span>  
 <span data-ttu-id="af2e0-140">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af2e0-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af2e0-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="af2e0-141">Example</span></span>  
 <span data-ttu-id="af2e0-142">W poniższym przykładzie pokazano, jak skorzystać z większą odporność względem niepoprawne deklaracje dla aplikacji, kosztem wolniejsze przejścia między wywołania platformy kodu zarządzanego i niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="af2e0-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af2e0-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af2e0-143">See also</span></span>

- [<span data-ttu-id="af2e0-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="af2e0-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="af2e0-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="af2e0-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="af2e0-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="af2e0-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)

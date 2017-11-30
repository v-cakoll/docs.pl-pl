---
title: "&lt;Netfx40_pinvokestackresilience —&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e77e43ed9d7520cbbcf453d067a49de3a86de3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a><span data-ttu-id="3bc73-102">&lt;Netfx40_pinvokestackresilience —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="3bc73-102">&lt;NetFx40_PInvokeStackResilience&gt; Element</span></span>
<span data-ttu-id="3bc73-103">Określa, czy środowisko uruchomieniowe platformy niepoprawne wywołanie deklaracje w czasie wykonywania, kosztem wolniejsze przejścia między poprawki zarządzane automatycznie i kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3bc73-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="3bc73-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3bc73-104">\<configuration></span></span>  
<span data-ttu-id="3bc73-105">\<Runtime ></span><span class="sxs-lookup"><span data-stu-id="3bc73-105">\<runtime></span></span>  
<span data-ttu-id="3bc73-106">< netfx40_pinvokestackresilience — ></span><span class="sxs-lookup"><span data-stu-id="3bc73-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bc73-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bc73-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bc73-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3bc73-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3bc73-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3bc73-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bc73-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3bc73-110">Attributes</span></span>  
  
|<span data-ttu-id="3bc73-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3bc73-111">Attribute</span></span>|<span data-ttu-id="3bc73-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc73-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3bc73-113">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="3bc73-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3bc73-114">Określa, czy środowisko uruchomieniowe wykryje platformy niepoprawne wywołanie deklaracje i automatycznie naprawia stosu w czasie wykonywania na platformach 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="3bc73-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3bc73-115">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="3bc73-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3bc73-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="3bc73-116">Value</span></span>|<span data-ttu-id="3bc73-117">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc73-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="3bc73-118">Środowisko wykonawcze używa interop szybsze, organizowanie architektura wprowadzone w systemie [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], które nie wykrywa i deklaracje wywołanie napraw niepoprawne platformy.</span><span class="sxs-lookup"><span data-stu-id="3bc73-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="3bc73-119">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="3bc73-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="3bc73-120">Środowisko uruchomieniowe używa wolniejszej przejścia Wykryj i napraw niepoprawne platformy wywołania deklaracji.</span><span class="sxs-lookup"><span data-stu-id="3bc73-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bc73-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3bc73-121">Child Elements</span></span>  
 <span data-ttu-id="3bc73-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="3bc73-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bc73-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3bc73-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3bc73-124">Element</span><span class="sxs-lookup"><span data-stu-id="3bc73-124">Element</span></span>|<span data-ttu-id="3bc73-125">Opis</span><span class="sxs-lookup"><span data-stu-id="3bc73-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3bc73-126">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3bc73-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3bc73-127">Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="3bc73-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bc73-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3bc73-128">Remarks</span></span>  
 <span data-ttu-id="3bc73-129">Ten element umożliwia handlu szybsze przekazywanie międzyoperacyjne dla odporności środowiska wykonawczego przed platformy niepoprawne wywołanie deklaracji.</span><span class="sxs-lookup"><span data-stu-id="3bc73-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="3bc73-130">Począwszy od [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], interop prostsze, organizowanie architektura zapewnia lepszą wydajność istotne dla przejść z kodu zarządzanego do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="3bc73-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="3bc73-131">We wcześniejszych wersjach programu .NET Framework kierowania warstwy wykryto platformy niepoprawne wywołanie deklaracje na platformach 32-bitowych i automatycznie naprawić stosu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="3bc73-132">Nowa architektura kierowania eliminuje ten krok.</span><span class="sxs-lookup"><span data-stu-id="3bc73-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="3bc73-133">W związku z tym przejścia są bardzo szybko, ale wywołanie niepoprawne platformy deklaracja może spowodować awarię programu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="3bc73-134">Aby ułatwić wykrywanie nieprawidłowe deklaracje podczas tworzenia, udoskonalono Visual Studio debugowanie.</span><span class="sxs-lookup"><span data-stu-id="3bc73-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="3bc73-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) zarządzany Asystent debugowania (MDA) powiadamia o niepoprawne platformy deklaracji wywołania, gdy aplikacja jest uruchomiona w debugerze.</span><span class="sxs-lookup"><span data-stu-id="3bc73-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="3bc73-136">Adres różnych scenariuszy, w którym aplikacja używa składników, że nie można ponownie skompilować i że ma nieprawidłowe wywołanie platformy deklaracje, można użyć `NetFx40_PInvokeStackResilience` elementu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="3bc73-137">Dodawanie tego elementu do pliku konfiguracji aplikacji z `enabled="1"` zdecyduje się w trybie zgodności z zachowaniem wcześniejszych wersji programu .NET Framework, kosztem wolniejsze przejścia.</span><span class="sxs-lookup"><span data-stu-id="3bc73-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="3bc73-138">Zestawy, które zostały skompilowane z wcześniejszych wersji programu .NET Framework są automatycznie wyłączony w tym trybie zgodności i nie wymagają tego elementu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3bc73-139">Plik konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3bc73-139">Configuration File</span></span>  
 <span data-ttu-id="3bc73-140">Ten element może być użyty tylko w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3bc73-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc73-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="3bc73-141">Example</span></span>  
 <span data-ttu-id="3bc73-142">W poniższym przykładzie przedstawiono sposób do uczestnictwa w zwiększonej odporności przed niepoprawne wywołanie platformy deklaracje dla aplikacji, kosztem wolniejsze przejścia między zarządzanych i niezarządzanych kodu.</span><span class="sxs-lookup"><span data-stu-id="3bc73-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3bc73-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bc73-143">See Also</span></span>  
 [<span data-ttu-id="3bc73-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="3bc73-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3bc73-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3bc73-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3bc73-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="3bc73-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)

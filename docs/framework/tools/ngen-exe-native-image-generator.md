---
title: Ngen.exe (Generator obrazu natywnego)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
caps.latest.revision: "57"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20c120323356171d78da35a490488f4654baece6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="e5970-102">Ngen.exe (Generator obrazu natywnego)</span><span class="sxs-lookup"><span data-stu-id="e5970-102">Ngen.exe (Native Image Generator)</span></span>
<span data-ttu-id="e5970-103">Generator obrazów natywnych (Ngen.exe) jest narzędziem, które poprawia wydajność zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="e5970-104">Program Ngen.exe tworzy obrazy natywne, które są plikami zawierającymi skompilowany kod maszynowy specyficzny dla procesora, i instaluje je w pamięci podręcznej obrazów natywnych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e5970-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="e5970-105">Środowisko uruchomieniowe może używać obrazów natywnych z tej pamięci podręcznej, zamiast używać kompilatora JIT (Just-In-Time) w celu skompilowania oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>  
  
 <span data-ttu-id="e5970-106">Zmienia się na Ngen.exe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="e5970-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>  
  
-   <span data-ttu-id="e5970-107">Program Ngen.exe obecnie kompiluje zestawy w trybie pełnego zaufania, a zasady zabezpieczeń dostępu kodu (CAS) nie są już uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="e5970-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
-   <span data-ttu-id="e5970-108">Obrazy natywne generowane przez program Ngen.exe nie mogą już być ładowane do aplikacji, które działają w trybie częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="e5970-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>  
  
 <span data-ttu-id="e5970-109">Zmiany w programie Ngen.exe wprowadzone w programie .NET Framework w wersji 2.0:</span><span class="sxs-lookup"><span data-stu-id="e5970-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>  
  
-   <span data-ttu-id="e5970-110">Instalacja zestawu powoduje także instalację jego zależności, co upraszcza składnię programu Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>  
  
-   <span data-ttu-id="e5970-111">Obrazy natywne mogą być współużytkowane w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-111">Native images can now be shared across application domains.</span></span>  
  
-   <span data-ttu-id="e5970-112">Nowa akcja, `update`, ponownie tworzy obrazy, które zostały unieważnione.</span><span class="sxs-lookup"><span data-stu-id="e5970-112">A new action, `update`, re-creates images that have been invalidated.</span></span>  
  
-   <span data-ttu-id="e5970-113">Akcje mogą być odraczane w celu wykonania przez usługę, która korzysta z czasu bezczynności komputera, aby generować i instalować obrazy.</span><span class="sxs-lookup"><span data-stu-id="e5970-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>  
  
-   <span data-ttu-id="e5970-114">Niektóre przyczyny unieważnienia obrazu zostały wyeliminowane.</span><span class="sxs-lookup"><span data-stu-id="e5970-114">Some causes of image invalidation have been eliminated.</span></span>  
  
 <span data-ttu-id="e5970-115">W systemie Windows 8, zobacz [zadań obrazu macierzystego](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span><span class="sxs-lookup"><span data-stu-id="e5970-115">On Windows 8, see [Native Image Task](http://msdn.microsoft.com/library/9b1f7590-4e0d-4737-90ef-eaf696932afb).</span></span>  
  
 <span data-ttu-id="e5970-116">Aby uzyskać dodatkowe informacje na temat używania Ngen.exe i usługę obrazu macierzystego, zobacz [usługi obrazu macierzystego][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service][Native Image Service].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-117">Składnia ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, można znaleźć w [składni starszych Generator obrazu natywnego (Ngen.exe)](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span><span class="sxs-lookup"><span data-stu-id="e5970-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](http://msdn.microsoft.com/library/5a69fc7a-103f-4afc-8ab4-606adcb46324).</span></span>  
  
 <span data-ttu-id="e5970-118">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e5970-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e5970-119">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="e5970-119">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e5970-120">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e5970-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="e5970-121">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e5970-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5970-122">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5970-122">Syntax</span></span>  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a><span data-ttu-id="e5970-123">Akcje</span><span class="sxs-lookup"><span data-stu-id="e5970-123">Actions</span></span>  
 <span data-ttu-id="e5970-124">W poniższej tabeli przedstawiono składnię każdego `action`.</span><span class="sxs-lookup"><span data-stu-id="e5970-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="e5970-125">Opis poszczególnych części `action`, zobacz [argumenty](#ArgumentTable), [poziomy priorytetu](#PriorityTable), [scenariusze](#ScenarioTable), i [Config](#ConfigTable)tabel.</span><span class="sxs-lookup"><span data-stu-id="e5970-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="e5970-126">[Opcje](#OptionTable) tabeli opisano `options` i przełączników pomocy.</span><span class="sxs-lookup"><span data-stu-id="e5970-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>  
  
|<span data-ttu-id="e5970-127">Akcja</span><span class="sxs-lookup"><span data-stu-id="e5970-127">Action</span></span>|<span data-ttu-id="e5970-128">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-128">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e5970-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="e5970-129">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="e5970-130">Generuje obrazy natywne dla zestawu i jego zależności, a także instaluje obrazy w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="e5970-131">Jeśli `/queue` jest określony, akcja jest w kolejce na usługę obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="e5970-132">Domyślnym priorytetem jest 3.</span><span class="sxs-lookup"><span data-stu-id="e5970-132">The default priority is 3.</span></span> <span data-ttu-id="e5970-133">Zobacz [poziomy priorytetu](#PriorityTable) tabeli.</span><span class="sxs-lookup"><span data-stu-id="e5970-133">See the [Priority Levels](#PriorityTable) table.</span></span>|  
|<span data-ttu-id="e5970-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="e5970-134">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="e5970-135">Usuwa obrazy natywne zestawu i jego zależności z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="e5970-136">Aby odinstalować pojedynczy obraz i jego zależności, należy użyć tych samych argumentów wiersza polecenia, które zostały użyte podczas instalacji obrazu.</span><span class="sxs-lookup"><span data-stu-id="e5970-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="e5970-137">**Uwaga:** począwszy [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Akcja `uninstall` \* nie jest już obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="e5970-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` \* is no longer supported.</span></span>|  
|<span data-ttu-id="e5970-138">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="e5970-138">`update` [`/queue`]</span></span>|<span data-ttu-id="e5970-139">Aktualizuje obrazy natywne, które stały się nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e5970-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="e5970-140">Jeśli `/queue` jest określony, aktualizacje oczekujących w kolejce na usługę obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="e5970-141">Aktualizacje są zawsze planowane z priorytetem 3, więc są uruchamiane, gdy komputer znajduje się w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|  
|<span data-ttu-id="e5970-142">`display` [`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="e5970-142">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="e5970-143">Wyświetla stan obrazów natywnych dla zestawu i jego zależności.</span><span class="sxs-lookup"><span data-stu-id="e5970-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="e5970-144">Jeśli nie zostaną dostarczone argumenty, będą wyświetlane wszystkie dane z pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|  
|<span data-ttu-id="e5970-145">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="e5970-145">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="e5970-146">—lub—</span><span class="sxs-lookup"><span data-stu-id="e5970-146">-or-</span></span><br /><br /> <span data-ttu-id="e5970-147">`eqi` [1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="e5970-147">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="e5970-148">Wykonuje umieszczone w kolejce zadania kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="e5970-149">Jeśli określono priorytet, wykonywane są zadania kompilacji z większym lub równym priorytetem.</span><span class="sxs-lookup"><span data-stu-id="e5970-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="e5970-150">Jeśli nie określono priorytetu, wykonywane są wszystkie skolejkowane zadania kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|  
|<span data-ttu-id="e5970-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="e5970-151">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="e5970-152">Wstrzymuje usługę obrazów natywnych, zezwala wstrzymanej usłudze na kontynuowanie działania lub bada stan usługi.</span><span class="sxs-lookup"><span data-stu-id="e5970-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a><span data-ttu-id="e5970-153">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e5970-153">Arguments</span></span>  
  
|<span data-ttu-id="e5970-154">Argument</span><span class="sxs-lookup"><span data-stu-id="e5970-154">Argument</span></span>|<span data-ttu-id="e5970-155">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-155">Description</span></span>|  
|--------------|-----------------|  
|`assemblyName`|<span data-ttu-id="e5970-156">Pełna nazwa wyświetlana zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-156">The full display name of the assembly.</span></span> <span data-ttu-id="e5970-157">Na przykład `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="e5970-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="e5970-158">**Uwaga:** można podać nazwę zestawu z częściowa, takich jak `myAssembly`, dla `display` i `uninstall` akcje.</span><span class="sxs-lookup"><span data-stu-id="e5970-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="e5970-159">W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.</span><span class="sxs-lookup"><span data-stu-id="e5970-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
|`assemblyPath`|<span data-ttu-id="e5970-160">Jawna ścieżka zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-160">The explicit path of the assembly.</span></span> <span data-ttu-id="e5970-161">Można określić pełną lub względną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="e5970-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="e5970-162">Jeśli użytkownik określi nazwę pliku bez ścieżki, zestaw musi znajdować się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5970-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="e5970-163">W jednym wierszu polecenia programu Ngen.exe można określić tylko jeden zestaw.</span><span class="sxs-lookup"><span data-stu-id="e5970-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a><span data-ttu-id="e5970-164">Poziomy priorytetów</span><span class="sxs-lookup"><span data-stu-id="e5970-164">Priority Levels</span></span>  
  
|<span data-ttu-id="e5970-165">Priorytet</span><span class="sxs-lookup"><span data-stu-id="e5970-165">Priority</span></span>|<span data-ttu-id="e5970-166">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-166">Description</span></span>|  
|--------------|-----------------|  
|`1`|<span data-ttu-id="e5970-167">Obrazy natywne są generowane i instalowane natychmiast, bez czekania na okres bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|  
|`2`|<span data-ttu-id="e5970-168">Obrazy natywne są generowane i instalowane bez czekania na okres bezczynności, ale po zakończeniu wszystkich akcji z priorytetem 1 (i ich zależności).</span><span class="sxs-lookup"><span data-stu-id="e5970-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|  
|`3`|<span data-ttu-id="e5970-169">Obrazy natywne są instalowane, gdy usługa obrazów natywnych wykryje, że komputer jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="e5970-170">Zobacz [obrazu macierzystego usługi][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-170">See [Native Image Service][Native Image Service].</span></span>|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a><span data-ttu-id="e5970-171">Scenariusze</span><span class="sxs-lookup"><span data-stu-id="e5970-171">Scenarios</span></span>  
  
|<span data-ttu-id="e5970-172">Scenariusz</span><span class="sxs-lookup"><span data-stu-id="e5970-172">Scenario</span></span>|<span data-ttu-id="e5970-173">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-173">Description</span></span>|  
|--------------|-----------------|  
|`/Debug`|<span data-ttu-id="e5970-174">Generuje obrazy natywne, których można używać w debugerze.</span><span class="sxs-lookup"><span data-stu-id="e5970-174">Generate native images that can be used under a debugger.</span></span>|  
|`/Profile`|<span data-ttu-id="e5970-175">Generuje obrazy natywne, które mogą być używane w profilerze.</span><span class="sxs-lookup"><span data-stu-id="e5970-175">Generate native images that can be used under a profiler.</span></span>|  
|`/NoDependencies`|<span data-ttu-id="e5970-176">Generuje minimalną liczbę obrazów natywnych wymaganą przez opcje określonego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="e5970-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a><span data-ttu-id="e5970-177">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e5970-177">Config</span></span>  
  
|<span data-ttu-id="e5970-178">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e5970-178">Configuration</span></span>|<span data-ttu-id="e5970-179">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-179">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="e5970-180">`/ExeConfig:``exePath`</span><span class="sxs-lookup"><span data-stu-id="e5970-180">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="e5970-181">Używa konfiguracji określonego zestawu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-181">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="e5970-182">Program Ngen.exe musi podjąć te same decyzje, co moduł ładowania podczas tworzenia powiązania z zależnościami.</span><span class="sxs-lookup"><span data-stu-id="e5970-182">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="e5970-183">Po załadowaniu składnika współużytkowanego w czasie wykonywania za pomocą <xref:System.Reflection.Assembly.Load%2A> metoda, pliku konfiguracji aplikacji określa zależności, które zostały załadowane dla składnika współużytkowanego — na przykład wersję zależności, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="e5970-183">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="e5970-184">`/ExeConfig` Przełącznika zapewnia wskazówki Ngen.exe, na którym będzie można załadować zależności w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5970-184">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|  
|<span data-ttu-id="e5970-185">`/AppBase:``directoryPath`</span><span class="sxs-lookup"><span data-stu-id="e5970-185">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="e5970-186">Podczas lokalizowania zależności należy użyć określonego katalogu jako podstawy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-186">When locating dependencies, use the specified directory as the application base.</span></span>|  
  
<a name="OptionTable"></a>   
## <a name="options"></a><span data-ttu-id="e5970-187">Opcje</span><span class="sxs-lookup"><span data-stu-id="e5970-187">Options</span></span>  
  
|<span data-ttu-id="e5970-188">Opcja</span><span class="sxs-lookup"><span data-stu-id="e5970-188">Option</span></span>|<span data-ttu-id="e5970-189">Opis</span><span class="sxs-lookup"><span data-stu-id="e5970-189">Description</span></span>|  
|------------|-----------------|  
|`/nologo`|<span data-ttu-id="e5970-190">Pomija wyświetlanie transparentu startowego firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e5970-190">Suppress the Microsoft startup banner display.</span></span>|  
|`/silent`|<span data-ttu-id="e5970-191">Pomija wyświetlanie komunikatów o sukcesie.</span><span class="sxs-lookup"><span data-stu-id="e5970-191">Suppress the display of success messages.</span></span>|  
|`/verbose`|<span data-ttu-id="e5970-192">Wyświetla szczegółowe informacje na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="e5970-192">Display detailed information for debugging.</span></span> <span data-ttu-id="e5970-193">**Uwaga:** ze względu na ograniczenia systemu operacyjnego, ta opcja nie powoduje wyświetlenie tylu informacji dodatkowych Windows 98 i Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="e5970-193">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|  
|<span data-ttu-id="e5970-194">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="e5970-194">`/help`, `/?`</span></span>|<span data-ttu-id="e5970-195">Wyświetla składnię polecenia i opcje dla aktualnego wydania.</span><span class="sxs-lookup"><span data-stu-id="e5970-195">Display command syntax and options for the current release.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5970-196">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5970-196">Remarks</span></span>  
 <span data-ttu-id="e5970-197">Użytkownik musi mieć uprawnienia administracyjne, aby uruchomić program Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-197">To run Ngen.exe, you must have administrative privileges.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e5970-198">Nie należy uruchamiać programu Ngen.exe dla zestawów, które nie są w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="e5970-198">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="e5970-199">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]Ngen.exe kompiluje zestawów o pełnym zaufaniu i zasady zabezpieczeń (CAS) kod dostępu nie była już oceniana.</span><span class="sxs-lookup"><span data-stu-id="e5970-199">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
 <span data-ttu-id="e5970-200">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], nie można załadować obrazów macierzystych, które są generowane z Ngen.exe do aplikacji, które są uruchomione w częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="e5970-200">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="e5970-201">Zamiast tego wywoływany jest kompilator JIT (Just-In-Time).</span><span class="sxs-lookup"><span data-stu-id="e5970-201">Instead, the just-in-time (JIT) compiler is invoked.</span></span>  
  
 <span data-ttu-id="e5970-202">Ngen.exe generuje obrazów macierzystych dla zestawu określony przez `assemblyname` argument `install` akcji i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="e5970-202">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="e5970-203">Zależności są ustalane na podstawie odwołań w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-203">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="e5970-204">Jedyny scenariusz, w którym należy zainstalować oddzielnie zależność jest podczas ładowania aplikacji za pomocą odbicia, na przykład wywołując <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-204">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5970-205">Nie używaj <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody z obrazów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="e5970-205">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="e5970-206">Obraz załadowany za pomocą tej metody nie może być używany przez inne zestawy w kontekście wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5970-206">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>  
  
 <span data-ttu-id="e5970-207">Program Ngen.exe utrzymuje licznik zależności.</span><span class="sxs-lookup"><span data-stu-id="e5970-207">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="e5970-208">Załóżmy na przykład, `MyAssembly.exe` i `YourAssembly.exe` w pamięci podręcznej obrazów natywnych są zainstalowane, a jednocześnie odwołują się do `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="e5970-208">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="e5970-209">Jeśli `MyAssembly.exe` zostanie odinstalowany, `OurDependency.dll` nie został odinstalowany.</span><span class="sxs-lookup"><span data-stu-id="e5970-209">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="e5970-210">Jest on tylko usunięte podczas `YourAssembly.exe` również zostanie odinstalowana.</span><span class="sxs-lookup"><span data-stu-id="e5970-210">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>  
  
 <span data-ttu-id="e5970-211">Jeśli jest generowany obraz natywny dla zestawu przechowywanego w globalnej pamięci podręcznej zestawów, należy określić jego nazwę wyświetlaną.</span><span class="sxs-lookup"><span data-stu-id="e5970-211">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="e5970-212">Zobacz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5970-212">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="e5970-213">Obrazy natywne, które generuje program Ngen.exe, mogą być współużytkowane w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-213">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="e5970-214">Oznacza to, że można używać programu Ngen.exe w scenariuszach aplikacji, które wymagają współużytkowania zestawów w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-214">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="e5970-215">Aby określić neutralność domeny:</span><span class="sxs-lookup"><span data-stu-id="e5970-215">To specify domain neutrality:</span></span>  
  
-   <span data-ttu-id="e5970-216">Zastosuj <xref:System.LoaderOptimizationAttribute> atrybutu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-216">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>  
  
-   <span data-ttu-id="e5970-217">Ustaw <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> właściwości po utworzeniu informacji Instalatora dla nowej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-217">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>  
  
 <span data-ttu-id="e5970-218">Zawsze należy używać kodu neutralnego względem domeny podczas ładowania jego zestawu do wielu domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-218">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="e5970-219">Jeśli obraz natywny zostanie załadowany do niewspółużytkowanej domeny aplikacji po załadowaniu do domeny współużytkowanej, nie będzie można go użyć.</span><span class="sxs-lookup"><span data-stu-id="e5970-219">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-220">Kod neutralny względem domeny nie może zostać zwolniony i wydajność może być nieco niższa, szczególnie w przypadku uzyskiwania dostępu do statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="e5970-220">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>  
  
 <span data-ttu-id="e5970-221">W tej sekcji Uwagi:</span><span class="sxs-lookup"><span data-stu-id="e5970-221">In this Remarks section:</span></span>  
  
-   [<span data-ttu-id="e5970-222">Trwa generowanie obrazów dla różnych scenariuszy</span><span class="sxs-lookup"><span data-stu-id="e5970-222">Generating images for different scenarios</span></span>](#Scenarios)  
  
-   [<span data-ttu-id="e5970-223">Określanie, kiedy należy używać obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="e5970-223">Determining when to Use native images</span></span>](#WhenToUse)  
  
    -   [<span data-ttu-id="e5970-224">Ulepszone użycia pamięci</span><span class="sxs-lookup"><span data-stu-id="e5970-224">Improved memory use</span></span>](#Memory)  
  
    -   [<span data-ttu-id="e5970-225">Szybsze uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e5970-225">Faster application startup</span></span>](#Startup)  
  
    -   [<span data-ttu-id="e5970-226">Podsumowanie planowanego sposobu użycia</span><span class="sxs-lookup"><span data-stu-id="e5970-226">Summary of usage considerations</span></span>](#UsageSummary)  
  
-   [<span data-ttu-id="e5970-227">Znaczenie adres podstawowy zestaw</span><span class="sxs-lookup"><span data-stu-id="e5970-227">Importance of assembly base addresses</span></span>](#BaseAddresses)  
  
-   [<span data-ttu-id="e5970-228">Twarde powiązania</span><span class="sxs-lookup"><span data-stu-id="e5970-228">Hard binding</span></span>](#HardBinding)  
  
    -   [<span data-ttu-id="e5970-229">Określanie wskazówki powiązanie zależność</span><span class="sxs-lookup"><span data-stu-id="e5970-229">Specifying a binding hint for a dependency</span></span>](#DependencyHint)  
  
    -   [<span data-ttu-id="e5970-230">Określanie domyślnego wskazówki powiązania dla zestawu</span><span class="sxs-lookup"><span data-stu-id="e5970-230">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)  
  
-   [<span data-ttu-id="e5970-231">Przetwarzanie z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="e5970-231">Deferred processing</span></span>](#Deferred)  
  
-   [<span data-ttu-id="e5970-232">Obrazy Native i kompilacja JIT</span><span class="sxs-lookup"><span data-stu-id="e5970-232">Native images and JIT compilation</span></span>](#JITCompilation)  
  
    -   [<span data-ttu-id="e5970-233">Nieprawidłowe obrazy</span><span class="sxs-lookup"><span data-stu-id="e5970-233">Invalid images</span></span>](#InvalidImages)  
  
-   [<span data-ttu-id="e5970-234">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="e5970-234">Troubleshooting</span></span>](#Troubleshooting)  
  
    -   [<span data-ttu-id="e5970-235">Podgląd dziennika powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="e5970-235">Assembly Binding Log Viewer</span></span>](#Fusion)  
  
    -   [<span data-ttu-id="e5970-236">JITCompilationStart zarządzany Asystent debugowania</span><span class="sxs-lookup"><span data-stu-id="e5970-236">The JITCompilationStart managed debugging assistant</span></span>](#MDA)  
  
    -   [<span data-ttu-id="e5970-237">Rezygnacja z generowanie obrazu natywnego</span><span class="sxs-lookup"><span data-stu-id="e5970-237">Opting out of native image generation</span></span>](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="e5970-238">Trwa generowanie obrazów dla różnych scenariuszy</span><span class="sxs-lookup"><span data-stu-id="e5970-238">Generating images for     different scenarios</span></span>  
 <span data-ttu-id="e5970-239">Po wygenerowaniu obrazu macierzystego dla zestawu środowiska wykonawczego automatycznie próbuje zlokalizować i użyć tego obrazu macierzystego z każdym uruchomieniu zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-239">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="e5970-240">W zależności od scenariuszy użycia można generować wiele obrazów.</span><span class="sxs-lookup"><span data-stu-id="e5970-240">Multiple images can be generated, depending on usage scenarios.</span></span>  
  
 <span data-ttu-id="e5970-241">Na przykład po uruchomieniu zestawu w debugowania lub scenariusz profilowania środowiska uruchomieniowego szuka obrazu macierzystego, który został wygenerowany z `/Debug` lub `/Profile` opcje.</span><span class="sxs-lookup"><span data-stu-id="e5970-241">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="e5970-242">Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca standardową kompilację JIT.</span><span class="sxs-lookup"><span data-stu-id="e5970-242">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="e5970-243">Jedynym sposobem debugowania obrazów natywnych jest utworzenie obrazu macierzystego z `/Debug` opcji.</span><span class="sxs-lookup"><span data-stu-id="e5970-243">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>  
  
 <span data-ttu-id="e5970-244">`uninstall` Akcji również rozpoznaje scenariuszy, więc można odinstalować wszystkie scenariusze lub tylko wybranego scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="e5970-244">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="e5970-245">Określanie, kiedy należy używać obrazów macierzystych</span><span class="sxs-lookup"><span data-stu-id="e5970-245">Determining when to Use native images</span></span>  
 <span data-ttu-id="e5970-246">Obrazy natywne zapewniają poprawę wydajności w dwóch obszarach: ulepszone wykorzystanie pamięci i skrócenie czasu uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e5970-246">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-247">Wydajność obrazów natywnych zależy od kilku czynników, które utrudniają analizę, takich jak wzorce dostępu kodu i danych, liczba wywołań, jakie miały miejsce między granicami modułów, a także liczba zależności, które zostały już załadowane przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="e5970-247">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="e5970-248">Jedynym sposobem ustalenia, czy obrazy natywne przynoszą korzyść aplikacji, są dokładne pomiary wydajności w kluczowych scenariuszach wdrażania.</span><span class="sxs-lookup"><span data-stu-id="e5970-248">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a><span data-ttu-id="e5970-249">Ulepszone użycia pamięci</span><span class="sxs-lookup"><span data-stu-id="e5970-249">Improved memory use</span></span>  
 <span data-ttu-id="e5970-250">Obrazy natywne mogą znacznie poprawić wykorzystanie pamięci, gdy kod jest współużytkowany w różnych procesach.</span><span class="sxs-lookup"><span data-stu-id="e5970-250">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="e5970-251">Obrazy natywne są plikami środowiska Windows PE, więc pojedyncza kopia pliku dll może być współużytkowana przez wiele procesów, natomiast kod natywny wytworzony przez kompilator JIT jest przechowywany w pamięci prywatnej i nie może być współużytkowany.</span><span class="sxs-lookup"><span data-stu-id="e5970-251">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>  
  
 <span data-ttu-id="e5970-252">Aplikacje uruchamiane w ramach usług terminalowych również mogą korzystać z udostępnionych stron kodowych.</span><span class="sxs-lookup"><span data-stu-id="e5970-252">Applications that are run under terminal services can also benefit from shared code pages.</span></span>  
  
 <span data-ttu-id="e5970-253">Ponadto rezygnacja z ładowania kompilatora JIT umożliwia oszczędzenie określonej ilości pamięci dla każdego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-253">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a><span data-ttu-id="e5970-254">Szybsze uruchamianie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e5970-254">Faster application startup</span></span>  
 <span data-ttu-id="e5970-255">Wstępna kompilacja zestawów przy użyciu programu Ngen.exe może poprawić czas uruchamiania niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-255">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="e5970-256">Ogólnie rzecz biorąc, współużytkowanie zestawów składnika przez aplikacje przynosi zyski, ponieważ po uruchomieniu pierwszej aplikacji składniki współużytkowane są już załadowane dla kolejnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-256">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="e5970-257">Podczas zimnego uruchamiania nie występują takie zyski z wykorzystania obrazów natywnych, ponieważ każdy zestaw aplikacji musi zostać załadowany z dysku twardego, przez co czas dostępu do dysku twardego przeważa zyski ze współużytkowania.</span><span class="sxs-lookup"><span data-stu-id="e5970-257">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>  
  
 <span data-ttu-id="e5970-258">Trwałe powiązania mogą wpływać na czas uruchamiania, ponieważ wszystkie obrazy trwale powiązane z głównym zestawem aplikacji muszą zostać załadowane w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="e5970-258">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-259">Przed [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], składniki o silnych nazwach, współdzielonych należy umieścić w globalnej pamięci podręcznej zestawów, ponieważ moduł ładujący przeprowadza weryfikację dodatkowe zestawy o silnych nazwach, które nie w pamięci podręcznej GAC, efektywnie eliminuje poprawy w czasie uruchamiania uzyskane przy użyciu obrazów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="e5970-259">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="e5970-260">Funkcje optymalizacji, które zostały wprowadzone w systemie [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] usunięte dodatkowej weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-260">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a><span data-ttu-id="e5970-261">Podsumowanie planowanego sposobu użycia</span><span class="sxs-lookup"><span data-stu-id="e5970-261">Summary of usage considerations</span></span>  
 <span data-ttu-id="e5970-262">Następujące zagadnienia ogólne i dotyczące aplikacji mogą pomóc zadecydować, czy warto używać obrazów natywnych dla swojej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="e5970-262">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>  
  
-   <span data-ttu-id="e5970-263">Obrazy natywne są ładowane szybciej niż pliki MSIL, ponieważ eliminują potrzebę wykonywania wielu działań podczas uruchamiania, takich jak kompilacja JIT i weryfikacja bezpieczeństwa typów.</span><span class="sxs-lookup"><span data-stu-id="e5970-263">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>  
  
-   <span data-ttu-id="e5970-264">Obrazy natywne wymagają mniejszego początkowego zestawu roboczego, ponieważ nie ma potrzeby wczytywania kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="e5970-264">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>  
  
-   <span data-ttu-id="e5970-265">Obrazy natywne umożliwiają współużytkowanie kodu przez różne procesy.</span><span class="sxs-lookup"><span data-stu-id="e5970-265">Native images enable code sharing between processes.</span></span>  
  
-   <span data-ttu-id="e5970-266">Obrazy natywne wymagają więcej miejsca na dysku twardym niż zestawy MSIL, a ich generowanie może długo trwać.</span><span class="sxs-lookup"><span data-stu-id="e5970-266">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>  
  
-   <span data-ttu-id="e5970-267">Obrazy natywne muszą być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e5970-267">Native images must be maintained.</span></span>  
  
    -   <span data-ttu-id="e5970-268">Obrazy muszą być generowane ponownie, gdy oryginalny zestaw lub jedna z jego zależności jest zmieniana.</span><span class="sxs-lookup"><span data-stu-id="e5970-268">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>  
  
    -   <span data-ttu-id="e5970-269">Pojedynczy zestaw może wymagać wielu obrazów natywnych, aby można było używać go w różnych aplikacjach lub scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="e5970-269">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="e5970-270">Na przykład informacje o konfiguracji w dwóch aplikacjach mogą powodować różne decyzje dotyczące powiązań dla tego samego zestawu zależnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-270">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>  
  
    -   <span data-ttu-id="e5970-271">Obrazy natywne muszą być generowane przez administratora, czyli za pomocą konta systemu Windows z grupy Administratorzy.</span><span class="sxs-lookup"><span data-stu-id="e5970-271">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>  
  
 <span data-ttu-id="e5970-272">Podczas określania, czy obrazy natywne mogą spowodować poprawę wydajności, oprócz tych ogólnych zagadnień, należy też rozważyć naturę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-272">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>  
  
-   <span data-ttu-id="e5970-273">Jeśli aplikacja działa w środowisku, w którym jest używanych wiele współużytkowanych składników, obrazy natywne umożliwią współużytkowanie składników przez wiele procesów.</span><span class="sxs-lookup"><span data-stu-id="e5970-273">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>  
  
-   <span data-ttu-id="e5970-274">Jeśli aplikacja używa wielu domen aplikacji, obrazy natywne umożliwią współużytkowanie stron kodu w różnych domenach.</span><span class="sxs-lookup"><span data-stu-id="e5970-274">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e5970-275">W wersjach 1.0 i 1.1 programu .NET Framework obrazów natywnych nie można współużytkować w różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-275">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="e5970-276">Inaczej jest w wersji 2.0 i późniejszych.</span><span class="sxs-lookup"><span data-stu-id="e5970-276">This is not the case in version 2.0 or later.</span></span>  
  
-   <span data-ttu-id="e5970-277">Jeśli aplikacja będzie uruchamiana na serwerze terminali, obrazy natywne umożliwią współużytkowanie stron kodu.</span><span class="sxs-lookup"><span data-stu-id="e5970-277">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>  
  
-   <span data-ttu-id="e5970-278">Zazwyczaj korzystne jest kompilowanie do obrazów natywnych dużych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-278">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="e5970-279">Taka kompilacja małych aplikacje zazwyczaj nie przynosi korzyści.</span><span class="sxs-lookup"><span data-stu-id="e5970-279">Small applications generally do not benefit.</span></span>  
  
-   <span data-ttu-id="e5970-280">W przypadku aplikacji działających przez długi czas kompilacja JIT w czasie wykonywania sprawdza się nieco lepiej niż obrazy natywne.</span><span class="sxs-lookup"><span data-stu-id="e5970-280">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="e5970-281">(Trwałe powiązania mogą do pewnego stopnia złagodzić różnicę w wydajności).</span><span class="sxs-lookup"><span data-stu-id="e5970-281">(Hard binding can mitigate this performance difference to some degree.)</span></span>  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="e5970-282">Znaczenie adres podstawowy zestaw</span><span class="sxs-lookup"><span data-stu-id="e5970-282">Importance of assembly base addresses</span></span>  
 <span data-ttu-id="e5970-283">Obrazy natywne są plikami środowiska Windows PE, więc dotyczą ich te same problemy zmiany podstawy, co innych plików wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-283">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="e5970-284">Spadek wydajności przy relokacji jest jeszcze bardziej widoczny, jeśli są stosowane powiązania trwałe.</span><span class="sxs-lookup"><span data-stu-id="e5970-284">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>  
  
 <span data-ttu-id="e5970-285">Aby ustawić adres podstawowy dla obrazu natywnego, należy użyć odpowiedniej opcji kompilatora, aby ustawić adres podstawowy dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-285">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="e5970-286">Program Ngen.exe używa tego adresu podstawowego dla obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-286">Ngen.exe uses this base address for the native image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-287">Obrazy natywne są większe niż zestawy zarządzane, na podstawie których zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="e5970-287">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="e5970-288">Adresy podstawowe muszą być obliczane tak, aby zezwalały na te większe rozmiary.</span><span class="sxs-lookup"><span data-stu-id="e5970-288">Base addresses must be calculated to allow for these larger sizes.</span></span>  
  
 <span data-ttu-id="e5970-289">Można użyć narzędzia, takiego jak dumpbin.exe, aby wyświetlić preferowany adres podstawowy obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-289">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a><span data-ttu-id="e5970-290">Twarde powiązania</span><span class="sxs-lookup"><span data-stu-id="e5970-290">Hard binding</span></span>  
 <span data-ttu-id="e5970-291">Trwałe powiązania zwiększają przepustowość i zmniejszają rozmiar zestawu roboczego dla obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-291">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="e5970-292">Wadą trwałych powiązań jest fakt, że wszystkie obrazy, które są trwale powiązane z zestawem, muszą być ładowane razem z zestawem.</span><span class="sxs-lookup"><span data-stu-id="e5970-292">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="e5970-293">Może to znacznie zwiększyć czas uruchamiania dużych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-293">This can significantly increase startup time for a large application.</span></span>  
  
 <span data-ttu-id="e5970-294">Trwałe powiązanie jest odpowiednie dla zależności, które są ładowane we wszystkich krytycznych pod względem wydajności scenariuszach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-294">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="e5970-295">Podobnie jak w przypadku każdego aspektu wykorzystania obrazu natywnego, staranne wykonywanie pomiarów wydajności jest jedynym sposobem ustalenia, czy trwałe powiązanie zwiększa wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-295">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>  
  
 <span data-ttu-id="e5970-296"><xref:System.Runtime.CompilerServices.DependencyAttribute> i <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> atrybutów umożliwiają zapewnienie wskazówek twardych powiązanie Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-296">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-297">Te atrybuty są wskazówkami dla programu Ngen.exe, a nie poleceniami.</span><span class="sxs-lookup"><span data-stu-id="e5970-297">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="e5970-298">Użycie ich nie gwarantuje uzyskania trwałego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e5970-298">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="e5970-299">Znaczenie tych atrybutów może się zmieniać w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="e5970-299">The meaning of these attributes may change in future releases.</span></span>  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="e5970-300">Określanie wskazówki powiązanie zależność</span><span class="sxs-lookup"><span data-stu-id="e5970-300">Specifying a binding hint for a dependency</span></span>  
 <span data-ttu-id="e5970-301">Zastosuj <xref:System.Runtime.CompilerServices.DependencyAttribute> do zestawu, które wskazują prawdopodobieństwo określona zależność zostanie załadowany.</span><span class="sxs-lookup"><span data-stu-id="e5970-301">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="e5970-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>Wskazuje, że powiązanie twardym jest odpowiednie, <xref:System.Runtime.CompilerServices.LoadHint.Default> wskazuje, że powinny być używane domyślne dla zależności, i <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> wskazuje twardych powiązania nie jest odpowiedni.</span><span class="sxs-lookup"><span data-stu-id="e5970-302"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>  
  
 <span data-ttu-id="e5970-303">Poniższy kod pokazuje atrybuty dla zestawu mającego dwie zależności.</span><span class="sxs-lookup"><span data-stu-id="e5970-303">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="e5970-304">Pierwsza zależność (Assembly1) jest odpowiednim kandydatem dla trwałego powiązania, ale druga zależność (Assembly2) nie jest.</span><span class="sxs-lookup"><span data-stu-id="e5970-304">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>  
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>  
```  
  
```csharp  
using System.Runtime.CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]  
```  
  
```cpp  
using namespace System::Runtime::CompilerServices;  
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];  
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];  
```  
  
 <span data-ttu-id="e5970-305">Nazwa zestawu nie zawiera rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="e5970-305">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="e5970-306">Można używać nazw wyświetlanych.</span><span class="sxs-lookup"><span data-stu-id="e5970-306">Display names can be used.</span></span>  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="e5970-307">Określanie domyślnego wskazówki powiązania dla zestawu</span><span class="sxs-lookup"><span data-stu-id="e5970-307">Specifying a default binding hint for an assembly</span></span>  
 <span data-ttu-id="e5970-308">Domyślne wskazówki powiązania potrzebne są tylko zestawom, które będą stosowane natychmiastowo i często przez dowolną aplikację, która jest od nich zależna.</span><span class="sxs-lookup"><span data-stu-id="e5970-308">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="e5970-309">Zastosuj <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> z <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> do tych zestawów, aby określić, że używane powiązanie twardych.</span><span class="sxs-lookup"><span data-stu-id="e5970-309">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-310">To nie ma powodu do zastosowania <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do zestawów .dll, które nie należą do tej kategorii, ponieważ stosowanie atrybutu o wartości innej niż <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> ma ten sam efekt co w ogóle nie stosowanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e5970-310">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>  
  
 <span data-ttu-id="e5970-311">Firma Microsoft używa <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> do określenia, czy powiązanie twardym jest ustawieniem domyślnym dla bardzo małą liczbę zestawów w programie .NET Framework, takie jak mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="e5970-311">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a><span data-ttu-id="e5970-312">Przetwarzanie z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="e5970-312">Deferred processing</span></span>  
 <span data-ttu-id="e5970-313">Generowanie obrazów natywnych dla bardzo dużych aplikacji może zająć znaczną ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="e5970-313">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="e5970-314">Podobnie zmiany składnika współużytkowanego lub zmiany w ustawieniach komputera mogą wymagać aktualizacji wielu obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-314">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="e5970-315">`install` i `update` akcji ma `/queue` opcję kolejkuje operację dla odroczonego wykonania przez usługę obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-315">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="e5970-316">Ponadto ma Ngen.exe `queue` i `executeQueuedItems` działania, które zapewniają pewną kontrolę nad usługi.</span><span class="sxs-lookup"><span data-stu-id="e5970-316">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="e5970-317">Aby uzyskać więcej informacji, zobacz [usługi obrazu macierzystego][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-317">For more information, see [Native Image Service][Native Image Service].</span></span>  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="e5970-318">Obrazy Native i kompilacja JIT</span><span class="sxs-lookup"><span data-stu-id="e5970-318">Native images and JIT compilation</span></span>  
 <span data-ttu-id="e5970-319">Jeśli program Ngen.exe napotka w zestawie jakiekolwiek metody, których nie może wygenerować, wyklucza je z obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-319">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="e5970-320">Gdy środowisko uruchomieniowe wykonuje zestaw, przywraca kompilację JIT dla metod, które nie zostały uwzględnione w obrazie natywnym.</span><span class="sxs-lookup"><span data-stu-id="e5970-320">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>  
  
 <span data-ttu-id="e5970-321">Ponadto obrazy natywne nie są używane, jeśli zestaw został uaktualniony lub jeśli obraz został unieważniony z jakiegokolwiek powodu.</span><span class="sxs-lookup"><span data-stu-id="e5970-321">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a><span data-ttu-id="e5970-322">Nieprawidłowe obrazy</span><span class="sxs-lookup"><span data-stu-id="e5970-322">Invalid images</span></span>  
 <span data-ttu-id="e5970-323">Użycie programu Ngen.exe w celu utworzenia obrazu natywnego zestawu powoduje, że dane wyjściowe zależą od opcji wiersza polecenia, które można określić, i niektórych ustawień na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5970-323">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="e5970-324">Są to m.in. następujące ustawienia:</span><span class="sxs-lookup"><span data-stu-id="e5970-324">These settings include the following:</span></span>  
  
-   <span data-ttu-id="e5970-325">Wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5970-325">The version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="e5970-326">Wersja systemu operacyjnego, jeśli zmiana dotyczy z rodziny Windows 9 x z rodziny Windows NT.</span><span class="sxs-lookup"><span data-stu-id="e5970-326">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
-   <span data-ttu-id="e5970-327">Dokładna tożsamość zestawu (ponowna kompilacja zmienia tożsamość).</span><span class="sxs-lookup"><span data-stu-id="e5970-327">The exact identity of the assembly (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="e5970-328">Dokładna tożsamość wszystkich zestawów, do których odwołuje się zestaw (ponowna kompilacja zmienia tożsamość).</span><span class="sxs-lookup"><span data-stu-id="e5970-328">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="e5970-329">Czynniki związane z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="e5970-329">Security factors.</span></span>  
  
 <span data-ttu-id="e5970-330">Program Ngen.exe rejestruje te informacje podczas generowania obrazu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e5970-330">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="e5970-331">Podczas wykonywania zestawu środowisko uruchomieniowe poszukuje obrazu natywnego wygenerowanego z użyciem opcji i ustawień, które odpowiadają bieżącemu środowisku komputera.</span><span class="sxs-lookup"><span data-stu-id="e5970-331">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="e5970-332">Jeśli nie można odnaleźć pasującego obrazu natywnego, środowisko uruchomieniowe przywraca kompilację JIT zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-332">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="e5970-333">Następujące zmiany w ustawieniach komputera i środowiska powodują, że obrazy natywne stają się nieprawidłowe:</span><span class="sxs-lookup"><span data-stu-id="e5970-333">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>  
  
-   <span data-ttu-id="e5970-334">Wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5970-334">The version of the .NET Framework.</span></span>  
  
     <span data-ttu-id="e5970-335">Jeśli zastosowano aktualizację programu .NET Framework, wszystkie obrazy natywne utworzone przy użyciu programu Ngen.exe stają się nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e5970-335">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="e5970-336">Z tego powodu wykonania wszystkich aktualizacji platformy .NET `Ngen Update` polecenie, aby upewnić się, że wszystkie obrazów macierzystych są generowane.</span><span class="sxs-lookup"><span data-stu-id="e5970-336">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="e5970-337">Program .NET Framework automatycznie tworzy nowe obrazy natywne dla bibliotek programu .NET Framework, które instaluje.</span><span class="sxs-lookup"><span data-stu-id="e5970-337">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>  
  
-   <span data-ttu-id="e5970-338">Wersja systemu operacyjnego, jeśli zmiana dotyczy z rodziny Windows 9 x z rodziny Windows NT.</span><span class="sxs-lookup"><span data-stu-id="e5970-338">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
     <span data-ttu-id="e5970-339">Na przykład jeśli wersja systemu operacyjnego na komputerze z systemem zmieni się z systemu Windows 98 do systemu Windows XP, wszystkich obrazów macierzystych przechowywanych w pamięci podręcznej obrazów natywnych staną się nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e5970-339">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="e5970-340">Jednak w przypadku systemu operacyjnego zmiany z systemu Windows 2000 do systemu Windows XP, obrazy nie są unieważniona.</span><span class="sxs-lookup"><span data-stu-id="e5970-340">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>  
  
-   <span data-ttu-id="e5970-341">Dokładna tożsamość zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-341">The exact identity of the assembly.</span></span>  
  
     <span data-ttu-id="e5970-342">Jeśli zestaw zostanie ponownie skompilowany, obraz natywny odpowiadający zestawowi staje się nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e5970-342">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>  
  
-   <span data-ttu-id="e5970-343">Dokładna tożsamość jakichkolwiek zestawów, do których odwołuje się zestaw.</span><span class="sxs-lookup"><span data-stu-id="e5970-343">The exact identity of any assemblies the assembly references.</span></span>  
  
     <span data-ttu-id="e5970-344">Jeżeli zestaw zarządzany zostanie zaktualizowany, wszystkie obrazy natywne zależne bezpośrednio lub pośrednio od tego zestawu stają się nieprawidłowe i muszą zostać wygenerowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="e5970-344">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="e5970-345">Obejmuje to zarówno zwykłe odwołania, jak i trwale powiązane zależności.</span><span class="sxs-lookup"><span data-stu-id="e5970-345">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="e5970-346">Zawsze, gdy aktualizacja oprogramowania nie zostanie zastosowana, program instalacyjny powinien zostać wykonany `Ngen Update` polecenie, aby upewnić się, że wszystkie zależne obrazów macierzystych są generowane.</span><span class="sxs-lookup"><span data-stu-id="e5970-346">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>  
  
-   <span data-ttu-id="e5970-347">Czynniki związane z zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="e5970-347">Security factors.</span></span>  
  
     <span data-ttu-id="e5970-348">Zmiana zasad zabezpieczeń komputera ograniczająca uprawnienia udzielone uprzednio zestawowi może spowodować, że poprzednio skompilowane obrazy natywne dla tego zestawu staną się nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e5970-348">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>  
  
     <span data-ttu-id="e5970-349">Aby uzyskać szczegółowe informacje dotyczące sposobu środowisko uruchomieniowe języka wspólnego zarządza zabezpieczenia dostępu kodu i sposobu korzystania z uprawnień, zobacz [zabezpieczenia dostępu kodu](../../../docs/framework/misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="e5970-349">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="e5970-350">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="e5970-350">Troubleshooting</span></span>  
 <span data-ttu-id="e5970-351">Następujące tematy dotyczące rozwiązywania problemów umożliwiają wyświetlanie które obrazów macierzystych są używane i nie można użyć przez aplikację, do określania, kiedy przy użyciu kompilatora JIT rozpoczyna się skompilować metody i pokazuje, jak rezygnacji z tworzenia obrazu macierzystego określona metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-351">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="e5970-352">podgląd dziennika powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="e5970-352">Assembly Binding Log Viewer</span></span>  
 <span data-ttu-id="e5970-353">Aby upewnić się, że obrazów macierzystych są używane przez aplikację, można użyć [Fuslogvw.exe (Podgląd dziennika powiązań zestawów)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="e5970-353">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="e5970-354">Wybierz **obrazów macierzystych** w **kategorie dziennika** pola w oknie Podgląd dziennika powiązań.</span><span class="sxs-lookup"><span data-stu-id="e5970-354">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="e5970-355">Program Fuslogvw.exe dostarcza informacje o tym, dlaczego obraz natywny został odrzucony.</span><span class="sxs-lookup"><span data-stu-id="e5970-355">Fuslogvw.exe provides information about why a native image was rejected.</span></span>  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="e5970-356">JITCompilationStart zarządzany Asystent debugowania</span><span class="sxs-lookup"><span data-stu-id="e5970-356">The JITCompilationStart managed debugging assistant</span></span>  
 <span data-ttu-id="e5970-357">Można użyć [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) zarządzany Asystent debugowania (MDA), aby określić podczas uruchamiania kompilatora JIT skompilować funkcję.</span><span class="sxs-lookup"><span data-stu-id="e5970-357">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="e5970-358">Rezygnacja z generowanie obrazu natywnego</span><span class="sxs-lookup"><span data-stu-id="e5970-358">Opting out of native image generation</span></span>  
 <span data-ttu-id="e5970-359">W niektórych przypadkach NGen.exe mogą mieć trudności generowania, który obrazu macierzystego dla określonej metody, lub mogą preferować, że metoda być skompilowana w trybie JIT zamiast skompilowanych do obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-359">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="e5970-360">W takim przypadku można użyć `System.Runtime.BypassNGenAttribute` atrybutu, aby zapobiec NGen.exe generowanie obrazu macierzystego dla określonej metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-360">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="e5970-361">Atrybut należy zastosować indywidualnie do każdej metody kodu, których nie chcesz dołączyć do obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-361">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="e5970-362">NGen.exe rozpoznaje atrybutu i nie generuje kod w obrazu macierzystego dla odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-362">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>  
  
 <span data-ttu-id="e5970-363">Zauważ, że `BypassNGenAttribute` nie jest zdefiniowany jako typ w bibliotece klas programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5970-363">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="e5970-364">Aby można było korzystać z atrybutu w kodzie, należy najpierw zdefiniować ją w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e5970-364">In order to consume the attribute in your code, you must first define it as follows:</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 <span data-ttu-id="e5970-365">Można użyć atrybutu na podstawie-method.</span><span class="sxs-lookup"><span data-stu-id="e5970-365">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="e5970-366">Poniższy przykład powoduje, że Generator obrazu natywnego czy nie powinna generować obrazu macierzystego dla `ExampleClass.ToJITCompile` metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-366">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a><span data-ttu-id="e5970-367">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e5970-367">Examples</span></span>  
 <span data-ttu-id="e5970-368">Polecenie generuje obrazu macierzystego dla `ClientApp.exe`, znajduje się w bieżącym katalogu i instaluje obraz w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-368">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="e5970-369">Jeśli istnieje plik konfiguracji zestawu, program Ngen.exe go użyje.</span><span class="sxs-lookup"><span data-stu-id="e5970-369">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="e5970-370">Ponadto obrazów macierzystych są generowane dla plików dll żadnych `ClientApp.exe` odwołania.</span><span class="sxs-lookup"><span data-stu-id="e5970-370">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>  
  
```  
ngen install ClientApp.exe  
```  
  
 <span data-ttu-id="e5970-371">Obraz instalowany za pomocą programu Ngen.exe jest również nazywany elementem głównym.</span><span class="sxs-lookup"><span data-stu-id="e5970-371">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="e5970-372">Elementem głównym może być aplikacja albo składnik współużytkowany.</span><span class="sxs-lookup"><span data-stu-id="e5970-372">A root can be an application or a shared component.</span></span>  
  
 <span data-ttu-id="e5970-373">Polecenie generuje obrazu macierzystego dla `MyAssembly.exe` z określoną ścieżką.</span><span class="sxs-lookup"><span data-stu-id="e5970-373">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 <span data-ttu-id="e5970-374">Podczas lokalizowania zestawów i ich zależności program Ngen.exe używa tej samej logiki badania, co środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e5970-374">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="e5970-375">Domyślnie katalog, który zawiera `ClientApp.exe` jest używany jako podstawowego katalogu aplikacji, a wszystkie badania zestawu rozpoczyna się w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5970-375">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="e5970-376">To zachowanie można przesłonić przy użyciu `/AppBase` opcji.</span><span class="sxs-lookup"><span data-stu-id="e5970-376">You can override this behavior by using the `/AppBase` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-377">Zachowanie to różni się od zachowania programu Ngen.exe w wersjach 1.0 i 1.1 programu .NET Framework, gdzie podstawa aplikacji znajduje się w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e5970-377">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>  
  
 <span data-ttu-id="e5970-378">Zestaw może mieć zależności bez odwołania, na przykład jeśli ładuje plik dll za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e5970-378">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e5970-379">Można utworzyć obrazu macierzystego pliku dll przy użyciu informacji o konfiguracji dla zestawu aplikacji `/ExeConfig` opcji.</span><span class="sxs-lookup"><span data-stu-id="e5970-379">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="e5970-380">Polecenie generuje obrazu macierzystego dla `MyLib.dll,` przy użyciu informacji konfiguracyjnych z `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="e5970-380">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="e5970-381">Zestawy instalowane w ten sposób nie są usuwane, gdy jest usuwana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="e5970-381">Assemblies installed in this way are not removed when the application is removed.</span></span>  
  
 <span data-ttu-id="e5970-382">Aby odinstalować zależność, należy użyć tych samych opcji wiersza polecenia, które zostały użyte podczas jej instalowania.</span><span class="sxs-lookup"><span data-stu-id="e5970-382">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="e5970-383">Polecenie odinstalowuje `MyLib.dll` z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="e5970-383">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="e5970-384">Aby utworzyć obraz natywny dla zestawu w globalnej pamięci podręcznej zestawów, należy użyć nazwy wyświetlanej zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-384">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="e5970-385">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e5970-385">For example:</span></span>  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 <span data-ttu-id="e5970-386">Program NGen.exe generuje oddzielny zestaw obrazów dla każdego instalowanego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="e5970-386">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="e5970-387">Na przykład poniższe polecenia instalują kompletny zestaw obrazów natywnych dla normalnych operacji, drugi kompletny zestaw na potrzeby debugowania i trzeci na potrzeby profilowania:</span><span class="sxs-lookup"><span data-stu-id="e5970-387">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="e5970-388">Wyświetlanie pamięci podręcznej obrazów natywnych</span><span class="sxs-lookup"><span data-stu-id="e5970-388">Displaying the Native Image Cache</span></span>  
 <span data-ttu-id="e5970-389">Obrazy natywne zainstalowane w pamięci podręcznej można wyświetlić przy użyciu programu Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-389">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="e5970-390">Poniższe polecenie wyświetla wszystkie obrazy natywne znajdujące się w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="e5970-390">The following command displays all native images in the native image cache.</span></span>  
  
```  
ngen display  
```  
  
 <span data-ttu-id="e5970-391">`display` Akcji zawiera wszystkie zestawy główne najpierw następuje lista wszystkich obrazów macierzystych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5970-391">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>  
  
 <span data-ttu-id="e5970-392">Prosta nazwa zestawu służy do wyświetlania informacji dotyczących tylko tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5970-392">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="e5970-393">Następujące polecenie wyświetla wszystkich obrazów natywnych w pamięci podręcznej obrazów natywnych zgodnych z częściowa nazwą `MyAssembly`, ich zależności i wszystkich katalogów głównych, które zależy od `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="e5970-393">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>  
  
```  
ngen display MyAssembly  
```  
  
 <span data-ttu-id="e5970-394">Wiedząc, jakie elementy główne są zależne od zestaw udostępnionego składnika jest przydatny do skalowania wpływ `update` akcji po uaktualnieniu składnika współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="e5970-394">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>  
  
 <span data-ttu-id="e5970-395">Aby określić rozszerzenie pliku zestawu, należy określić ścieżkę lub wykonać program Ngen.exe z katalogu zawierającego zestaw:</span><span class="sxs-lookup"><span data-stu-id="e5970-395">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 <span data-ttu-id="e5970-396">Następujące polecenie wyświetla wszystkich obrazów natywnych w pamięci podręcznej obrazów natywnych o nazwie `MyAssembly` i w wersji 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="e5970-396">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a><span data-ttu-id="e5970-397">Aktualizacja obrazów</span><span class="sxs-lookup"><span data-stu-id="e5970-397">Updating Images</span></span>  
 <span data-ttu-id="e5970-398">Obrazy są zazwyczaj aktualizowane po uaktualnieniu składnika współużytkowanego.</span><span class="sxs-lookup"><span data-stu-id="e5970-398">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="e5970-399">Aby zaktualizować wszystkich obrazów macierzystych, które zostały zmienione lub którego zależności zostały zmienione, należy użyć `update` akcji bez argumentów.</span><span class="sxs-lookup"><span data-stu-id="e5970-399">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>  
  
```  
ngen update  
```  
  
 <span data-ttu-id="e5970-400">Aktualizacja wszystkich obrazów może być długotrwałym procesem.</span><span class="sxs-lookup"><span data-stu-id="e5970-400">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="e5970-401">Można dodać do kolejki aktualizacje do wykonywania przez usługę obrazu macierzystego przy użyciu `/queue` opcji.</span><span class="sxs-lookup"><span data-stu-id="e5970-401">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="e5970-402">Aby uzyskać więcej informacji na temat `/queue` priorytetów opcji i instalacji, zobacz [usługi obrazu macierzystego][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-402">For more information on the `/queue` option and installation priorities, see [Native Image Service][Native Image Service].</span></span>  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a><span data-ttu-id="e5970-403">Odinstalowywanie obrazów</span><span class="sxs-lookup"><span data-stu-id="e5970-403">Uninstalling Images</span></span>  
 <span data-ttu-id="e5970-404">Program Ngen.exe utrzymuje listę zależności, aby składniki współużytkowane były usuwane tylko wtedy, gdy wszystkie zestawy, które od nich zależą, zostały usunięte.</span><span class="sxs-lookup"><span data-stu-id="e5970-404">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="e5970-405">Ponadto współużytkowany składnik nie zostanie usunięty, jeśli został zainstalowany jako element główny.</span><span class="sxs-lookup"><span data-stu-id="e5970-405">In addition, a shared component is not removed if it has been installed as a root.</span></span>  
  
 <span data-ttu-id="e5970-406">Polecenie Odinstalowuje wszystkie scenariusze dla głównego `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="e5970-406">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp  
```  
  
 <span data-ttu-id="e5970-407">`uninstall` Akcja może zostać użyta do usunięcia konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="e5970-407">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="e5970-408">Poniższe polecenie powoduje odinstalowanie wszystkich scenariuszach debugowania dla `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="e5970-408">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  <span data-ttu-id="e5970-409">Odinstalowywanie `/debug` scenariuszy nie powoduje odinstalowania scenariusz obejmuje `/profile` i`/debug.`</span><span class="sxs-lookup"><span data-stu-id="e5970-409">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>  
  
 <span data-ttu-id="e5970-410">Polecenie Odinstalowuje wszystkie scenariusze dla określonej wersji `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="e5970-410">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 <span data-ttu-id="e5970-411">Następujące polecenia Odinstaluj wszystkie scenariusze `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` lub po prostu scenariusza debugowania dla tego zestawu:</span><span class="sxs-lookup"><span data-stu-id="e5970-411">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 <span data-ttu-id="e5970-412">Jak `install` akcja, podając rozszerzenie wymaga albo wykonywania Ngen.exe od katalogu zawierającego zestaw lub określ pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="e5970-412">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>  
  
 <span data-ttu-id="e5970-413">Przykłady dotyczące obrazu macierzystego usługi można znaleźć [usługi obrazu macierzystego][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-413">For examples relating to the native image service, see [Native Image Service][Native Image Service].</span></span>  
  
## <a name="native-image-task"></a><span data-ttu-id="e5970-414">Obraz macierzysty — zadanie</span><span class="sxs-lookup"><span data-stu-id="e5970-414">Native Image Task</span></span>  
 <span data-ttu-id="e5970-415">Zadanie obrazu macierzystego jest zadanie systemu Windows, które generuje i obsługuje obrazów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="e5970-415">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="e5970-416">Zadanie obrazu macierzystego generuje i zwraca obrazów macierzystych automatycznie dla obsługiwanych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="e5970-416">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="e5970-417">(Zobacz [tworzenia obrazów macierzystych](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) Umożliwia również instalatorów do użycia [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) do tworzenia i aktualizowania obrazów macierzystych odroczonego naraz.</span><span class="sxs-lookup"><span data-stu-id="e5970-417">(See [Creating Native Images](http://msdn.microsoft.com/library/2bc8b678-dd8d-4742-ad82-319e9bf52418).) It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>  
  
 <span data-ttu-id="e5970-418">Zadanie obrazu macierzystego jest zarejestrowany, gdy dla każdego Procesora architektura obsługiwana na komputerze, aby umożliwić kompilacji dla aplikacji przeznaczonych każdej architektury:</span><span class="sxs-lookup"><span data-stu-id="e5970-418">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>  
  
|<span data-ttu-id="e5970-419">Nazwa zadania</span><span class="sxs-lookup"><span data-stu-id="e5970-419">Task name</span></span>|<span data-ttu-id="e5970-420">komputer 32-bitowy</span><span class="sxs-lookup"><span data-stu-id="e5970-420">32-bit computer</span></span>|<span data-ttu-id="e5970-421">komputer 64-bitowy</span><span class="sxs-lookup"><span data-stu-id="e5970-421">64-bit computer</span></span>|  
|---------------|----------------------|----------------------|  
|<span data-ttu-id="e5970-422">NET Framework NGEN 4.0.30319</span><span class="sxs-lookup"><span data-stu-id="e5970-422">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="e5970-423">Tak</span><span class="sxs-lookup"><span data-stu-id="e5970-423">Yes</span></span>|<span data-ttu-id="e5970-424">Tak</span><span class="sxs-lookup"><span data-stu-id="e5970-424">Yes</span></span>|  
|<span data-ttu-id="e5970-425">NET Framework NGEN 4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="e5970-425">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="e5970-426">Nie</span><span class="sxs-lookup"><span data-stu-id="e5970-426">No</span></span>|<span data-ttu-id="e5970-427">Tak</span><span class="sxs-lookup"><span data-stu-id="e5970-427">Yes</span></span>|  
  
 <span data-ttu-id="e5970-428">Zadanie obrazu macierzystego jest jest dostępna w .NET Framework 4.5 lub nowszy, podczas uruchamiania w systemie Windows 8 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="e5970-428">The native image task is is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="e5970-429">We wcześniejszych wersjach systemu Windows korzysta z programu .NET Framework [usługi obrazu macierzystego][Native Image Service].</span><span class="sxs-lookup"><span data-stu-id="e5970-429">On earlier versions of Windows, the .NET Framework uses the [Native Image Service][Native Image Service].</span></span>  
  
### <a name="task-lifetime"></a><span data-ttu-id="e5970-430">Cykl życia zadania</span><span class="sxs-lookup"><span data-stu-id="e5970-430">Task Lifetime</span></span>  
 <span data-ttu-id="e5970-431">Ogólnie rzecz biorąc harmonogramu zadań systemu Windows uruchamia zadanie obrazu macierzystego, każdej nocy, gdy komputer jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-431">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="e5970-432">Zadanie sprawdza, czy odroczonego pracę umieszczonych w kolejce przez programy instalacyjne, żądań aktualizacji odroczonego obrazu macierzystego i tworzenia żadnych obrazów automatycznego.</span><span class="sxs-lookup"><span data-stu-id="e5970-432">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="e5970-433">Zadanie kończy zaległych elementów pracy i zamknięcie.</span><span class="sxs-lookup"><span data-stu-id="e5970-433">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="e5970-434">Jeśli komputer nie jest bezczynne podczas wykonywania zadania, zatrzymuje zadanie.</span><span class="sxs-lookup"><span data-stu-id="e5970-434">If the computer stops being idle while the task is running, the task stops.</span></span>  
  
 <span data-ttu-id="e5970-435">Można również uruchomić ręcznie za pośrednictwem interfejsu użytkownika harmonogramu zadań lub ręcznego wywołania NGen.exe zadania obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-435">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="e5970-436">Jeśli zadanie zostało uruchomione przy użyciu jednej z tych metod, będzie nadal uruchomiona, gdy komputer nie jest już bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-436">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="e5970-437">Obrazy utworzone ręcznie za pomocą NGen.exe mają pierwszeństwo umożliwiające przewidywalne zachowanie dla instalatorów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-437">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>  
  
## <a name="native-image-service"></a><span data-ttu-id="e5970-438">Usługa obrazu macierzystego</span><span class="sxs-lookup"><span data-stu-id="e5970-438">Native Image Service</span></span>  
 <span data-ttu-id="e5970-439">Usługa obrazu macierzystego jest usługa systemu Windows, który generuje i przechowuje obrazów macierzystych.</span><span class="sxs-lookup"><span data-stu-id="e5970-439">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="e5970-440">Usługa obrazu macierzystego umożliwia deweloperowi odroczenie instalacji i aktualizacji obrazów macierzystych okresów, gdy komputer jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-440">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>  
  
 <span data-ttu-id="e5970-441">Zazwyczaj usługa obrazu macierzystego jest inicjowane przez program instalacyjny (Instalator) dla aplikacji lub aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="e5970-441">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="e5970-442">Priorytet 3 działań usługa wykonuje w czasie bezczynności na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e5970-442">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="e5970-443">Usługa zapisuje swój stan i może ona nadal przez wiele ponownych uruchomień komputera, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="e5970-443">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="e5970-444">Wiele kompilacje obrazu można umieścić w kolejce.</span><span class="sxs-lookup"><span data-stu-id="e5970-444">Multiple image compilations can be queued.</span></span>  
  
 <span data-ttu-id="e5970-445">Usługa także współdziała z ręcznego polecenie Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-445">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="e5970-446">Ręczne polecenia mają pierwszeństwo przed aktywności w tle.</span><span class="sxs-lookup"><span data-stu-id="e5970-446">Manual commands take precedence over background activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5970-447">W systemie Windows Vista Nazwa wyświetlana usługi obrazu macierzystego jest "v2.0.50727_X86 NGEN Microsoft.NET Framework" lub "NGEN Microsoft.NET Framework v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="e5970-447">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="e5970-448">We wszystkich wcześniejszych wersjach systemu Microsoft Windows nazwa jest "V2.0.50727_X86 usługi optymalizacji środowiska wykonawczego .NET" lub "Usługi optymalizacji środowiska wykonawczego .NET v2.0.50727_X64".</span><span class="sxs-lookup"><span data-stu-id="e5970-448">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>  
  
### <a name="launching-deferred-operations"></a><span data-ttu-id="e5970-449">Uruchamianie operacji odroczone</span><span class="sxs-lookup"><span data-stu-id="e5970-449">Launching Deferred Operations</span></span>  
 <span data-ttu-id="e5970-450">Przed rozpoczęciem instalacji lub uaktualniania, zaleca się wstrzymanie usługi.</span><span class="sxs-lookup"><span data-stu-id="e5970-450">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="e5970-451">Dzięki temu, że usługa nie wykonać, gdy Instalator jest kopiowanie plików lub umieszczanie zestawów w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e5970-451">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="e5970-452">Następujące polecenie w wierszu Ngen.exe wstrzymuje usługę:</span><span class="sxs-lookup"><span data-stu-id="e5970-452">The following Ngen.exe command line pauses the service:</span></span>  
  
```  
ngen queue pause  
```  
  
 <span data-ttu-id="e5970-453">Gdy wszystkie operacje odroczonego zostały umieszczone w kolejce, polecenie umożliwia usłudze wznowić:</span><span class="sxs-lookup"><span data-stu-id="e5970-453">When all deferred operations have been queued, the following command allows the service to resume:</span></span>  
  
```  
ngen queue continue  
```  
  
 <span data-ttu-id="e5970-454">Odroczenie generowanie obrazu natywnego podczas instalowania nowej aplikacji lub podczas aktualizowania składnika współużytkowanego, użyj `/queue` opcję z `install` lub `update` akcje.</span><span class="sxs-lookup"><span data-stu-id="e5970-454">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="e5970-455">Następujące wiersze polecenia Ngen.exe zainstalować obrazu macierzystego dla składnika współużytkowanego i wykonać aktualizację wszystkich katalogów głównych, które mogą mieć wpływ:</span><span class="sxs-lookup"><span data-stu-id="e5970-455">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 <span data-ttu-id="e5970-456">`update` Akcji ponowne wygenerowanie wszystkich obrazów macierzystych, które zostały unieważnione, nie tylko te, które używają `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="e5970-456">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>  
  
 <span data-ttu-id="e5970-457">Jeśli aplikacja zawiera wiele elementów głównych, można kontrolować priorytet odroczonego akcje.</span><span class="sxs-lookup"><span data-stu-id="e5970-457">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="e5970-458">Następujące polecenia w kolejce instalacji trzech głównych.</span><span class="sxs-lookup"><span data-stu-id="e5970-458">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="e5970-459">`Assembly1`jest najpierw zainstalowany bez oczekiwania na czas bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-459">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="e5970-460">`Assembly2`jest również instalowany bez oczekiwania przez czas bezczynności, ale po zakończeniu wszystkich akcji o priorytecie 1.</span><span class="sxs-lookup"><span data-stu-id="e5970-460">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="e5970-461">`Assembly3`jest zainstalowany, gdy usługa wykryje, że komputer jest w stanie bezczynności.</span><span class="sxs-lookup"><span data-stu-id="e5970-461">`Assembly3` is installed when the service detects that the computer is idle.</span></span>  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 <span data-ttu-id="e5970-462">Możesz wymusić akcji w kolejce do pojawia się synchronicznie przy użyciu `executeQueuedItems` akcji.</span><span class="sxs-lookup"><span data-stu-id="e5970-462">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="e5970-463">Jeśli podasz opcjonalne priorytet, ta akcja dotyczy tylko akcji w kolejce, które mają taki sam lub niższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="e5970-463">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="e5970-464">Priorytet domyślny jest 3, aby polecenie Ngen.exe natychmiast przetwarza wszystkich akcji w kolejce, a nie może zwracać aż do ich zakończono:</span><span class="sxs-lookup"><span data-stu-id="e5970-464">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>  
  
```  
ngen executeQueuedItems  
```  
  
 <span data-ttu-id="e5970-465">Synchroniczne polecenia są wykonywane przez Ngen.exe i nie jest używana usługa obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-465">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="e5970-466">Można wykonywać akcji przy użyciu Ngen.exe jest uruchomiona usługa obrazu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="e5970-466">You can execute actions using Ngen.exe while the native image service is running.</span></span>  
  
### <a name="service-shutdown"></a><span data-ttu-id="e5970-467">Zamykanie usługi</span><span class="sxs-lookup"><span data-stu-id="e5970-467">Service Shutdown</span></span>  
 <span data-ttu-id="e5970-468">Po jest inicjowane przez wykonanie polecenia Ngen.exe zawierającą `/queue` opcja, usługa działa w tle, dopóki wszystkie akcje zostały ukończone.</span><span class="sxs-lookup"><span data-stu-id="e5970-468">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="e5970-469">Usługa zapisuje swój stan, dzięki czemu w razie potrzeby można kontynuować podczas ponownych rozruchów wiele.</span><span class="sxs-lookup"><span data-stu-id="e5970-469">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="e5970-470">Gdy usługa wykryje, że ma żadnych więcej akcji w kolejce, następuje zresetowanie jego stan, aby nie zostanie uruchomiony ponownie przy następnym rozruchu komputera i jej zamknięcie się.</span><span class="sxs-lookup"><span data-stu-id="e5970-470">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>  
  
### <a name="service-interaction-with-clients"></a><span data-ttu-id="e5970-471">Usługa interakcji z klientami</span><span class="sxs-lookup"><span data-stu-id="e5970-471">Service Interaction with Clients</span></span>  
 <span data-ttu-id="e5970-472">W programie .NET Framework w wersji 2.0 tylko interakcji z usługą obrazu macierzystego jest przy użyciu wiersza polecenia narzędzia Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e5970-472">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="e5970-473">Narzędzie wiersza polecenia w skryptach instalacji do kolejki akcji dla usługi obrazu macierzystego i interakcję z usługą.</span><span class="sxs-lookup"><span data-stu-id="e5970-473">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5970-474">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5970-474">See Also</span></span>  
 [<span data-ttu-id="e5970-475">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="e5970-475">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="e5970-476">Proces zarządzanego wykonania</span><span class="sxs-lookup"><span data-stu-id="e5970-476">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)  
 [<span data-ttu-id="e5970-477">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e5970-477">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="e5970-478">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="e5970-478">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

[Native Image Service]: #native-image-service

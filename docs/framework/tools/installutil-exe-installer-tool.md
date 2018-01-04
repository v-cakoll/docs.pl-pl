---
title: "Installutil.exe (Narzędzie instalatora)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
caps.latest.revision: "40"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edda4e415f8ce0246ce6aa1a4d39f5bb6cec7728
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="5e8b2-102">Installutil.exe (Narzędzie instalatora)</span><span class="sxs-lookup"><span data-stu-id="5e8b2-102">Installutil.exe (Installer Tool)</span></span>
<span data-ttu-id="5e8b2-103">Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="5e8b2-104">To narzędzie działa w połączeniu z klasami <xref:System.Configuration.Install> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>  
  
 <span data-ttu-id="5e8b2-105">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="5e8b2-106">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="5e8b2-106">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5e8b2-107">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="5e8b2-107">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="5e8b2-108">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="5e8b2-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e8b2-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e8b2-109">Syntax</span></span>  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e8b2-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e8b2-110">Parameters</span></span>  
  
|<span data-ttu-id="5e8b2-111">Argument</span><span class="sxs-lookup"><span data-stu-id="5e8b2-111">Argument</span></span>|<span data-ttu-id="5e8b2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5e8b2-112">Description</span></span>|  
|--------------|-----------------|  
|`assembly`|<span data-ttu-id="5e8b2-113">Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="5e8b2-114">Pominięcie tego parametru, jeśli chcesz określić przy użyciu silnej nazwy zestawu `/AssemblyName` opcji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|  
  
<a name="options"></a>   
## <a name="options"></a><span data-ttu-id="5e8b2-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="5e8b2-115">Options</span></span>  
  
|<span data-ttu-id="5e8b2-116">Opcja</span><span class="sxs-lookup"><span data-stu-id="5e8b2-116">Option</span></span>|<span data-ttu-id="5e8b2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5e8b2-117">Description</span></span>|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> <span data-ttu-id="5e8b2-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e8b2-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="5e8b2-119">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-119">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="5e8b2-120">`/help`*zestawu*</span><span class="sxs-lookup"><span data-stu-id="5e8b2-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="5e8b2-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="5e8b2-121">-or-</span></span><br /><br /> <span data-ttu-id="5e8b2-122">`/?`*zestawu*</span><span class="sxs-lookup"><span data-stu-id="5e8b2-122">`/?` *assembly*</span></span>|<span data-ttu-id="5e8b2-123">Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="5e8b2-124">Ta opcja dodaje tekst zwracany przez każdego składnika Instalator <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości InstallUtil.exe tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|  
|<span data-ttu-id="5e8b2-125">`/AssemblyName`"*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="5e8b2-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="5e8b2-126">, Wersja =*główna.pomocnicza.kompilacja.poprawka*</span><span class="sxs-lookup"><span data-stu-id="5e8b2-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="5e8b2-127">, Culture =*ustawień regionalnych*</span><span class="sxs-lookup"><span data-stu-id="5e8b2-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="5e8b2-128">PublicKeyToken =*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="5e8b2-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="5e8b2-129">Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="5e8b2-130">Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="5e8b2-131">W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="5e8b2-132">Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="5e8b2-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|  
|<span data-ttu-id="5e8b2-133">`/InstallStateDir=[`*directoryName*`]`</span><span class="sxs-lookup"><span data-stu-id="5e8b2-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="5e8b2-134">Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="5e8b2-135">Domyślnie, jest to katalog, w którym znajduje się zestaw.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-135">The default is the directory that contains the assembly.</span></span>|  
|<span data-ttu-id="5e8b2-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="5e8b2-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="5e8b2-137">Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="5e8b2-138">Domyślnie jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *assemblyname*. InstallLog jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="5e8b2-139">Jeśli *filename* jest pominięty, plik dziennika nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-139">If *filename* is omitted, no log file is generated.</span></span>|  
|<span data-ttu-id="5e8b2-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="5e8b2-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="5e8b2-141">Jeśli `true`, wyświetla dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="5e8b2-142">Jeśli `false` (ustawienie domyślne), pomija dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-142">If `false` (the default), suppresses output to the console.</span></span>|  
|`/ShowCallStack`|<span data-ttu-id="5e8b2-143">Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|  
|<span data-ttu-id="5e8b2-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="5e8b2-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="5e8b2-145">Odinstalowuje określone zestawy.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="5e8b2-146">W przeciwieństwie do innych opcji `/u` ma zastosowanie do wszystkich zestawów niezależnie od tego, gdzie jest dostępna w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a><span data-ttu-id="5e8b2-147">Dodatkowe opcje instalatora</span><span class="sxs-lookup"><span data-stu-id="5e8b2-147">Additional Installer Options</span></span>  
 <span data-ttu-id="5e8b2-148">Indywidualne instalatory użyte w zestawie mogą rozpoznawać opcje Ponadto uprawnienia wymienione w [opcje](#options) sekcji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="5e8b2-149">Aby dowiedzieć się więcej o tych opcjach, uruchom InstallUtil.exe ze ścieżkami zestawów w wierszu polecenia, wraz z `/?` lub `/help` opcji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="5e8b2-150">Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e8b2-151">Zwraca tekst pomocy na opcje obsługiwane przez Instalator poszczególne składniki <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5e8b2-152">Poszczególne opcje, które zostały wprowadzone w wierszu polecenia są dostępne programowo z <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="5e8b2-153">Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="5e8b2-154">Jednak jeśli używasz `/Password` parametr, który jest rozpoznawany przez niektóre składniki Instalatora, zostanie zastąpiony przez osiem gwiazdki (*) informacji o hasłach i nie pojawią się w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (*) and will not appear in the log file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5e8b2-155">W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="5e8b2-156">Aby temu zapobiec, można pominąć w pliku dziennika, określając `/LogFile=` (bez *filename* argument) po Installutil.exe w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e8b2-157">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e8b2-157">Remarks</span></span>  
 <span data-ttu-id="5e8b2-158">Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="5e8b2-159">Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="5e8b2-160">Program Installutil.exe wykrywa i wykonuje te składniki instalatora.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-160">Installutil.exe detects and executes these installer components.</span></span>  
  
 <span data-ttu-id="5e8b2-161">W jednym wierszu polecenia można określić wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="5e8b2-162">Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="5e8b2-163">Z wyjątkiem `/u` i `/AssemblyName`, opcje są zbiorczą, ale możliwym do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="5e8b2-164">Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>  
  
 <span data-ttu-id="5e8b2-165">Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:</span><span class="sxs-lookup"><span data-stu-id="5e8b2-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>  
  
-   <span data-ttu-id="5e8b2-166">InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>  
  
-   <span data-ttu-id="5e8b2-167">*AssemblyName*. InstallLog — zawiera informacje specyficzne dla fazy rezerwacji procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="5e8b2-168">Aby uzyskać więcej informacji dotyczących fazy rezerwacji, zobacz <xref:System.Configuration.Install.Installer.Commit%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>  
  
-   <span data-ttu-id="5e8b2-169">*AssemblyName*. InstallState - zawiera dane używane w celu odinstalowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>  
  
 <span data-ttu-id="5e8b2-170">Installutil.exe używa odbicia, aby sprawdzić określonych zestawów i Znajdź wszystkie <xref:System.Configuration.Install.Installer> typów, które mają <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> ustawić atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="5e8b2-171">Narzędzie wykonuje następnie jedną <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> lub <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metody na każde wystąpienie <xref:System.Configuration.Install.Installer> typu.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="5e8b2-172">Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="5e8b2-173">Odinstalowanie nie jest transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-173">Uninstall is not transactional.</span></span>  
  
 <span data-ttu-id="5e8b2-174">Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>  
  
 <span data-ttu-id="5e8b2-175">Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="5e8b2-176">Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="5e8b2-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="5e8b2-177">Obie wersje narzędzia instalatora działają tak samo.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-177">Both versions of the Installer tool behave the same.</span></span>  
  
 <span data-ttu-id="5e8b2-178">Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="5e8b2-179">Jeśli spróbujesz takich jak wdrożyć usługę Windows w języku C++ z Installutil.exe, wyjątek <xref:System.BadImageFormatException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="5e8b2-180">Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5e8b2-181">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5e8b2-181">Examples</span></span>  
 <span data-ttu-id="5e8b2-182">Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>  
  
```  
installutil /?  
```  
  
 <span data-ttu-id="5e8b2-183">Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="5e8b2-184">Wyświetla również opis oraz listę obsługiwanych przez składniki Instalatora w opcji `myAssembly.exe` Jeśli przypisano tekst pomocy do Instalatora <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>  
  
```  
installutil /? myAssembly.exe  
```  
  
 <span data-ttu-id="5e8b2-185">Polecenie wykonuje składników Instalatora w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil myAssembly.exe  
```  
  
 <span data-ttu-id="5e8b2-186">Polecenie wykonuje składników Instalatora w zestawie przy użyciu `/AssemblyName` przełącznika i w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="5e8b2-187">Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="5e8b2-188">Uwaga, wszystkie zestawy określonego za pomocą nazwy pliku musi poprzedzać zestawy określone przez silnej nazwy w wierszu polecenia, ponieważ `/AssemblyName` opcji nie może zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 <span data-ttu-id="5e8b2-189">Polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>  
  
```  
installutil /u myAssembly.exe   
```  
  
 <span data-ttu-id="5e8b2-190">Polecenie wykonuje składniki uninistaller zestawy `myAssembly1.exe` i `myAssembly2.exe`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-190">The following command executes the uninistaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 <span data-ttu-id="5e8b2-191">Ponieważ pozycja `/u` opcji w wierszu polecenia nie jest ważna, jest odpowiednikiem następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 <span data-ttu-id="5e8b2-192">Polecenie wykonuje instalatorów w zestawie `myAssembly.exe` i określa, czy informacje o postępie będą zapisywane `myLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 <span data-ttu-id="5e8b2-193">Polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, określa, czy mają być zapisywane informacje o postępie `myLog.InstallLog`i używa niestandardowych instalatorów `/reg` opcję, aby określić, że należy dokonać aktualizacji do systemu rejestr.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 <span data-ttu-id="5e8b2-194">Polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, używa niestandardowego obiektu Instalator `/email` opcję, aby określić adres e-mail użytkownika, a pomija dane wyjściowe do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's e-mail address, and suppresses output to the log file.</span></span>  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 <span data-ttu-id="5e8b2-195">Poniższe polecenie zapisuje postęp instalacji dla `myAssembly.exe` do `myLog.InstallLog` i zapisuje postęp `myTestAssembly.exe` do `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="5e8b2-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e8b2-196">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e8b2-196">See Also</span></span>  
 <xref:System.Configuration.Install>  
 [<span data-ttu-id="5e8b2-197">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="5e8b2-197">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="5e8b2-198">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="5e8b2-198">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

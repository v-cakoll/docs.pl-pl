---
title: Installutil.exe (Narzędzie instalatora)
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ad0497bd5303dc4113dbb7b8078c70cb044cc95
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044542"
---
# <a name="installutilexe-installer-tool"></a><span data-ttu-id="bfe79-102">Installutil.exe (Narzędzie instalatora)</span><span class="sxs-lookup"><span data-stu-id="bfe79-102">Installutil.exe (Installer Tool)</span></span>

<span data-ttu-id="bfe79-103">Narzędzie Instalator to narzędzie wiersza polecenia umożliwiające instalowanie i odinstalowywanie zasobów serwera przez wykonywanie składników instalatora w określonych zestawach.</span><span class="sxs-lookup"><span data-stu-id="bfe79-103">The Installer tool is a command-line utility that allows you to install and uninstall server resources by executing the installer components in specified assemblies.</span></span> <span data-ttu-id="bfe79-104">To narzędzie działa w połączeniu z klasami w <xref:System.Configuration.Install> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bfe79-104">This tool works in conjunction with classes in the <xref:System.Configuration.Install> namespace.</span></span>

<span data-ttu-id="bfe79-105">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bfe79-105">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="bfe79-106">Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="bfe79-106">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="bfe79-107">Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="bfe79-107">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="bfe79-108">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="bfe79-108">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="bfe79-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfe79-109">Syntax</span></span>

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a><span data-ttu-id="bfe79-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfe79-110">Parameters</span></span>

|<span data-ttu-id="bfe79-111">Argument</span><span class="sxs-lookup"><span data-stu-id="bfe79-111">Argument</span></span>|<span data-ttu-id="bfe79-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bfe79-112">Description</span></span>|
|--------------|-----------------|
|`assembly`|<span data-ttu-id="bfe79-113">Nazwa pliku zestawu, w którym mają zostać wykonane składniki instalatora.</span><span class="sxs-lookup"><span data-stu-id="bfe79-113">The file name of the assembly in which to execute the installer components.</span></span> <span data-ttu-id="bfe79-114">Pomiń ten parametr, jeśli chcesz określić silną nazwę zestawu przy użyciu `/AssemblyName` opcji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-114">Omit this parameter if you want to specify the assembly's strong name by using the `/AssemblyName` option.</span></span>|

<a name="options"></a>

## <a name="options"></a><span data-ttu-id="bfe79-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="bfe79-115">Options</span></span>

|<span data-ttu-id="bfe79-116">Opcja</span><span class="sxs-lookup"><span data-stu-id="bfe79-116">Option</span></span>|<span data-ttu-id="bfe79-117">Opis</span><span class="sxs-lookup"><span data-stu-id="bfe79-117">Description</span></span>|
|------------|-----------------|
|`/h[elp]`<br /><br /> <span data-ttu-id="bfe79-118">—lub—</span><span class="sxs-lookup"><span data-stu-id="bfe79-118">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="bfe79-119">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bfe79-119">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="bfe79-120">`/help`*zestaw*</span><span class="sxs-lookup"><span data-stu-id="bfe79-120">`/help` *assembly*</span></span><br /><br /> <span data-ttu-id="bfe79-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="bfe79-121">-or-</span></span><br /><br /> <span data-ttu-id="bfe79-122">`/?`*zestaw*</span><span class="sxs-lookup"><span data-stu-id="bfe79-122">`/?` *assembly*</span></span>|<span data-ttu-id="bfe79-123">Wyświetla dodatkowe opcje rozpoznawane przez poszczególne instalatory w określonym zestawie, wraz ze składnią poleceń i opcjami programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="bfe79-123">Displays additional options recognized by individual installers within the specified assembly, along with command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="bfe79-124">Ta opcja powoduje dodanie tekstu zwróconego przez każdą <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> Właściwość składnika Instalatora do tekstu pomocy programu Installutil. exe.</span><span class="sxs-lookup"><span data-stu-id="bfe79-124">This option adds the text returned by each installer component's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property to the help text of InstallUtil.exe.</span></span>|
|<span data-ttu-id="bfe79-125">`/AssemblyName`"*AssemblyName*</span><span class="sxs-lookup"><span data-stu-id="bfe79-125">`/AssemblyName` "*assemblyName*</span></span><br /><br /> <span data-ttu-id="bfe79-126">,Version=*major.minor.build.revision*</span><span class="sxs-lookup"><span data-stu-id="bfe79-126">,Version=*major.minor.build.revision*</span></span><br /><br /> <span data-ttu-id="bfe79-127">, Kultura =*Ustawienia regionalne*</span><span class="sxs-lookup"><span data-stu-id="bfe79-127">,Culture=*locale*</span></span><br /><br /> <span data-ttu-id="bfe79-128">,PublicKeyToken=*publicKeyToken*"</span><span class="sxs-lookup"><span data-stu-id="bfe79-128">,PublicKeyToken=*publicKeyToken*"</span></span>|<span data-ttu-id="bfe79-129">Określa silną nazwę zestawu, która musi zostać zarejestrowana w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfe79-129">Specifies the strong name of an assembly, which must be registered in the global assembly cache.</span></span> <span data-ttu-id="bfe79-130">Nazwa zestawu musi być w pełni kwalifikowaną nazwą zawierającą wersję, kulturę i token klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-130">The assembly name must be fully qualified with the version, culture, and public key token of the assembly.</span></span> <span data-ttu-id="bfe79-131">W pełni kwalifikowana nazwa musi być ujęte w cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="bfe79-131">The fully qualified name must be surrounded by quotes.</span></span><br /><br /> <span data-ttu-id="bfe79-132">Na przykład w pełni kwalifikowaną nazwą zestawu jest "mójZestaw, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="bfe79-132">For example, "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0" is a fully qualified assembly name.</span></span>|
|<span data-ttu-id="bfe79-133">`/InstallStateDir=[` *directoryName* `]`</span><span class="sxs-lookup"><span data-stu-id="bfe79-133">`/InstallStateDir=[` *directoryName* `]`</span></span>|<span data-ttu-id="bfe79-134">Określa katalog pliku InstallState, który zawiera dane służące do odinstalowywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-134">Specifies the directory of the .InstallState file that contains the data used to uninstall the assembly.</span></span> <span data-ttu-id="bfe79-135">Domyślnie, jest to katalog, w którym znajduje się zestaw.</span><span class="sxs-lookup"><span data-stu-id="bfe79-135">The default is the directory that contains the assembly.</span></span>|
|<span data-ttu-id="bfe79-136">`/LogFile=`[*filename*]</span><span class="sxs-lookup"><span data-stu-id="bfe79-136">`/LogFile=`[*filename*]</span></span>|<span data-ttu-id="bfe79-137">Określa nazwę pliku dziennika, w którym jest rejestrowany postęp instalacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-137">Specifies the name of the log file where installation progress is recorded.</span></span> <span data-ttu-id="bfe79-138">Domyślnie, jeśli `/LogFile` opcja zostanie pominięta, plik dziennika o nazwie *AssemblyName*. InstallLog.</span><span class="sxs-lookup"><span data-stu-id="bfe79-138">By default, if the `/LogFile` option is omitted, a log file named *assemblyname*.InstallLog is created.</span></span> <span data-ttu-id="bfe79-139">Jeśli *Nazwa pliku* zostanie pominięta, żaden plik dziennika nie zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="bfe79-139">If *filename* is omitted, no log file is generated.</span></span>|
|<span data-ttu-id="bfe79-140">`/LogToConsole`={`true`&#124;`false`}</span><span class="sxs-lookup"><span data-stu-id="bfe79-140">`/LogToConsole`={`true`&#124;`false`}</span></span>|<span data-ttu-id="bfe79-141">Jeśli `true`, wyświetla dane wyjściowe w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-141">If `true`, displays output to the console.</span></span> <span data-ttu-id="bfe79-142">Jeśli `false` (wartość domyślna), pomija dane wyjściowe w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-142">If `false` (the default), suppresses output to the console.</span></span>|
|`/ShowCallStack`|<span data-ttu-id="bfe79-143">Przesyła stos wywołań do pliku dziennika, jeśli w jakimkolwiek punkcie instalacji wystąpi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bfe79-143">Outputs the call stack to the log file if an exception occurs at any point during installation.</span></span>|
|<span data-ttu-id="bfe79-144">`/u`[`ninstall`]</span><span class="sxs-lookup"><span data-stu-id="bfe79-144">`/u`[`ninstall`]</span></span>|<span data-ttu-id="bfe79-145">Odinstalowuje określone zestawy.</span><span class="sxs-lookup"><span data-stu-id="bfe79-145">Uninstalls the specified assemblies.</span></span> <span data-ttu-id="bfe79-146">W przeciwieństwie do innych opcji `/u` , ma zastosowanie do wszystkich zestawów bez względu na to, gdzie opcja pojawia się w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfe79-146">Unlike the other options, `/u` applies to all assemblies regardless of where the option appears on the command line.</span></span>|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a><span data-ttu-id="bfe79-147">Dodatkowe opcje instalatora</span><span class="sxs-lookup"><span data-stu-id="bfe79-147">Additional Installer Options</span></span>

<span data-ttu-id="bfe79-148">Poszczególne Instalatory używane w ramach zestawu mogą rozpoznawać opcje oprócz tych wymienionych w sekcji [Opcje](#options) .</span><span class="sxs-lookup"><span data-stu-id="bfe79-148">Individual installers used within an assembly may recognize options in addition to those listed in the [Options](#options) section.</span></span> <span data-ttu-id="bfe79-149">Aby dowiedzieć się więcej na temat tych opcji, uruchom program Installutil. exe z ścieżkami zestawów w wierszu polecenia oraz `/?` z `/help` opcją or.</span><span class="sxs-lookup"><span data-stu-id="bfe79-149">To learn about these options, run InstallUtil.exe with the paths of the assemblies on the command line along with the `/?` or `/help` option.</span></span> <span data-ttu-id="bfe79-150">Aby określić te opcje, należy umieścić je w wierszu polecenia wraz z opcjami rozpoznawanymi przez program InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="bfe79-150">To specify these options, you include them on the command line along with the options recognized by InstallUtil.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="bfe79-151">Tekst pomocy na temat opcji obsługiwanych przez poszczególne składniki instalatora jest zwracany przez <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwość.</span><span class="sxs-lookup"><span data-stu-id="bfe79-151">Help text on the options supported by individual installer components is returned by the <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bfe79-152">Poszczególne opcje, które zostały wprowadzone w wierszu polecenia, są dostępne programowo z <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bfe79-152">The individual options that have been entered on the command line are accessible programmatically from the <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="bfe79-153">Wszystkie opcje i parametry wiersza polecenia są zapisywane w pliku dziennika instalacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-153">All options and command-line parameters are written to the installation log file.</span></span> <span data-ttu-id="bfe79-154">Jeśli jednak użyjesz `/Password` parametru, który jest rozpoznawany przez niektóre składniki instalatora, informacje o haśle zostaną zastąpione przez osiem gwiazdek (\*) i nie będą wyświetlane w pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="bfe79-154">However, if you use the `/Password` parameter, which is recognized by some installer components, the password information will be replaced by eight asterisks (\*) and will not appear in the log file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bfe79-155">W niektórych przypadkach parametry przekazywane do instalatora mogą zawierać informacje poufne lub dane osobowe, które domyślnie są zapisywane w pliku dziennika w postaci czystego tekstu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-155">In some cases, parameters passed to the installer may include sensitive or personally identifiable information, which, by default, is written to a plain text log file.</span></span> <span data-ttu-id="bfe79-156">Aby uniknąć tego zachowania, można pominąć plik dziennika, określając `/LogFile=` (bez argumentu *filename* ) po Installutil. exe w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="bfe79-156">To prevent this behavior, you can suppress the log file by specifying `/LogFile=` (with no *filename* argument) after Installutil.exe on the command line.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfe79-157">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfe79-157">Remarks</span></span>

<span data-ttu-id="bfe79-158">Aplikacje programu .NET Framework składają się z tradycyjnych plików programów oraz skojarzonych zasobów, takich jak kolejki komunikatów, dzienniki zdarzeń i liczniki wydajności, które muszą zostać utworzone podczas wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-158">.NET Framework applications consist of traditional program files and associated resources, such as message queues, event logs, and performance counters that must be created when the application is deployed.</span></span> <span data-ttu-id="bfe79-159">Można użyć składników instalatora zestawu, aby utworzyć te zasoby podczas instalowania aplikacji oraz aby je usunąć podczas odinstalowywania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-159">You can use an assembly's installer components to create these resources when your application is installed and to remove them when your application is uninstalled.</span></span> <span data-ttu-id="bfe79-160">Program Installutil.exe wykrywa i wykonuje te składniki instalatora.</span><span class="sxs-lookup"><span data-stu-id="bfe79-160">Installutil.exe detects and executes these installer components.</span></span>

<span data-ttu-id="bfe79-161">W jednym wierszu polecenia można określić wiele zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfe79-161">You can specify multiple assemblies on the same command line.</span></span> <span data-ttu-id="bfe79-162">Każda opcja występująca przed nazwą zestawu jest stosowana do instalacji tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-162">Any option that occurs before an assembly name applies to that assembly's installation.</span></span> <span data-ttu-id="bfe79-163">Z wyjątkiem `/AssemblyName`i, opcje są skumulowane, ale Zastąp. `/u`</span><span class="sxs-lookup"><span data-stu-id="bfe79-163">Except for `/u` and `/AssemblyName`, options are cumulative but overridable.</span></span> <span data-ttu-id="bfe79-164">Oznacza to, że opcje określone dla jednego zestawu są stosowane do wszystkich kolejnych zestawów, chyba że dana opcja zostanie określona z nową wartością.</span><span class="sxs-lookup"><span data-stu-id="bfe79-164">That is, options specified for one assembly apply to all subsequent assemblies unless the option is specified with a new value.</span></span>

<span data-ttu-id="bfe79-165">Uruchomienie programu Installutil.exe dla zestawu bez określenia żadnych opcji spowoduje umieszczenie w katalogu tego zestawu następujących trzech plików:</span><span class="sxs-lookup"><span data-stu-id="bfe79-165">If you run Installutil.exe against an assembly without specifying any options, it places the following three files into the assembly's directory:</span></span>

- <span data-ttu-id="bfe79-166">InstallUtil.InstallLog — zawiera ogólny opis postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-166">InstallUtil.InstallLog - Contains a general description of the installation progress.</span></span>

- <span data-ttu-id="bfe79-167">*AssemblyName*. InstallLog — zawiera informacje specyficzne dla fazy zatwierdzania procesu instalacji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-167">*assemblyname*.InstallLog - Contains information specific to the commit phase of the installation process.</span></span> <span data-ttu-id="bfe79-168">Aby uzyskać więcej informacji na temat fazy zatwierdzania, <xref:System.Configuration.Install.Installer.Commit%2A> Zobacz metodę.</span><span class="sxs-lookup"><span data-stu-id="bfe79-168">For more information about the commit phase, see the <xref:System.Configuration.Install.Installer.Commit%2A> method.</span></span>

- <span data-ttu-id="bfe79-169">*AssemblyName*. InstallState — zawiera dane używane do odinstalowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-169">*assemblyname*.InstallState - Contains data used to uninstall the assembly.</span></span>

<span data-ttu-id="bfe79-170">Installutil. exe używa odbicia w celu sprawdzenia określonych zestawów i znalezienia wszystkich <xref:System.Configuration.Install.Installer> typów, które <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> mają ustawiony `true`atrybut.</span><span class="sxs-lookup"><span data-stu-id="bfe79-170">Installutil.exe uses reflection to inspect the specified assemblies and to find all <xref:System.Configuration.Install.Installer> types that have the <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> attribute set to `true`.</span></span> <span data-ttu-id="bfe79-171">Narzędzie wykonuje <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> <xref:System.Configuration.Install.Installer> następnie albo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metodę dla każdego wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="bfe79-171">The tool then executes either the <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> or the <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> method on each instance of the <xref:System.Configuration.Install.Installer> type.</span></span> <span data-ttu-id="bfe79-172">Program Installutil.exe wykonuje instalację w sposób transakcyjny, a więc niepowodzenie instalacji dowolnego zestawu powoduje wycofanie instalacji wszystkich innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="bfe79-172">Installutil.exe performs installation in a transactional manner; that is, if one of the assemblies fails to install, it rolls back the installations of all other assemblies.</span></span> <span data-ttu-id="bfe79-173">Odinstalowanie nie jest transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="bfe79-173">Uninstall is not transactional.</span></span>

<span data-ttu-id="bfe79-174">Program Installutil.exe nie może instalować ani odinstalowywać zestawów podpisywanych z opóźnieniem, ale może instalować i odinstalowywać zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="bfe79-174">Installutil.exe cannot install or uninstall delay-signed assemblies, but it can install or uninstall strong-named assemblies.</span></span>

<span data-ttu-id="bfe79-175">Począwszy od programu .NET Framework w wersji 2.0, 32-bitowa wersja środowiska uruchomieniowego języka wspólnego (CLR) jest dostarczana tylko z 32-bitową wersją narzędzia Instalator, ale 64-bitowa wersja środowiska CLR jest dostarczana z 32-bitową i 64-bitową wersją narzędzia Instalator.</span><span class="sxs-lookup"><span data-stu-id="bfe79-175">Starting with the .NET Framework version 2.0, the 32-bit version of the common language runtime (CLR) ships with only the 32-bit version of the Installer tool, but the 64-bit version of the CLR ships with both 32-bit and 64-bit versions of the Installer tool.</span></span> <span data-ttu-id="bfe79-176">Gdy jest używane 64-bitowe środowisko CLR, 32-bitowe narzędzie instalatora jest używane do instalowania zestawów 32-bitowych, a 64-bitowe narzędzie instalatora do instalowania zestawów 64-bitowych oraz zestawów języka Microsoft Intermediate Language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="bfe79-176">When using the 64-bit CLR, use the 32-bit Installer tool to install 32-bit assemblies, and the 64-bit Installer tool to install 64-bit and Microsoft intermediate language (MSIL) assemblies.</span></span> <span data-ttu-id="bfe79-177">Obie wersje narzędzia instalatora działają tak samo.</span><span class="sxs-lookup"><span data-stu-id="bfe79-177">Both versions of the Installer tool behave the same.</span></span>

<span data-ttu-id="bfe79-178">Za pomocą programu Installutil.exe nie można wdrażać usług systemu Windows napisanych w języku C++, ponieważ program Installutil.exe nie rozpoznaje osadzonego natywnego kodu generowanego przez kompilator C++.</span><span class="sxs-lookup"><span data-stu-id="bfe79-178">You cannot use Installutil.exe to deploy a Windows service that was created by using C++, because Installutil.exe cannot recognize the embedded native code that is produced by the C++ compiler.</span></span> <span data-ttu-id="bfe79-179">Jeśli spróbujesz wdrożyć usługę C++ systemu Windows przy użyciu Installutil. exe, zostanie zgłoszony wyjątek, <xref:System.BadImageFormatException> taki jak.</span><span class="sxs-lookup"><span data-stu-id="bfe79-179">If you try to deploy a C++ Windows service with Installutil.exe, an exception such as <xref:System.BadImageFormatException> will be thrown.</span></span> <span data-ttu-id="bfe79-180">Aby wykonać taki scenariusz, należy przenieść kod usługi do modułu języka C++, a następnie napisać obiekt instalatora w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bfe79-180">To work with this scenario, move the service code to a C++ module, and then write the installer object in C# or Visual Basic.</span></span>

## <a name="examples"></a><span data-ttu-id="bfe79-181">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bfe79-181">Examples</span></span>

<span data-ttu-id="bfe79-182">Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="bfe79-182">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span>

```console
installutil /?
```

<span data-ttu-id="bfe79-183">Poniższe polecenie wyświetla opis składni poleceń oraz opcje programu InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="bfe79-183">The following command displays a description of the command syntax and options for InstallUtil.exe.</span></span> <span data-ttu-id="bfe79-184">Wyświetla również opis i listę opcji obsługiwanych przez składniki instalatora w programie `myAssembly.exe` , jeśli tekst pomocy został przypisany do <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> właściwości Instalatora.</span><span class="sxs-lookup"><span data-stu-id="bfe79-184">It also displays a description and list of options supported by the installer components in `myAssembly.exe` if help text has been assigned to the installer's <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> property.</span></span>

```console
installutil /? myAssembly.exe
```

<span data-ttu-id="bfe79-185">Następujące polecenie wykonuje składniki instalatora w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="bfe79-185">The following command executes the installer components in the assembly `myAssembly.exe`.</span></span>

```console
installutil myAssembly.exe
```

<span data-ttu-id="bfe79-186">Następujące polecenie wykonuje składniki instalatora w zestawie przy użyciu `/AssemblyName` przełącznika i w pełni kwalifikowanej nazwy.</span><span class="sxs-lookup"><span data-stu-id="bfe79-186">The following command executes the installer components in an assembly by using the `/AssemblyName` switch and a fully qualified name.</span></span>

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="bfe79-187">Poniższe polecenie wykonuje składniki instalatora w zestawie określonym przez nazwę pliku oraz w zestawie określonym przez silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="bfe79-187">The following command executes the installer components in an assembly specified by file name and in an assembly specified by strong name.</span></span> <span data-ttu-id="bfe79-188">Należy zauważyć, że wszystkie zestawy określone przez nazwę pliku muszą poprzedzać zestawy określone przez silną nazwę w wierszu polecenia `/AssemblyName` , ponieważ nie można zastąpić tej opcji.</span><span class="sxs-lookup"><span data-stu-id="bfe79-188">Note that all assemblies specified by file name must precede assemblies specified by strong name on the command line, because the `/AssemblyName` option cannot be overridden.</span></span>

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

<span data-ttu-id="bfe79-189">Następujące polecenie wykonuje składniki dezinstalatora w zestawie `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="bfe79-189">The following command executes the uninstaller components in the assembly `myAssembly.exe`.</span></span>

```console
installutil /u myAssembly.exe
```

<span data-ttu-id="bfe79-190">Następujące polecenie wykonuje składniki dezinstalatora w zestawach `myAssembly1.exe` i. `myAssembly2.exe`</span><span class="sxs-lookup"><span data-stu-id="bfe79-190">The following command executes the uninstaller components in the assemblies `myAssembly1.exe` and `myAssembly2.exe`.</span></span>

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

<span data-ttu-id="bfe79-191">Ponieważ pozycja `/u` opcji w wierszu polecenia nie jest ważna, jest to równoznaczne z następującym poleceniem.</span><span class="sxs-lookup"><span data-stu-id="bfe79-191">Because the position of the `/u` option on the command line is not important, this is equivalent to the following command.</span></span>

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

<span data-ttu-id="bfe79-192">Następujące polecenie wykonuje Instalatory w zestawie `myAssembly.exe` i określa, w `myLog.InstallLog`jaki sposób informacje o postępie będą zapisywane.</span><span class="sxs-lookup"><span data-stu-id="bfe79-192">The following command executes the installers in the assembly `myAssembly.exe` and specifies that progress information will be written to `myLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

<span data-ttu-id="bfe79-193">Następujące polecenie wykonuje instalatorów w zestawie `myAssembly.exe`, określa, czy informacje o postępie powinny być `myLog.InstallLog`zapisywane w, i używa opcji niestandardowej `/reg` instalacji, aby określić, że aktualizacje powinny zostać wprowadzone do systemu Secret.</span><span class="sxs-lookup"><span data-stu-id="bfe79-193">The following command executes the installers in the assembly `myAssembly.exe`, specifies that progress information should be written to `myLog.InstallLog`, and uses the installers' custom `/reg` option to specify that updates should be made to the system registry.</span></span>

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

<span data-ttu-id="bfe79-194">Następujące polecenie wykonuje Instalatory w zestawie `myAssembly.exe`, używa opcji niestandardowej `/email` Instalatora, aby określić adres e-mail użytkownika i pomija dane wyjściowe do pliku dziennika.</span><span class="sxs-lookup"><span data-stu-id="bfe79-194">The following command executes the installers in the assembly `myAssembly.exe`, uses the installer's custom `/email` option to specify the user's email address, and suppresses output to the log file.</span></span>

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

<span data-ttu-id="bfe79-195">Następujące polecenie zapisuje postęp instalacji `myAssembly.exe` programu do `myLog.InstallLog` programu i zapisuje postęp dla `myTestAssembly.exe` programu do `myTestLog.InstallLog`.</span><span class="sxs-lookup"><span data-stu-id="bfe79-195">The following command writes the installation progress for `myAssembly.exe` to `myLog.InstallLog` and writes the progress for `myTestAssembly.exe` to `myTestLog.InstallLog`.</span></span>

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a><span data-ttu-id="bfe79-196">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfe79-196">See also</span></span>

- <xref:System.Configuration.Install>
- [<span data-ttu-id="bfe79-197">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="bfe79-197">Tools</span></span>](index.md)
- [<span data-ttu-id="bfe79-198">Wiersze polecenia</span><span class="sxs-lookup"><span data-stu-id="bfe79-198">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

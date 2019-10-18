---
title: dotnet-dump-.NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia dotnet-dump.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 7eba0cba28f0575be4b374b26e9aca26a70df603
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321597"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="6c7ee-103">Narzędzie do zbierania i analizy zrzutów (`dotnet-dump`)</span><span class="sxs-lookup"><span data-stu-id="6c7ee-103">Dump collection and analysis utility (`dotnet-dump`)</span></span>

<span data-ttu-id="6c7ee-104">**Ten artykuł dotyczy: ✓** .net Core 3,0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="6c7ee-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="6c7ee-105">`dotnet-dump` nie jest obsługiwana w macOS.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="installing-dotnet-dump"></a><span data-ttu-id="6c7ee-106">Instalowanie `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="6c7ee-106">Installing `dotnet-dump`</span></span>

<span data-ttu-id="6c7ee-107">Aby zainstalować najnowszą wersję [pakietu NuGet](https://www.nuget.org/packages/dotnet-dump)`dotnet-dump`, należy użyć polecenia [Install narzędzia dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="6c7ee-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="6c7ee-108">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6c7ee-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="6c7ee-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6c7ee-109">Description</span></span>

<span data-ttu-id="6c7ee-110">Narzędzie globalne `dotnet-dump` umożliwia zbieranie i analizowanie zrzutów systemów Windows i Linux bez żadnego natywnego debugera, takiego jak `lldb` w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="6c7ee-111">To narzędzie jest ważne na platformach, takich jak Alpine Linux, gdzie w pełni działa `lldb` nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="6c7ee-112">Narzędzie `dotnet-dump` umożliwia uruchamianie poleceń SOS, aby analizować awarie i moduł wyrzucania elementów bezużytecznych (GC), ale nie jest to debuger natywny, więc nie są obsługiwane elementy, takie jak wyświetlanie natywnych ramek stosu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="6c7ee-113">Opcje</span><span class="sxs-lookup"><span data-stu-id="6c7ee-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="6c7ee-114">Wyświetla wersję narzędzia dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-114">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6c7ee-115">Wyświetla pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="6c7ee-116">Polecenia</span><span class="sxs-lookup"><span data-stu-id="6c7ee-116">Commands</span></span>

| <span data-ttu-id="6c7ee-117">Polecenie</span><span class="sxs-lookup"><span data-stu-id="6c7ee-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="6c7ee-118">Platforma dotnet — Zbieranie zrzutów</span><span class="sxs-lookup"><span data-stu-id="6c7ee-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="6c7ee-119">Analiza zrzutów dotnet</span><span class="sxs-lookup"><span data-stu-id="6c7ee-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="6c7ee-120">Platforma dotnet — Zbieranie zrzutów</span><span class="sxs-lookup"><span data-stu-id="6c7ee-120">dotnet-dump collect</span></span>

<span data-ttu-id="6c7ee-121">Przechwytuje Zrzut z procesu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="6c7ee-122">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6c7ee-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="6c7ee-123">Opcje</span><span class="sxs-lookup"><span data-stu-id="6c7ee-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="6c7ee-124">Wyświetla pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="6c7ee-125">Określa numer identyfikatora procesu, z którego ma zostać zebrany zrzut pamięci.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="6c7ee-126">Określa typ Dumb, który określa rodzaje informacji zbieranych z procesu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-126">Specifies the dumb type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="6c7ee-127">Istnieją dwa typy:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-127">There are two types:</span></span>

  - <span data-ttu-id="6c7ee-128">`Heap`-duże i stosunkowo kompleksowe zrzuty zawierające listy modułów, listy wątków, wszystkie stosy, informacje o wyjątkach, informacje o obsłudze i wszystkie pamięci z wyjątkiem zamapowanych obrazów.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="6c7ee-129">`Mini`-Mały zrzut zawierający listy modułów, listy wątków, informacje o wyjątku i wszystkie stosy.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="6c7ee-130">Jeśli nie zostanie określony, `Heap` jest wartością domyślną.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="6c7ee-131">Pełna ścieżka i nazwa pliku, w którym ma zostać zapisany zebrany zrzut.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="6c7ee-132">Jeśli nie zostanie określony:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-132">If not specified:</span></span>

  - <span data-ttu-id="6c7ee-133">Wartość domyślna to *.\dump_YYYYMMDD_HHMMSS.dmp* w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="6c7ee-134">Wartość domyślna to *./core_YYYYMMDD_HHMMSS* w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="6c7ee-135">RRRRMMDD to rok/miesiąc/dzień, a HHMMSS to godzina/minutę/sekundę.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="6c7ee-136">Włącza rejestrowanie diagnostyczne kolekcji zrzutów.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="6c7ee-137">Analiza zrzutów dotnet</span><span class="sxs-lookup"><span data-stu-id="6c7ee-137">dotnet-dump analyze</span></span>

<span data-ttu-id="6c7ee-138">Uruchamia powłokę interaktywną w celu eksplorowania zrzutu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="6c7ee-139">Powłoka akceptuje różne [polecenia sos](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="6c7ee-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="6c7ee-140">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6c7ee-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="6c7ee-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6c7ee-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="6c7ee-142">Określa ścieżkę do pliku zrzutu do przeanalizowania.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="6c7ee-143">Opcje</span><span class="sxs-lookup"><span data-stu-id="6c7ee-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="6c7ee-144">Określa [polecenie](#analyze-sos-commands) , które ma być uruchamiane w powłoce przy uruchamianiu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="6c7ee-145">Analizowanie poleceń SOS</span><span class="sxs-lookup"><span data-stu-id="6c7ee-145">Analyze SOS commands</span></span>

| <span data-ttu-id="6c7ee-146">Polecenie</span><span class="sxs-lookup"><span data-stu-id="6c7ee-146">Command</span></span>                             | <span data-ttu-id="6c7ee-147">Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c7ee-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="6c7ee-148">Wyświetla wszystkie dostępne polecenia</span><span class="sxs-lookup"><span data-stu-id="6c7ee-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="6c7ee-149">Wyświetla określone polecenie.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="6c7ee-150">Zamyka tryb interaktywny.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="6c7ee-151">Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="6c7ee-152">Wyświetla listę zarządzanych wątków, na których działa program.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="6c7ee-153">Wyświetla informacje o maszynach stanu asynchronicznego na stertie zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="6c7ee-154">Wyświetla szczegółowe informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="6c7ee-155">Wyświetla informacje o strukturze klasy EE pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="6c7ee-156">Wyświetla informacje o delegacie.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="6c7ee-157">Wyświetla informacje o wszystkich domenach aplikacji i wszystkich zestawach należących do domen.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="6c7ee-158">Wyświetla informacje na temat sterty i statystyk zbierania danych bezużytecznych dotyczących obiektów.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="6c7ee-159">Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="6c7ee-160">Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="6c7ee-161">Wyświetla informacje o strukturze MethodDesc pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="6c7ee-162">Wyświetla informacje o strukturze modułu EE pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="6c7ee-163">Wyświetla informacje dotyczące tabeli metod pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="6c7ee-164">Wyświetla informacje o obiekcie pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="6c7ee-165">Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="6c7ee-166">Wyświetla informacje o pamięci procesu używanej przez wewnętrzne struktury danych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="6c7ee-167">Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="6c7ee-168">Wyświetla informacje o odwołaniach (lub elementach głównych) do obiektu pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="6c7ee-169">Wyświetla lokalizację w stercie GC argumentu przekazano.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="6c7ee-170">Wyświetla strukturę MethodDesc o określonym adresie w kodzie JIT.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="6c7ee-171">Zwalnia wszystkie zasoby używane przez rodzinę poleceń `hist*`.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="6c7ee-172">Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="6c7ee-173">Wyświetla przemieszczenie dzienników obciążeniowych wyrzucania elementów bezużytecznych związanych z `<arguments>`.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="6c7ee-174">Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="6c7ee-175">Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="6c7ee-176">Wyświetla moduły macierzyste w procesie.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="6c7ee-177">Wyświetla strukturę metody i strukturę EEClass dla `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="6c7ee-178">Wyświetla dowolny obiekt pochodny klasy Exception pod adresem `<argument>`.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="6c7ee-179">Włącza obsługę serwera symboli</span><span class="sxs-lookup"><span data-stu-id="6c7ee-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="6c7ee-180">Wyświetla informacje o posiadaczu SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="6c7ee-181">Ustawia lub wyświetla bieżący identyfikator wątku dla poleceń SOS.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="6c7ee-182">Używanie `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="6c7ee-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="6c7ee-183">Pierwszym krokiem jest zebranie zrzutu.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-183">The first step is to collect a dump.</span></span> <span data-ttu-id="6c7ee-184">Ten krok można pominąć, jeśli zrzut podstawowy został już wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="6c7ee-185">System operacyjny lub wbudowana [Funkcja generowania zrzutów](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) środowiska uruchomieniowego platformy .NET Core może tworzyć zrzuty rdzeni.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="6c7ee-186">Teraz Analizuj podstawowy zrzut przy użyciu polecenia `analyze`:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="6c7ee-187">Ta akcja wywołuje interaktywną sesję, która akceptuje polecenia takie jak:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-187">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="6c7ee-188">Aby wyświetlić nieobsłużony wyjątek, który zabicia aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-188">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="6c7ee-189">Specjalne instrukcje dotyczące platformy Docker</span><span class="sxs-lookup"><span data-stu-id="6c7ee-189">Special instructions for Docker</span></span>

<span data-ttu-id="6c7ee-190">Jeśli używasz programu Docker, Zbieranie zrzutów wymaga możliwości `SYS_PTRACE` (`--cap-add=SYS_PTRACE` lub `--privileged`).</span><span class="sxs-lookup"><span data-stu-id="6c7ee-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="6c7ee-191">W przypadku obrazów platformy Docker w systemie Microsoft .NET Core SDK Linux niektóre polecenia `dotnet-dump` mogą zgłosić następujący wyjątek:</span><span class="sxs-lookup"><span data-stu-id="6c7ee-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="6c7ee-192">Nieobsługiwany wyjątek: System. DllNotFoundException —: nie można załadować biblioteki udostępnionej "libdl.so" ani jednego z jej wyjątków zależności.</span><span class="sxs-lookup"><span data-stu-id="6c7ee-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="6c7ee-193">Aby obejść ten problem, zainstaluj pakiet "libc6-dev".</span><span class="sxs-lookup"><span data-stu-id="6c7ee-193">To work around this problem, install the "libc6-dev" package.</span></span>
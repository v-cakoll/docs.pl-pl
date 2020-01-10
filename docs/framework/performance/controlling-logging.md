---
title: Kontrolowanie logowania w programie .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: 180cce516a1209711430429a46cb5b718b29f1d9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716111"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="259df-102">Kontrolowanie logowania w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="259df-102">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="259df-103">Śledzenia zdarzeń systemu Windows (ETW) można użyć do rejestrowania zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="259df-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="259df-104">Można tworzyć i przeglądać ślady za pomocą następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="259df-104">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="259df-105">Narzędzia wiersza polecenia [logman](/windows-server/administration/windows-commands/logman) i [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) dołączone do systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="259df-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="259df-106">Narzędzia [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) w zestawie narzędzi [wydajności systemu Windows](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="259df-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="259df-107">Aby uzyskać więcej informacji na temat Xperf, zobacz [blog wydajności systemu Windows](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span><span class="sxs-lookup"><span data-stu-id="259df-107">For more information about Xperf, see the [Windows Performance blog](https://blogs.msdn.microsoft.com/pigscanfly/tag/xperf/).</span></span>

<span data-ttu-id="259df-108">Aby można było przechwytywać informacje o zdarzeniu CLR, dostawca CLR musi być zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="259df-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="259df-109">Aby upewnić się, że dostawca jest zainstalowany, wpisz `logman query providers` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="259df-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="259df-110">Zostanie wyświetlona lista dostawców.</span><span class="sxs-lookup"><span data-stu-id="259df-110">A list of providers is displayed.</span></span> <span data-ttu-id="259df-111">Ta lista powinna zawierać następujący wpis dla dostawcy CLR.</span><span class="sxs-lookup"><span data-stu-id="259df-111">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="259df-112">Jeśli dostawcy CLR nie ma na liście, można go zainstalować w systemie Windows Vista i nowszych systemach operacyjnych przy użyciu narzędzia wiersza polecenia [wevtutil](/windows-server/administration/windows-commands/wevtutil) systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="259df-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="259df-113">Otwórz okno wiersza polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="259df-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="259df-114">Zmień katalog monitów na folder .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4.\<.NET Version > \).</span><span class="sxs-lookup"><span data-stu-id="259df-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="259df-115">Ten folder zawiera plik CLR-ETW.man.</span><span class="sxs-lookup"><span data-stu-id="259df-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="259df-116">W wierszu polecenia wpisz następujące polecenie, aby zainstalować dostawcę CLR:</span><span class="sxs-lookup"><span data-stu-id="259df-116">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="259df-117">Przechwytywanie zdarzeń CLR ETW</span><span class="sxs-lookup"><span data-stu-id="259df-117">Capturing CLR ETW Events</span></span>

<span data-ttu-id="259df-118">Możesz użyć narzędzi wiersza polecenia [logman](/windows-server/administration/windows-commands/logman) i [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) do przechwytywania zdarzeń ETW oraz narzędzi [tracerpt](/windows-server/administration/windows-commands/tracerpt_1) i [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) do dekodowania zdarzeń śledzenia.</span><span class="sxs-lookup"><span data-stu-id="259df-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="259df-119">Aby włączyć rejestrowanie, użytkownik musi określić trzy rzeczy:</span><span class="sxs-lookup"><span data-stu-id="259df-119">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="259df-120">Dostawca do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="259df-120">The provider to communicate to.</span></span>

- <span data-ttu-id="259df-121">64-bitowa liczba, która reprezentuje zestaw słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="259df-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="259df-122">Każde słowo kluczowe reprezentuje zestaw zdarzeń, które dostawca może włączyć.</span><span class="sxs-lookup"><span data-stu-id="259df-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="259df-123">Ta liczba przedstawia połączony zestaw słów kluczowych do włączenia.</span><span class="sxs-lookup"><span data-stu-id="259df-123">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="259df-124">Mała liczba reprezentująca poziom (szczegółowości) rejestrowania.</span><span class="sxs-lookup"><span data-stu-id="259df-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="259df-125">Poziom 1 jest najmniej szczegółowy, a poziom 5 jest najbardziej szczegółowy.</span><span class="sxs-lookup"><span data-stu-id="259df-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="259df-126">Poziom 0 jest domyślny, a jego znaczenie jest specyficzne dla dostawcy.</span><span class="sxs-lookup"><span data-stu-id="259df-126">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="259df-127">Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Logman</span><span class="sxs-lookup"><span data-stu-id="259df-127">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="259df-128">W wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="259df-128">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="259df-129">gdzie:</span><span class="sxs-lookup"><span data-stu-id="259df-129">where:</span></span>

    - <span data-ttu-id="259df-130">`-p` parametr identyfikuje identyfikator GUID dostawcy.</span><span class="sxs-lookup"><span data-stu-id="259df-130">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="259df-131">`0x1CCBD` określa kategorie zdarzeń, które zostaną zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="259df-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="259df-132">`0x5` ustawia poziom rejestrowania (w tym przypadku, verbose (5)).</span><span class="sxs-lookup"><span data-stu-id="259df-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="259df-133">Parametr `-ets` nakazuje programowi logman Wysyłanie poleceń do sesji śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="259df-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="259df-134">`-ct perf` parametr określa, że funkcja `QueryPerformanceCounter` zostanie użyta do rejestrowania sygnatury czasowej dla każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="259df-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="259df-135">Aby zatrzymać rejestrowanie zdarzeń, wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="259df-135">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="259df-136">To polecenie tworzy plik binarny śledzenia o nazwie clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="259df-136">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="259df-137">Aby przechwytywać zdarzenia CLR ETW przy użyciu narzędzia Xperf</span><span class="sxs-lookup"><span data-stu-id="259df-137">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="259df-138">W wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="259df-138">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="259df-139">gdzie GUID jest identyfikatorem GUID dostawcy ETW CLR, a `0x1CCBD:5` śledzi wszystko na poziomie i poniżej poziomu 5 (pełne).</span><span class="sxs-lookup"><span data-stu-id="259df-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="259df-140">Aby zatrzymać śledzenie, wpisz polecenie:</span><span class="sxs-lookup"><span data-stu-id="259df-140">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="259df-141">To polecenie tworzy plik śledzenia o nazwie clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="259df-141">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="259df-142">Wyświetlanie zdarzeń CLR ETW</span><span class="sxs-lookup"><span data-stu-id="259df-142">Viewing CLR ETW Events</span></span>

<span data-ttu-id="259df-143">Aby wyświetlić zdarzenia CLR ETW, należy użyć poleceń wymienionych poniżej.</span><span class="sxs-lookup"><span data-stu-id="259df-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="259df-144">Opis zdarzeń można znaleźć w temacie [zdarzenia ETW środowiska CLR](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="259df-144">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="259df-145">Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Tracerpt</span><span class="sxs-lookup"><span data-stu-id="259df-145">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="259df-146">W wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="259df-146">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="259df-147">To polecenie tworzy dwa pliki: dumpfile.xml i summary.txt.</span><span class="sxs-lookup"><span data-stu-id="259df-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="259df-148">Plik dumpfile.xml zawiera listę wszystkich zdarzeń, a plik summary.txt zawiera podsumowanie wszystkich zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="259df-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="259df-149">Aby wyświetlić zdarzenia CLR ETW przy użyciu narzędzia Xperf</span><span class="sxs-lookup"><span data-stu-id="259df-149">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="259df-150">W wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="259df-150">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="259df-151">To polecenie otwiera podgląd plików Xperf ETL.</span><span class="sxs-lookup"><span data-stu-id="259df-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="259df-152">W tej przeglądarce zdarzenia CLR są wyświetlane w widoku **zdarzenia ogólne** .</span><span class="sxs-lookup"><span data-stu-id="259df-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="259df-153">Aby wyświetlić siatkę danych zdarzeń uporządkowanych według typu, wybierz region czasu w tym widoku, a następnie kliknij prawym przyciskiem myszy i wybierz polecenie **Podsumowanie**.</span><span class="sxs-lookup"><span data-stu-id="259df-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="259df-154">Aby przekonwertować plik etl na plik z wartościami rozdzielanymi przecinkami</span><span class="sxs-lookup"><span data-stu-id="259df-154">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="259df-155">W wierszu polecenia wpisz:</span><span class="sxs-lookup"><span data-stu-id="259df-155">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="259df-156">To polecenie powoduje zrzucenie przez narzędzie XPerf zdarzeń do pliku z wartościami rozdzielanymi przecinkami (CSV), który można wyświetlać.</span><span class="sxs-lookup"><span data-stu-id="259df-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="259df-157">Różne zdarzenia mają różne pola, więc ten plik CSV zawiera więcej niż jeden wiersz nagłówka przed danymi.</span><span class="sxs-lookup"><span data-stu-id="259df-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="259df-158">Pierwsze pole w każdym wierszu jest typem zdarzenia wskazującym, który nagłówek powinien być używany do określenia pozostałych pól.</span><span class="sxs-lookup"><span data-stu-id="259df-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="259df-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="259df-159">See also</span></span>

- [<span data-ttu-id="259df-160">Zestaw narzędzi wydajności systemu Windows</span><span class="sxs-lookup"><span data-stu-id="259df-160">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="259df-161">Zdarzenia ETW w środowisku CLR</span><span class="sxs-lookup"><span data-stu-id="259df-161">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)

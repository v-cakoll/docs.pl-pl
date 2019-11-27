---
title: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: f3fd0ed0388276f1400bf77d0abfb488634a45a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353607"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="4d611-102">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d611-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="4d611-103">Obiekt `My.Application.Log` może zapisywać informacje do kilku odbiorników dzienników.</span><span class="sxs-lookup"><span data-stu-id="4d611-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="4d611-104">Odbiorniki dzienników są konfigurowane przez plik konfiguracji komputera i mogą zostać zastąpione przez plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d611-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="4d611-105">W tym temacie opisano ustawienia domyślne i sposób określania ustawień aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d611-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="4d611-106">Aby uzyskać więcej informacji na temat domyślnych lokalizacji wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="4d611-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="4d611-107">Aby określić odbiorniki my. Application. log</span><span class="sxs-lookup"><span data-stu-id="4d611-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="4d611-108">Zlokalizuj plik konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="4d611-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="4d611-109">Jeśli tworzysz zestaw, możesz uzyskać dostęp do pliku App. config w programie Visual Studio z **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4d611-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="4d611-110">W przeciwnym razie nazwa pliku konfiguracji jest dołączona do zestawu ". config" i znajduje się w tym samym katalogu, w którym znajduje się zestaw.</span><span class="sxs-lookup"><span data-stu-id="4d611-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4d611-111">Nie każdy zestaw ma plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="4d611-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="4d611-112">Plik konfiguracji jest plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="4d611-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="4d611-113">Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" znajdującym się w sekcji `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="4d611-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="4d611-114">Sekcja `<sources>` znajduje się w sekcji `<system.diagnostics>` w sekcji `<configuration>` najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4d611-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="4d611-115">Jeśli te sekcje nie istnieją, plik konfiguracji komputera może skonfigurować odbiorniki dziennika `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="4d611-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="4d611-116">W poniższych krokach opisano sposób określania konfiguracji komputera:</span><span class="sxs-lookup"><span data-stu-id="4d611-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="4d611-117">Zlokalizuj plik Machine. config komputera.</span><span class="sxs-lookup"><span data-stu-id="4d611-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="4d611-118">Zazwyczaj znajduje się on w katalogu *systemroot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , gdzie `SystemRoot` jest katalogiem systemu operacyjnego, a `frameworkVersion` to wersja .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4d611-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="4d611-119">Ustawienia w pliku Machine. config mogą zostać zastąpione przez plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4d611-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="4d611-120">Jeśli opcjonalne elementy wymienione poniżej nie istnieją, można je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="4d611-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="4d611-121">Znajdź sekcję `<listeners>` w sekcji `<source>` z atrybutem `name` "DefaultSource" w sekcji `<sources>`, w sekcji `<system.diagnostics>`, na liście `<configuration>` najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4d611-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="4d611-122">Jeśli te sekcje nie istnieją, `My.Application.Log` ma tylko domyślne odbiorniki dzienników.</span><span class="sxs-lookup"><span data-stu-id="4d611-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="4d611-123">Znajdź <`add>` elementy w sekcji <`listeners>`.</span><span class="sxs-lookup"><span data-stu-id="4d611-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="4d611-124">Te elementy Dodaj nazwane odbiorniki dzienników do `My.Application.Log` źródło.</span><span class="sxs-lookup"><span data-stu-id="4d611-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="4d611-125">Znajdź `<add>` elementy z nazwami odbiorników dziennika w sekcji `<sharedListeners>`, w sekcji `<system.diagnostics>`, w sekcji `<configuration>` najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4d611-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="4d611-126">W przypadku wielu typów udostępnionych odbiorników dane inicjujące odbiornika zawierają opis, gdzie odbiornik kieruje dane:</span><span class="sxs-lookup"><span data-stu-id="4d611-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="4d611-127">Odbiornik <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> zapisuje dane w dzienniku plików zgodnie z opisem we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="4d611-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="4d611-128">Odbiornik <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> zapisuje informacje w dzienniku zdarzeń komputera określonym przez parametr `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4d611-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="4d611-129">Aby wyświetlić dziennik zdarzeń, można użyć **Eksplorator serwera** lub **Podgląd zdarzeń systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="4d611-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="4d611-130">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="4d611-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="4d611-131">Odbiorniki <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisują do pliku określonego w parametrze `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="4d611-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="4d611-132">Odbiornik <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> zapisuje dane w konsoli wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4d611-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="4d611-133">Aby uzyskać informacje o tym, gdzie inne typy odbiorników dzienników zapisują informacje, zapoznaj się z dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="4d611-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d611-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d611-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="4d611-135">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="4d611-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="4d611-136">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="4d611-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="4d611-137">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="4d611-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="4d611-138">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="4d611-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="4d611-139">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4d611-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="4d611-140">Rozwiązywanie problemów: odbiorcy dzienników</span><span class="sxs-lookup"><span data-stu-id="4d611-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

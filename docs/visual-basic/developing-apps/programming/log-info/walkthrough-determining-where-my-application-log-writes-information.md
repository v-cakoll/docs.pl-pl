---
title: Ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, output location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: 895c49fb1fde56a1c9bf8b3a0ecf9de4f29f9972
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591214"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="ebdea-102">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebdea-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="ebdea-103">`My.Application.Log` Obiektu można zapisać informacji do kilku odbiorniki logu.</span><span class="sxs-lookup"><span data-stu-id="ebdea-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="ebdea-104">Odbiorniki logu są konfigurowane przez plik konfiguracji komputera i może zostać przesłonięta przez plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="ebdea-105">W tym temacie opisano domyślne ustawienia i jak określić ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-105">This topic describes the default settings and how to determine the settings for your application.</span></span>

<span data-ttu-id="ebdea-106">Aby uzyskać więcej informacji na temat domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="ebdea-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="ebdea-107">Aby określić odbiorników dla obiektu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="ebdea-107">To determine the listeners for My.Application.Log</span></span>

1. <span data-ttu-id="ebdea-108">Zlokalizuj plik konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="ebdea-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="ebdea-109">Tworzysz zestawu, można przejść do pliku app.config w programie Visual Studio z **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ebdea-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="ebdea-110">W przeciwnym razie nazwa pliku konfiguracji jest dołączona za pomocą "config" Nazwa zestawu i znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="ebdea-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="ebdea-111">Nie każdy zestaw ma plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-111">Not every assembly has a configuration file.</span></span>

    <span data-ttu-id="ebdea-112">Plik konfiguracji jest plik XML.</span><span class="sxs-lookup"><span data-stu-id="ebdea-112">The configuration file is an XML file.</span></span>

2. <span data-ttu-id="ebdea-113">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajdujący się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="ebdea-114">`<sources>` Sekcji znajduje się w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

    <span data-ttu-id="ebdea-115">Jeśli nie istnieją następujące sekcje, a następnie skonfigurować w pliku konfiguracji komputera `My.Application.Log` dziennika odbiorników.</span><span class="sxs-lookup"><span data-stu-id="ebdea-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="ebdea-116">W poniższych krokach opisano sposób określania definiuje plik konfiguracji komputera:</span><span class="sxs-lookup"><span data-stu-id="ebdea-116">The following steps describe how to determine what the computer configuration file defines:</span></span>

    1. <span data-ttu-id="ebdea-117">Zlokalizuj plik machine.config komputera.</span><span class="sxs-lookup"><span data-stu-id="ebdea-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="ebdea-118">Zazwyczaj znajduje się on w *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* katalogu, gdzie `SystemRoot` to nazwa katalogu systemu operacyjnego i `frameworkVersion` jest wersja programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebdea-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the .NET Framework.</span></span>

        <span data-ttu-id="ebdea-119">Ustawienia w pliku machine.config mogą zostać zastąpione przez plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>

        <span data-ttu-id="ebdea-120">Jeśli nie istnieją opcjonalne elementy wymienione poniżej, można je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="ebdea-120">If the optional elements listed below do not exist, you can create them.</span></span>

    2. <span data-ttu-id="ebdea-121">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

        <span data-ttu-id="ebdea-122">Jeśli te sekcje nie istnieje, a następnie `My.Application.Log` ma odbiorniki logu domyślne.</span><span class="sxs-lookup"><span data-stu-id="ebdea-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>

3. <span data-ttu-id="ebdea-123">Znajdź <`add>` elementów w <`listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>

     <span data-ttu-id="ebdea-124">Te elementy Dodaj odbiorniki logu o nazwie, aby `My.Application.Log` źródła.</span><span class="sxs-lookup"><span data-stu-id="ebdea-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>

4. <span data-ttu-id="ebdea-125">Znajdź `<add>` elementy o nazwach odbiorniki logu w `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="ebdea-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="ebdea-126">Dla wielu typów współdzielonych detektorów dane inicjowania odbiornika zawiera opis gdzie odbiornik kieruje dane:</span><span class="sxs-lookup"><span data-stu-id="ebdea-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>

    - <span data-ttu-id="ebdea-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje do pliku dziennika, jak opisano we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="ebdea-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>

    - <span data-ttu-id="ebdea-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje informacje w dzienniku zdarzeń komputera, które są określone przez `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="ebdea-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="ebdea-129">Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń Windows**.</span><span class="sxs-lookup"><span data-stu-id="ebdea-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="ebdea-130">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="ebdea-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

    - <span data-ttu-id="ebdea-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników zapis do pliku określonego w `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="ebdea-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="ebdea-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika zapisuje konsoli wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="ebdea-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>

    - <span data-ttu-id="ebdea-133">Uzyskać informacji o tym, gdzie innych rodzajów odbiorniki logu wpisać informacje zapoznaj się dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="ebdea-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebdea-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebdea-134">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DelimitedListTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics>
- [<span data-ttu-id="ebdea-135">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="ebdea-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="ebdea-136">Instrukcje: Rejestruje wyjątki</span><span class="sxs-lookup"><span data-stu-id="ebdea-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="ebdea-137">Instrukcje: Zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="ebdea-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="ebdea-138">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="ebdea-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="ebdea-139">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ebdea-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)
- [<span data-ttu-id="ebdea-140">Rozwiązywanie problemów: Odbiorniki logu</span><span class="sxs-lookup"><span data-stu-id="ebdea-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

---
title: Ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
ms.openlocfilehash: fa177fa1f07c52d900f57e5bf61c967f06203c4f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908228"
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="56417-102">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56417-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="56417-103">`My.Application.Log` Obiektu można zapisać informacji do kilku odbiorniki logu.</span><span class="sxs-lookup"><span data-stu-id="56417-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="56417-104">Odbiorniki logu są konfigurowane przez plik konfiguracji komputera i może zostać przesłonięta przez plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56417-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="56417-105">W tym temacie opisano domyślne ustawienia i jak określić ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56417-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="56417-106">Aby uzyskać więcej informacji na temat domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="56417-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="56417-107">Aby określić odbiorników dla obiektu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="56417-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="56417-108">Zlokalizuj plik konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="56417-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="56417-109">Tworzysz zestawu, można przejść do pliku app.config w programie Visual Studio z **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="56417-109">If you are developing the assembly, you can access the app.config in Visual Studio from the **Solution Explorer**.</span></span> <span data-ttu-id="56417-110">W przeciwnym razie nazwa pliku konfiguracji jest dołączona za pomocą "config" Nazwa zestawu i znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="56417-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="56417-111">Nie każdy zestaw ma plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="56417-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="56417-112">Plik konfiguracji jest plik XML.</span><span class="sxs-lookup"><span data-stu-id="56417-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="56417-113">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajdujący się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="56417-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="56417-114">`<sources>` Sekcji znajduje się w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="56417-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="56417-115">Jeśli nie istnieją następujące sekcje, a następnie skonfigurować w pliku konfiguracji komputera `My.Application.Log` dziennika odbiorników.</span><span class="sxs-lookup"><span data-stu-id="56417-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="56417-116">W poniższych krokach opisano sposób określania definiuje plik konfiguracji komputera:</span><span class="sxs-lookup"><span data-stu-id="56417-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="56417-117">Zlokalizuj plik machine.config komputera.</span><span class="sxs-lookup"><span data-stu-id="56417-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="56417-118">Zazwyczaj znajduje się on w *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* katalogu, gdzie `SystemRoot` to nazwa katalogu systemu operacyjnego i `frameworkVersion` jest wersją [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="56417-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="56417-119">Ustawienia w pliku machine.config mogą zostać zastąpione przez plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="56417-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="56417-120">Jeśli nie istnieją opcjonalne elementy wymienione poniżej, można je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="56417-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="56417-121">Znajdź `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="56417-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="56417-122">Jeśli te sekcje nie istnieje, a następnie `My.Application.Log` ma odbiorniki logu domyślne.</span><span class="sxs-lookup"><span data-stu-id="56417-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="56417-123">Znajdź <`add>` elementów w <`listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="56417-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="56417-124">Te elementy Dodaj odbiorniki logu o nazwie, aby `My.Application.Log` źródła.</span><span class="sxs-lookup"><span data-stu-id="56417-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="56417-125">Znajdź `<add>` elementy o nazwach odbiorniki logu w `<sharedListeners>` sekcji w `<system.diagnostics>` sekcji w najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="56417-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="56417-126">Dla wielu typów współdzielonych detektorów dane inicjowania odbiornika zawiera opis gdzie odbiornik kieruje dane:</span><span class="sxs-lookup"><span data-stu-id="56417-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="56417-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje do pliku dziennika, jak opisano we wprowadzeniu.</span><span class="sxs-lookup"><span data-stu-id="56417-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="56417-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje informacje w dzienniku zdarzeń komputera, które są określone przez `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="56417-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="56417-129">Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń Windows**.</span><span class="sxs-lookup"><span data-stu-id="56417-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="56417-130">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="56417-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="56417-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników zapis do pliku określonego w `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="56417-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="56417-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika zapisuje konsoli wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="56417-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="56417-133">Uzyskać informacji o tym, gdzie innych rodzajów odbiorniki logu wpisać informacje zapoznaj się dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="56417-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56417-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56417-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="56417-135">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="56417-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="56417-136">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="56417-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="56417-137">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="56417-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="56417-138">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="56417-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="56417-139">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="56417-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)  
 [<span data-ttu-id="56417-140">Rozwiązywanie problemów: odbiorcy dzienników</span><span class="sxs-lookup"><span data-stu-id="56417-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

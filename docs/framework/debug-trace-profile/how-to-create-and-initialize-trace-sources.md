---
title: 'Porady: tworzenie i inicjowanie źródeł śledzenia'
description: Utwórz i zainicjuj źródła śledzenia przy użyciu klasy TraceSource na platformie .NET. Ta klasa zawiera metody śledzenia zdarzeń i danych oraz wystawiające ślady informacyjne.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: 55d7854bff991ba185d3f5d6e4c6e7222c9e3039
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051275"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="09337-104">Porady: tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="09337-104">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="09337-105"><xref:System.Diagnostics.TraceSource>Klasa jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="09337-105">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="09337-106"><xref:System.Diagnostics.TraceSource>oferuje metody śledzenia, które umożliwiają łatwe śledzenie zdarzeń, danych śledzenia i wystawianie śladów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="09337-106"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="09337-107">Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> można utworzyć i zainicjować przy użyciu plików konfiguracyjnych lub bez nich.</span><span class="sxs-lookup"><span data-stu-id="09337-107">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="09337-108">Ten temat zawiera instrukcje dotyczące obu tych opcji.</span><span class="sxs-lookup"><span data-stu-id="09337-108">This topic provides instructions for both options.</span></span> <span data-ttu-id="09337-109">Zaleca się jednak używanie plików konfiguracji w celu ułatwienia ponownej konfiguracji śladów generowanych przez źródła śledzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="09337-109">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="09337-110">Aby utworzyć i zainicjować Źródło śledzenia przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="09337-110">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="09337-111">Utwórz projekt aplikacji konsolowej programu Visual Studio (.NET Framework) i Zastąp podany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="09337-111">Create a Visual Studio console application project (.NET Framework) and replace the supplied code with the following code.</span></span> <span data-ttu-id="09337-112">Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich do konsoli programu, a niektóre z nich do pliku, który jest tworzony przez wpisy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09337-112">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="09337-113">Dodaj do projektu plik konfiguracji aplikacji, jeśli nie istnieje, w celu zainicjowania źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="09337-113">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="09337-114">Zastąp domyślną zawartość pliku konfiguracji następującymi ustawieniami, aby zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia tekstu składnika zapisywania dla źródła śledzenia, które zostało utworzone w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="09337-114">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <sources>  
          <source name="TraceSourceApp"
            switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch">  
            <listeners>  
              <add name="console"
                type="System.Diagnostics.ConsoleTraceListener">  
                <filter type="System.Diagnostics.EventTypeFilter"
                  initializeData="Error"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Error"/>  
        </switches>  
        <sharedListeners>  
          <add name="myListener"
            type="System.Diagnostics.TextWriterTraceListener"
            initializeData="myListener.log">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
        </sharedListeners>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     <span data-ttu-id="09337-115">Oprócz konfigurowania detektorów śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników i tworzy przełącznik źródła dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="09337-115">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="09337-116">Dwie techniki są pokazane w przypadku dodawania detektorów śledzenia: dodanie odbiornika bezpośrednio do źródła śledzenia i dodanie odbiornika do kolekcji udostępnionych odbiorników, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="09337-116">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="09337-117">Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnymi poziomami źródła.</span><span class="sxs-lookup"><span data-stu-id="09337-117">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="09337-118">Powoduje to, że niektóre komunikaty są zapisywane tylko przez jeden z dwóch odbiorników.</span><span class="sxs-lookup"><span data-stu-id="09337-118">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="09337-119">Plik konfiguracji inicjuje ustawienia dla źródła śledzenia w momencie zainicjowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09337-119">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="09337-120">Aplikacja może dynamicznie zmieniać właściwości ustawiane przez plik konfiguracji w celu zastąpienia wszelkich ustawień określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="09337-120">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="09337-121">Można na przykład upewnić się, że komunikaty krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09337-121">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="09337-122">Przykładowy kod demonstruje sposób przesłania ustawień pliku konfiguracji, aby zapewnić, że krytyczne komunikaty są wyprowadzane do odbiorników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="09337-122">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="09337-123">Zmiana ustawień pliku konfiguracji w trakcie wykonywania aplikacji nie powoduje zmiany ustawień początkowych.</span><span class="sxs-lookup"><span data-stu-id="09337-123">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="09337-124">Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="09337-124">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="09337-125">Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="09337-125">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="09337-126">Użyj następującego przykładowego kodu, aby włączyć śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09337-126">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="09337-127">Nie jest to zalecane rozwiązanie, ale mogą wystąpić sytuacje, w których nie należy zależeć od plików konfiguracji w celu zapewnienia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="09337-127">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="09337-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09337-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="09337-129">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="09337-129">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)

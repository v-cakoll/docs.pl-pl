---
title: 'Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia'
ms.date: 03/30/2017
helpviewer_keywords:
- initializing trace listeners
- configuration files [.NET Framework], trace listeners
- app.config files, trace listeners
- levels of writing trace messages
- trace listeners, TraceSource class
- application configuration files, trace listeners
- filters, trace listeners
- TraceSource class, trace listeners
- trace listeners, creating
- trace listeners, filters
- trace listeners, initializing
ms.assetid: 21dc2169-947d-453a-b0e2-3dac3ba0cc9f
ms.openlocfilehash: 7d2b9da72ae0b2a5c60eb90da0b56b45634e6e05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181815"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="cfc82-102">Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfc82-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="cfc82-103">Jedną z nowych funkcji w .NET Framework w wersji 2.0 jest ulepszony system śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="cfc82-104">Podstawowe założenie pozostaje niezmienione: komunikaty śledzenia są wysyłane za pośrednictwem przełączników do odbiorników, które zgłaszają dane do skojarzonego nośnika wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="cfc82-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="cfc82-105">Podstawową różnicą dla wersji 2.0 jest to, że <xref:System.Diagnostics.TraceSource> ślady mogą być inicjowane za pośrednictwem wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="cfc82-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="cfc82-106"><xref:System.Diagnostics.TraceSource>jest przeznaczony do działania jako ulepszony system śledzenia i może być stosowany <xref:System.Diagnostics.Trace> zamiast <xref:System.Diagnostics.Debug> metod statycznych starszych i klas śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="cfc82-107">Znane <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieją, ale zalecaną <xref:System.Diagnostics.TraceSource> praktyką jest użycie klasy do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="cfc82-108">W tym temacie opisano <xref:System.Diagnostics.TraceSource> użycie pliku konfiguracji aplikacji w połączeniu z plikiem.</span><span class="sxs-lookup"><span data-stu-id="cfc82-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="cfc82-109">Jest możliwe, choć nie zalecane, <xref:System.Diagnostics.TraceSource> do śledzenia przy użyciu bez użycia pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="cfc82-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="cfc82-110">Aby uzyskać informacje na temat śledzenia bez pliku konfiguracyjnego, zobacz [Jak: Tworzenie i inicjowanie źródeł śledzenia](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="cfc82-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="cfc82-111">Aby utworzyć i zainicjować źródło śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfc82-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="cfc82-112">Pierwszym krokiem do instrumentowania aplikacji z śledzenia jest utworzenie źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="cfc82-113">W dużych projektach z różnymi składnikami można utworzyć oddzielne źródło śledzenia dla każdego składnika.</span><span class="sxs-lookup"><span data-stu-id="cfc82-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="cfc82-114">Zalecaną praktyką jest użycie nazwy aplikacji dla nazwy źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="cfc82-115">Ułatwi to oddzielanie różnych śladów.</span><span class="sxs-lookup"><span data-stu-id="cfc82-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="cfc82-116">Poniższy kod tworzy nowe`mySource)` źródło śledzenia (`Activity1`i wywołuje metodę ( ), która śledzi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="cfc82-117">Komunikaty śledzenia są zapisywane przez domyślny odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-117">The trace messages are written by the default trace listener.</span></span>  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
        }  
    }  
    ```  
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="cfc82-118">Aby utworzyć i zainicjować detektory śledzenia i filtry</span><span class="sxs-lookup"><span data-stu-id="cfc82-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="cfc82-119">Kod w pierwszej procedurze nie programowo zidentyfikować żadnych detektorów śledzenia lub filtrów.</span><span class="sxs-lookup"><span data-stu-id="cfc82-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="cfc82-120">Sam kod powoduje, że komunikaty śledzenia są zapisywane do domyślnego odbiornika śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="cfc82-121">Aby skonfigurować określone detektory śledzenia i skojarzone z nimi filtry, należy edytować plik konfiguracyjny odpowiadający nazwie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfc82-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="cfc82-122">W tym pliku można dodać lub usunąć odbiornika, ustawić właściwości i filtr dla odbiornika lub usunąć odbiorniki.</span><span class="sxs-lookup"><span data-stu-id="cfc82-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="cfc82-123">W poniższym przykładzie pliku konfiguracji pokazano, jak zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia, który jest tworzony w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="cfc82-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="cfc82-124">Oprócz konfigurowania odbiorników śledzenia plik konfiguracyjny tworzy filtry dla obu odbiorników i tworzy przełącznik źródłowy dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="cfc82-125">Dwie techniki są wyświetlane do dodawania detektorów śledzenia: dodawanie odbiornika bezpośrednio do źródła śledzenia i dodawanie odbiornika do kolekcji odbiorników udostępnionych, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="cfc82-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="cfc82-126">Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnych poziomów źródła.</span><span class="sxs-lookup"><span data-stu-id="cfc82-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="cfc82-127">Powoduje to, że niektóre wiadomości są zapisywane przez tylko jednego z dwóch odbiorników.</span><span class="sxs-lookup"><span data-stu-id="cfc82-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
                  initializeData="Warning"/>  
              </add>  
              <add name="myListener"/>  
              <remove name="Default"/>  
            </listeners>  
          </source>  
        </sources>  
        <switches>  
          <add name="sourceSwitch" value="Warning"/>  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="cfc82-128">Aby zmienić poziom, na którym odbiornik zapisuje komunikat śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfc82-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="cfc82-129">Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w momencie zainicjowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cfc82-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="cfc82-130">Aby zmienić te ustawienia, należy zmienić plik konfiguracyjny i <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu tej metody.</span><span class="sxs-lookup"><span data-stu-id="cfc82-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cfc82-131">Aplikacja może dynamicznie zmieniać właściwości ustawione przez plik konfiguracyjny, aby zastąpić wszystkie ustawienia określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cfc82-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="cfc82-132">Na przykład można zapewnić, że wiadomości krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cfc82-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
    ```csharp
    using System;  
    using System.Diagnostics;  
    using System.Threading;  
  
    namespace TraceSourceApp  
    {  
        class Program  
        {  
            private static TraceSource mySource =
                new TraceSource("TraceSourceApp");  
            static void Main(string[] args)  
            {  
                Activity1();  
  
                // Change the event type for which tracing occurs.  
                // The console trace listener must be specified
                // in the configuration file. First, save the original  
                // settings from the configuration file.  
                EventTypeFilter configFilter =
                    (EventTypeFilter)mySource.Listeners["console"].Filter;  
  
                // Then create a new event type filter that ensures
                // critical messages will be written.  
                mySource.Listeners["console"].Filter =  
                    new EventTypeFilter(SourceLevels.Critical);  
                Activity2();  
  
                // Allow the trace source to send messages to listeners
                // for all event types. This statement will override
                // any settings in the configuration file.  
                mySource.Switch.Level = SourceLevels.All;  
  
                // Restore the original filter settings.  
                mySource.Listeners["console"].Filter = configFilter;  
                Activity3();  
                mySource.Close();  
                return;  
            }  
            static void Activity1()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 1,
                    "Error message.");  
                mySource.TraceEvent(TraceEventType.Warning, 2,
                    "Warning message.");  
            }  
            static void Activity2()  
            {  
                mySource.TraceEvent(TraceEventType.Critical, 3,
                    "Critical message.");  
                mySource.TraceInformation("Informational message.");  
            }  
            static void Activity3()  
            {  
                mySource.TraceEvent(TraceEventType.Error, 4,
                    "Error message.");  
                mySource.TraceInformation("Informational message.");  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="cfc82-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cfc82-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="cfc82-134">Instrukcje: Tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfc82-134">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="cfc82-135">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="cfc82-135">Trace Listeners</span></span>](trace-listeners.md)

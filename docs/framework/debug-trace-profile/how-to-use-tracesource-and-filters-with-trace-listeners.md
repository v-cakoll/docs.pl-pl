---
title: 'Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6805385ec21deb8748354647ab0f09b3a51353fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338582"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="3d4f0-102">Instrukcje: Użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia</span><span class="sxs-lookup"><span data-stu-id="3d4f0-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="3d4f0-103">Jedną z nowych funkcji programu .NET Framework w wersji 2.0 to system rozszerzone śledzenie.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="3d4f0-104">Podstawowe założenia pozostaje niezmieniony: komunikaty śledzenia są wysyłane za pośrednictwem przełączników do odbiorników, które wysyłają raporty danych średni skojarzone dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="3d4f0-105">Główną różnicą w wersji 2.0 to, że ślady mogą być inicjowane za pośrednictwem wystąpień <xref:System.Diagnostics.TraceSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="3d4f0-106"><xref:System.Diagnostics.TraceSource> jest przeznaczony do działania jako system rozszerzone śledzenie i mogą być używane zamiast metod statycznych starszej wersji <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="3d4f0-107">Znanej <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieje, ale zalecaną praktyką jest użycie <xref:System.Diagnostics.TraceSource> klasy do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="3d4f0-108">W tym temacie opisano korzystanie z <xref:System.Diagnostics.TraceSource> połączone z pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="3d4f0-109">Jest to możliwe, chociaż nie jest to zalecane, do śledzenia przy użyciu <xref:System.Diagnostics.TraceSource> bez użycia pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="3d4f0-110">Aby uzyskać informacji na temat śledzenia bez pliku konfiguracji, zobacz [jak: Tworzenie i Inicjowanie źródeł śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="3d4f0-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="3d4f0-111">Aby utworzyć i zainicjować źródła śledzenia</span><span class="sxs-lookup"><span data-stu-id="3d4f0-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="3d4f0-112">Pierwszym krokiem do instrumentacji aplikacji z włączonym śledzeniem jest utworzyć źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="3d4f0-113">W dużych projektów z różnych składników można utworzyć źródła śledzenia osobne dla każdego składnika.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="3d4f0-114">Zaleca się użycie nazwy aplikacji dla nazwy źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="3d4f0-115">Ułatwi do zachowania ich odrębności różnych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="3d4f0-116">Poniższy kod tworzy nowe źródło śledzenia (`mySource)` i wywołuje metodę (`Activity1`) zapisująca zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="3d4f0-117">Komunikaty śledzenia są zapisywane przez odbiornik śledzenia domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="3d4f0-118">Aby utworzyć i zainicjować odbiorniki śledzenia i filtry</span><span class="sxs-lookup"><span data-stu-id="3d4f0-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="3d4f0-119">Kod w pierwszej procedurze nie programowo zidentyfikować wszystkie obiekty nasłuchujące śledzenia lub filtrów.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="3d4f0-120">Kod samodzielnie powoduje komunikaty śledzenia zapisywana odbiornik śledzenia domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="3d4f0-121">Aby skonfigurować detektorów śledzenia określonych i ich skojarzone filtry, Edytuj plik konfiguracyjny, który odpowiada nazwie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="3d4f0-122">W tym pliku możesz dodać lub usunąć odbiornik, ustawianie właściwości i filtr dla odbiornika lub usunąć odbiorników.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="3d4f0-123">W poniższym przykładzie plik konfiguracji pokazuje, jak zainicjować detektor śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia utworzonego w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="3d4f0-124">Poza skonfigurowaniem detektorów śledzenia, plik konfiguracyjny tworzy filtry dla obu detektorów oraz tworzy przełącznik źródła dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="3d4f0-125">Do dodawania detektorów śledzenia pokazano dwie techniki: dodanie detektora bezpośrednio do źródła śledzenia i dodanie detektora do kolekcji współdzielonych detektorów, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="3d4f0-126">Filtry określone dla obu detektorów są inicjowane z różnymi poziomami źródła.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="3d4f0-127">Skutkuje to pewne komunikaty są zapisywane przez tylko jeden z dwóch detektorów.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="3d4f0-128">Aby zmienić poziom, jaką odbiornik zapisuje komunikat śledzenia</span><span class="sxs-lookup"><span data-stu-id="3d4f0-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="3d4f0-129">Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w czasie, w których aplikacja została zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="3d4f0-130">Się zmiany tych ustawień należy zmienić plik konfiguracji i ponownie uruchom aplikację lub programowo odświeżyć aplikacji przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d4f0-131">Aplikacja można dynamicznie zmieniać właściwości ustawione w pliku konfiguracyjnym, aby zastąpić wszelkie ustawienia określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="3d4f0-132">Na przykład możesz chcieć zapewnić, komunikatów krytycznych, są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3d4f0-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d4f0-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d4f0-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="3d4f0-134">Instrukcje: Tworzenie i Inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="3d4f0-134">How to: Create and Initialize Trace Sources</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="3d4f0-135">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="3d4f0-135">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)

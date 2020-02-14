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
ms.openlocfilehash: 53cdce767d437c47aab94e883381954f8cf70653
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215923"
---
# <a name="how-to-use-tracesource-and-filters-with-trace-listeners"></a><span data-ttu-id="bfb6f-102">Porady: użycie TraceSource i filtrów z obiektami nasłuchującymi śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfb6f-102">How to: Use TraceSource and Filters with Trace Listeners</span></span>
<span data-ttu-id="bfb6f-103">Jedną z nowych funkcji w .NET Framework wersja 2,0 to udoskonalony system śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-103">One of the new features in the .NET Framework version 2.0 is an enhanced tracing system.</span></span> <span data-ttu-id="bfb6f-104">Podstawowa lokalna jest niezmieniona: komunikaty śledzenia są wysyłane przez przełączniki do odbiorników, które raportują dane na skojarzonym nośniku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-104">The basic premise is unchanged: tracing messages are sent through switches to listeners, which report the data to an associated output medium.</span></span> <span data-ttu-id="bfb6f-105">Podstawową różnicą w wersji 2,0 jest to, że ślady mogą być inicjowane za pomocą wystąpień klasy <xref:System.Diagnostics.TraceSource>.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-105">A primary difference for version 2.0 is that traces can be initiated through instances of the <xref:System.Diagnostics.TraceSource> class.</span></span> <span data-ttu-id="bfb6f-106"><xref:System.Diagnostics.TraceSource> jest przeznaczony do działania jako udoskonalony system śledzenia i może służyć zamiast metod statycznych starszych <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug>ych klas śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-106"><xref:System.Diagnostics.TraceSource> is intended to function as an enhanced tracing system and can be used in place of the static methods of the older <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> tracing classes.</span></span> <span data-ttu-id="bfb6f-107">Znane <xref:System.Diagnostics.Trace> i <xref:System.Diagnostics.Debug> klasy nadal istnieją, ale zalecanym sposobem jest użycie klasy <xref:System.Diagnostics.TraceSource> do śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-107">The familiar <xref:System.Diagnostics.Trace> and <xref:System.Diagnostics.Debug> classes still exist, but the recommended practice is to use the <xref:System.Diagnostics.TraceSource> class for tracing.</span></span>  
  
 <span data-ttu-id="bfb6f-108">W tym temacie opisano sposób użycia <xref:System.Diagnostics.TraceSource> połączonego z plikiem konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-108">This topic describes the use of a <xref:System.Diagnostics.TraceSource> coupled with an application configuration file.</span></span>  <span data-ttu-id="bfb6f-109">Jest to możliwe, chociaż nie jest to zalecane, do śledzenia przy użyciu <xref:System.Diagnostics.TraceSource> bez użycia pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-109">It is possible, although not recommended, to trace using a <xref:System.Diagnostics.TraceSource> without the use of a configuration file.</span></span> <span data-ttu-id="bfb6f-110">Informacje dotyczące śledzenia bez pliku konfiguracji znajdują się w temacie [How to: Create and Initialize Source TRACES](how-to-create-and-initialize-trace-sources.md).</span><span class="sxs-lookup"><span data-stu-id="bfb6f-110">For information on tracing without a configuration file, see [How to: Create and Initialize Trace Sources](how-to-create-and-initialize-trace-sources.md).</span></span>  
  
### <a name="to-create-and-initialize-your-trace-source"></a><span data-ttu-id="bfb6f-111">Aby utworzyć i zainicjować Źródło śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfb6f-111">To create and initialize your trace source</span></span>  
  
1. <span data-ttu-id="bfb6f-112">Pierwszym krokiem do Instrumentacji aplikacji przy użyciu funkcji śledzenia jest utworzenie źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-112">The first step to instrumenting an application with tracing is to create a trace source.</span></span> <span data-ttu-id="bfb6f-113">W dużych projektach z różnymi składnikami można utworzyć oddzielne źródło śledzenia dla każdego składnika.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-113">In large projects with various components, you can create a separate trace source for each component.</span></span> <span data-ttu-id="bfb6f-114">Zalecanym sposobem jest użycie nazwy aplikacji dla nazwy źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-114">The recommended practice is to use the application name for the trace source name.</span></span> <span data-ttu-id="bfb6f-115">Ułatwi to zachowanie różnych śladów.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-115">This will make it easier to keep the different traces separate.</span></span> <span data-ttu-id="bfb6f-116">Poniższy kod tworzy nowe źródło śledzenia (`mySource)` i wywołuje metodę (`Activity1`), która śledzi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-116">The following code creates a new trace source (`mySource)` and calls a method (`Activity1`) that traces events.</span></span>  <span data-ttu-id="bfb6f-117">Komunikaty śledzenia są zapisywane przez domyślny odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-117">The trace messages are written by the default trace listener.</span></span>  
  
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
  
### <a name="to-create-and-initialize-trace-listeners-and-filters"></a><span data-ttu-id="bfb6f-118">Aby tworzyć i inicjować detektory i filtry śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfb6f-118">To create and initialize trace listeners and filters</span></span>  
  
1. <span data-ttu-id="bfb6f-119">Kod w pierwszej procedurze nie identyfikuje programowo żadnych detektorów ani filtrów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-119">The code in the first procedure does not programmatically identify any trace listeners or filters.</span></span> <span data-ttu-id="bfb6f-120">Sam kod skutkuje zapisaniem komunikatów śledzenia w domyślnym odbiorniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-120">The code alone results in the trace messages being written to the default trace listener.</span></span> <span data-ttu-id="bfb6f-121">Aby skonfigurować określone detektory śledzenia i powiązane z nimi filtry, należy edytować plik konfiguracji, który odnosi się do nazwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-121">To configure specific trace listeners and their associated filters, edit the configuration file that corresponds to the name of your application.</span></span> <span data-ttu-id="bfb6f-122">W tym pliku można dodać lub usunąć odbiornik, ustawić właściwości i filtr dla odbiornika lub usunąć detektory.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-122">In this file, you can add or remove a listener, set the properties and filter for a listener, or remove listeners.</span></span> <span data-ttu-id="bfb6f-123">Poniższy przykład pliku konfiguracji pokazuje, jak zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia tekstu składnika zapisywania dla źródła śledzenia, które zostało utworzone w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-123">The following configuration file example shows how to initialize a console trace listener and a text writer trace listener for the trace source that is created in the preceding procedure.</span></span> <span data-ttu-id="bfb6f-124">Oprócz konfigurowania detektorów śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników i tworzy przełącznik źródła dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-124">In addition to configuring the trace listeners, the configuration file creates filters for both of the listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="bfb6f-125">Dwie techniki są pokazane w przypadku dodawania detektorów śledzenia: dodanie odbiornika bezpośrednio do źródła śledzenia i dodanie odbiornika do kolekcji udostępnionych odbiorników, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-125">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="bfb6f-126">Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnymi poziomami źródła.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-126">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="bfb6f-127">Powoduje to, że niektóre komunikaty są zapisywane tylko przez jeden z dwóch odbiorników.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-127">This results in some messages being written by only one of the two listeners.</span></span>  
  
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
  
### <a name="to-change-the-level-at-which-a-listener-writes-a-trace-message"></a><span data-ttu-id="bfb6f-128">Aby zmienić poziom, na którym odbiornik zapisuje komunikat śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfb6f-128">To change the level at which a listener writes a trace message</span></span>  
  
1. <span data-ttu-id="bfb6f-129">Plik konfiguracji inicjuje ustawienia dla źródła śledzenia w momencie zainicjowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-129">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="bfb6f-130">Aby zmienić te ustawienia, należy zmienić plik konfiguracji i ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu metody <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-130">To change those settings you must change the configuration file and restart the application or programmatically refresh the application using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bfb6f-131">Aplikacja może dynamicznie zmieniać właściwości ustawiane przez plik konfiguracji w celu zastąpienia wszelkich ustawień określonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-131">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span>  <span data-ttu-id="bfb6f-132">Na przykład możesz chcieć zapewnić, że komunikaty krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bfb6f-132">For example, you might want to assure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfb6f-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfb6f-133">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="bfb6f-134">Instrukcje: Tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfb6f-134">How to: Create and Initialize Trace Sources</span></span>](how-to-create-and-initialize-trace-sources.md)
- [<span data-ttu-id="bfb6f-135">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="bfb6f-135">Trace Listeners</span></span>](trace-listeners.md)

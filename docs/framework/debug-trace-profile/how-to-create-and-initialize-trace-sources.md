---
title: 'Instrukcje: Tworzenie i inicjowanie źródeł śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d96de43d258e4a7ff925e0c5b1702727e67d737
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754521"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="840f0-102">Instrukcje: Tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="840f0-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="840f0-103"><xref:System.Diagnostics.TraceSource> Klasa jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="840f0-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="840f0-104"><xref:System.Diagnostics.TraceSource> udostępnia metody śledzenia, które pozwalają na łatwe śledzenie zdarzeń, dane śledzenia i ślady informacyjne problemu.</span><span class="sxs-lookup"><span data-stu-id="840f0-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="840f0-105">Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> mogą być tworzone i inicjowane z użyciem lub bez korzystania z plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="840f0-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="840f0-106">Ten temat zawiera instrukcje dla obu opcji.</span><span class="sxs-lookup"><span data-stu-id="840f0-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="840f0-107">Jednak zaleca się używać plików konfiguracyjnych ułatwiających rekonfigurację śladów produkowanych przez źródła śledzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="840f0-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="840f0-108">Aby utworzyć i zainicjować źródło śledzenia przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="840f0-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="840f0-109">Utwórz projekt aplikacji konsoli Visual Studio i Zastąp dostarczony kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="840f0-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="840f0-110">Ten kod rejestruje błędy i ostrzeżenia i wysyła niektóre z nich do konsoli, a niektóre z nich do pliku myListener, który jest tworzony przez wpisy w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="840f0-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="840f0-111">Dodaj plik konfiguracji aplikacji, jeśli nie został jeszcze dołączony, do projektu, aby zainicjować źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="840f0-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="840f0-112">Zastąp domyślną treść pliku konfiguracji z następującymi ustawieniami, aby zainicjować detektor śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia, który został utworzony w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="840f0-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="840f0-113">Poza skonfigurowaniem detektorów śledzenia, plik konfiguracyjny tworzy filtry dla obu detektorów oraz tworzy przełącznik źródła dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="840f0-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="840f0-114">Do dodawania detektorów śledzenia pokazano dwie techniki: dodanie detektora bezpośrednio do źródła śledzenia i dodanie detektora do kolekcji współdzielonych detektorów, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="840f0-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="840f0-115">Filtry określone dla obu detektorów są inicjowane z różnymi poziomami źródła.</span><span class="sxs-lookup"><span data-stu-id="840f0-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="840f0-116">Skutkuje to pewne komunikaty są zapisywane przez tylko jeden z dwóch detektorów.</span><span class="sxs-lookup"><span data-stu-id="840f0-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="840f0-117">Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w czasie, w których aplikacja została zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="840f0-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="840f0-118">Aplikacja można dynamicznie zmieniać właściwości ustawione w pliku konfiguracyjnym, aby zastąpić wszelkie ustawienia określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="840f0-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="840f0-119">Na przykład możesz chcieć upewnij się, że krytyczne wiadomości są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="840f0-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="840f0-120">Przykładowy kod ilustruje sposób zastąpienia ustawień pliku konfiguracji, aby upewnić się, że newralgiczne komunikaty są do odbiorników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="840f0-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="840f0-121">Zmiana ustawień pliku konfiguracji, podczas wykonywania aplikacji nie powoduje zmiany ustawień początkowych.</span><span class="sxs-lookup"><span data-stu-id="840f0-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="840f0-122">Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację za pomocą <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="840f0-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="840f0-123">Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="840f0-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="840f0-124">Użyj poniższy przykład kodu umożliwia śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="840f0-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="840f0-125">Nie jest to zalecana praktyka, ale mogą zaistnieć okoliczności, w których nie chcesz zależało od plików konfiguracyjnych, aby upewnić się, śledzenia.</span><span class="sxs-lookup"><span data-stu-id="840f0-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="840f0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="840f0-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="840f0-127">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="840f0-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

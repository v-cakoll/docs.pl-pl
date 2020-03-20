---
title: 'Porady: tworzenie i inicjowanie źródeł śledzenia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
ms.openlocfilehash: eeccad44bd2719a3cb2a721ba4e32a7bf477636f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174735"
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="714ee-102">Porady: tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="714ee-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="714ee-103">Klasa <xref:System.Diagnostics.TraceSource> jest używana przez aplikacje do tworzenia śladów, które mogą być skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="714ee-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="714ee-104"><xref:System.Diagnostics.TraceSource>zawiera metody śledzenia, które umożliwiają łatwe śledzenie zdarzeń, śledzenie danych i wykrywanie śladów informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="714ee-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="714ee-105">Dane wyjściowe śledzenia z <xref:System.Diagnostics.TraceSource> mogą być tworzone i inicjowane z lub bez użycia plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="714ee-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="714ee-106">Ten temat zawiera instrukcje dla obu opcji.</span><span class="sxs-lookup"><span data-stu-id="714ee-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="714ee-107">Jednak zaleca się użycie plików konfiguracyjnych w celu ułatwienia ponownej konfiguracji śladów wytwarzanych przez źródła śledzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="714ee-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="714ee-108">Aby utworzyć i zainicjować źródło śledzenia przy użyciu pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="714ee-108">To create and initialize a trace source using a configuration file</span></span>  
  
1. <span data-ttu-id="714ee-109">Utwórz projekt aplikacji konsoli programu Visual Studio (.NET Framework) i zastąp dostarczony kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="714ee-109">Create a Visual Studio console application project (.NET Framework) and replace the supplied code with the following code.</span></span> <span data-ttu-id="714ee-110">Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich do konsoli, a niektóre z nich do pliku myListener, który jest tworzony przez wpisy w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="714ee-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2. <span data-ttu-id="714ee-111">Dodaj plik konfiguracji aplikacji, jeśli nie ma, do projektu, aby `TraceSourceApp` zainicjować źródło śledzenia o nazwie w przykładzie kodu w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="714ee-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3. <span data-ttu-id="714ee-112">Zastąp domyślną zawartość pliku konfiguracji następującymi ustawieniami, aby zainicjować odbiornik śledzenia konsoli i odbiornik śledzenia modułu zapisującego tekst dla źródła śledzenia utworzonego w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="714ee-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="714ee-113">Oprócz konfigurowania odbiorników śledzenia plik konfiguracyjny tworzy filtry dla detektorów i tworzy przełącznik źródłowy dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="714ee-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="714ee-114">Dwie techniki są wyświetlane do dodawania detektorów śledzenia: dodawanie odbiornika bezpośrednio do źródła śledzenia i dodawanie odbiornika do kolekcji odbiorników udostępnionych, a następnie dodanie go według nazwy do źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="714ee-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="714ee-115">Filtry zidentyfikowane dla dwóch odbiorników są inicjowane z różnych poziomów źródła.</span><span class="sxs-lookup"><span data-stu-id="714ee-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="714ee-116">Powoduje to, że niektóre wiadomości są zapisywane przez tylko jednego z dwóch odbiorników.</span><span class="sxs-lookup"><span data-stu-id="714ee-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="714ee-117">Plik konfiguracyjny inicjuje ustawienia źródła śledzenia w momencie zainicjowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="714ee-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="714ee-118">Aplikacja może dynamicznie zmieniać właściwości ustawione przez plik konfiguracyjny, aby zastąpić wszystkie ustawienia określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="714ee-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="714ee-119">Na przykład można upewnić się, że wiadomości krytyczne są zawsze wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="714ee-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="714ee-120">Przykładowy kod pokazuje, jak zastąpić ustawienia pliku konfiguracji, aby upewnić się, że wiadomości krytyczne są dane wyjściowe do detektorów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="714ee-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="714ee-121">Zmiana ustawień pliku konfiguracyjnego podczas wykonywania aplikacji nie powoduje zmiany ustawień początkowych.</span><span class="sxs-lookup"><span data-stu-id="714ee-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="714ee-122">Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżyć aplikację przy użyciu <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="714ee-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="714ee-123">Aby zainicjować źródła śledzenia, detektory i filtry bez pliku konfiguracyjnego</span><span class="sxs-lookup"><span data-stu-id="714ee-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
- <span data-ttu-id="714ee-124">Użyj poniższego przykładu kodu, aby włączyć śledzenie za pośrednictwem źródła śledzenia bez użycia pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="714ee-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="714ee-125">Nie jest to zalecana praktyka, ale mogą wystąpić okoliczności, w których nie chcesz polegać na plikach konfiguracyjnych w celu zapewnienia śledzenia.</span><span class="sxs-lookup"><span data-stu-id="714ee-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="714ee-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="714ee-126">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventTypeFilter>
- [<span data-ttu-id="714ee-127">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="714ee-127">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)

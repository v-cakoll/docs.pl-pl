---
title: "Porady: tworzenie i inicjowanie źródeł śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace sources
- initializing trace sources
- configuration files [.NET Framework], trace sources
ms.assetid: f88dda6f-5fda-45be-9b3c-745a9b708c4d
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1fc1e843bb5841fcd5571bb1b57d6fb449336240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-initialize-trace-sources"></a><span data-ttu-id="d13c3-102">Porady: tworzenie i inicjowanie źródeł śledzenia</span><span class="sxs-lookup"><span data-stu-id="d13c3-102">How to: Create and Initialize Trace Sources</span></span>
<span data-ttu-id="d13c3-103"><xref:System.Diagnostics.TraceSource> Klasa jest używana przez aplikacje do tworzenia śledzenia, które mogą być skojarzone z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="d13c3-103">The <xref:System.Diagnostics.TraceSource> class is used by applications to produce traces that can be associated with the application.</span></span> <span data-ttu-id="d13c3-104"><xref:System.Diagnostics.TraceSource>udostępnia metody śledzenia, które pozwalają łatwo śledzić zdarzenia, dane śledzenia i zapisy informacyjne problem.</span><span class="sxs-lookup"><span data-stu-id="d13c3-104"><xref:System.Diagnostics.TraceSource> provides tracing methods that allow you to easily trace events, trace data, and issue informational traces.</span></span> <span data-ttu-id="d13c3-105">Dane wyjściowe z śledzenia <xref:System.Diagnostics.TraceSource> można tworzyć i zainicjować z lub bez użycia plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="d13c3-105">Trace output from <xref:System.Diagnostics.TraceSource> can be created and initialized with or without the use of configuration files.</span></span> <span data-ttu-id="d13c3-106">Ten temat zawiera instrukcje dla obu opcji.</span><span class="sxs-lookup"><span data-stu-id="d13c3-106">This topic provides instructions for both options.</span></span> <span data-ttu-id="d13c3-107">Jednak zaleca się stosowania plików konfiguracji ułatwia ponowne konfigurowanie śledzenia utworzonego przez źródła śledzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d13c3-107">However, we recommend that you use configuration files to facilitate the reconfiguration of the traces produced by trace sources at run time.</span></span>  
  
### <a name="to-create-and-initialize-a-trace-source-using-a-configuration-file"></a><span data-ttu-id="d13c3-108">Aby utworzyć i zainicjować źródła śledzenia, przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d13c3-108">To create and initialize a trace source using a configuration file</span></span>  
  
1.  <span data-ttu-id="d13c3-109">Utwórz projekt aplikacji konsoli programu Visual Studio i Zastąp podany kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="d13c3-109">Create a Visual Studio console application project and replace the supplied code with the following code.</span></span> <span data-ttu-id="d13c3-110">Ten kod rejestruje błędy i ostrzeżenia i wyprowadza niektóre z nich w konsoli, a niektóre z nich do pliku myListener, który jest tworzony na podstawie pozycji w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d13c3-110">This code logs errors and warnings and outputs some of them to the console, and some of them to the myListener file that is created by the entries in the configuration file.</span></span>  
  
     [!code-csharp[TraceSourceExample1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample1/cs/program.cs#1)]
     [!code-vb[TraceSourceExample1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample1/vb/program.vb#1)]  
  
2.  <span data-ttu-id="d13c3-111">Dodaj plik konfiguracji aplikacji, jeśli nie został już dołączony do projektu, aby zainicjować źródła śledzenia o nazwie `TraceSourceApp` w przykładzie kodu w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="d13c3-111">Add an application configuration file, if one is not present, to the project to initialize the trace source named `TraceSourceApp` in the code example in step 1.</span></span>  
  
3.  <span data-ttu-id="d13c3-112">Zastąp zawartość pliku konfiguracji domyślnej następujących ustawień, aby zainicjować odbiornika śledzenia konsoli i odbiornik śledzenia składnika zapisywania tekstu dla źródła śledzenia, który został utworzony w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="d13c3-112">Replace the default configuration file content with the following settings to initialize a console trace listener and a text writer trace listener for the trace source that was created in step 1.</span></span>  
  
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
  
     <span data-ttu-id="d13c3-113">Oprócz konfigurowania obiektów nasłuchujących śledzenia, plik konfiguracji tworzy filtry dla obu odbiorników oraz przełącznik źródła dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d13c3-113">In addition to configuring the trace listeners, the configuration file creates filters for both listeners and creates a source switch for the trace source.</span></span> <span data-ttu-id="d13c3-114">Przedstawiono dwie metody dodawania obiektów nasłuchujących śledzenia: Dodawanie odbiornika bezpośrednio w źródle śledzenia i dodawanie odbiornik do kolekcji udostępnione obiekty nasłuchujące i dodanie go przez nazwę źródła.</span><span class="sxs-lookup"><span data-stu-id="d13c3-114">Two techniques are shown for adding trace listeners: adding the listener directly to the trace source and adding a listener to the shared listeners collection and then adding it by name to the trace source.</span></span> <span data-ttu-id="d13c3-115">Filtry dla dwa odbiorniki są inicjowane z poziomu innego źródła.</span><span class="sxs-lookup"><span data-stu-id="d13c3-115">The filters identified for the two listeners are initialized with different source levels.</span></span> <span data-ttu-id="d13c3-116">Powoduje to niektóre komunikaty zapisywana przez tylko jeden z dwóch odbiorników.</span><span class="sxs-lookup"><span data-stu-id="d13c3-116">This results in some messages being written by only one of the two listeners.</span></span>  
  
     <span data-ttu-id="d13c3-117">Plik konfiguracji inicjuje ustawienia źródła śledzenia w czasie aplikacji został zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="d13c3-117">The configuration file initializes the settings for the trace source at the time the application is initialized.</span></span> <span data-ttu-id="d13c3-118">Aplikację można dynamicznie zmieniać właściwości ustawione przy użyciu pliku konfiguracji, aby zastąpić wszystkie ustawienia określone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d13c3-118">The application can dynamically change the properties set by the configuration file to override any settings specified by the user.</span></span> <span data-ttu-id="d13c3-119">Na przykład możesz chcieć upewnij się, że krytycznych wiadomości zawsze są wysyłane do pliku tekstowego, niezależnie od bieżących ustawień konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d13c3-119">For example, you might want to ensure that critical messages are always sent to a text file, regardless of the current configuration settings.</span></span> <span data-ttu-id="d13c3-120">Przykładowy kod przedstawia sposób zastępują ustawienia pliku konfiguracji w celu zapewnienia krytycznych wiadomości o dane wyjściowe do obiektów nasłuchujących śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d13c3-120">The example code demonstrates how to override configuration file settings to ensure that critical messages are output to the trace listeners.</span></span>  
  
     <span data-ttu-id="d13c3-121">Zmiana ustawień pliku konfiguracji, gdy aplikacja jest wykonywany nie zmienia ustawienia początkowe.</span><span class="sxs-lookup"><span data-stu-id="d13c3-121">Changing the configuration file settings while the application is executing does not change the initial settings.</span></span> <span data-ttu-id="d13c3-122">Aby zmienić ustawienia, należy ponownie uruchomić aplikację lub programowo odświeżania aplikacji za pomocą <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="d13c3-122">To change the settings, you must either restart the application or programmatically refresh the application by using the <xref:System.Diagnostics.Trace.Refresh%2A?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-initialize-trace-sources-listeners-and-filters-without-a-configuration-file"></a><span data-ttu-id="d13c3-123">Aby zainicjować źródła śledzenia, odbiorników i filtry bez pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d13c3-123">To initialize trace sources, listeners, and filters without a configuration file</span></span>  
  
-   <span data-ttu-id="d13c3-124">Poniższy przykładowy kod umożliwia włączanie śledzenia przez źródło śladu bez użycia pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d13c3-124">Use the following example code to enable tracing through a trace source without using a configuration file.</span></span> <span data-ttu-id="d13c3-125">To nie jest zalecanym rozwiązaniem, ale może być okoliczności, w których nie chcesz zależą od pliki konfiguracji, aby upewnić się, śledzenie.</span><span class="sxs-lookup"><span data-stu-id="d13c3-125">This is not a recommended practice, but there may be circumstances in which you do not want to depend on configuration files to ensure tracing.</span></span>  
  
     [!code-csharp[TraceSourceExample2#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tracesourceexample2/cs/program.cs#1)]
     [!code-vb[TraceSourceExample2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tracesourceexample2/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d13c3-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d13c3-126">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.EventTypeFilter>  
 [<span data-ttu-id="d13c3-127">Śledzenie i Instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="d13c3-127">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

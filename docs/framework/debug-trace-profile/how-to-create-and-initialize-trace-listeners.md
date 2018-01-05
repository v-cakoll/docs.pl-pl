---
title: "Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia"
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
- initializing trace listeners
- trace listeners, creating
- trace listeners, initializing
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 21726de1-61ee-4fdc-9dd0-3be49324d066
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ebc50e4075a5793c344cbc017eb60247c1c8774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="12eeb-102">Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia</span><span class="sxs-lookup"><span data-stu-id="12eeb-102">How to: Create and Initialize Trace Listeners</span></span>
<span data-ttu-id="12eeb-103"><xref:System.Diagnostics.Debug?displayProperty=nameWithType> i <xref:System.Diagnostics.Trace?displayProperty=nameWithType> klasy wysyłania komunikatów do obiektów o nazwie nasłuchujących odbierały i przetwarzały tych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="12eeb-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="12eeb-104">Jeden taki odbiornika <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, jest automatycznie tworzony i inicjowana, gdy jest włączone śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="12eeb-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="12eeb-105">Jeśli chcesz <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.Debug> dane wyjściowe będą kierowane do wszelkich dodatkowych źródeł, należy utworzyć i Inicjowanie obiektów nasłuchujących śledzenia dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="12eeb-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>  
  
 <span data-ttu-id="12eeb-106">Odbiorniki tworzonych powinien odzwierciedlać potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12eeb-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="12eeb-107">Na przykład rekordu tekstu zawierającego wszystkie dane wyjściowe śledzenia, utworzyć <xref:System.Diagnostics.TextWriterTraceListener> odbiornika, który zapisuje wszystkie dane wyjściowe do nowego pliku tekstowego, gdy jest włączone.</span><span class="sxs-lookup"><span data-stu-id="12eeb-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="12eeb-108">Z drugiej strony, jeśli chcesz wyświetlić dane wyjściowe tylko podczas wykonywania aplikacji, Utwórz <xref:System.Diagnostics.ConsoleTraceListener> odbiornika, który określa, że wszystkie dane wyjściowe okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="12eeb-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="12eeb-109"><xref:System.Diagnostics.EventLogTraceListener> Mogą kierować danych wyjściowych śledzenia do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="12eeb-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="12eeb-110">Aby uzyskać więcej informacji, zobacz [obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="12eeb-110">For more information, see [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md).</span></span>  
  
 <span data-ttu-id="12eeb-111">Można tworzyć obiektów nasłuchujących śledzenia w [pliku konfiguracji aplikacji](../../../docs/framework/configure-apps/index.md) lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="12eeb-111">You can create trace listeners in an [application configuration file](../../../docs/framework/configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="12eeb-112">Firma Microsoft zaleca użycie pliki konfiguracji aplikacji, ponieważ umożliwiają dodawanie, modyfikowanie lub usuwanie obiektów nasłuchujących śledzenia bez konieczności zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="12eeb-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>  
  
### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="12eeb-113">Tworzenie i używanie nasłuchującego śledzenia przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="12eeb-113">To create and use a trace listener by using a configuration file</span></span>  
  
1.  <span data-ttu-id="12eeb-114">Deklarowanie Twojej nasłuchującego śledzenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12eeb-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="12eeb-115">Jeśli odbiornik, które tworzysz wymaga inne obiekty, zadeklarować je również.</span><span class="sxs-lookup"><span data-stu-id="12eeb-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="12eeb-116">Poniższy przykład pokazuje, jak utworzyć odbiornik o nazwie `myListener` zapisuje plik tekstowy `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="12eeb-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
        <trace autoflush="false" indentsize="4">  
          <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener" initializeData="TextWriterOutput.log" />  
            <remove name="Default" />  
          </listeners>  
        </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
2.  <span data-ttu-id="12eeb-117">Użyj <xref:System.Diagnostics.Trace> klasy w kodzie do zapisu obiektów nasłuchujących śledzenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="12eeb-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>  
  
    ```vb  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="12eeb-118">Do utworzenia i użycia nasłuchującego śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="12eeb-118">To create and use a trace listener in code</span></span>  
  
-   <span data-ttu-id="12eeb-119">Dodać obiektu nasłuchującego śledzenia do <xref:System.Diagnostics.Trace.Listeners%2A> zbierania i wysyłania informacji do odbiorniki śledzenia.</span><span class="sxs-lookup"><span data-stu-id="12eeb-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>  
  
    ```vb  
    Trace.Listeners.Add(New TextWriterTraceListener("TextWriterOutput.log", "myListener"))  
    Trace.TraceInformation("Test message.")  
    ' You must close or flush the trace to empty the output buffer.  
    Trace.Flush()  
    ```  
  
    ```csharp  
    Trace.Listeners.Add(new TextWriterTraceListener("TextWriterOutput.log", "myListener"));  
    Trace.TraceInformation("Test message.");  
    // You must close or flush the trace to empty the output buffer.  
    Trace.Flush();  
    ```  
  
     - <span data-ttu-id="12eeb-120">lub -</span><span class="sxs-lookup"><span data-stu-id="12eeb-120">or -</span></span>  
  
-   <span data-ttu-id="12eeb-121">Jeśli nie chcesz, aby Twoje odbiornika do odbierania danych wyjściowych śledzenia, nie należy dodawać go do <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="12eeb-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="12eeb-122">Można Emituj danych wyjściowych przez odbiornik niezależnie od <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji, wywołując odbiornika dla własnych danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="12eeb-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="12eeb-123">Poniższy przykład przedstawia sposób zapisania wiersza do odbiornika, który nie znajduje się w <xref:System.Diagnostics.Trace.Listeners%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="12eeb-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>  
  
    ```vb  
    Dim myListener As New TextWriterTraceListener("TextWriterOutput.log", "myListener")  
    myListener.WriteLine("Test message.")  
    ' You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush()  
    ```  
  
    ```csharp  
    TextWriterTraceListener myListener = new TextWriterTraceListener("TextWriterOutput.log", "myListener");  
    myListener.WriteLine("Test message.");  
    // You must close or flush the trace listener to empty the output buffer.  
    myListener.Flush();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="12eeb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12eeb-124">See Also</span></span>  
 [<span data-ttu-id="12eeb-125">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="12eeb-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="12eeb-126">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="12eeb-126">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="12eeb-127">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="12eeb-127">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="12eeb-128">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="12eeb-128">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)

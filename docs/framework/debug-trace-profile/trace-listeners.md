---
title: Obiekty nasłuchujące śledzenia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 35aec3a311680e398d9f2bba94bf4c9a274c8a04
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137907"
---
# <a name="trace-listeners"></a><span data-ttu-id="a8940-102">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="a8940-102">Trace Listeners</span></span>
<span data-ttu-id="a8940-103">Korzystając z **śledzenia**, **debugowania** i <xref:System.Diagnostics.TraceSource>, musi mieć mechanizm do gromadzenia i rejestrowania wiadomości, które są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="a8940-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="a8940-104">Komunikaty śledzenia są odbierane przez *odbiorników*.</span><span class="sxs-lookup"><span data-stu-id="a8940-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="a8940-105">Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy.</span><span class="sxs-lookup"><span data-stu-id="a8940-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="a8940-106">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="a8940-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="a8940-107">Odbiorniki są dostępne dla **debugowania**, **śledzenia**, i <xref:System.Diagnostics.TraceSource> klasy, z których każdy może wysyłać dane wyjściowe do wielu obiektów odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a8940-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="a8940-108">Często używanych wstępnie zdefiniowanych obiektów nasłuchujących są następujące:</span><span class="sxs-lookup"><span data-stu-id="a8940-108">The following are the commonly used predefined listeners:</span></span>  
  
-   <span data-ttu-id="a8940-109">A <xref:System.Diagnostics.TextWriterTraceListener> przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub miejscem <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="a8940-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="a8940-110">Go także zapisać konsoli lub w pliku, ponieważ są one <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="a8940-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
-   <span data-ttu-id="a8940-111"><xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a8940-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
-   <span data-ttu-id="a8940-112">A <xref:System.Diagnostics.DefaultTraceListener> emituje **zapisu** i **WriteLine** komunikatów **OutputDebugString** i **Debugger.Log** metody.</span><span class="sxs-lookup"><span data-stu-id="a8940-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="a8940-113">W programie Visual Studio to powoduje, że komunikaty debugowania pojawią się w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a8940-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="a8940-114">**Się nie powieść** , jak i nieudane **Asercja** wiadomości również emisji do **OutputDebugString** interfejsu Windows API i **Debugger.Log** metody i przyczynę, komunikat pole, aby być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="a8940-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="a8940-115">To zachowanie jest zachowaniem domyślnym **debugowania** i **śledzenia** wiadomości, ponieważ **DefaultTraceListener** jest automatycznie uwzględnione w każdym `Listeners` zbieranie i jest tylko odbiornik automatycznie dołączane.</span><span class="sxs-lookup"><span data-stu-id="a8940-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
-   <span data-ttu-id="a8940-116">A <xref:System.Diagnostics.ConsoleTraceListener> kieruje śledzenia i debugowania dane wyjściowe do wyjścia standardowego lub Standardowy strumień błędów.</span><span class="sxs-lookup"><span data-stu-id="a8940-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
-   <span data-ttu-id="a8940-117">A <xref:System.Diagnostics.DelimitedListTraceListener> kieruje śledzenia i debugowania danych wyjściowych w składniku zapisywania tekstu, takich jak edytor strumienia lub do strumienia, takich jak strumienia pliku.</span><span class="sxs-lookup"><span data-stu-id="a8940-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="a8940-118">Dane wyjściowe śledzenia znajduje się w format tekstu rozdzielanego, który używa ogranicznik określony przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a8940-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
-   <span data-ttu-id="a8940-119"><xref:System.Diagnostics.XmlWriterTraceListener> Kieruje śledzenia lub dane wyjściowe debugowania jako dane zakodowane w formacie XML do <xref:System.IO.TextWriter> lub <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="a8940-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="a8940-120">Jeśli chcesz, aby wszystkie odbiornika oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> danych wyjściowych, należy dodać go do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a8940-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="a8940-121">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [jak: Użycie TraceSource i filtrów z obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="a8940-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="a8940-122">Wszelkie odbiornik **odbiorników** kolekcji pobiera tymi samymi komunikatami ze śledzenia danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="a8940-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="a8940-123">Załóżmy na przykład, należy skonfigurować dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="a8940-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="a8940-124">Każdego odbiornika otrzymuje ten sam komunikat.</span><span class="sxs-lookup"><span data-stu-id="a8940-124">Each listener receives the same message.</span></span> <span data-ttu-id="a8940-125">**TextWriterTraceListener** będzie kierować dane wyjściowe do strumienia, a **EventLogTraceListener** będzie kierować dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a8940-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="a8940-126">Poniższy przykład przedstawia sposób wysłania danych wyjściowych do **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a8940-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 <span data-ttu-id="a8940-127">Debugowania i śledzenia współużytkować ten sam **odbiorników** kolekcji, więc jeśli dodasz obiekt detektor **Debug.Listeners** kolekcji w aplikacji, pobiera dodać go do **Trace.Listeners** również kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a8940-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="a8940-128">Poniższy przykład pokazuje, jak wysyłać za pomocą odbiornik informacje śledzenia do konsoli:</span><span class="sxs-lookup"><span data-stu-id="a8940-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="a8940-129">Odbiorniki zdefiniowane dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="a8940-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="a8940-130">Można zdefiniować własne odbiorników przez dziedziczenie z **TraceListener** bazowa, klasy i przesłanianie jej metod przy użyciu niestandardowych metod.</span><span class="sxs-lookup"><span data-stu-id="a8940-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="a8940-131">Aby uzyskać więcej informacji na temat tworzenia odbiorników zdefiniowane dla deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w dokumentacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a8940-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8940-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8940-132">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="a8940-133">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="a8940-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="a8940-134">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="a8940-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)

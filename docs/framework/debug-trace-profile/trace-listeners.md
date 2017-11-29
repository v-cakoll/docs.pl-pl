---
title: "Obiekty nasłuchujące śledzenia"
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
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56cbde16eff89d25960e510e7eec2424f15e51b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="trace-listeners"></a><span data-ttu-id="8d216-102">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="8d216-102">Trace Listeners</span></span>
<span data-ttu-id="8d216-103">Korzystając z **śledzenia**, **debugowania** i <xref:System.Diagnostics.TraceSource>, musi mieć mechanizm zbieranie i rejestrowanie komunikatów, które są wysyłane.</span><span class="sxs-lookup"><span data-stu-id="8d216-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="8d216-104">Komunikaty śledzenia są odbierane przez *odbiorników*.</span><span class="sxs-lookup"><span data-stu-id="8d216-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="8d216-105">Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy.</span><span class="sxs-lookup"><span data-stu-id="8d216-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="8d216-106">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="8d216-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="8d216-107">Obiekty nasłuchujące są dostępne dla **debugowania**, **śledzenia**, i <xref:System.Diagnostics.TraceSource> klasy, z których każdy może wysłać dane wyjściowe do różnych obiektów odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8d216-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="8d216-108">Poniżej przedstawiono typowe odbiorników wstępnie zdefiniowane:</span><span class="sxs-lookup"><span data-stu-id="8d216-108">The following are the commonly used predefined listeners:</span></span>  
  
-   <span data-ttu-id="8d216-109">A <xref:System.Diagnostics.TextWriterTraceListener> przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub niczego, który jest <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d216-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="8d216-110">Może on również zapisywać w konsoli lub do pliku, ponieważ są one <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d216-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
-   <span data-ttu-id="8d216-111"><xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8d216-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
-   <span data-ttu-id="8d216-112">A <xref:System.Diagnostics.DefaultTraceListener> emituje **zapisu** i **WriteLine** komunikaty **OutputDebugString** i **Debugger.Log** metody.</span><span class="sxs-lookup"><span data-stu-id="8d216-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="8d216-113">W programie Visual Studio powoduje to komunikaty debugowania pojawią się w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8d216-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="8d216-114">**Niepowodzenie** i operacja nie powiodła **Assert** wiadomości również wysyłać do **OutputDebugString** interfejsu API systemu Windows i **Debugger.Log** metody i Przyczyna polu komunikat można wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="8d216-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="8d216-115">To zachowanie jest to domyślne zachowanie dla **debugowania** i **śledzenia** wiadomości, ponieważ **DefaultTraceListener** jest automatycznie uwzględnione w każdym `Listeners` Kolekcja i jest tylko odbiornika automatycznie dołączane.</span><span class="sxs-lookup"><span data-stu-id="8d216-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
-   <span data-ttu-id="8d216-116">A <xref:System.Diagnostics.ConsoleTraceListener> kieruje śledzenia i debugowania dane wyjściowe do standardowego wyjścia lub Standardowy strumień błędów.</span><span class="sxs-lookup"><span data-stu-id="8d216-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
-   <span data-ttu-id="8d216-117">A <xref:System.Diagnostics.DelimitedListTraceListener> kieruje śledzenia i debugowania dane wyjściowe w składniku zapisywania tekstu, takich jak piszący strumienia, lub do strumienia, takich jak strumienia pliku.</span><span class="sxs-lookup"><span data-stu-id="8d216-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="8d216-118">Dane wyjściowe śledzenia jest format tekstu rozdzielanego używa ogranicznik określony przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="8d216-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
-   <span data-ttu-id="8d216-119"><xref:System.Diagnostics.XmlWriterTraceListener> Kieruje śledzenia lub dane wyjściowe debugowania jako dane zakodowane w formacie XML <xref:System.IO.TextWriter> lub <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="8d216-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="8d216-120">Jeśli chcesz, aby wszystkie odbiornika oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> danych wyjściowych, należy dodać go do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d216-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="8d216-121">Aby uzyskać więcej informacji, zobacz [porady: tworzenie i Inicjowanie obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) i [porady: użycie TraceSource i filtrów z obiektów nasłuchujących śledzenia](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="8d216-121">For more information, see [How to: Create and Initialize Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="8d216-122">Wszelkie odbiornika w **odbiorników** kolekcji pobiera tej wiadomości z śledzenie danych wyjściowych metody.</span><span class="sxs-lookup"><span data-stu-id="8d216-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="8d216-123">Załóżmy na przykład, należy skonfigurować dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="8d216-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="8d216-124">Każdy odbiornika odbiera tę samą wiadomość.</span><span class="sxs-lookup"><span data-stu-id="8d216-124">Each listener receives the same message.</span></span> <span data-ttu-id="8d216-125">**TextWriterTraceListener** może bezpośrednia dane wyjściowe do strumienia i **EventLogTraceListener** może bezpośrednia dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8d216-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="8d216-126">Poniższy przykład przedstawia sposób wysłania danych wyjściowych do **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d216-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="8d216-127">Debugowania i śledzenia udziału takie same **odbiorników** kolekcji, tak aby w przypadku dodania obiektu odbiornika do **Debug.Listeners** kolekcji w aplikacji, pobiera dodać go do **Trace.Listeners** również kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8d216-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="8d216-128">Poniższy przykład przedstawia użycie odbiornik o wysłanie informacji śledzenia do konsoli:</span><span class="sxs-lookup"><span data-stu-id="8d216-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="8d216-129">Zdefiniowane przez dewelopera odbiorników</span><span class="sxs-lookup"><span data-stu-id="8d216-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="8d216-130">Możesz definiować własne odbiorników za dziedziczenie z **TraceListener** podstawowa klasa i przesłanianie jej metody o niestandardowych metody.</span><span class="sxs-lookup"><span data-stu-id="8d216-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="8d216-131">Aby uzyskać więcej informacji o tworzeniu odbiorników zdefiniowane przez deweloperów, zobacz <xref:System.Diagnostics.TraceListener> w odwołania programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d216-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d216-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d216-132">See Also</span></span>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="8d216-133">Śledzenie i Instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="8d216-133">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="8d216-134">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="8d216-134">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)

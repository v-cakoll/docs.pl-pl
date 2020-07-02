---
title: Obiekty nasłuchujące śledzenia
description: Poznaj detektory śledzenia, które są mechanizmem do zbierania i rejestrowania komunikatów śledzenia przesyłanych w programie .NET. Odbiornik zbiera, przechowuje i kieruje komunikaty.
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
ms.openlocfilehash: d08f86c782284a296090cf63e4b03c8d446a95fc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803526"
---
# <a name="trace-listeners"></a><span data-ttu-id="1c083-104">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="1c083-104">Trace Listeners</span></span>
<span data-ttu-id="1c083-105">W przypadku korzystania z **funkcji trace**, **Debug** i <xref:System.Diagnostics.TraceSource> , musisz mieć mechanizm zbierania i rejestrowania wysyłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="1c083-105">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="1c083-106">Komunikaty śledzenia są odbierane przez *odbiorniki*.</span><span class="sxs-lookup"><span data-stu-id="1c083-106">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="1c083-107">Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy.</span><span class="sxs-lookup"><span data-stu-id="1c083-107">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="1c083-108">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="1c083-108">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="1c083-109">Odbiorniki są dostępne dla **debugowania**, **śledzenia**i <xref:System.Diagnostics.TraceSource> klas, z których każdy może wysyłać dane wyjściowe do różnych obiektów odbiornika.</span><span class="sxs-lookup"><span data-stu-id="1c083-109">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="1c083-110">Poniżej przedstawiono najczęściej używane wstępnie zdefiniowane detektory:</span><span class="sxs-lookup"><span data-stu-id="1c083-110">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="1c083-111"><xref:System.Diagnostics.TextWriterTraceListener>Przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub do elementu, który jest <xref:System.IO.Stream> klasą.</span><span class="sxs-lookup"><span data-stu-id="1c083-111">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="1c083-112">Może również zapisywać w konsoli lub w pliku, ponieważ są to <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c083-112">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="1c083-113"><xref:System.Diagnostics.EventLogTraceListener>Przekierowuje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1c083-113">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="1c083-114"><xref:System.Diagnostics.DefaultTraceListener>Emituje komunikaty **Write** i **WriteLine** do **Funkcja OutputDebugString** oraz do metody **Debugger. log** .</span><span class="sxs-lookup"><span data-stu-id="1c083-114">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="1c083-115">W programie Visual Studio powoduje to wyświetlenie komunikatów debugowania w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="1c083-115">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="1c083-116">Komunikaty **potwierdzenia** zakończone **niepowodzeniem** i niepowodzeniem EMITUJĄ również do interfejsu API systemu Windows **Funkcja OutputDebugString** oraz metody **Debugger. log** , a także powodują wyświetlenie okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="1c083-116">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="1c083-117">To zachowanie jest zachowaniem domyślnym dla komunikatów **debugowania** i **śledzenia** , ponieważ **DefaultTraceListener** jest automatycznie dołączany do każdej `Listeners` kolekcji i jest jedynym odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="1c083-117">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="1c083-118"><xref:System.Diagnostics.ConsoleTraceListener>Kieruje śledzenie lub debugowanie danych wyjściowych do standardowego wyjścia lub standardowego strumienia błędów.</span><span class="sxs-lookup"><span data-stu-id="1c083-118">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="1c083-119"><xref:System.Diagnostics.DelimitedListTraceListener>Kierowanie kieruje lub debuguje dane wyjściowe do składnika zapisywania tekstu, takiego jak składnik zapisywania strumienia lub strumień, taki jak strumień pliku.</span><span class="sxs-lookup"><span data-stu-id="1c083-119">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="1c083-120">Wynik śledzenia jest w rozdzielonym formacie tekstowym, który używa ogranicznika określonego przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="1c083-120">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="1c083-121"><xref:System.Diagnostics.XmlWriterTraceListener>Kieruje śledzenie lub debugowanie danych wyjściowych w formacie XML zakodowanym do <xref:System.IO.TextWriter> lub do <xref:System.IO.Stream> , takich jak <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="1c083-121">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="1c083-122">Jeśli chcesz, aby każdy odbiornik oprócz <xref:System.Diagnostics.DefaultTraceListener> do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> wyprowadzania, należy dodać go do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1c083-122">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="1c083-123">Aby uzyskać więcej informacji, zobacz [How to: Create and Initialize detektory śledzenia](how-to-create-and-initialize-trace-listeners.md) i [instrukcje: użycie TraceSource i filtrów z odbiornikami śledzenia](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="1c083-123">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="1c083-124">Każdy odbiornik w kolekcji **odbiorników** pobiera te same komunikaty z metod danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1c083-124">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="1c083-125">Załóżmy na przykład, że skonfigurowano dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="1c083-125">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="1c083-126">Każdy odbiornik otrzymuje ten sam komunikat.</span><span class="sxs-lookup"><span data-stu-id="1c083-126">Each listener receives the same message.</span></span> <span data-ttu-id="1c083-127">**TextWriterTraceListener** przekierowuje dane wyjściowe do strumienia, a **EventLogTraceListener** przekieruje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1c083-127">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="1c083-128">Poniższy przykład pokazuje, jak wysyłać dane wyjściowe do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="1c083-128">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="1c083-129">Debugowanie i śledzenie współdzielą tę samą kolekcję **detektorów** , więc jeśli obiekt odbiornika zostanie dodany do kolekcji **Debug.** Listeners w aplikacji, zostanie dodany do kolekcji **Trace.** Listeners.</span><span class="sxs-lookup"><span data-stu-id="1c083-129">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="1c083-130">Poniższy przykład przedstawia sposób użycia odbiornika do wysyłania informacji o śledzeniu do konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="1c083-130">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="1c083-131">Detektory zdefiniowane przez dewelopera</span><span class="sxs-lookup"><span data-stu-id="1c083-131">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="1c083-132">Można zdefiniować własne detektory, dziedzicząc klasę bazową **TraceListener** i zastępując jej metody przy użyciu dostosowanych metod.</span><span class="sxs-lookup"><span data-stu-id="1c083-132">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="1c083-133">Aby uzyskać więcej informacji na temat tworzenia detektorów zdefiniowanych przez dewelopera, zobacz sekcję <xref:System.Diagnostics.TraceListener> w temacie .NET Framework Reference.</span><span class="sxs-lookup"><span data-stu-id="1c083-133">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c083-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c083-134">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="1c083-135">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="1c083-135">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="1c083-136">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="1c083-136">Trace Switches</span></span>](trace-switches.md)

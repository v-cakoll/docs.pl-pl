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
ms.openlocfilehash: 752a6a5f9608aa260f192ee3e9e0709b7a10e27e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052287"
---
# <a name="trace-listeners"></a><span data-ttu-id="8170e-102">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="8170e-102">Trace Listeners</span></span>
<span data-ttu-id="8170e-103">W przypadku korzystania z **funkcji trace**, **Debug** i <xref:System.Diagnostics.TraceSource>, musisz mieć mechanizm zbierania i rejestrowania wysyłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8170e-103">When using **Trace**, **Debug** and <xref:System.Diagnostics.TraceSource>, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="8170e-104">Komunikaty śledzenia są odbierane przez *odbiorniki*.</span><span class="sxs-lookup"><span data-stu-id="8170e-104">Trace messages are received by *listeners*.</span></span> <span data-ttu-id="8170e-105">Odbiornik ma na celu zbierania, przechowywania i komunikatów śledzenia, które trasy.</span><span class="sxs-lookup"><span data-stu-id="8170e-105">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="8170e-106">Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego, takie jak dziennik, okno lub PLiku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="8170e-106">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="8170e-107">Odbiorniki są dostępne dla **debugowania**, **śledzenia**i <xref:System.Diagnostics.TraceSource> klas, z których każdy może wysyłać dane wyjściowe do różnych obiektów odbiornika.</span><span class="sxs-lookup"><span data-stu-id="8170e-107">Listeners are available to the **Debug**, **Trace**, and <xref:System.Diagnostics.TraceSource> classes, each of which can send its output to a variety of listener objects.</span></span> <span data-ttu-id="8170e-108">Poniżej przedstawiono najczęściej używane wstępnie zdefiniowane detektory:</span><span class="sxs-lookup"><span data-stu-id="8170e-108">The following are the commonly used predefined listeners:</span></span>  
  
- <span data-ttu-id="8170e-109">Przekierowuje dane wyjściowe do wystąpienia <xref:System.IO.TextWriter> klasy lub do elementu <xref:System.IO.Stream> , który jest klasą. <xref:System.Diagnostics.TextWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="8170e-109">A <xref:System.Diagnostics.TextWriterTraceListener> redirects output to an instance of the <xref:System.IO.TextWriter> class or to anything that is a <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="8170e-110">Może również zapisywać w konsoli lub w pliku, ponieważ są to <xref:System.IO.Stream> klasy.</span><span class="sxs-lookup"><span data-stu-id="8170e-110">It can also write to the console or to a file, because these are <xref:System.IO.Stream> classes.</span></span>  
  
- <span data-ttu-id="8170e-111"><xref:System.Diagnostics.EventLogTraceListener> Przekierowuje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8170e-111">An <xref:System.Diagnostics.EventLogTraceListener> redirects output to an event log.</span></span>  
  
- <span data-ttu-id="8170e-112">Emituje komunikaty Write i WriteLine do funkcja OutputDebugString oraz do metody Debugger. log. <xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="8170e-112">A <xref:System.Diagnostics.DefaultTraceListener> emits **Write** and **WriteLine** messages to the **OutputDebugString** and to the **Debugger.Log** method.</span></span> <span data-ttu-id="8170e-113">W programie Visual Studio powoduje to wyświetlenie komunikatów debugowania w oknie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8170e-113">In Visual Studio, this causes the debugging messages to appear in the Output window.</span></span> <span data-ttu-id="8170e-114">Komunikaty **potwierdzenia** zakończone **niepowodzeniem** i niepowodzeniem EMITUJĄ również do interfejsu API systemu Windows **Funkcja OutputDebugString** oraz metody **Debugger. log** , a także powodują wyświetlenie okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8170e-114">**Fail** and failed **Assert** messages also emit to the **OutputDebugString** Windows API and the **Debugger.Log** method, and also cause a message box to be displayed.</span></span> <span data-ttu-id="8170e-115">To zachowanie jest zachowaniem domyślnym dla komunikatów **debugowania** i **śledzenia** , ponieważ **DefaultTraceListener** jest automatycznie dołączany `Listeners` do każdej kolekcji i jest jedynym odbiornikiem.</span><span class="sxs-lookup"><span data-stu-id="8170e-115">This behavior is the default behavior for **Debug** and **Trace** messages, because **DefaultTraceListener** is automatically included in every `Listeners` collection and is the only listener automatically included.</span></span>  
  
- <span data-ttu-id="8170e-116"><xref:System.Diagnostics.ConsoleTraceListener> Kieruje śledzenie lub debugowanie danych wyjściowych do standardowego wyjścia lub standardowego strumienia błędów.</span><span class="sxs-lookup"><span data-stu-id="8170e-116">A <xref:System.Diagnostics.ConsoleTraceListener> directs tracing or debugging output to either the standard output or the standard error stream.</span></span>  
  
- <span data-ttu-id="8170e-117"><xref:System.Diagnostics.DelimitedListTraceListener> Kierowanie kieruje lub debuguje dane wyjściowe do składnika zapisywania tekstu, takiego jak składnik zapisywania strumienia lub strumień, taki jak strumień pliku.</span><span class="sxs-lookup"><span data-stu-id="8170e-117">A <xref:System.Diagnostics.DelimitedListTraceListener> directs tracing or debugging output to a text writer, such as a stream writer, or to a stream, such as a file stream.</span></span> <span data-ttu-id="8170e-118">Wynik śledzenia jest w rozdzielonym formacie tekstowym, który używa ogranicznika określonego przez <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="8170e-118">The trace output is in a delimited text format that uses the delimiter specified by the <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> property.</span></span>  
  
- <span data-ttu-id="8170e-119">Kieruje śledzenie lub debugowanie danych wyjściowych w formacie XML zakodowanym <xref:System.IO.TextWriter> do lub do <xref:System.IO.Stream>, takich jak <xref:System.IO.FileStream>. <xref:System.Diagnostics.XmlWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="8170e-119">An <xref:System.Diagnostics.XmlWriterTraceListener> directs tracing or debugging output as XML-encoded data to a <xref:System.IO.TextWriter> or to a <xref:System.IO.Stream>, such as a <xref:System.IO.FileStream>.</span></span>  
  
 <span data-ttu-id="8170e-120">Jeśli chcesz <xref:System.Diagnostics.DefaultTraceListener> , aby każdy odbiornik oprócz do odbierania **debugowania**, **śledzenia** i <xref:System.Diagnostics.TraceSource> wyprowadzania, należy dodać go do `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8170e-120">If you want any listener besides the <xref:System.Diagnostics.DefaultTraceListener> to receive **Debug**, **Trace** and <xref:System.Diagnostics.TraceSource> output, you must add it to the `Listeners` collection.</span></span> <span data-ttu-id="8170e-121">Aby uzyskać więcej informacji, zobacz [jak: Utwórz i zainicjuj](how-to-create-and-initialize-trace-listeners.md) detektory [śledzenia i instrukcje: Używaj TraceSource i filtrów z odbiornikami](how-to-use-tracesource-and-filters-with-trace-listeners.md)śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8170e-121">For more information, see [How to: Create and Initialize Trace Listeners](how-to-create-and-initialize-trace-listeners.md) and [How to: Use TraceSource and Filters with Trace Listeners](how-to-use-tracesource-and-filters-with-trace-listeners.md).</span></span> <span data-ttu-id="8170e-122">Każdy odbiornik w kolekcji **odbiorników** pobiera te same komunikaty z metod danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8170e-122">Any listener in the **Listeners** collection gets the same messages from the trace output methods.</span></span> <span data-ttu-id="8170e-123">Załóżmy na przykład, że skonfigurowano dwa odbiorniki: **TextWriterTraceListener** i **EventLogTraceListener**.</span><span class="sxs-lookup"><span data-stu-id="8170e-123">For example, suppose you set up two listeners: a **TextWriterTraceListener** and an **EventLogTraceListener**.</span></span> <span data-ttu-id="8170e-124">Każdy odbiornik otrzymuje ten sam komunikat.</span><span class="sxs-lookup"><span data-stu-id="8170e-124">Each listener receives the same message.</span></span> <span data-ttu-id="8170e-125">**TextWriterTraceListener** przekierowuje dane wyjściowe do strumienia, a **EventLogTraceListener** przekieruje dane wyjściowe do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8170e-125">The **TextWriterTraceListener** would direct its output to a stream, and the **EventLogTraceListener** would direct its output to an event log.</span></span>  
  
 <span data-ttu-id="8170e-126">Poniższy przykład pokazuje, jak wysyłać dane wyjściowe do kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="8170e-126">The following example shows how to send output to the **Listeners** collection.</span></span>  
  
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
  
 <span data-ttu-id="8170e-127">Debugowanie i śledzenie współdzielą tę samą kolekcję **detektorów** , więc jeśli obiekt odbiornika zostanie dodany do kolekcji **Debug.** Listeners w aplikacji, zostanie dodany do kolekcji **Trace.** Listeners.</span><span class="sxs-lookup"><span data-stu-id="8170e-127">Debug and trace share the same **Listeners** collection, so if you add a listener object to a **Debug.Listeners** collection in your application, it gets added to the **Trace.Listeners** collection as well.</span></span>  
  
 <span data-ttu-id="8170e-128">Poniższy przykład przedstawia sposób użycia odbiornika do wysyłania informacji o śledzeniu do konsoli programu:</span><span class="sxs-lookup"><span data-stu-id="8170e-128">The following example shows how to use a listener to send tracing information to a console:</span></span>  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a><span data-ttu-id="8170e-129">Detektory zdefiniowane przez dewelopera</span><span class="sxs-lookup"><span data-stu-id="8170e-129">Developer-Defined Listeners</span></span>  
 <span data-ttu-id="8170e-130">Można zdefiniować własne detektory, dziedzicząc klasę bazową **TraceListener** i zastępując jej metody przy użyciu dostosowanych metod.</span><span class="sxs-lookup"><span data-stu-id="8170e-130">You can define your own listeners by inheriting from the **TraceListener** base class and overriding its methods with your customized methods.</span></span> <span data-ttu-id="8170e-131">Aby uzyskać więcej informacji na temat tworzenia detektorów zdefiniowanych przez <xref:System.Diagnostics.TraceListener> dewelopera, zobacz sekcję w temacie .NET Framework Reference.</span><span class="sxs-lookup"><span data-stu-id="8170e-131">For more information on creating developer-defined listeners, see <xref:System.Diagnostics.TraceListener> in the .NET Framework reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8170e-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8170e-132">See also</span></span>

- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="8170e-133">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="8170e-133">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="8170e-134">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="8170e-134">Trace Switches</span></span>](trace-switches.md)

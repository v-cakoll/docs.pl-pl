---
title: 'Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia'
ms.date: 03/30/2017
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
ms.openlocfilehash: ce0df0af32d6798c89c8db6761d18febc1c398bb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217440"
---
# <a name="how-to-create-and-initialize-trace-listeners"></a><span data-ttu-id="98811-102">Porady: tworzenie i inicjowanie obiektów nasłuchujących śledzenia</span><span class="sxs-lookup"><span data-stu-id="98811-102">How to: Create and Initialize Trace Listeners</span></span>

<span data-ttu-id="98811-103">Klasy <xref:System.Diagnostics.Debug?displayProperty=nameWithType> i <xref:System.Diagnostics.Trace?displayProperty=nameWithType> wysyłają komunikaty do obiektów o nazwie detektory, które odbierają i przetwarzają te komunikaty.</span><span class="sxs-lookup"><span data-stu-id="98811-103">The <xref:System.Diagnostics.Debug?displayProperty=nameWithType> and <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes send messages to objects called listeners that receive and process these messages.</span></span> <span data-ttu-id="98811-104">Jeden taki odbiornik, <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, jest automatycznie tworzony i inicjowany po włączeniu śledzenia lub debugowania.</span><span class="sxs-lookup"><span data-stu-id="98811-104">One such listener, the <xref:System.Diagnostics.DefaultTraceListener?displayProperty=nameWithType>, is automatically created and initialized when tracing or debugging is enabled.</span></span> <span data-ttu-id="98811-105">Jeśli chcesz, aby <xref:System.Diagnostics.Trace> lub <xref:System.Diagnostics.Debug> dane wyjściowe były kierowane do wszelkich dodatkowych źródeł, musisz utworzyć i zainicjować dodatkowe detektory śledzenia.</span><span class="sxs-lookup"><span data-stu-id="98811-105">If you want <xref:System.Diagnostics.Trace> or <xref:System.Diagnostics.Debug> output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span>

<span data-ttu-id="98811-106">Utworzone odbiorniki powinny odzwierciedlać potrzeby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98811-106">The listeners you create should reflect your application's needs.</span></span> <span data-ttu-id="98811-107">Na przykład, jeśli chcesz, aby rekord tekstowy wszystkich danych wyjściowych śledzenia, Utwórz odbiornik <xref:System.Diagnostics.TextWriterTraceListener>, który zapisuje wszystkie dane wyjściowe w nowym pliku tekstowym, gdy jest włączony.</span><span class="sxs-lookup"><span data-stu-id="98811-107">For example, if you want a text record of all trace output, create a <xref:System.Diagnostics.TextWriterTraceListener> listener, which writes all output to a new text file when it is enabled.</span></span> <span data-ttu-id="98811-108">Z drugiej strony, jeśli chcesz wyświetlić dane wyjściowe tylko podczas wykonywania aplikacji, Utwórz odbiornik <xref:System.Diagnostics.ConsoleTraceListener>, który kieruje wszystkie dane wyjściowe do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="98811-108">On the other hand, if you want to view output only during application execution, create a <xref:System.Diagnostics.ConsoleTraceListener> listener, which directs all output to a console window.</span></span> <span data-ttu-id="98811-109"><xref:System.Diagnostics.EventLogTraceListener> może kierować dane wyjściowe śledzenia do dziennika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="98811-109">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log.</span></span> <span data-ttu-id="98811-110">Aby uzyskać więcej informacji, zobacz [detektory śledzenia](trace-listeners.md).</span><span class="sxs-lookup"><span data-stu-id="98811-110">For more information, see [Trace Listeners](trace-listeners.md).</span></span>

<span data-ttu-id="98811-111">Można utworzyć detektory śledzenia w [pliku konfiguracyjnym aplikacji](../configure-apps/index.md) lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="98811-111">You can create trace listeners in an [application configuration file](../configure-apps/index.md) or in your code.</span></span> <span data-ttu-id="98811-112">Zalecamy korzystanie z plików konfiguracji aplikacji, ponieważ umożliwiają one Dodawanie, modyfikowanie lub usuwanie detektorów śledzenia bez konieczności zmiany kodu.</span><span class="sxs-lookup"><span data-stu-id="98811-112">We recommend the use of application configuration files, because they let you add, modify, or remove trace listeners without having to change your code.</span></span>

### <a name="to-create-and-use-a-trace-listener-by-using-a-configuration-file"></a><span data-ttu-id="98811-113">Aby utworzyć odbiornik śledzenia i używać go przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="98811-113">To create and use a trace listener by using a configuration file</span></span>

1. <span data-ttu-id="98811-114">Zadeklaruj odbiornik śledzenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98811-114">Declare your trace listener in your application configuration file.</span></span> <span data-ttu-id="98811-115">Jeśli tworzony odbiornik wymaga innych obiektów, należy je także zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="98811-115">If the listener you are creating requires any other objects, declare them as well.</span></span> <span data-ttu-id="98811-116">Poniższy przykład pokazuje, jak utworzyć odbiornik o nazwie `myListener` zapisywania do pliku tekstowego `TextWriterOutput.log`.</span><span class="sxs-lookup"><span data-stu-id="98811-116">The following example shows how to create a listener called `myListener` that writes to the text file `TextWriterOutput.log`.</span></span>

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

2. <span data-ttu-id="98811-117">Użyj klasy <xref:System.Diagnostics.Trace> w kodzie, aby napisać komunikat do odbiorników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="98811-117">Use the <xref:System.Diagnostics.Trace> class in your code to write a message to the trace listeners.</span></span>

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

### <a name="to-create-and-use-a-trace-listener-in-code"></a><span data-ttu-id="98811-118">Tworzenie i używanie odbiornika śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="98811-118">To create and use a trace listener in code</span></span>

- <span data-ttu-id="98811-119">Dodaj odbiornik śledzenia do kolekcji <xref:System.Diagnostics.Trace.Listeners%2A> i Wyślij informacje o śledzeniu do odbiorników.</span><span class="sxs-lookup"><span data-stu-id="98811-119">Add the trace listener to the <xref:System.Diagnostics.Trace.Listeners%2A> collection and send trace information to the listeners.</span></span>

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

    <span data-ttu-id="98811-120">\- lub-</span><span class="sxs-lookup"><span data-stu-id="98811-120">\- or -</span></span>

- <span data-ttu-id="98811-121">Jeśli nie chcesz, aby odbiornik odbierał dane wyjściowe śledzenia, nie dodawaj go do kolekcji <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="98811-121">If you do not want your listener to receive trace output, do not add it to the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span> <span data-ttu-id="98811-122">Można emitować dane wyjściowe przez odbiornik niezależny od kolekcji <xref:System.Diagnostics.Trace.Listeners%2A>, wywołując własne metody wyjściowe odbiornika.</span><span class="sxs-lookup"><span data-stu-id="98811-122">You can emit output through a listener independent of the <xref:System.Diagnostics.Trace.Listeners%2A> collection by calling the listener's own output methods.</span></span> <span data-ttu-id="98811-123">Poniższy przykład pokazuje, jak napisać linię do odbiornika, który nie znajduje się w kolekcji <xref:System.Diagnostics.Trace.Listeners%2A>.</span><span class="sxs-lookup"><span data-stu-id="98811-123">The following example shows how to write a line to a listener that is not in the <xref:System.Diagnostics.Trace.Listeners%2A> collection.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="98811-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98811-124">See also</span></span>

- [<span data-ttu-id="98811-125">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="98811-125">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="98811-126">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="98811-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="98811-127">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="98811-127">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="98811-128">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="98811-128">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)

---
title: 'Porady: dodawanie instrukcji śledzenia do kodu aplikacji'
description: Dowiedz się, jak dodać instrukcje śledzenia do kodu aplikacji w programie .NET. Metody używane najczęściej do śledzenia są metodami zapisywania danych wyjściowych dla odbiorników.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 0c75a8775649aabe73b02187c4604d2eb3a8435b
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415891"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="5bbe2-104">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="5bbe2-104">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="5bbe2-105">Metody używane najczęściej do śledzenia to metody zapisywania danych wyjściowych dla odbiorników: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**i **niepowodzenia**.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-105">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="5bbe2-106">Te metody można podzielić na dwie kategorie: **zapis**, **WriteLine**i **Niepowodzenie** wszystkie dane wyjściowe Emituj bezwarunkowo, natomiast **WriteIf**, **WriteLineIf**i **Assert** testuje warunek logiczny, a następnie zapisują lub nie zapisu na podstawie wartości warunku.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-106">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="5bbe2-107">**WriteIf** i **WriteLineIf** Emituj dane wyjściowe, jeśli warunek jest `true` , i **Assert** emituje dane wyjściowe, jeśli warunek to `false` .</span><span class="sxs-lookup"><span data-stu-id="5bbe2-107">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="5bbe2-108">Podczas projektowania strategii śledzenia i debugowania należy zastanowić się, jak ma wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-108">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="5bbe2-109">W przypadku wielu instrukcji **zapisu** zapełnione niepowiązane informacje spowodują utworzenie dziennika, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-109">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="5bbe2-110">Z drugiej strony, używanie funkcji **WriteLine** do umieszczania powiązanych instrukcji w osobnych wierszach może utrudnić odróżnienie informacji, jakie należą do siebie.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-110">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="5bbe2-111">Ogólnie rzecz biorąc, Użyj wielu instrukcji **Write** , jeśli chcesz połączyć informacje z wielu źródeł, aby utworzyć pojedynczy komunikat informacyjny, a następnie użyć instrukcji **WriteLine** , gdy chcesz utworzyć pojedynczy, kompletny komunikat.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-111">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="5bbe2-112">Aby napisać kompletny wiersz</span><span class="sxs-lookup"><span data-stu-id="5bbe2-112">To write a complete line</span></span>  
  
1. <span data-ttu-id="5bbe2-113">Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-113">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="5bbe2-114">Znak powrotu karetki jest dołączany na końcu wiadomości zwracanej przez tę metodę, dzięki czemu następny komunikat zwrócony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="5bbe2-114">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="5bbe2-115">Aby napisać linię częściową</span><span class="sxs-lookup"><span data-stu-id="5bbe2-115">To write a partial line</span></span>  
  
1. <span data-ttu-id="5bbe2-116">Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-116">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="5bbe2-117">Następny komunikat umieszczony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w tym samym wierszu co komunikat umieszczony przez instrukcję **Write** lub **WriteIf** :</span><span class="sxs-lookup"><span data-stu-id="5bbe2-117">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="5bbe2-118">Aby sprawdzić, czy określone warunki istnieją przed lub po wykonaniu metody</span><span class="sxs-lookup"><span data-stu-id="5bbe2-118">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="5bbe2-119">Wywołaj <xref:System.Diagnostics.Trace.Assert%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-119">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5bbe2-120">Można użyć metody **Assert** zarówno do śledzenia, jak i debugowania.</span><span class="sxs-lookup"><span data-stu-id="5bbe2-120">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="5bbe2-121">Ten przykład wyprowadza stos wywołań do dowolnego odbiornika w kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="5bbe2-121">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="5bbe2-122">Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5bbe2-122">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bbe2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5bbe2-123">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5bbe2-124">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="5bbe2-124">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="5bbe2-125">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="5bbe2-125">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="5bbe2-126">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="5bbe2-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="5bbe2-127">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="5bbe2-127">Trace Listeners</span></span>](trace-listeners.md)

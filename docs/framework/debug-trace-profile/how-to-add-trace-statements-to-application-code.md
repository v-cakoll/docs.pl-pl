---
title: 'Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 626e9823bbf7d379a21ae353a9189485259f3c42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948007"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="af60d-102">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="af60d-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="af60d-103">Metody używane najczęściej do śledzenia są metodami zapisywania danych wyjściowych w detektorach: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**i **zakończony niepowodzeniem**.</span><span class="sxs-lookup"><span data-stu-id="af60d-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="af60d-104">Te metody można podzielić na dwie kategorie: **Zapis**, **WriteLine**i **Niepowodzenie** wszystkie emitowanie danych wyjściowych bezwarunkowo, podczas gdy **WriteIf**, **WriteLineIf**i **Assert** testuje warunek logiczny i zapisują lub nie zapisu na podstawie wartości warunku.</span><span class="sxs-lookup"><span data-stu-id="af60d-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="af60d-105">**WriteIf** i **WriteLineIf** Emituj dane wyjściowe, jeśli warunek `true`jest, i **Assert** emituje dane wyjściowe, jeśli `false`warunek to.</span><span class="sxs-lookup"><span data-stu-id="af60d-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="af60d-106">Podczas projektowania strategii śledzenia i debugowania należy zastanowić się, jak ma wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="af60d-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="af60d-107">W przypadku wielu instrukcji **zapisu** zapełnione niepowiązane informacje spowodują utworzenie dziennika, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="af60d-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="af60d-108">Z drugiej strony, używanie funkcji **WriteLine** do umieszczania powiązanych instrukcji w osobnych wierszach może utrudnić odróżnienie informacji, jakie należą do siebie.</span><span class="sxs-lookup"><span data-stu-id="af60d-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="af60d-109">Ogólnie rzecz biorąc, Użyj wielu instrukcji **Write** , jeśli chcesz połączyć informacje z wielu źródeł, aby utworzyć pojedynczy komunikat informacyjny, a następnie użyć instrukcji **WriteLine** , gdy chcesz utworzyć pojedynczy, kompletny komunikat.</span><span class="sxs-lookup"><span data-stu-id="af60d-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="af60d-110">Aby napisać kompletny wiersz</span><span class="sxs-lookup"><span data-stu-id="af60d-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="af60d-111">Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af60d-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="af60d-112">Znak powrotu karetki jest dołączany na końcu wiadomości zwracanej przez tę metodę, dzięki czemu następny komunikat zwrócony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="af60d-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="af60d-113">Aby napisać linię częściową</span><span class="sxs-lookup"><span data-stu-id="af60d-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="af60d-114">Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af60d-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="af60d-115">Następny komunikat umieszczony przez **zapis**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w tym samym wierszu co komunikat umieszczony przez instrukcję **Write** lub **WriteIf** :</span><span class="sxs-lookup"><span data-stu-id="af60d-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="af60d-116">Aby sprawdzić, czy określone warunki istnieją przed lub po wykonaniu metody</span><span class="sxs-lookup"><span data-stu-id="af60d-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="af60d-117">Wywołaj <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af60d-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="af60d-118">Można użyć metody **Assert** zarówno do śledzenia, jak i debugowania.</span><span class="sxs-lookup"><span data-stu-id="af60d-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="af60d-119">Ten przykład wyprowadza stos wywołań do dowolnego odbiornika w kolekcji **odbiorników** .</span><span class="sxs-lookup"><span data-stu-id="af60d-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="af60d-120">Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie](/visualstudio/debugger/assertions-in-managed-code) zarządzanym <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>i.</span><span class="sxs-lookup"><span data-stu-id="af60d-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af60d-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af60d-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="af60d-122">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="af60d-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="af60d-123">Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="af60d-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="af60d-124">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="af60d-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="af60d-125">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="af60d-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)

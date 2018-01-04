---
title: "Porady: dodawanie instrukcji śledzenia do kodu aplikacji"
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
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 134e03a1438e4c9399962a245eb44eec9dd02924
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="7f260-102">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f260-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="7f260-103">Najczęściej używane do śledzenia przedstawiono metody do zapisywania danych wyjściowych do odbiorników: **zapisu**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, i **niepowodzenie**.</span><span class="sxs-lookup"><span data-stu-id="7f260-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="7f260-104">Te metody można podzielić na dwie kategorie: **zapisu**, **WriteLine**, i **niepowodzenie** wszystkie Emituj danych wyjściowych bezwarunkowo, podczas gdy **WriteIf**, **WriteLineIf**, i **Assert** przetestować warunek typu Boolean i zapisu lub nie zapisuj oparte na wartości warunku.</span><span class="sxs-lookup"><span data-stu-id="7f260-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="7f260-105">**WriteIf** i **WriteLineIf** Emituj danych wyjściowych, jeśli wynikiem warunku jest `true`, i **Assert** emituje dane wyjściowe, jeśli wynikiem warunku jest `false`.</span><span class="sxs-lookup"><span data-stu-id="7f260-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="7f260-106">Podczas projektowania sieci śledzenie i debugowanie strategii, możesz pomyśleć o sposób dane wyjściowe do wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="7f260-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="7f260-107">Wiele **zapisu** instrukcje wypełniane informacjami niepowiązanych utworzy dziennika, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="7f260-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="7f260-108">Z drugiej strony, przy użyciu **WriteLine** umieszczanie pokrewne instrukcje w osobnych wierszach może utrudniać rozróżnienie, jakie informacje należy razem.</span><span class="sxs-lookup"><span data-stu-id="7f260-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="7f260-109">Ogólnie rzecz biorąc, używając wielu **zapisu** instrukcji, gdy chcesz połączyć informacje z wielu źródeł, aby utworzyć jeden komunikat informacyjny i użyj **WriteLine** instrukcji, gdy chcesz utworzyć pełną, jeden komunikat.</span><span class="sxs-lookup"><span data-stu-id="7f260-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="7f260-110">Aby zapisać pełny wiersz</span><span class="sxs-lookup"><span data-stu-id="7f260-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="7f260-111">Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7f260-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="7f260-112">Znak powrotu karetki jest dołączany na końcu ta metoda zwraca komunikat tak, aby następny komunikat zwrócony przez **zapisu**, **WriteIf**, **WriteLine**, lub  **WriteLineIf** rozpocznie się o następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="7f260-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="7f260-113">Do zapisywania częściowej wiersza</span><span class="sxs-lookup"><span data-stu-id="7f260-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="7f260-114">Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7f260-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="7f260-115">Następny komunikat przedmiotem **zapisu**, **WriteIf**, **WriteLine**, lub **WriteLineIf** rozpocznie się na tym samym wierszu co komunikat przez **zapisu** lub **WriteIf** instrukcji:</span><span class="sxs-lookup"><span data-stu-id="7f260-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="7f260-116">Aby sprawdzić, że niektóre warunki przed lub po wykonaniu metody</span><span class="sxs-lookup"><span data-stu-id="7f260-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="7f260-117">Wywołanie <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7f260-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7f260-118">Można użyć **Assert** śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="7f260-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="7f260-119">Stos wywołań żadnych odbiornika w danych wyjściowych w tym przykładzie **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7f260-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="7f260-120">Aby uzyskać więcej informacji, zobacz [potwierdzenia w kod zarządzany](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f260-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f260-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f260-121">See Also</span></span>  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="7f260-122">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f260-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="7f260-123">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="7f260-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="7f260-124">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="7f260-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="7f260-125">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="7f260-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)

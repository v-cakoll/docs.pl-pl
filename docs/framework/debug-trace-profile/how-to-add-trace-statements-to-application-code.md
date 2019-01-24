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
ms.openlocfilehash: 8a347919617e495ace19ca12eebc9b9a77f613ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684380"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="36155-102">Instrukcje: Dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="36155-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="36155-103">Najczęściej używane do śledzenia przedstawiono metody do zapisywania danych wyjściowych odbiorniki: **Zapis**, **writeif —**, **WriteLine**, **WriteLineIf**, **Asercja**, i **się nie powieść**.</span><span class="sxs-lookup"><span data-stu-id="36155-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="36155-104">Metody te można podzielić na dwie kategorie: **Zapis**, **WriteLine**, i **się nie powieść** wszystkie wyemituj dane wyjściowe bezwarunkowo, natomiast **writeif —**, **WriteLineIf**i  **Asercja** warunek logiczny, testowanie i go zapisuje lub nie zapisują na podstawie wartości warunku.</span><span class="sxs-lookup"><span data-stu-id="36155-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="36155-105">**Writeif —** i **WriteLineIf** wyemituj dane wyjściowe, jeśli wynikiem warunku jest `true`, i **Asercja** emituje dane wyjściowe, jeśli warunek nie jest `false`.</span><span class="sxs-lookup"><span data-stu-id="36155-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="36155-106">Podczas projektowania usługi śledzenia i debugowania strategii, możesz pomyśleć o jak ma wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="36155-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="36155-107">Wiele **zapisu** instrukcji wypełnione informacjami niepowiązanych spowoduje utworzenie dziennika, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="36155-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="36155-108">Z drugiej strony, przy użyciu **WriteLine** umieszczanie pokrewnych instrukcji w osobnych wierszach może utrudnić odróżnić, jakie informacje należy ze sobą.</span><span class="sxs-lookup"><span data-stu-id="36155-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="36155-109">Ogólnie rzecz biorąc, używanych jest wiele **zapisu** instrukcji, jeśli chcesz połączyć informacje z wielu źródeł, aby utworzyć pojedynczy komunikat informacyjny i użyć **WriteLine** instrukcji, gdy chcesz utworzyć pojedynczy, pełny komunikat.</span><span class="sxs-lookup"><span data-stu-id="36155-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="36155-110">Aby zapisać pełny wiersz</span><span class="sxs-lookup"><span data-stu-id="36155-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="36155-111">Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36155-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="36155-112">Znak powrotu karetki jest dołączany na końcu komunikat, ta metoda zwraca wartość, tak, aby następny komunikat zwrócony przez **zapisu**, **writeif —**, **WriteLine**, lub  **WriteLineIf —** rozpocznie się w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="36155-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="36155-113">Aby zapisać wiersz częściowy</span><span class="sxs-lookup"><span data-stu-id="36155-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="36155-114">Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36155-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="36155-115">Następny komunikat przedmiotem **zapisu**, **writeif —**, **WriteLine**, lub **WriteLineIf** rozpocznie się w tym samym wierszu co komunikat przez **zapisu** lub **writeif —** instrukcji:</span><span class="sxs-lookup"><span data-stu-id="36155-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="36155-116">Aby sprawdzić, że niektóre warunki przed lub po wykonaniu metody</span><span class="sxs-lookup"><span data-stu-id="36155-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="36155-117">Wywołaj <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36155-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="36155-118">Możesz użyć **Asercja** przy użyciu śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="36155-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="36155-119">W tym przykładzie generuje stos wywołań, aby wszelkie odbiornik **odbiorników** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="36155-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="36155-120">Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzany](/visualstudio/debugger/assertions-in-managed-code) i <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="36155-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36155-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36155-121">See also</span></span>
- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="36155-122">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="36155-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="36155-123">Instrukcje: Tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="36155-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="36155-124">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="36155-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="36155-125">Obiekty nasłuchujące śledzenie</span><span class="sxs-lookup"><span data-stu-id="36155-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)

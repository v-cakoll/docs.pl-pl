---
title: 'Porady: dodawanie instrukcji śledzenia do kodu aplikacji'
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
ms.openlocfilehash: 9903a0357d1d8ceade21b590fd54c8cab517f134
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174748"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="36c95-102">Porady: dodawanie instrukcji śledzenia do kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="36c95-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="36c95-103">Metody stosowane najczęściej do śledzenia są metody pisania danych wyjściowych do odbiorników: **Write**, **WriteIf**, **WriteLine**, WriteLine , **WriteLine ,** **Assert**, i **Fail**.</span><span class="sxs-lookup"><span data-stu-id="36c95-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="36c95-104">Metody te można podzielić na dwie kategorie: **Write**, Write , **WriteLine**i **Fail** wszystkie emitują dane wyjściowe bezwarunkowo, natomiast **WriteIf**, **WriteLineIf**i **Assert** testować warunek logiczny i zapisywać lub nie zapisywać na podstawie wartości warunku.</span><span class="sxs-lookup"><span data-stu-id="36c95-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="36c95-105">**WriteIf** i **WriteLineIf** emitują `true`dane wyjściowe, jeśli warunek `false`jest , i **Assert** emituje dane wyjściowe, jeśli warunek jest .</span><span class="sxs-lookup"><span data-stu-id="36c95-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="36c95-106">Podczas projektowania strategii śledzenia i debugowania, należy pomyśleć o tym, jak mają wyglądać dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="36c95-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="36c95-107">Wiele **instrukcji Write** wypełnione niepowiązanych informacji utworzy dziennik, który jest trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="36c95-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="36c95-108">Z drugiej strony za pomocą **WriteLine** umieścić powiązane instrukcje w oddzielnych wierszach może utrudnić rozróżnienie, jakie informacje należą do siebie.</span><span class="sxs-lookup"><span data-stu-id="36c95-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="36c95-109">Ogólnie rzecz biorąc, należy użyć wielu **Write** instrukcji, gdy chcesz połączyć informacje z wielu źródeł, aby utworzyć jedną wiadomość informacyjną i użyj **WriteLine** instrukcji, gdy chcesz utworzyć pojedynczą, pełną wiadomość.</span><span class="sxs-lookup"><span data-stu-id="36c95-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="36c95-110">Aby napisać pełny wiersz</span><span class="sxs-lookup"><span data-stu-id="36c95-110">To write a complete line</span></span>  
  
1. <span data-ttu-id="36c95-111">Wywołanie <xref:System.Diagnostics.Trace.WriteLine%2A> lub <xref:System.Diagnostics.Trace.WriteLineIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36c95-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="36c95-112">Powrót karetki jest dołączany na końcu wiadomości zwraca tej metody, tak aby następna wiadomość zwrócona przez **Write**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w następującym wierszu:</span><span class="sxs-lookup"><span data-stu-id="36c95-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
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
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="36c95-113">Aby napisać wiersz częściowy</span><span class="sxs-lookup"><span data-stu-id="36c95-113">To write a partial line</span></span>  
  
1. <span data-ttu-id="36c95-114">Wywołanie <xref:System.Diagnostics.Trace.Write%2A> lub <xref:System.Diagnostics.Trace.WriteIf%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36c95-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="36c95-115">Następna wiadomość wystawiona przez **Write**, **WriteIf**, **WriteLine**lub **WriteLineIf** rozpocznie się w tym samym wierszu, co wiadomość wystawiona przez **Write** lub **WriteIf** instrukcji:</span><span class="sxs-lookup"><span data-stu-id="36c95-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="36c95-116">Aby sprawdzić, czy istnieją określone warunki przed lub po wykonaniu metody</span><span class="sxs-lookup"><span data-stu-id="36c95-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="36c95-117">Wywołanie <xref:System.Diagnostics.Trace.Assert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36c95-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="36c95-118">Można użyć **Assert** zarówno śledzenia i debugowania.</span><span class="sxs-lookup"><span data-stu-id="36c95-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="36c95-119">W tym przykładzie wyprowadza stos wywołań do dowolnego odbiornika w **kolekcji odbiorników.**</span><span class="sxs-lookup"><span data-stu-id="36c95-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="36c95-120">Aby uzyskać więcej informacji, zobacz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>potwierdzenia w [kodzie zarządzanym](/visualstudio/debugger/assertions-in-managed-code) i .</span><span class="sxs-lookup"><span data-stu-id="36c95-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c95-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36c95-121">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="36c95-122">Śledzenie i instrumentacja aplikacji</span><span class="sxs-lookup"><span data-stu-id="36c95-122">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="36c95-123">Instrukcje: tworzenie, inicjowanie i konfigurowanie przełączników śledzenia</span><span class="sxs-lookup"><span data-stu-id="36c95-123">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="36c95-124">Przełączniki śledzenia</span><span class="sxs-lookup"><span data-stu-id="36c95-124">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="36c95-125">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="36c95-125">Trace Listeners</span></span>](trace-listeners.md)

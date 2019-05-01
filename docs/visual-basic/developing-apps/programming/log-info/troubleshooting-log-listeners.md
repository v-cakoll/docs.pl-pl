---
title: 'Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 12282df50bc42d2a153a9aa8db01f2654acd91ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013858"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="24918-102">Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24918-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="24918-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="24918-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="24918-104">Aby określić, które odbiorniki logu odebrania tych komunikatów, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="24918-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="24918-105">`Log` Obiekt umożliwia filtrowanie dziennika ograniczyć ilość informacji, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="24918-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="24918-106">Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="24918-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="24918-107">Aby uzyskać więcej informacji na temat filtrowania, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="24918-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="24918-108">Jednak jeśli dziennik jest niepoprawnie skonfigurowana, konieczne może dowiedzieć się więcej o bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="24918-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="24918-109">Aby przejść do zaawansowane te informacje za pośrednictwem dziennika `TraceSource` właściwości.</span><span class="sxs-lookup"><span data-stu-id="24918-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="24918-110">Aby określić odbiorniki logu dla obiektu dziennika w kodzie</span><span class="sxs-lookup"><span data-stu-id="24918-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="24918-111">Importuj <xref:System.Diagnostics> przestrzeni nazw na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="24918-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="24918-112">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="24918-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="24918-113">Tworzy funkcję, która zwraca ciąg składający się z informacji dla każdego dziennika odbiorników.</span><span class="sxs-lookup"><span data-stu-id="24918-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="24918-114">Kolekcja obiektów nasłuchujących śledzenia dziennika do przekazania `GetListeners` funkcji i wyświetlić wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="24918-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="24918-115">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="24918-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24918-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24918-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="24918-117">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="24918-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="24918-118">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="24918-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

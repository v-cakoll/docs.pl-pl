---
title: 'Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 3d21024a7ebda749f337a95b0fca419b529d2872
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662819"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="93e73-102">Rozwiązywanie problemów: Odbiorniki logu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93e73-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="93e73-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93e73-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="93e73-104">Aby określić, które odbiorniki logu odebrania tych komunikatów, zobacz [instruktażu: Ustalanie, gdzie My.Application.Log zapisuje informacje](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="93e73-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="93e73-105">`Log` Obiekt umożliwia filtrowanie dziennika ograniczyć ilość informacji, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="93e73-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="93e73-106">Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="93e73-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="93e73-107">Aby uzyskać więcej informacji na temat filtrowania, zobacz [instruktażu: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="93e73-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="93e73-108">Jednak jeśli dziennik jest niepoprawnie skonfigurowana, konieczne może dowiedzieć się więcej o bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="93e73-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="93e73-109">Aby przejść do zaawansowane te informacje za pośrednictwem dziennika `TraceSource` właściwości.</span><span class="sxs-lookup"><span data-stu-id="93e73-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="93e73-110">Aby określić odbiorniki logu dla obiektu dziennika w kodzie</span><span class="sxs-lookup"><span data-stu-id="93e73-110">To determine the log listeners for the Log object in code</span></span>  
  
1.  <span data-ttu-id="93e73-111">Importuj <xref:System.Diagnostics> przestrzeni nazw na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="93e73-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="93e73-112">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="93e73-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_1.vb)]  
  
2.  <span data-ttu-id="93e73-113">Tworzy funkcję, która zwraca ciąg składający się z informacji dla każdego dziennika odbiorników.</span><span class="sxs-lookup"><span data-stu-id="93e73-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_2.vb)]  
  
3.  <span data-ttu-id="93e73-114">Kolekcja obiektów nasłuchujących śledzenia dziennika do przekazania `GetListeners` funkcji i wyświetlić wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="93e73-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/troubleshooting-log-listeners_3.vb)]  
  
     <span data-ttu-id="93e73-115">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="93e73-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93e73-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93e73-116">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="93e73-117">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="93e73-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="93e73-118">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="93e73-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

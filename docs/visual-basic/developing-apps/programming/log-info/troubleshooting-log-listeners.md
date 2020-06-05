---
title: 'Rozwiązywanie problemów: odbiorcy dzienników'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: 8d2d8294d9e9bb42d72fe4f6c37bf846bd644907
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398321"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="7fd7a-102">Rozwiązywanie problemów: odbiorniki logu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fd7a-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="7fd7a-103">Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="7fd7a-104">Aby określić, które detektory dzienników odbierają te komunikaty, zobacz [Przewodnik: Określanie, gdzie my. Application. Log zapisuje informacje](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="7fd7a-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="7fd7a-105">`Log`Obiekt może korzystać z filtrowania dzienników w celu ograniczenia ilości informacji, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="7fd7a-106">Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="7fd7a-107">Aby uzyskać więcej informacji na temat filtrowania, zobacz [Przewodnik: filtrowanie danych wyjściowych my. Application. log](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="7fd7a-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="7fd7a-108">Jeśli jednak dziennik jest niepoprawnie skonfigurowany, może być konieczne więcej informacji na temat jego bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="7fd7a-109">Te informacje można uzyskać, korzystając z właściwości zaawansowane dziennika `TraceSource` .</span><span class="sxs-lookup"><span data-stu-id="7fd7a-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="7fd7a-110">Aby określić detektory dzienników dla obiektu dziennika w kodzie</span><span class="sxs-lookup"><span data-stu-id="7fd7a-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="7fd7a-111">Zaimportuj <xref:System.Diagnostics> przestrzeń nazw na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="7fd7a-112">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="7fd7a-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="7fd7a-113">Utwórz funkcję zwracającą ciąg składający się z informacji dla każdego z odbiorników dziennika.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="7fd7a-114">Przekaż kolekcję detektorów śledzenia dziennika do `GetListeners` funkcji i wyświetl wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="7fd7a-115">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="7fd7a-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd7a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fd7a-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="7fd7a-117">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="7fd7a-117">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="7fd7a-118">Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="7fd7a-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)

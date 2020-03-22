---
title: 'Rozwiązywanie problemów: odbiorniki logu'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, troubleshooting
- troubleshooting Visual Basic, event logs
- troubleshooting event logs
ms.assetid: ac6eb760-3d5d-461e-aedd-40599ee22e49
ms.openlocfilehash: dd139935dae7fe4d1334b861e6590df29bab7202
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74346854"
---
# <a name="troubleshooting-log-listeners-visual-basic"></a><span data-ttu-id="acec9-102">Rozwiązywanie problemów: odbiorniki logu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acec9-102">Troubleshooting: Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="acec9-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="acec9-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span>  
  
 <span data-ttu-id="acec9-104">Aby ustalić, które detektory dzienników odbierają te wiadomości, zobacz [Przewodnik: Określanie, gdzie informacje o zapisach my.application.log.](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)</span><span class="sxs-lookup"><span data-stu-id="acec9-104">To determine which log listeners receive those messages, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="acec9-105">Obiekt `Log` może użyć filtrowania dziennika, aby ograniczyć ilość informacji, które rejestruje.</span><span class="sxs-lookup"><span data-stu-id="acec9-105">The `Log` object can use log filtering to limit the amount of information that it logs.</span></span> <span data-ttu-id="acec9-106">Jeśli filtry są nieprawidłowo skonfigurowane, dzienniki mogą zawierać nieprawidłowe informacje.</span><span class="sxs-lookup"><span data-stu-id="acec9-106">If the filters are misconfigured, the logs might contain the wrong information.</span></span> <span data-ttu-id="acec9-107">Aby uzyskać więcej informacji na temat filtrowania, zobacz [Instruktaż: Filtrowanie danych wyjściowych My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="acec9-107">For more information about filtering, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>  
  
 <span data-ttu-id="acec9-108">Jeśli jednak dziennik jest niepoprawnie skonfigurowany, może być konieczne więcej informacji na temat jego bieżącej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="acec9-108">However, if a log is configured incorrectly, you may need more information about its current configuration.</span></span> <span data-ttu-id="acec9-109">Można uzyskać informacje do tych informacji `TraceSource` za pośrednictwem zaawansowanej właściwości dziennika.</span><span class="sxs-lookup"><span data-stu-id="acec9-109">You can get to this information through the log's advanced `TraceSource` property.</span></span>  
  
### <a name="to-determine-the-log-listeners-for-the-log-object-in-code"></a><span data-ttu-id="acec9-110">Aby określić detektory dziennika dla obiektu Log w kodzie</span><span class="sxs-lookup"><span data-stu-id="acec9-110">To determine the log listeners for the Log object in code</span></span>  
  
1. <span data-ttu-id="acec9-111">Zaimportuj <xref:System.Diagnostics> obszar nazw na początku pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="acec9-111">Import the <xref:System.Diagnostics> namespace at the beginning of the code file.</span></span> <span data-ttu-id="acec9-112">Aby uzyskać więcej informacji, zobacz [Oświadczenie importu (.NET Obszar nazw i Typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="acec9-112">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#13)]  
  
2. <span data-ttu-id="acec9-113">Utwórz funkcję, która zwraca ciąg składający się z informacji dla każdego z detektorów dziennika.</span><span class="sxs-lookup"><span data-stu-id="acec9-113">Create a function that returns a string consisting of information for each of the log's listeners.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#14)]  
  
3. <span data-ttu-id="acec9-114">Przekaż kolekcję detektorów śledzenia dziennika do `GetListeners` funkcji i wyświetlić wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="acec9-114">Pass the collection of the log's trace listeners to the `GetListeners` function, and display the return value.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#19)]  
  
     <span data-ttu-id="acec9-115">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="acec9-115">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acec9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="acec9-116">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="acec9-117">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="acec9-117">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="acec9-118">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="acec9-118">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)

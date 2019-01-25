---
title: 'Instrukcje: Zapisywanie wiadomości rejestru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 4b4210983aa5bd57f1b0a89f2f06f089e98670f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594954"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="75a00-102">Instrukcje: Zapisywanie wiadomości rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75a00-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="75a00-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="75a00-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="75a00-104">W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metody do rejestrowania informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="75a00-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="75a00-105">Rejestrowanie informacji o wyjątku, użyj `My.Application.Log.WriteException` metoda; zobacz [jak: Rejestrowania wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="75a00-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a00-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="75a00-106">Example</span></span>  
 <span data-ttu-id="75a00-107">W tym przykładzie użyto `My.Application.Log.WriteEntry` metodę, aby zapisać informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="75a00-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="75a00-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="75a00-108">.NET Framework Security</span></span>  
 <span data-ttu-id="75a00-109">Upewnij się, że dane, które są zapisywane w dzienniku nie zawiera poufne informacje, takie jak hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="75a00-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="75a00-110">Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="75a00-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a00-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75a00-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="75a00-112">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="75a00-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="75a00-113">Instrukcje: Rejestruje wyjątki</span><span class="sxs-lookup"><span data-stu-id="75a00-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="75a00-114">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="75a00-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="75a00-115">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="75a00-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="75a00-116">Przewodnik: Filtrowanie danych wyjściowych My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="75a00-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

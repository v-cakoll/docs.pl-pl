---
title: 'Porady: zapisywanie wiadomości rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352056"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="9a777-102">Porady: zapisywanie wiadomości rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a777-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="9a777-103">Za pomocą `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a777-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="9a777-104">W tym przykładzie `My.Application.Log.WriteEntry` pokazano, jak używać metody do rejestrowania informacji o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="9a777-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="9a777-105">W przypadku rejestrowania informacji `My.Application.Log.WriteException` o wyjątkach należy użyć tej metody; zobacz [Jak: Rejestrowanie wyjątków](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="9a777-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a777-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a777-106">Example</span></span>

<span data-ttu-id="9a777-107">W tym przykładzie `My.Application.Log.WriteEntry` użyto metody do zapisywania informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9a777-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="9a777-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a777-108">.NET Framework Security</span></span>

<span data-ttu-id="9a777-109">Upewnij się, że dane zapisywane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9a777-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="9a777-110">Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="9a777-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a777-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a777-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="9a777-112">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="9a777-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="9a777-113">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="9a777-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="9a777-114">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="9a777-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="9a777-115">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="9a777-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="9a777-116">Wskazówki: filtrowanie danych wyjściowych My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="9a777-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

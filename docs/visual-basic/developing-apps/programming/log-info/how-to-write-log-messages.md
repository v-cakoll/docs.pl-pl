---
title: 'Porady: zapisywanie wiadomości rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 38570047db48e009aea2af376304430db1ec29f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352056"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="a2e75-102">Porady: zapisywanie wiadomości rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2e75-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="a2e75-103">Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a2e75-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="a2e75-104">W tym przykładzie pokazano, jak za pomocą metody `My.Application.Log.WriteEntry` rejestrować informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="a2e75-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="a2e75-105">Aby rejestrować informacje o wyjątkach, użyj metody `My.Application.Log.WriteException`. Zobacz [jak: wyjątki dzienników](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="a2e75-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="a2e75-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2e75-106">Example</span></span>

<span data-ttu-id="a2e75-107">W tym przykładzie zastosowano metodę `My.Application.Log.WriteEntry`, aby napisać informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="a2e75-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="a2e75-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a2e75-108">.NET Framework Security</span></span>

<span data-ttu-id="a2e75-109">Upewnij się, że dane zapisane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a2e75-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="a2e75-110">Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="a2e75-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e75-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2e75-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="a2e75-112">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="a2e75-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="a2e75-113">Instrukcje: wyjątki dziennika</span><span class="sxs-lookup"><span data-stu-id="a2e75-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="a2e75-114">Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="a2e75-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a2e75-115">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="a2e75-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="a2e75-116">Przewodnik: filtrowanie danych wyjściowych My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="a2e75-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

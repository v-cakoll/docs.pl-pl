---
title: 'Instrukcje: zapisywanie komunikatów dziennika'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, writing log messages
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
ms.openlocfilehash: 28c5fe77e2711dfcac96e621a90fb9506eb74775
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410052"
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="f8ca6-102">Porady: zapisywanie wiadomości rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ca6-102">How to: Write Log Messages (Visual Basic)</span></span>

<span data-ttu-id="f8ca6-103">Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="f8ca6-104">Ten przykład pokazuje, jak używać `My.Application.Log.WriteEntry` metody do rejestrowania informacji o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>

<span data-ttu-id="f8ca6-105">Informacje o wyjątku rejestrowania można znaleźć w `My.Application.Log.WriteException` temacie [How to: log Exceptions](how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f8ca6-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

## <a name="example"></a><span data-ttu-id="f8ca6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8ca6-106">Example</span></span>

<span data-ttu-id="f8ca6-107">W tym przykładzie zastosowano `My.Application.Log.WriteEntry` metodę, aby napisać informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>

[!code-vb[VbVbalrMyApplicationLog#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#11)]

## <a name="net-framework-security"></a><span data-ttu-id="f8ca6-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f8ca6-108">.NET Framework Security</span></span>

<span data-ttu-id="f8ca6-109">Upewnij się, że dane zapisane w dzienniku nie zawierają poufnych informacji, takich jak hasła użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f8ca6-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="f8ca6-110">Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="f8ca6-110">For more information, see [Working with Application Logs](working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8ca6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8ca6-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="f8ca6-112">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="f8ca6-112">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="f8ca6-113">Instrukcje: rejestrowanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="f8ca6-113">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
- [<span data-ttu-id="f8ca6-114">Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="f8ca6-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="f8ca6-115">Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="f8ca6-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="f8ca6-116">Przewodnik: filtrowanie danych wyjściowych elementu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f8ca6-116">Walkthrough: Filtering My.Application.Log Output</span></span>](walkthrough-filtering-my-application-log-output.md)

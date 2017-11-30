---
title: "Porady: zapisywanie wiadomości rejestru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: My.Application.Log object, writing log messags
ms.assetid: 972a3e0c-2996-4623-a7a9-d7ebc4d207f8
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4d875fd4f95ca51fff565551009e780b17d07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-log-messages-visual-basic"></a><span data-ttu-id="351db-102">Porady: zapisywanie wiadomości rejestru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="351db-102">How to: Write Log Messages (Visual Basic)</span></span>
<span data-ttu-id="351db-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="351db-103">You can use the `My.Application.Log` and `My.Log` objects to log information about your application.</span></span> <span data-ttu-id="351db-104">Ten przykład przedstawia sposób użycia `My.Application.Log.WriteEntry` metody do rejestrowania informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="351db-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information.</span></span>  
  
 <span data-ttu-id="351db-105">Rejestrowanie informacji o wyjątku, użyj `My.Application.Log.WriteException` metody; zobacz [porady: wyjątki dziennika](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="351db-105">For logging exception information, use the `My.Application.Log.WriteException` method; see [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="351db-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="351db-106">Example</span></span>  
 <span data-ttu-id="351db-107">W tym przykładzie użyto `My.Application.Log.WriteEntry` metodę, aby zapisać informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="351db-107">This example uses the `My.Application.Log.WriteEntry` method to write out the trace information.</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#11](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-write-log-messages_1.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="351db-108">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="351db-108">.NET Framework Security</span></span>  
 <span data-ttu-id="351db-109">Upewnij się, że dane, które są zapisywane w dzienniku nie zawiera poufne informacje, takie jak hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="351db-109">Make sure the data you write to the log does not include sensitive information such as user passwords.</span></span> <span data-ttu-id="351db-110">Aby uzyskać więcej informacji, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="351db-110">For more information, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="351db-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="351db-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="351db-112">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="351db-112">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="351db-113">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="351db-113">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="351db-114">Wskazówki: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="351db-114">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="351db-115">Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="351db-115">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="351db-116">Wskazówki: Filtrowanie danych wyjściowych My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="351db-116">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)

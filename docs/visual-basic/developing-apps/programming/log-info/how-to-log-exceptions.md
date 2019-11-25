---
title: 'Porady: wyjątki rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352084"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="b0e43-102">Porady: wyjątki rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0e43-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="b0e43-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span><span class="sxs-lookup"><span data-stu-id="b0e43-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="b0e43-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span><span class="sxs-lookup"><span data-stu-id="b0e43-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="b0e43-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span><span class="sxs-lookup"><span data-stu-id="b0e43-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="b0e43-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="b0e43-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="b0e43-107">To log a handled exception</span><span class="sxs-lookup"><span data-stu-id="b0e43-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="b0e43-108">Create the method that will generate the exception information.</span><span class="sxs-lookup"><span data-stu-id="b0e43-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="b0e43-109">Use a `Try...Catch` block to catch the exception.</span><span class="sxs-lookup"><span data-stu-id="b0e43-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="b0e43-110">Put the code that could generate an exception in the `Try` block.</span><span class="sxs-lookup"><span data-stu-id="b0e43-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="b0e43-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span><span class="sxs-lookup"><span data-stu-id="b0e43-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="b0e43-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span><span class="sxs-lookup"><span data-stu-id="b0e43-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="b0e43-113">The following example shows the complete code for logging a handled exception.</span><span class="sxs-lookup"><span data-stu-id="b0e43-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="b0e43-114">To log an unhandled exception</span><span class="sxs-lookup"><span data-stu-id="b0e43-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="b0e43-115">Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="b0e43-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b0e43-116">On the **Project** menu, choose **Properties**.</span><span class="sxs-lookup"><span data-stu-id="b0e43-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="b0e43-117">Click the **Application** tab.</span><span class="sxs-lookup"><span data-stu-id="b0e43-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="b0e43-118">Click the **View Application Events** button to open the Code Editor.</span><span class="sxs-lookup"><span data-stu-id="b0e43-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="b0e43-119">This opens the ApplicationEvents.vb file.</span><span class="sxs-lookup"><span data-stu-id="b0e43-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="b0e43-120">Have the ApplicationEvents.vb file open in the Code Editor.</span><span class="sxs-lookup"><span data-stu-id="b0e43-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="b0e43-121">On the **General** menu, choose **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="b0e43-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="b0e43-122">On the **Declarations** menu, choose **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="b0e43-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="b0e43-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span><span class="sxs-lookup"><span data-stu-id="b0e43-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="b0e43-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span><span class="sxs-lookup"><span data-stu-id="b0e43-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="b0e43-125">The following example shows the complete code for logging an unhandled exception.</span><span class="sxs-lookup"><span data-stu-id="b0e43-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="b0e43-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0e43-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="b0e43-127">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="b0e43-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="b0e43-128">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="b0e43-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="b0e43-129">Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="b0e43-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="b0e43-130">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="b0e43-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

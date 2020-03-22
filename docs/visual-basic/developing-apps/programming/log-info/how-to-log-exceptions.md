---
title: 'Porady: wyjątki rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: fe6949d727fae0c230ce7421b32fdaf2a498edbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352084"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="667f7-102">Porady: wyjątki rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="667f7-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="667f7-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o wyjątkach, które występują w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="667f7-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="667f7-104">Te przykłady pokazują, `My.Application.Log.WriteException` jak używać metody do rejestrowania wyjątków, które można przechwyć jawnie i wyjątki, które są nieobsługiwał.</span><span class="sxs-lookup"><span data-stu-id="667f7-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="667f7-105">Aby rejestrować informacje o `My.Application.Log.WriteEntry` śledzeniu, użyj metody.</span><span class="sxs-lookup"><span data-stu-id="667f7-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="667f7-106">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="667f7-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="667f7-107">Aby zarejestrować obsługiwany wyjątek</span><span class="sxs-lookup"><span data-stu-id="667f7-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="667f7-108">Utwórz metodę, która wygeneruje informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="667f7-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="667f7-109">Użyj `Try...Catch` bloku, aby przechwyć wyjątek.</span><span class="sxs-lookup"><span data-stu-id="667f7-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="667f7-110">Umieść kod, który może wygenerować wyjątek w `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="667f7-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="667f7-111">`Dim` Odkomentuj `MsgBox` wiersze <xref:System.NullReferenceException> i spowodować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="667f7-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="667f7-112">W `Catch` bloku użyj `My.Application.Log.WriteException` metody, aby zapisać informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="667f7-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="667f7-113">W poniższym przykładzie przedstawiono pełny kod do rejestrowania obsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="667f7-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="667f7-114">Aby zarejestrować nieobsługiwalny wyjątek</span><span class="sxs-lookup"><span data-stu-id="667f7-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="667f7-115">Wybierz projekt w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="667f7-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="667f7-116">W menu **Projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="667f7-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="667f7-117">Kliknij kartę **Aplikacja.**</span><span class="sxs-lookup"><span data-stu-id="667f7-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="667f7-118">Kliknij przycisk **Wyświetl zdarzenia aplikacji,** aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="667f7-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="667f7-119">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="667f7-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="667f7-120">Otwórz plik ApplicationEvents.vb w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="667f7-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="667f7-121">W menu **Ogólne** wybierz polecenie **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="667f7-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="667f7-122">W menu **Deklaracje** wybierz polecenie **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="667f7-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="667f7-123">Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenie przed uruchomieniu aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="667f7-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="667f7-124">Dodaj `My.Application.Log.WriteException` metodę do `UnhandledException` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="667f7-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="667f7-125">W poniższym przykładzie przedstawiono pełny kod do rejestrowania nieobsługiwał wyjątek.</span><span class="sxs-lookup"><span data-stu-id="667f7-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="667f7-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="667f7-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="667f7-127">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="667f7-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="667f7-128">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="667f7-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="667f7-129">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="667f7-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="667f7-130">Wskazówki: zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="667f7-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

---
title: 'Instrukcje: Rejestruje wyjątki w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: bdbe9b1d05acdc0f67f0264ed1583dff922e527b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832661"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="51624-102">Instrukcje: Rejestruje wyjątki w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51624-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="51624-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o wyjątkach, które występują w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51624-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="51624-104">Te przykłady pokazują, jak używać `My.Application.Log.WriteException` metody do rejestrowania wyjątków, które można jawnie przechwycić i wyjątki, które są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="51624-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="51624-105">Rejestrowanie informacji śledzenia, użyj `My.Application.Log.WriteEntry` metody.</span><span class="sxs-lookup"><span data-stu-id="51624-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="51624-106">Aby uzyskać więcej informacji zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="51624-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="51624-107">Aby rejestrować obsługiwanego wyjątku</span><span class="sxs-lookup"><span data-stu-id="51624-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="51624-108">Utwórz metodę, która będzie generować informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51624-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2.  <span data-ttu-id="51624-109">Użyj `Try...Catch` bloku, aby przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="51624-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3.  <span data-ttu-id="51624-110">Umieść kod, który można wygenerować wyjątek `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="51624-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="51624-111">Usuń znaczniki komentarza `Dim` i `MsgBox` wierszy, aby spowodować, że <xref:System.NullReferenceException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51624-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4.  <span data-ttu-id="51624-112">W `Catch` blokowania, należy użyć `My.Application.Log.WriteException` metodę, aby zapisać informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51624-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="51624-113">Poniższy przykład pokazuje kompletny kod dla rejestrowania obsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="51624-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="51624-114">Do logowania się nieobsłużonego wyjątku</span><span class="sxs-lookup"><span data-stu-id="51624-114">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="51624-115">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="51624-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="51624-116">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="51624-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="51624-117">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="51624-117">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="51624-118">Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="51624-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="51624-119">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="51624-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="51624-120">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="51624-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="51624-121">Na **ogólne** menu, wybierz **zdarzenia MojaAplikacja**.</span><span class="sxs-lookup"><span data-stu-id="51624-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="51624-122">Na **deklaracje** menu, wybierz **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="51624-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="51624-123">Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzeń przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="51624-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="51624-124">Dodaj `My.Application.Log.WriteException` metody `UnhandledException` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="51624-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="51624-125">Poniższy przykład pokazuje kompletny kod dla rejestrowania nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="51624-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="51624-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51624-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="51624-127">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="51624-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="51624-128">Instrukcje: Zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="51624-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="51624-129">Przewodnik: Ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="51624-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="51624-130">Przewodnik: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="51624-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

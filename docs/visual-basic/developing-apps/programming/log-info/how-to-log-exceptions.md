---
title: 'Porady: wyjątki rejestru w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: b8ec45f43438f8181d9e045cdf43c81db34e4242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="5e4f2-102">Porady: wyjątki rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e4f2-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="5e4f2-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o wyjątków, które występują w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="5e4f2-104">Poniższe przykłady pokazują, jak użyć `My.Application.Log.WriteException` metody do rejestrowania wyjątków, które zostaną jawnie wychwycone i wyjątków, które są nieobsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="5e4f2-105">Rejestrowanie informacji śledzenia, użyj `My.Application.Log.WriteEntry` metody.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="5e4f2-106">Aby uzyskać więcej informacji zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="5e4f2-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="5e4f2-107">Aby rejestrować obsłużył wyjątek</span><span class="sxs-lookup"><span data-stu-id="5e4f2-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="5e4f2-108">Tworzenie metody, która będzie generować informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  <span data-ttu-id="5e4f2-109">Użyj `Try...Catch` bloku catch wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  <span data-ttu-id="5e4f2-110">Umieść kod, który można wygenerować wyjątek `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="5e4f2-111">Usuń znaczniki komentarza `Dim` i `MsgBox` wiersze spowodują <xref:System.NullReferenceException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  <span data-ttu-id="5e4f2-112">W `Catch` bloków, użyj `My.Application.Log.WriteException` metodę, aby zapisać informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     <span data-ttu-id="5e4f2-113">Poniższy przykład przedstawia kompletny kod dla rejestrowania obsłużył wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="5e4f2-114">Wystąpił nieobsługiwany wyjątek logowania</span><span class="sxs-lookup"><span data-stu-id="5e4f2-114">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="5e4f2-115">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5e4f2-116">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="5e4f2-117">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-117">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="5e4f2-118">Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="5e4f2-119">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="5e4f2-120">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="5e4f2-121">Na **ogólne** menu, wybierz **zdarzenia moja_aplikacja**.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="5e4f2-122">Na **deklaracje** menu, wybierz **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="5e4f2-123">Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzeń przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="5e4f2-124">Dodaj `My.Application.Log.WriteException` metodę `UnhandledException` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     <span data-ttu-id="5e4f2-125">Poniższy przykład przedstawia kompletny kod dla rejestrowania nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="5e4f2-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5e4f2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e4f2-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="5e4f2-127">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="5e4f2-127">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="5e4f2-128">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="5e4f2-128">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="5e4f2-129">Przewodnik: ustalanie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="5e4f2-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="5e4f2-130">Przewodnik: zmienianie lokalizacji, w której My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="5e4f2-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

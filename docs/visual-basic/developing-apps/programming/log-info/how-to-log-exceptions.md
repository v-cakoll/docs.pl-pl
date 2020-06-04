---
title: 'Instrukcje: rejestrowanie wyjątków'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
ms.openlocfilehash: 59ed7b836126a38f32b7c6f479570a566d236e6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410117"
---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="90089-102">Porady: wyjątki rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90089-102">How to: Log Exceptions in Visual Basic</span></span>

<span data-ttu-id="90089-103">Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o wyjątkach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="90089-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="90089-104">W poniższych przykładach pokazano, jak używać `My.Application.Log.WriteException` metody do rejestrowania wyjątków, które są przechwytywane jawnie, oraz wyjątków, które nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="90089-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="90089-105">Aby uzyskać informacje o śledzeniu rejestrowania, użyj `My.Application.Log.WriteEntry` metody.</span><span class="sxs-lookup"><span data-stu-id="90089-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="90089-106">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>.</span><span class="sxs-lookup"><span data-stu-id="90089-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="90089-107">Aby zarejestrować obsłużony wyjątek</span><span class="sxs-lookup"><span data-stu-id="90089-107">To log a handled exception</span></span>  
  
1. <span data-ttu-id="90089-108">Utwórz metodę, która będzie generować informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90089-108">Create the method that will generate the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#9)]  
  
2. <span data-ttu-id="90089-109">Użyj `Try...Catch` bloku, aby przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="90089-109">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#6)]  
  
3. <span data-ttu-id="90089-110">Umieść kod, który może generować wyjątek w `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="90089-110">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="90089-111">Usuń komentarz z `Dim` wierszy i, `MsgBox` Aby wywołać <xref:System.NullReferenceException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="90089-111">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#7)]  
  
4. <span data-ttu-id="90089-112">W `Catch` bloku Użyj `My.Application.Log.WriteException` metody, aby zapisać informacje o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90089-112">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#8)]  
  
     <span data-ttu-id="90089-113">Poniższy przykład pokazuje kompletny kod rejestrowania obsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90089-113">The following example shows the complete code for logging a handled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#10)]  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="90089-114">Aby zarejestrować nieobsłużony wyjątek</span><span class="sxs-lookup"><span data-stu-id="90089-114">To log an unhandled exception</span></span>  
  
1. <span data-ttu-id="90089-115">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="90089-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="90089-116">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="90089-116">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="90089-117">Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="90089-117">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="90089-118">Kliknij przycisk **Wyświetl zdarzenia aplikacji** , aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="90089-118">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="90089-119">Spowoduje to otwarcie pliku ApplicationEvents. vb.</span><span class="sxs-lookup"><span data-stu-id="90089-119">This opens the ApplicationEvents.vb file.</span></span>  
  
4. <span data-ttu-id="90089-120">Plik ApplicationEvents. vb jest otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="90089-120">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="90089-121">W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="90089-121">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5. <span data-ttu-id="90089-122">W menu **deklaracje** wybierz pozycję **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="90089-122">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="90089-123">Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> zdarzenie przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="90089-123">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6. <span data-ttu-id="90089-124">Dodaj `My.Application.Log.WriteException` metodę do `UnhandledException` procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="90089-124">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#4)]  
  
     <span data-ttu-id="90089-125">Poniższy przykład pokazuje kompletny kod rejestrowania nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="90089-125">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="90089-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90089-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="90089-127">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="90089-127">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="90089-128">Instrukcje: zapisywanie komunikatów dziennika</span><span class="sxs-lookup"><span data-stu-id="90089-128">How to: Write Log Messages</span></span>](how-to-write-log-messages.md)
- [<span data-ttu-id="90089-129">Przewodnik: ustalanie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="90089-129">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="90089-130">Przewodnik: zmienianie lokalizacji, w której element My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="90089-130">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](walkthrough-changing-where-my-application-log-writes-information.md)

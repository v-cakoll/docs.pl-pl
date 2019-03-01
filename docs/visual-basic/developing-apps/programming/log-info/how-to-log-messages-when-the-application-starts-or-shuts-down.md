---
title: 'Instrukcje: Komunikaty dziennika podczas uruchamiania aplikacji lub zamknięciu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 40236a1ab5daea0003fce0ad6e35e258a42cc405
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973928"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="aacad-102">Instrukcje: Komunikaty dziennika podczas uruchamiania aplikacji lub zamknięciu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aacad-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="aacad-103">Możesz użyć `My.Application.Log` i `My.Log` obiekty do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aacad-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="aacad-104">W tym przykładzie pokazano, jak używać `My.Application.Log.WriteEntry` metody z `Startup` i `Shutdown` zdarzenia do zapisania informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aacad-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="aacad-105">Dostęp do kodu programu obsługi zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="aacad-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="aacad-106">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="aacad-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="aacad-107">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="aacad-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="aacad-108">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="aacad-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="aacad-109">Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="aacad-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="aacad-110">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="aacad-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="aacad-111">Umożliwiają rejestrowanie wiadomości podczas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="aacad-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="aacad-112">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="aacad-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="aacad-113">Na **ogólne** menu, wybierz **zdarzenia MojaAplikacja**.</span><span class="sxs-lookup"><span data-stu-id="aacad-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="aacad-114">Na **deklaracje** menu, wybierz **uruchamiania**.</span><span class="sxs-lookup"><span data-stu-id="aacad-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="aacad-115">Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="aacad-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="aacad-116">Dodaj `My.Application.Log.WriteEntry` metody `Startup` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aacad-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="aacad-117">Aby rejestrowanie wiadomości podczas zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="aacad-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="aacad-118">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="aacad-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="aacad-119">Na **ogólne** menu, wybierz **zdarzenia MojaAplikacja**.</span><span class="sxs-lookup"><span data-stu-id="aacad-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="aacad-120">Na **deklaracje** menu, wybierz **zamknięcia**.</span><span class="sxs-lookup"><span data-stu-id="aacad-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="aacad-121">Wywołuje aplikację <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń po uruchomień aplikacji głównej, ale przed jego zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="aacad-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="aacad-122">Dodaj `My.Application.Log.WriteEntry` metody `Shutdown` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aacad-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="aacad-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="aacad-123">Example</span></span>  
 <span data-ttu-id="aacad-124">Możesz użyć **projektanta projektu** można uzyskiwać dostęp do zdarzeń aplikacji w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="aacad-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="aacad-125">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="aacad-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="aacad-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aacad-126">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="aacad-127">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aacad-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="aacad-128">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="aacad-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

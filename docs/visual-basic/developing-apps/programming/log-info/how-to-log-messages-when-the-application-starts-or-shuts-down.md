---
title: 'Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 80b07e67cb307d461e63df9f94c9d0962eb6374a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="3a6ce-102">Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="3a6ce-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="3a6ce-104">Ten przykład przedstawia sposób użycia `My.Application.Log.WriteEntry` metody z `Startup` i `Shutdown` zdarzeń w celu zapisania informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="3a6ce-105">Dostęp do kodu obsługi zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a6ce-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="3a6ce-106">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3a6ce-107">Na **projektu** menu, wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="3a6ce-108">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="3a6ce-109">Kliknij przycisk **Wyświetl zdarzenia aplikacji** przycisk, aby otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="3a6ce-110">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="3a6ce-111">Aby rejestrowanie wiadomości podczas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a6ce-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="3a6ce-112">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="3a6ce-113">Na **ogólne** menu, wybierz **zdarzenia moja_aplikacja**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="3a6ce-114">Na **deklaracje** menu, wybierz **uruchamiania**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="3a6ce-115">Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzeń przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="3a6ce-116">Dodaj `My.Application.Log.WriteEntry` metodę `Startup` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="3a6ce-117">Aby rejestrowanie wiadomości podczas zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a6ce-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="3a6ce-118">ApplicationEvents.vb plik zostać otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="3a6ce-119">Na **ogólne** menu, wybierz **zdarzenia moja_aplikacja**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="3a6ce-120">Na **deklaracje** menu, wybierz **zamknięcia**.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="3a6ce-121">Generuje aplikacji <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzeń po uruchomieniu aplikacji głównej, ale przed jego zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="3a6ce-122">Dodaj `My.Application.Log.WriteEntry` metodę `Shutdown` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3a6ce-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a6ce-123">Example</span></span>  
 <span data-ttu-id="3a6ce-124">Można użyć **projektanta projektu** do zdarzeń aplikacji w edytorze kodu dostępu.</span><span class="sxs-lookup"><span data-stu-id="3a6ce-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="3a6ce-125">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3a6ce-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3a6ce-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a6ce-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="3a6ce-127">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a6ce-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="3a6ce-128">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="3a6ce-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

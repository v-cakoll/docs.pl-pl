---
title: 'Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: 5a4ef3888ba8371d26204c3569b5fb9bae1f15f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352097"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="c7e46-102">Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e46-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="c7e46-103">Można użyć `My.Application.Log` i `My.Log` obiektów do rejestrowania informacji o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7e46-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="c7e46-104">W tym przykładzie `My.Application.Log.WriteEntry` pokazano, `Startup` jak `Shutdown` używać metody z i zdarzeń do zapisu informacji śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c7e46-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="c7e46-105">Aby uzyskać dostęp do kodu obsługi zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e46-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="c7e46-106">Wybierz projekt w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c7e46-107">W menu **Projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="c7e46-108">Kliknij kartę **Aplikacja.**</span><span class="sxs-lookup"><span data-stu-id="c7e46-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="c7e46-109">Kliknij przycisk **Wyświetl zdarzenia aplikacji,** aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="c7e46-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="c7e46-110">Spowoduje to otwarcie pliku ApplicationEvents.vb.</span><span class="sxs-lookup"><span data-stu-id="c7e46-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="c7e46-111">Aby rejestrować komunikaty po uruchomieniu aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e46-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="c7e46-112">Otwórz plik ApplicationEvents.vb w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="c7e46-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="c7e46-113">W menu **Ogólne** wybierz polecenie **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="c7e46-114">W menu **Deklaracje** wybierz polecenie **Uruchamianie**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="c7e46-115">Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenie przed uruchomieniu aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="c7e46-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="c7e46-116">Dodaj `My.Application.Log.WriteEntry` metodę do `Startup` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7e46-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="c7e46-117">Aby rejestrować komunikaty po zamknięciu aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e46-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="c7e46-118">Otwórz plik ApplicationEvents.vb w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="c7e46-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="c7e46-119">W menu **Ogólne** wybierz polecenie **MyApplication Events**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="c7e46-120">W menu **Deklaracje** wybierz polecenie **Zamknięcie**.</span><span class="sxs-lookup"><span data-stu-id="c7e46-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="c7e46-121">Aplikacja wywołuje <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenie po uruchomieniu głównej aplikacji, ale przed zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="c7e46-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="c7e46-122">Dodaj `My.Application.Log.WriteEntry` metodę do `Shutdown` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7e46-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="c7e46-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7e46-123">Example</span></span>  

 <span data-ttu-id="c7e46-124">**Projektantprojektu** można użyć, aby uzyskać dostęp do zdarzeń aplikacji w Edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="c7e46-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="c7e46-125">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c7e46-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c7e46-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7e46-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="c7e46-127">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e46-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="c7e46-128">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="c7e46-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

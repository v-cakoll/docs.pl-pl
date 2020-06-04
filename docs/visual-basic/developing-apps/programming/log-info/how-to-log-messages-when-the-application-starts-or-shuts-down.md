---
title: 'Instrukcje: rejestrowanie komunikatów podczas uruchamiania lub zamykania aplikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
ms.openlocfilehash: ac5fb17e527bcbcb55f98ec0ced06c152555ce6c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410078"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="81ca2-102">Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81ca2-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="81ca2-103">Za pomocą `My.Application.Log` obiektów i można `My.Log` rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="81ca2-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="81ca2-104">Ten przykład pokazuje, jak używać `My.Application.Log.WriteEntry` metody ze `Startup` `Shutdown` zdarzeniami i, aby pisać informacje o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="81ca2-105">Aby uzyskać dostęp do kodu programu obsługi zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="81ca2-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="81ca2-106">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="81ca2-107">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="81ca2-108">Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="81ca2-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="81ca2-109">Kliknij przycisk **Wyświetl zdarzenia aplikacji** , aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="81ca2-110">Spowoduje to otwarcie pliku ApplicationEvents. vb.</span><span class="sxs-lookup"><span data-stu-id="81ca2-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="81ca2-111">Aby rejestrować komunikaty podczas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="81ca2-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="81ca2-112">Plik ApplicationEvents. vb jest otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="81ca2-113">W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="81ca2-114">W menu **deklaracje** wybierz pozycję **Uruchamianie**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="81ca2-115">Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> zdarzenie przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="81ca2-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="81ca2-116">Dodaj `My.Application.Log.WriteEntry` metodę do `Startup` procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="81ca2-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="81ca2-117">Aby rejestrować komunikaty podczas zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="81ca2-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="81ca2-118">Plik ApplicationEvents. vb jest otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="81ca2-119">W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="81ca2-120">W menu **deklaracje** wybierz pozycję **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="81ca2-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="81ca2-121">Aplikacja zgłasza <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> zdarzenie po uruchomieniu aplikacji głównej, ale przed jej zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="81ca2-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="81ca2-122">Dodaj `My.Application.Log.WriteEntry` metodę do `Shutdown` procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="81ca2-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="81ca2-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="81ca2-123">Example</span></span>  

 <span data-ttu-id="81ca2-124">Możesz użyć **projektanta projektu** , aby uzyskać dostęp do zdarzeń aplikacji w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="81ca2-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="81ca2-125">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="81ca2-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="81ca2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81ca2-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="81ca2-127">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81ca2-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="81ca2-128">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="81ca2-128">Working with Application Logs</span></span>](working-with-application-logs.md)

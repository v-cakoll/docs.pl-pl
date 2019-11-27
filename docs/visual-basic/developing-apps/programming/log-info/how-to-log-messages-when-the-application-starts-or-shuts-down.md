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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352097"
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="d28b0-102">Porady: rejestrowanie wiadomości podczas uruchamiania lub wyłączania aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d28b0-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>

<span data-ttu-id="d28b0-103">Za pomocą obiektów `My.Application.Log` i `My.Log` można rejestrować informacje o zdarzeniach występujących w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d28b0-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="d28b0-104">Ten przykład pokazuje, jak używać metody `My.Application.Log.WriteEntry` ze zdarzeniami `Startup` i `Shutdown` do zapisywania informacji o śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="d28b0-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="d28b0-105">Aby uzyskać dostęp do kodu programu obsługi zdarzeń aplikacji</span><span class="sxs-lookup"><span data-stu-id="d28b0-105">To access the application's event-handler code</span></span>  
  
1. <span data-ttu-id="d28b0-106">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d28b0-107">W menu **projekt** wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2. <span data-ttu-id="d28b0-108">Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="d28b0-108">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="d28b0-109">Kliknij przycisk **Wyświetl zdarzenia aplikacji** , aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="d28b0-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="d28b0-110">Spowoduje to otwarcie pliku ApplicationEvents. vb.</span><span class="sxs-lookup"><span data-stu-id="d28b0-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="d28b0-111">Aby rejestrować komunikaty podczas uruchamiania aplikacji</span><span class="sxs-lookup"><span data-stu-id="d28b0-111">To log messages when the application starts</span></span>  
  
1. <span data-ttu-id="d28b0-112">Plik ApplicationEvents. vb jest otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d28b0-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="d28b0-113">W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="d28b0-114">W menu **deklaracje** wybierz pozycję **Uruchamianie**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="d28b0-115">Aplikacja zgłasza zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> przed uruchomieniem aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="d28b0-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3. <span data-ttu-id="d28b0-116">Dodaj metodę `My.Application.Log.WriteEntry` do procedury obsługi zdarzeń `Startup`.</span><span class="sxs-lookup"><span data-stu-id="d28b0-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#1)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="d28b0-117">Aby rejestrować komunikaty podczas zamykania aplikacji</span><span class="sxs-lookup"><span data-stu-id="d28b0-117">To log messages when the application shuts down</span></span>  
  
1. <span data-ttu-id="d28b0-118">Plik ApplicationEvents. vb jest otwarty w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d28b0-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="d28b0-119">W menu **Ogólne** wybierz pozycję **zdarzenia aplikacji**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2. <span data-ttu-id="d28b0-120">W menu **deklaracje** wybierz pozycję **Zamknij**.</span><span class="sxs-lookup"><span data-stu-id="d28b0-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="d28b0-121">Aplikacja zgłasza zdarzenie <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> po uruchomieniu aplikacji głównej, ale przed jej zamknięciem.</span><span class="sxs-lookup"><span data-stu-id="d28b0-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3. <span data-ttu-id="d28b0-122">Dodaj metodę `My.Application.Log.WriteEntry` do procedury obsługi zdarzeń `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="d28b0-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="d28b0-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="d28b0-123">Example</span></span>  

 <span data-ttu-id="d28b0-124">Możesz użyć **projektanta projektu** , aby uzyskać dostęp do zdarzeń aplikacji w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="d28b0-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="d28b0-125">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d28b0-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/MyEventsFake.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d28b0-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d28b0-126">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="d28b0-127">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d28b0-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="d28b0-128">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="d28b0-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

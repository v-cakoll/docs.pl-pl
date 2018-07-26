---
title: 'Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: a96641e6dd42e033f2d28b847fc071dfc514912d
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937000"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f82a9-102">Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="f82a9-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="f82a9-103">Wiele składników zapewniają możliwość wykonywania pracy asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f82a9-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="f82a9-104"><xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> składników, na przykład włączyć ładowanie dźwięków i obrazy "w tle" nadal działa bez przerwy z wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="f82a9-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="f82a9-105">Używanie metod asynchronicznych klasy, która obsługuje [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) mogą być proste i polega na dołączanie programu obsługi zdarzeń do składnika *MethodName *** Ukończono** zdarzenia Podobnie jak każde inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f82a9-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName***Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="f82a9-106">Gdy wywołujesz *MethodName *** Async** metody, aplikacja będzie nadal działa nieprzerwanie aż do *MethodName *** Ukończono** zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="f82a9-106">When you call the *MethodName***Async** method, your application will continue running without interruption until the *MethodName***Completed** event is raised.</span></span> <span data-ttu-id="f82a9-107">W przypadku obsługi zdarzenia, można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametru, aby określić, czy pomyślnie Ukończono operację asynchroniczną, czy został anulowany.</span><span class="sxs-lookup"><span data-stu-id="f82a9-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="f82a9-108">Aby uzyskać więcej informacji o używaniu procedur obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f82a9-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="f82a9-109">Poniższa procedura przedstawia sposób użycia asynchronicznego możliwości ładowania obrazu <xref:System.Windows.Forms.PictureBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="f82a9-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="f82a9-110">Aby włączyć formant PictureBox, aby asynchronicznie załadować obrazu</span><span class="sxs-lookup"><span data-stu-id="f82a9-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="f82a9-111">Utwórz wystąpienie obiektu <xref:System.Windows.Forms.PictureBox> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="f82a9-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="f82a9-112">Program obsługi zdarzeń, aby przypisać <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f82a9-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="f82a9-113">Sprawdź, czy wszystkie błędy, które mogły wystąpić podczas asynchronicznego pobierania w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="f82a9-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="f82a9-114">Jest to również, gdzie sprawdzania występowania unieważnienia.</span><span class="sxs-lookup"><span data-stu-id="f82a9-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="f82a9-115">Dodaje dwa przyciski, o nazwie `loadButton` i `cancelLoadButton`, do formularza.</span><span class="sxs-lookup"><span data-stu-id="f82a9-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="f82a9-116">Dodaj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń, aby uruchomić i anulować pobieranie.</span><span class="sxs-lookup"><span data-stu-id="f82a9-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="f82a9-117">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f82a9-117">Run your application.</span></span>  
  
     <span data-ttu-id="f82a9-118">W trakcie wykonywania pobrania obrazu można swobodnie przemieszczać się formularz, zminimalizować i zmaksymalizować go.</span><span class="sxs-lookup"><span data-stu-id="f82a9-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82a9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f82a9-119">See Also</span></span>  
 [<span data-ttu-id="f82a9-120">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="f82a9-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="f82a9-121">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="f82a9-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="f82a9-122">Wielowątkowość w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f82a9-122">Multithreading in Visual Basic</span></span>](../../../docs/visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)

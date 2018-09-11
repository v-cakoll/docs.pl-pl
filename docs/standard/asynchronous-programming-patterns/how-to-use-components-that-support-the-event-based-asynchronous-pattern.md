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
ms.openlocfilehash: e11bf8af6f56cbdcdcc920cafe145edcf744efed
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337515"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="74652-102">Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="74652-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="74652-103">Wiele składników zapewniają możliwość wykonywania pracy asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="74652-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="74652-104"><xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> składników, na przykład włączyć ładowanie dźwięków i obrazy "w tle" nadal działa bez przerwy z wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="74652-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="74652-105">Używanie metod asynchronicznych klasy, która obsługuje [oparte na zdarzeniach asynchronicznych omówienie wzorca](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) mogą być proste i polega na dołączanie programu obsługi zdarzeń do składnika _MethodName_  **Ukończono** zdarzenia, tak jak dowolne inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="74652-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="74652-106">Gdy wywołujesz _MethodName_**Async** metody, aplikacja będzie nadal działa nieprzerwanie aż do _MethodName_**Ukończono** zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="74652-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="74652-107">W przypadku obsługi zdarzenia, można sprawdzić <xref:System.ComponentModel.AsyncCompletedEventArgs> parametru, aby określić, czy pomyślnie Ukończono operację asynchroniczną, czy został anulowany.</span><span class="sxs-lookup"><span data-stu-id="74652-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="74652-108">Aby uzyskać więcej informacji o używaniu procedur obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="74652-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="74652-109">Poniższa procedura przedstawia sposób użycia asynchronicznego możliwości ładowania obrazu <xref:System.Windows.Forms.PictureBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="74652-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="74652-110">Aby włączyć formant PictureBox, aby asynchronicznie załadować obrazu</span><span class="sxs-lookup"><span data-stu-id="74652-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="74652-111">Utwórz wystąpienie obiektu <xref:System.Windows.Forms.PictureBox> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="74652-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="74652-112">Program obsługi zdarzeń, aby przypisać <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74652-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="74652-113">Sprawdź, czy wszystkie błędy, które mogły wystąpić podczas asynchronicznego pobierania w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="74652-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="74652-114">Jest to również, gdzie sprawdzania występowania unieważnienia.</span><span class="sxs-lookup"><span data-stu-id="74652-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="74652-115">Dodaje dwa przyciski, o nazwie `loadButton` i `cancelLoadButton`, do formularza.</span><span class="sxs-lookup"><span data-stu-id="74652-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="74652-116">Dodaj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń, aby uruchomić i anulować pobieranie.</span><span class="sxs-lookup"><span data-stu-id="74652-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="74652-117">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="74652-117">Run your application.</span></span>  
  
     <span data-ttu-id="74652-118">W trakcie wykonywania pobrania obrazu można swobodnie przemieszczać się formularz, zminimalizować i zmaksymalizować go.</span><span class="sxs-lookup"><span data-stu-id="74652-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74652-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74652-119">See also</span></span>

- [<span data-ttu-id="74652-120">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="74652-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [<span data-ttu-id="74652-121">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="74652-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  

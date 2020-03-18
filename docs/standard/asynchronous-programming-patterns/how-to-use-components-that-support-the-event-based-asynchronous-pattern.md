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
ms.openlocfilehash: 9ac98b5c576c065f8944714c72b492539e0d2f05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "61870243"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="9d18d-102">Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="9d18d-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="9d18d-103">Wiele składników zapewnia możliwość wykonywania ich pracy asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="9d18d-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="9d18d-104"><xref:System.Media.SoundPlayer> Komponenty <xref:System.Windows.Forms.PictureBox> i, na przykład, umożliwiają ładowanie dźwięków i obrazów "w tle", podczas gdy główny wątek nadal działa bez przerwy.</span><span class="sxs-lookup"><span data-stu-id="9d18d-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="9d18d-105">Przy użyciu metod asynchronicznych w klasie, która obsługuje [omówienie wzorca asynchronicznego opartego](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) na zdarzeniach może być tak proste, jak dołączanie programu obsługi zdarzeń do zdarzenia _MethodName_**Complete** składnika, tak jak w przypadku każdego innego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9d18d-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="9d18d-106">Po wywołaniu _MethodName_**Async** metody, aplikacja będzie nadal działać bez przerwy, dopóki _MethodName_**Completed** zdarzenie zostanie podniesiona.</span><span class="sxs-lookup"><span data-stu-id="9d18d-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="9d18d-107">W programie obsługi zdarzeń <xref:System.ComponentModel.AsyncCompletedEventArgs> można sprawdzić parametr, aby ustalić, czy operacja asynchroniczna została pomyślnie ukończona lub czy została anulowana.</span><span class="sxs-lookup"><span data-stu-id="9d18d-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="9d18d-108">Aby uzyskać więcej informacji na temat korzystania z programów obsługi zdarzeń, zobacz [Omówienie programów obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9d18d-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="9d18d-109">W poniższej procedurze pokazano, jak używać asynchronicznej możliwości ładowania obrazu formantu. <xref:System.Windows.Forms.PictureBox></span><span class="sxs-lookup"><span data-stu-id="9d18d-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="9d18d-110">Aby włączyć formant PictureBox do asynchronicznie załadować obraz</span><span class="sxs-lookup"><span data-stu-id="9d18d-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="9d18d-111">Utwórz wystąpienie <xref:System.Windows.Forms.PictureBox> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="9d18d-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="9d18d-112">Przypisz program obsługi <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9d18d-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="9d18d-113">Sprawdź, czy nie wystąpiły błędy podczas pobierania asynchronicznego tutaj.</span><span class="sxs-lookup"><span data-stu-id="9d18d-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="9d18d-114">W tym miejscu można również sprawdzić możliwość anulowania.</span><span class="sxs-lookup"><span data-stu-id="9d18d-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. <span data-ttu-id="9d18d-115">Dodaj dwa przyciski, o nazwie `loadButton` i `cancelLoadButton`, do formularza.</span><span class="sxs-lookup"><span data-stu-id="9d18d-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="9d18d-116">Dodaj <xref:System.Windows.Forms.Control.Click> programy obsługi zdarzeń, aby rozpocząć i anulować pobieranie.</span><span class="sxs-lookup"><span data-stu-id="9d18d-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. <span data-ttu-id="9d18d-117">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="9d18d-117">Run your application.</span></span>  
  
     <span data-ttu-id="9d18d-118">W miarę pobierania obrazu można swobodnie przenosić formularz, minimalizować go i zmaksymalizować.</span><span class="sxs-lookup"><span data-stu-id="9d18d-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d18d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d18d-119">See also</span></span>

- [<span data-ttu-id="9d18d-120">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="9d18d-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="9d18d-121">Asynchroniczny wzorzec oparty na zdarzeniach — przegląd</span><span class="sxs-lookup"><span data-stu-id="9d18d-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)

---
title: "Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dd5371c8ce80383e2929099c9d9658694858f8df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="753d2-102">Porady: używanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="753d2-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="753d2-103">Wiele składników dają możliwość wykonywania pracy asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="753d2-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="753d2-104"><xref:System.Media.SoundPlayer> i <xref:System.Windows.Forms.PictureBox> składników, na przykład umożliwiają ładowania dźwięki i obrazy "w tle", gdy z wątku głównego będzie kontynuował działanie bez przeszkód.</span><span class="sxs-lookup"><span data-stu-id="753d2-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="753d2-105">Używanie metod asynchronicznych klasy, która obsługuje [oparty na zdarzeniach asynchroniczny wzorzec — Przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) może być prosty jak dołączanie program obsługi zdarzeń do składnika *MethodName *** Ukończono** zdarzenia Podobnie jak inne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="753d2-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's *MethodName***Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="753d2-106">Podczas wywoływania *MethodName *** Async** metody, aplikacja będzie nadal działa nieprzerwanie aż do *MethodName *** Ukończono** zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="753d2-106">When you call the *MethodName***Async** method, your application will continue running without interruption until the *MethodName***Completed** event is raised.</span></span> <span data-ttu-id="753d2-107">W przypadku obsługi zdarzenia należy zbadać <xref:System.ComponentModel.AsyncCompletedEventArgs> parametr, aby określić, czy pomyślnie Ukończono operację asynchroniczną, czy została anulowana.</span><span class="sxs-lookup"><span data-stu-id="753d2-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="753d2-108">Aby uzyskać więcej informacji o korzystaniu z obsługi zdarzeń, zobacz [Przegląd obsługi zdarzeń](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="753d2-108">For more information about using event handlers, see [Event Handlers Overview](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).</span></span>  
  
 <span data-ttu-id="753d2-109">Poniższa procedura przedstawia sposób użycia możliwości asynchroniczne ładowanie obrazu <xref:System.Windows.Forms.PictureBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="753d2-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="753d2-110">Aby włączyć formantu PictureBox asynchroniczne ładowanie obrazu</span><span class="sxs-lookup"><span data-stu-id="753d2-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1.  <span data-ttu-id="753d2-111">Utwórz wystąpienie <xref:System.Windows.Forms.PictureBox> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="753d2-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2.  <span data-ttu-id="753d2-112">Program obsługi zdarzeń, aby przypisać <xref:System.Windows.Forms.PictureBox.LoadCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="753d2-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="753d2-113">Sprawdź, czy wszystkie błędy, które mogły wystąpić podczas asynchronicznego pobierania w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="753d2-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="753d2-114">Jest to również, gdzie sprawdzaj anulowania.</span><span class="sxs-lookup"><span data-stu-id="753d2-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  <span data-ttu-id="753d2-115">Dodawanie przycisków, nazywany `loadButton` i `cancelLoadButton`, do formularza.</span><span class="sxs-lookup"><span data-stu-id="753d2-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="753d2-116">Dodaj <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń, aby uruchomić i anulować pobieranie.</span><span class="sxs-lookup"><span data-stu-id="753d2-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="753d2-117">Uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="753d2-117">Run your application.</span></span>  
  
     <span data-ttu-id="753d2-118">W trakcie wykonywania pobrania obrazu można swobodnie przemieszczać się formularz, zminimalizować i zmaksymalizować go.</span><span class="sxs-lookup"><span data-stu-id="753d2-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753d2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="753d2-119">See Also</span></span>  
 [<span data-ttu-id="753d2-120">Instrukcje: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="753d2-120">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="753d2-121">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="753d2-121">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="753d2-122">NIE w kompilacji: Wielowątkowość w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="753d2-122">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)

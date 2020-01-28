---
title: 'Instrukcje: łączenie wielu zdarzeń z pojedynczym programem obsługi zdarzeń'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739608"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="78983-102">Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="78983-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="78983-103">W projekcie aplikacji może być konieczne użycie jednego programu obsługi zdarzeń dla wielu zdarzeń lub wykonanie tej samej procedury przez wiele zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="78983-104">Na przykład często zaawansowaną funkcją oszczędzania czasu jest to, że polecenie menu podnosi takie samo zdarzenie jak przycisk w formularzu, jeśli uwidacznia te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="78983-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="78983-105">Można to zrobić za pomocą widoku zdarzeń okno Właściwości w C# lub przy użyciu słowa kluczowego `Handles` i pola listy rozwijanej **Nazwa klasy** i **Metoda** w edytorze kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="78983-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="78983-106">Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="78983-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="78983-107">Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="78983-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="78983-108">W polu listy rozwijanej **Nazwa klasy** wybierz jedną z formantów, które mają być obsługiwane przez procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="78983-109">W polu listy rozwijanej **Nazwa metody** wybierz jedno z zdarzeń, które ma być obsługiwane przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="78983-110">Edytor kodu wstawia odpowiednią procedurę obsługi zdarzeń i ustawia punkt wstawiania w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="78983-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="78983-111">W poniższym przykładzie jest to zdarzenie <xref:System.Windows.Forms.Control.Click> dla kontrolki <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="78983-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="78983-112">Dołącz inne zdarzenia, które mają być obsługiwane w klauzuli `Handles`.</span><span class="sxs-lookup"><span data-stu-id="78983-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="78983-113">Dodaj odpowiedni kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="78983-114">Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w języku C\#</span><span class="sxs-lookup"><span data-stu-id="78983-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="78983-115">Wybierz kontrolkę, z którą chcesz połączyć procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="78983-116">W okno Właściwości kliknij przycisk **zdarzenia** (![przycisk zdarzenia](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="78983-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="78983-117">Kliknij nazwę zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="78983-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="78983-118">W sekcji wartość obok nazwy zdarzenia kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń, które pasują do sygnatury metody dla zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="78983-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="78983-119">Wybierz odpowiednią procedurę obsługi zdarzeń z listy.</span><span class="sxs-lookup"><span data-stu-id="78983-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="78983-120">Kod zostanie dodany do formularza w celu powiązania zdarzenia z istniejącym programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="78983-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78983-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78983-121">See also</span></span>

- [<span data-ttu-id="78983-122">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="78983-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="78983-123">Przegląd procedur obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="78983-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)

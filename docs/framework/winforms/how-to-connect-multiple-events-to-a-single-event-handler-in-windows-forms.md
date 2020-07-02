---
title: 'Instrukcje: łączenie wielu zdarzeń z pojedynczym programem obsługi zdarzeń'
description: Dowiedz się, jak połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Windows Forms przy użyciu widoku zdarzeń okno Właściwości w języku C#.
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
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621889"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="52887-103">Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="52887-103">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="52887-104">W projekcie aplikacji może być konieczne użycie jednego programu obsługi zdarzeń dla wielu zdarzeń lub wykonanie tej samej procedury przez wiele zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-104">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="52887-105">Na przykład często zaawansowaną funkcją oszczędzania czasu jest to, że polecenie menu podnosi takie samo zdarzenie jak przycisk w formularzu, jeśli uwidacznia te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="52887-105">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="52887-106">Można to zrobić za pomocą widoku zdarzeń okno Właściwości w języku C# lub przy użyciu `Handles` słowa kluczowego oraz pól rozwijanych **Nazwa klasy** i **metoda** w edytorze kodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="52887-106">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="52887-107">Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52887-107">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="52887-108">Kliknij prawym przyciskiem myszy formularz i wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="52887-108">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="52887-109">W polu listy rozwijanej **Nazwa klasy** wybierz jedną z formantów, które mają być obsługiwane przez procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-109">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="52887-110">W polu listy rozwijanej **Nazwa metody** wybierz jedno z zdarzeń, które ma być obsługiwane przez program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-110">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="52887-111">Edytor kodu wstawia odpowiednią procedurę obsługi zdarzeń i ustawia punkt wstawiania w ramach metody.</span><span class="sxs-lookup"><span data-stu-id="52887-111">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="52887-112">W poniższym przykładzie jest to <xref:System.Windows.Forms.Control.Click> zdarzenie dla <xref:System.Windows.Forms.Button> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="52887-112">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="52887-113">Dołącz inne zdarzenia, które chcesz obsłużyć do `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="52887-113">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="52887-114">Dodaj odpowiedni kod do programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-114">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="52887-115">Aby połączyć wiele zdarzeń z jednym programem obsługi zdarzeń w języku C\#</span><span class="sxs-lookup"><span data-stu-id="52887-115">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="52887-116">Wybierz kontrolkę, z którą chcesz połączyć procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-116">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="52887-117">W okno Właściwości kliknij przycisk **zdarzenia** (![przycisk zdarzenia](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="52887-117">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="52887-118">Kliknij nazwę zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="52887-118">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="52887-119">W sekcji wartość obok nazwy zdarzenia kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń, które pasują do sygnatury metody dla zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="52887-119">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="52887-120">Wybierz odpowiednią procedurę obsługi zdarzeń z listy.</span><span class="sxs-lookup"><span data-stu-id="52887-120">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="52887-121">Kod zostanie dodany do formularza w celu powiązania zdarzenia z istniejącym programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52887-121">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52887-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52887-122">See also</span></span>

- [<span data-ttu-id="52887-123">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="52887-123">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="52887-124">Przegląd programów obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="52887-124">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)

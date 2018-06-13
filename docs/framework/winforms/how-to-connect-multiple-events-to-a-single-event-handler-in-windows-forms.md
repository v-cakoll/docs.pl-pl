---
title: 'Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows'
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
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538583"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="c227c-102">Porady: łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c227c-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="c227c-103">W projekcie aplikacji może być konieczne użycie obsługą jednego zdarzenia dla wielu zdarzeń lub ma wiele zdarzeń wykonanie tej procedury.</span><span class="sxs-lookup"><span data-stu-id="c227c-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="c227c-104">Na przykład często jest zaawansowanym oszczędność czasu do polecenia wywołaj zdarzenie sam, jak przycisk w formularzu, jeśli udostępniają te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="c227c-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="c227c-105">Aby to zrobić, za pomocą widoku zdarzeń okna właściwości w języku C# lub `Handles` — słowo kluczowe i **Nazwa klasy** i **nazwę metody** list rozwijanych w edytorze kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c227c-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="c227c-106">Aby połączyć wiele zdarzeń do jednego zdarzenia programu obsługi w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c227c-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="c227c-107">Kliknij prawym przyciskiem myszy formularz, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="c227c-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="c227c-108">Z **Nazwa klasy** pole listy rozwijanej, wybierz jedną z formantów, które chcesz, aby obsłużyć programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c227c-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="c227c-109">Z **nazwę metody** pole listy rozwijanej, wybierz jedną z zdarzenia, które ma być obsługi program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c227c-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="c227c-110">Edytor kodu wstawia programu obsługi zdarzeń odpowiednie i umieszcza kursor w metodzie.</span><span class="sxs-lookup"><span data-stu-id="c227c-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="c227c-111">W poniższym przykładzie jest <xref:System.Windows.Forms.Control.Click> zdarzenia dla <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="c227c-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="c227c-112">Dołącz inne zdarzenia chcesz dla właściwości handled `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c227c-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="c227c-113">Dodaj odpowiedni kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c227c-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="c227c-114">Aby połączyć wiele zdarzeń do jednego zdarzenia programu obsługi w języku C#</span><span class="sxs-lookup"><span data-stu-id="c227c-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="c227c-115">Wybierz kontrolkę, z którym chcesz się połączyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c227c-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="c227c-116">Kliknij w oknie właściwości **zdarzenia** przycisk (![przycisk zdarzeń](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="c227c-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="c227c-117">Kliknij nazwę zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c227c-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="c227c-118">W sekcji wartość obok nazwy zdarzenia kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń zgodnych podpis metody zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="c227c-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="c227c-119">Program obsługi zdarzeń odpowiednie wybierz z listy.</span><span class="sxs-lookup"><span data-stu-id="c227c-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="c227c-120">Kod zostanie dodany do formularza, aby powiązać zdarzenia istniejącego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c227c-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c227c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c227c-121">See Also</span></span>  
 [<span data-ttu-id="c227c-122">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c227c-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="c227c-123">Przegląd procedur obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c227c-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)

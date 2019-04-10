---
title: 'Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms'
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
ms.openlocfilehash: eec6a754b885cd169e5542221caefb3233c4c8af
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300726"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="aa3c2-102">Instrukcje: Łączenie wielu zdarzeń z jednym programem obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="aa3c2-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="aa3c2-103">W projekcie aplikacji może okazać się niezbędne do obsługi pojedynczego zdarzenia na użytek wielu zdarzeń lub ma wiele zdarzeń, wykonaj tę samą procedurę.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="aa3c2-104">Na przykład często jest zaawansowane oszczędność czasu do polecenia podnieść te same zdarzenia, jak przycisk w formularzu, jeśli eksponowanie taką samą funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="aa3c2-105">Można to zrobić, korzystając z widoku zdarzenia w oknie właściwości w C# lub za pomocą `Handles` — słowo kluczowe i **Nazwa klasy** i **nazwę metody** list rozwijanych w edytorze kodu języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="aa3c2-106">Aby połączyć wiele zdarzeń do obsługi pojedynczego zdarzenia w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa3c2-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1. <span data-ttu-id="aa3c2-107">Kliknij prawym przyciskiem myszy formularz, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-107">Right-click the form and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="aa3c2-108">Z **Nazwa klasy** listy rozwijanej, wybierz jeden z elementów sterujących, które chcesz mieć obsługi program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3. <span data-ttu-id="aa3c2-109">Z **nazwę metody** listy rozwijanej, wybierz jedną z zdarzenia, które chcesz, aby program obsługi zdarzeń do obsługi.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4. <span data-ttu-id="aa3c2-110">Edytor kodu wstawia obsługi odpowiednie zdarzenia i umieszcza kursor w metodzie.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="aa3c2-111">W poniższym przykładzie jest <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. <span data-ttu-id="aa3c2-112">Dołącz innych zdarzeń chcesz użyte do `Handles` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. <span data-ttu-id="aa3c2-113">Dodaj odpowiedni kod do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="aa3c2-114">Aby połączyć wiele zdarzeń do obsługi pojedynczego zdarzenia w języku C\#</span><span class="sxs-lookup"><span data-stu-id="aa3c2-114">To connect multiple events to a single event handler in C\#</span></span>
  
1. <span data-ttu-id="aa3c2-115">Wybierz kontrolkę, do którego chcesz się połączyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-115">Select the control to which you want to connect an event handler.</span></span>  
  
2. <span data-ttu-id="aa3c2-116">W oknie dialogowym właściwości kliknij **zdarzenia** przycisku (![przycisk zdarzeń](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span><span class="sxs-lookup"><span data-stu-id="aa3c2-116">In the Properties window, click the **Events** button (![Events Button](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3. <span data-ttu-id="aa3c2-117">Kliknij nazwę zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-117">Click the name of the event that you want to handle.</span></span>  
  
4. <span data-ttu-id="aa3c2-118">W sekcji wartość obok nazwy zdarzeń kliknij przycisk listy rozwijanej, aby wyświetlić listę istniejących programów obsługi zdarzeń, które pasuje do podpisu metody, zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5. <span data-ttu-id="aa3c2-119">Wybierz odpowiednie zdarzenie obsługi z listy.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="aa3c2-120">Kod zostanie dodany do formularza, aby powiązać zdarzenia istniejącego programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aa3c2-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3c2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa3c2-121">See also</span></span>

- [<span data-ttu-id="aa3c2-122">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="aa3c2-122">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="aa3c2-123">Przegląd programów obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="aa3c2-123">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)

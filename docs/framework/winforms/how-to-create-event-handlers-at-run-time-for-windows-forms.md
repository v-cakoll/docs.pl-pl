---
title: 'Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 3c1dca420b9e63fe8a2cb93b2e7918d9dc35e84d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158551"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="85e83-102">Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85e83-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="85e83-103">Oprócz tworzenia zdarzeń za pomocą programu Windows Forms Designer, możesz również utworzyć program obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="85e83-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="85e83-104">Ta akcja umożliwia łączenie programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, a nie po ich połączone po początkowym uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="85e83-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="85e83-105">Aby utworzyć program obsługi zdarzeń w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="85e83-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="85e83-106">Otwórz formularz w edytorze kodu, którą chcesz dodać program obsługi zdarzeń do.</span><span class="sxs-lookup"><span data-stu-id="85e83-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="85e83-107">Dodaj metodę do formularza przy użyciu podpisu metody dla zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="85e83-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="85e83-108">Na przykład, jeśli zostały obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> kontrolki, należy utworzyć metodę podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="85e83-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  <span data-ttu-id="85e83-109">Dodaj kod do narzędzia obsługi zdarzeń, odpowiednio do swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="85e83-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="85e83-110">Ustal, które formularza lub kontrolki, w której chcesz utworzyć program obsługi zdarzeń dla.</span><span class="sxs-lookup"><span data-stu-id="85e83-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="85e83-111">W przypadku metody w klasie formularza Dodaj kod, który określa program obsługi zdarzeń, aby obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="85e83-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="85e83-112">Na przykład, poniższy kod określa program obsługi zdarzeń `button1_Click` uchwyty <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> sterowania:</span><span class="sxs-lookup"><span data-stu-id="85e83-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="85e83-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda pokazano w powyższym kodzie języka Visual Basic ustanawia obsługi zdarzeń kliknięcia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="85e83-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e83-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85e83-114">See also</span></span>

- [<span data-ttu-id="85e83-115">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="85e83-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="85e83-116">Przegląd programów obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="85e83-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="85e83-117">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85e83-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)

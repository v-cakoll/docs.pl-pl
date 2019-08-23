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
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964333"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="34a4e-102">Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34a4e-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="34a4e-103">Oprócz tworzenia zdarzeń przy użyciu Projektant formularzy systemu Windows w programie Visual Studio, można również utworzyć procedurę obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34a4e-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="34a4e-104">Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, które nie są połączone podczas początkowego uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="34a4e-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="34a4e-105">Utwórz procedurę obsługi zdarzeń w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="34a4e-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="34a4e-106">Otwórz formularz, do którego chcesz dodać procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="34a4e-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="34a4e-107">Dodaj metodę do formularza z podpisem metody dla zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="34a4e-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="34a4e-108">Na przykład w przypadku obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> kontrolki należy utworzyć metodę taką jak następujące:</span><span class="sxs-lookup"><span data-stu-id="34a4e-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="34a4e-109">Dodaj kod do programu obsługi zdarzeń odpowiednio do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34a4e-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="34a4e-110">Określ formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="34a4e-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="34a4e-111">W metodzie w klasie formularza Dodaj kod, który określa procedurę obsługi zdarzeń, aby obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="34a4e-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="34a4e-112">Na przykład poniższy kod określa, że program obsługi `button1_Click` zdarzeń <xref:System.Windows.Forms.Control.Click> obsługuje zdarzenie <xref:System.Windows.Forms.Button> formantu:</span><span class="sxs-lookup"><span data-stu-id="34a4e-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="34a4e-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda pokazana w kodzie Visual Basic powyżej określa procedurę obsługi zdarzeń kliknięcia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="34a4e-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="34a4e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34a4e-114">See also</span></span>

- [<span data-ttu-id="34a4e-115">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="34a4e-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="34a4e-116">Przegląd procedur obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="34a4e-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="34a4e-117">Rozwiązywanie problemów z dziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34a4e-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)

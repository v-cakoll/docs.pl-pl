---
title: 'Instrukcje: tworzenie programów obsługi zdarzeń w czasie wykonywania'
description: Dowiedz się, jak utworzyć procedurę obsługi zdarzeń w czasie wykonywania przy użyciu Projektant formularzy systemu Windows w programie Visual Studio. Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń w czasie wykonywania.
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
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325807"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="573e0-104">Instrukcje: Tworzenie programów obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="573e0-104">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="573e0-105">Oprócz tworzenia zdarzeń przy użyciu Projektant formularzy systemu Windows w programie Visual Studio, można również utworzyć procedurę obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="573e0-105">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="573e0-106">Ta akcja umożliwia nawiązanie połączenia programów obsługi zdarzeń na podstawie warunków w kodzie w czasie wykonywania, które nie są połączone podczas początkowego uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="573e0-106">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="573e0-107">Utwórz procedurę obsługi zdarzeń w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="573e0-107">Create an event handler at run time</span></span>

1. <span data-ttu-id="573e0-108">Otwórz formularz, do którego chcesz dodać procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="573e0-108">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="573e0-109">Dodaj metodę do formularza z podpisem metody dla zdarzenia, które chcesz obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="573e0-109">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="573e0-110">Na przykład w przypadku obsługi <xref:System.Windows.Forms.Control.Click> zdarzenia <xref:System.Windows.Forms.Button> kontrolki należy utworzyć metodę taką jak następujące:</span><span class="sxs-lookup"><span data-stu-id="573e0-110">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="573e0-111">Dodaj kod do programu obsługi zdarzeń odpowiednio do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="573e0-111">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="573e0-112">Określ formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="573e0-112">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="573e0-113">W metodzie w klasie formularza Dodaj kod, który określa procedurę obsługi zdarzeń, aby obsłużyć zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="573e0-113">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="573e0-114">Na przykład poniższy kod określa, że program obsługi zdarzeń `button1_Click` obsługuje <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> formantu:</span><span class="sxs-lookup"><span data-stu-id="573e0-114">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="573e0-115"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A>Metoda pokazana w kodzie Visual Basic powyżej określa procedurę obsługi zdarzeń kliknięcia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="573e0-115">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="573e0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="573e0-116">See also</span></span>

- [<span data-ttu-id="573e0-117">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="573e0-117">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="573e0-118">Przegląd programów obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="573e0-118">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="573e0-119">Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="573e0-119">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)

---
title: 'Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: f1d22079dfa3a6452efb74ef57530bb43e059a4a
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197103"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="65098-102">Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="65098-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="65098-103">Kontrolki <xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> zastępują i dodają funkcje do kontrolek <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel>; jednak kontrolki <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> są zachowywane w celu zapewnienia zgodności z poprzednimi wersjami i w przyszłości, jeśli wybierzesz opcję.</span><span class="sxs-lookup"><span data-stu-id="65098-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="65098-104">Często program będzie wywoływał, aby zaktualizować zawartość paneli paska stanu dynamicznie w czasie wykonywania, na podstawie zmian stanu aplikacji lub innej interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="65098-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="65098-105">Jest to typowy sposób, aby sygnalizować użytkownikom, że klucze takie jak Caps Lock, NUM LOCK lub SCROLL LOCK są włączone, lub podać datę lub zegar jako wygodne odwołanie.</span><span class="sxs-lookup"><span data-stu-id="65098-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="65098-106">W poniższym przykładzie zostanie użyte wystąpienie klasy <xref:System.Windows.Forms.StatusBarPanel> do hostowania zegara.</span><span class="sxs-lookup"><span data-stu-id="65098-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="65098-107">Aby wyświetlić pasek stanu gotowy do aktualizacji</span><span class="sxs-lookup"><span data-stu-id="65098-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="65098-108">Utwórz nowy formularz systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="65098-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="65098-109">Dodaj kontrolkę <xref:System.Windows.Forms.StatusBar> do formularza.</span><span class="sxs-lookup"><span data-stu-id="65098-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="65098-110">Aby uzyskać szczegółowe informacje, zobacz [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="65098-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="65098-111">Dodaj panel paska stanu do kontrolki <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="65098-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="65098-112">Aby uzyskać szczegółowe informacje, zobacz [jak: dodać panele do kontrolki StatusBar](how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="65098-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="65098-113">Dla kontrolki <xref:System.Windows.Forms.StatusBar> dodanej do formularza ustaw właściwość <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="65098-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="65098-114">Dodaj składnik <xref:System.Windows.Forms.Timer> Windows Forms do formularza.</span><span class="sxs-lookup"><span data-stu-id="65098-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="65098-115">Składnik <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="65098-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="65098-116">Jeśli potrzebujesz czasomierza odpowiedniego dla środowiska serwera, zobacz [wprowadzenie do czasomierzy oparte na serwerze](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="65098-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="65098-117">Ustaw właściwość <xref:System.Windows.Forms.Timer.Enabled%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="65098-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="65098-118">Dla właściwości <xref:System.Windows.Forms.Timer.Interval%2A> <xref:System.Windows.Forms.Timer> ustaw wartość 30000.</span><span class="sxs-lookup"><span data-stu-id="65098-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="65098-119">Właściwość <xref:System.Windows.Forms.Timer.Interval%2A> składnika <xref:System.Windows.Forms.Timer> jest ustawiona na 30 sekund (30 000 milisekund), aby mieć pewność, że dokładny czas zostanie odzwierciedlony w wyświetlonym czasie.</span><span class="sxs-lookup"><span data-stu-id="65098-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="65098-120">Aby zaimplementować czasomierz w celu zaktualizowania paska stanu</span><span class="sxs-lookup"><span data-stu-id="65098-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="65098-121">Wstaw następujący kod do procedury obsługi zdarzeń składnika <xref:System.Windows.Forms.Timer>, aby zaktualizować panel kontrolki <xref:System.Windows.Forms.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="65098-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     <span data-ttu-id="65098-122">W tym momencie można przystąpić do uruchamiania aplikacji i obserwować zegar uruchomiony w panelu pasek stanu.</span><span class="sxs-lookup"><span data-stu-id="65098-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="65098-123">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="65098-123">To test the application</span></span>  
  
1. <span data-ttu-id="65098-124">Debuguj aplikację i naciśnij klawisz F5, aby ją uruchomić.</span><span class="sxs-lookup"><span data-stu-id="65098-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="65098-125">Aby uzyskać szczegółowe informacje o debugowaniu, zobacz [debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour).</span><span class="sxs-lookup"><span data-stu-id="65098-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="65098-126">Zegar będzie wyświetlany na pasku stanu przez około 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="65098-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="65098-127">Jest to najlepszy możliwy czas.</span><span class="sxs-lookup"><span data-stu-id="65098-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="65098-128">Z drugiej strony, aby zegar pojawił się wcześniej, można zmniejszyć wartość właściwości <xref:System.Windows.Forms.Timer.Interval%2A> ustawionej w kroku 7 w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="65098-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65098-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65098-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="65098-130">Instrukcje: dodawanie paneli do kontrolki StatusBar</span><span class="sxs-lookup"><span data-stu-id="65098-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="65098-131">Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="65098-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="65098-132">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="65098-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)

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
ms.openlocfilehash: 49722d5dadf694e8ee3037646652b921ddda3e91
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401722"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="6d0f7-102">Wskazówki: aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="6d0f7-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="6d0f7-103"><xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> kontrolki Zastąp i dodawania funkcjonalności do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontroluje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> kontrolek zostaną zachowane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="6d0f7-104">Często program będzie wywoływać parametr dla aktualizacji zawartości paneli paska stanu dynamicznie w czasie wykonywania, na podstawie zmian do stanu aplikacji lub innych interakcji z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="6d0f7-105">Jest to często stosowaną metodą sygnał użytkownikom włączenie kluczy, takie jak włączony klawisz CAPS LOCK, NUM LOCK lub SCROLL LOCK lub podaj datę lub zegara jako odwołanie wygodne.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="6d0f7-106">W poniższym przykładzie użyjesz wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klasy do hostowania zegara.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="6d0f7-107">Aby uzyskać gotowe do aktualizacji paska stanu</span><span class="sxs-lookup"><span data-stu-id="6d0f7-107">To get the status bar ready for updating</span></span>  
  
1.  <span data-ttu-id="6d0f7-108">Tworzenie nowego formularza Windows.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-108">Create a new Windows form.</span></span>  
  
2.  <span data-ttu-id="6d0f7-109">Dodaj <xref:System.Windows.Forms.StatusBar> formantu do formularza.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="6d0f7-110">Aby uzyskać więcej informacji, zobacz [porady: dodawanie formantów do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6d0f7-110">For details, see [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
3.  <span data-ttu-id="6d0f7-111">Dodawanie panelu pasek stanu, aby Twoje <xref:System.Windows.Forms.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="6d0f7-112">Aby uzyskać więcej informacji, zobacz [porady: dodawanie paneli do formantu StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="6d0f7-112">For details, see [How to: Add Panels to a StatusBar Control](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4.  <span data-ttu-id="6d0f7-113">Aby uzyskać <xref:System.Windows.Forms.StatusBar> formant został dodany do formularza, ustaw <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5.  <span data-ttu-id="6d0f7-114">Dodawanie formularzy Windows <xref:System.Windows.Forms.Timer> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d0f7-115">Formularze Windows <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> składnik jest przeznaczony dla środowiska Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="6d0f7-116">Jeśli potrzebujesz czasomierza, która jest odpowiednia w środowisku serwera, zobacz [wprowadzenie do serwerowych czasomierzy](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="6d0f7-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
6.  <span data-ttu-id="6d0f7-117">Ustaw <xref:System.Windows.Forms.Timer.Enabled%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7.  <span data-ttu-id="6d0f7-118">Ustaw <xref:System.Windows.Forms.Timer.Interval%2A> właściwość <xref:System.Windows.Forms.Timer> na 30000.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d0f7-119"><xref:System.Windows.Forms.Timer.Interval%2A> Właściwość <xref:System.Windows.Forms.Timer> składnika jest ustawiony na 30 sekund (30 000 milisekund), aby upewnić się, że dokładnego czasu jest odzwierciedlana w czasie wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="6d0f7-120">Aby zaimplementować czasomierza do aktualizacji paska stanu</span><span class="sxs-lookup"><span data-stu-id="6d0f7-120">To implement the timer to update the status bar</span></span>  
  
1.  <span data-ttu-id="6d0f7-121">Wstaw następujący kod do programu obsługi zdarzeń z <xref:System.Windows.Forms.Timer> składnik do aktualizacji na panelu <xref:System.Windows.Forms.StatusBar> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="6d0f7-122">W tym momencie można przystąpić do uruchomienia aplikacji i obserwuj zegara działa w panelu pasek stanu.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="6d0f7-123">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="6d0f7-123">To test the application</span></span>  
  
1.  <span data-ttu-id="6d0f7-124">Debugowanie aplikacji, a następnie naciśnij klawisz F5, aby go uruchomić.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="6d0f7-125">Aby uzyskać szczegółowe informacje o debugowaniu, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="6d0f7-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6d0f7-126">Potrwa około 30 sekund w przypadku zegara pojawią się w pasku stanu.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="6d0f7-127">To jest uzyskanie czas najdokładniejszych możliwe.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="6d0f7-128">Z drugiej strony, aby zegar pojawić się wcześniej, można zmniejszyć wartość <xref:System.Windows.Forms.Timer.Interval%2A> właściwości ustawionej w kroku 7 w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="6d0f7-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d0f7-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d0f7-129">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="6d0f7-130">Instrukcje: dodawanie paneli do kontrolki StatusBar</span><span class="sxs-lookup"><span data-stu-id="6d0f7-130">How to: Add Panels to a StatusBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)  
 [<span data-ttu-id="6d0f7-131">Instrukcje: ustalanie, który panel został kliknięty w kontrolce StatusBar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d0f7-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="6d0f7-132">StatusBar, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6d0f7-132">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)

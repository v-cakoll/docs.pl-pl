---
title: 'Porady: zmiana w formancie MonthCalendar formularzy Windows&#39;wygląd'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 4f91363764099cabfa1a7939ff07e627aeb6c815
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802018"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a><span data-ttu-id="0f866-102">Porady: zmiana w formancie MonthCalendar formularzy Windows&#39;wygląd</span><span class="sxs-lookup"><span data-stu-id="0f866-102">How to: Change the Windows Forms MonthCalendar Control&#39;s Appearance</span></span>
<span data-ttu-id="0f866-103">Formularze Windows <xref:System.Windows.Forms.MonthCalendar> kontroli umożliwia dostosowanie wyglądu kalendarza na wiele sposobów.</span><span class="sxs-lookup"><span data-stu-id="0f866-103">The Windows Forms <xref:System.Windows.Forms.MonthCalendar> control allows you to customize the calendar's appearance in many ways.</span></span> <span data-ttu-id="0f866-104">Na przykład można ustawić schemat kolorów i wybierz opcję wyświetlić lub ukryć numery tygodni i bieżącą datą.</span><span class="sxs-lookup"><span data-stu-id="0f866-104">For example, you can set the color scheme and choose to display or hide week numbers and the current date.</span></span>  
  
### <a name="to-change-the-month-calendars-color-scheme"></a><span data-ttu-id="0f866-105">Aby zmienić schemat kolorów kalendarza miesięcznego</span><span class="sxs-lookup"><span data-stu-id="0f866-105">To change the month calendar's color scheme</span></span>  
  
-   <span data-ttu-id="0f866-106">Ustaw właściwości, takie jak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> i <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="0f866-106">Set properties such as <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> and <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>.</span></span> <span data-ttu-id="0f866-107"><xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Właściwość również określa kolor czcionki dla poszczególnych dni tygodnia.</span><span class="sxs-lookup"><span data-stu-id="0f866-107">The <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> property also determines the font color for the days of the week.</span></span> <span data-ttu-id="0f866-108"><xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Właściwość określa kolor daty, dla których przed i po wyświetlany miesiąc lub miesiące.</span><span class="sxs-lookup"><span data-stu-id="0f866-108">The <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> property determines the color of the dates that precede and follow the displayed month or months.</span></span>  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0f866-109">Uruchamianie, Windows Vista, jak i w zależności od motywu, ustawienie niektóre właściwości mogą pozostać bez zmian wyglądu kalendarza.</span><span class="sxs-lookup"><span data-stu-id="0f866-109">Starting with Windows Vista and depending on the theme, setting some properties might not change the appearance of the calendar.</span></span> <span data-ttu-id="0f866-110">Na przykład jeśli Windows jest ustawiony do korzystania z motywu Aero, ustawienie <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, lub <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> właściwości nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="0f866-110">For example, if Windows is set to use the Aero theme, setting the <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, or <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> properties has no effect.</span></span> <span data-ttu-id="0f866-111">Jest to spowodowane zaktualizowaną wersję kalendarz jest renderowany przy użyciu wrażenie, że jest tworzony w czasie wykonywania na podstawie bieżącego motywu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0f866-111">This is because an updated version of the calendar is rendered with an appearance that is derived at run time from the current operating system theme.</span></span> <span data-ttu-id="0f866-112">Jeśli chcesz korzystać z tych właściwości i Włącz starszą wersję kalendarza można wyłączyć funkcji stylów wizualnych dla swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f866-112">If you want to use these properties and enable the earlier version of the calendar, you can disable visual styles for your application.</span></span> <span data-ttu-id="0f866-113">Wyłączanie funkcji stylów wizualnych mogą mieć wpływ na wygląd i zachowanie innych kontrolek w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f866-113">Disabling visual styles might affect the appearance and behavior of other controls in your application.</span></span> <span data-ttu-id="0f866-114">Aby wyłączyć stylów wizualnych w języku Visual Basic, otwórz projektanta projektu i usuń zaznaczenie pola wyboru **style wizualne XP włącz** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="0f866-114">To disable visual styles in Visual Basic, open the Project Designer and uncheck the **Enable XP visual styles** check box.</span></span> <span data-ttu-id="0f866-115">Aby wyłączyć stylów wizualnych w języku C#, otwórz plik Program.cs i komentarz `Application.EnableVisualStyles();`.</span><span class="sxs-lookup"><span data-stu-id="0f866-115">To disable visual styles in C#, open Program.cs and comment out `Application.EnableVisualStyles();`.</span></span> <span data-ttu-id="0f866-116">Aby uzyskać więcej informacji na temat funkcji stylów wizualnych zobacz [porady: Włączanie style wizualne XP Windows](https://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span><span class="sxs-lookup"><span data-stu-id="0f866-116">For more information about visual styles, see [How to: Enable Windows XP Visual Styles](https://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).</span></span>  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a><span data-ttu-id="0f866-117">Aby wyświetlić bieżącą datę w dolnej części kontrolki</span><span class="sxs-lookup"><span data-stu-id="0f866-117">To display the current date at the bottom of the control</span></span>  
  
-   <span data-ttu-id="0f866-118">Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0f866-118">Set the <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> property to `true`.</span></span> <span data-ttu-id="0f866-119">W poniższym przykładzie przełącza między wyświetlaniem i pomijanie dzisiaj po dwukrotnym kliknięciu formularza.</span><span class="sxs-lookup"><span data-stu-id="0f866-119">The example below toggles between displaying and omitting today's date when the form is double-clicked.</span></span>  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     <span data-ttu-id="0f866-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0f866-120">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a><span data-ttu-id="0f866-121">Aby wyświetlać numery tygodni</span><span class="sxs-lookup"><span data-stu-id="0f866-121">To display week numbers</span></span>  
  
-   <span data-ttu-id="0f866-122">Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="0f866-122">Set the <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> property to `true`.</span></span> <span data-ttu-id="0f866-123">Tę właściwość można ustawić w kodzie lub w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="0f866-123">You can set this property either in code or in the Properties window.</span></span>  
  
     <span data-ttu-id="0f866-124">Numery tygodni pojawiają się w oddzielnej kolumnie na lewo od pierwszego dnia tygodnia.</span><span class="sxs-lookup"><span data-stu-id="0f866-124">Week numbers appear in a separate column to the left of the first day of the week.</span></span>  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0f866-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f866-125">See Also</span></span>  
 [<span data-ttu-id="0f866-126">MonthCalendar, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0f866-126">MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [<span data-ttu-id="0f866-127">Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f866-127">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [<span data-ttu-id="0f866-128">Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f866-128">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [<span data-ttu-id="0f866-129">Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0f866-129">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)

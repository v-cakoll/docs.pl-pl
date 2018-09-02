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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467668"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>Porady: zmiana w formancie MonthCalendar formularzy Windows&#39;wygląd
Formularze Windows <xref:System.Windows.Forms.MonthCalendar> kontroli umożliwia dostosowanie wyglądu kalendarza na wiele sposobów. Na przykład można ustawić schemat kolorów i wybierz opcję wyświetlić lub ukryć numery tygodni i bieżącą datą.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Aby zmienić schemat kolorów kalendarza miesięcznego  
  
-   Ustaw właściwości, takie jak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> i <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Właściwość również określa kolor czcionki dla poszczególnych dni tygodnia. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Właściwość określa kolor daty, dla których przed i po wyświetlany miesiąc lub miesiące.  
  
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
    >  Uruchamianie, Windows Vista, jak i w zależności od motywu, ustawienie niektóre właściwości mogą pozostać bez zmian wyglądu kalendarza. Na przykład jeśli Windows jest ustawiony do korzystania z motywu Aero, ustawienie <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>, lub <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> właściwości nie ma wpływu. Jest to spowodowane zaktualizowaną wersję kalendarz jest renderowany przy użyciu wrażenie, że jest tworzony w czasie wykonywania na podstawie bieżącego motywu systemu operacyjnego. Jeśli chcesz korzystać z tych właściwości i Włącz starszą wersję kalendarza można wyłączyć funkcji stylów wizualnych dla swojej aplikacji. Wyłączanie funkcji stylów wizualnych mogą mieć wpływ na wygląd i zachowanie innych kontrolek w aplikacji. Aby wyłączyć stylów wizualnych w języku Visual Basic, otwórz projektanta projektu i usuń zaznaczenie pola wyboru **style wizualne XP włącz** pole wyboru. Aby wyłączyć stylów wizualnych w języku C#, otwórz plik Program.cs i komentarz `Application.EnableVisualStyles();`. Aby uzyskać więcej informacji na temat funkcji stylów wizualnych zobacz [porady: Włączanie style wizualne XP Windows](https://msdn.microsoft.com/library/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Aby wyświetlić bieżącą datę w dolnej części kontrolki  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> właściwość `true`. W poniższym przykładzie przełącza między wyświetlaniem i pomijanie dzisiaj po dwukrotnym kliknięciu formularza.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Aby wyświetlać numery tygodni  
  
-   Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwość `true`. Tę właściwość można ustawić w kodzie lub w oknie dialogowym właściwości.  
  
     Numery tygodni pojawiają się w oddzielnej kolumnie na lewo od pierwszego dnia tygodnia.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [MonthCalendar, kontrolka](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)

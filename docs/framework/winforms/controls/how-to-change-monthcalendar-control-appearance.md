---
title: Zmień wygląd formantu MonthCalendar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: ded9059ede4ad03f637c0e697b880c41a9a8ba32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746652"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Porady: zmienianie wyglądu formantu MonthCalendar formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.MonthCalendar> Windows Forms umożliwia dostosowanie wyglądu kalendarza na wiele sposobów. Na przykład można ustawić schemat kolorów i wybrać opcję wyświetlania lub ukrywania numerów tygodni i bieżącej daty.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Aby zmienić schemat kolorów kalendarza miesięcznego  
  
- Ustaw właściwości, takie jak <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> i <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>. Właściwość <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> określa również kolor czcionki dla dni tygodnia. Właściwość <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> określa kolor dat poprzedzających i zgodny z wyświetlanym miesiącem lub miesiącami.  
  
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
    > Począwszy od systemu Windows Vista i w zależności od motywu, ustawienie niektórych właściwości może nie zmieniać wyglądu kalendarza. Na przykład jeśli system Windows jest skonfigurowany do używania motywu Aero, ustawienie właściwości <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>, <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>lub <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> nie ma żadnego wpływu. Wynika to z faktu, że zaktualizowana wersja kalendarza jest renderowana przy użyciu wyglądu, który jest tworzony w czasie wykonywania z bieżącego motywu systemu operacyjnego. Jeśli chcesz użyć tych właściwości i włączyć wcześniejszą wersję kalendarza, możesz wyłączyć style wizualne dla aplikacji. Wyłączenie stylów wizualnych może mieć wpływ na wygląd i zachowanie innych kontrolek w aplikacji. Aby wyłączyć style wizualne w Visual Basic, Otwórz projektanta projektu i usuń zaznaczenie pola wyboru **Włącz style wizualne XP** . Aby wyłączyć style wizualizacji C#w, Otwórz program.cs i Skomentuj `Application.EnableVisualStyles();`. Aby uzyskać więcej informacji na temat stylów wizualizacji, zobacz [Włączanie stylów wizualnych](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Aby wyświetlić bieżącą datę w dolnej części kontrolki  
  
- Ustaw właściwość <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> na `true`. W poniższym przykładzie przełączają się do wyświetlania i pomijania dzisiejszej daty po dwukrotnym kliknięciu formularza.  
  
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
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>Aby wyświetlić numery tygodniowe  
  
- Ustaw właściwość <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> na `true`. Tę właściwość można ustawić w kodzie lub w okno Właściwości.  
  
     Numery tygodni są wyświetlane w oddzielnej kolumnie z lewej strony pierwszego dnia tygodnia.  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [MonthCalendar, kontrolka](monthcalendar-control-windows-forms.md)
- [Instrukcje: wybieranie zakresu dat w kontrolce MonthCalendar formularzy Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: wyświetlanie określonych dni pogrubioną czcionką za pomocą kontrolki MonthCalendar formularzy Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Instrukcje: wyświetlanie więcej niż jednego miesiąca w kontrolce MonthCalendar formularzy Windows Forms](display-more-than-one-month-wf-monthcalendar-control.md)

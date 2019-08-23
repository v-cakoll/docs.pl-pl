---
title: 'Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
ms.openlocfilehash: 5582624d881b2d8039bcd5e8ac45e548c7b38f57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929048"
---
# <a name="how-to-change-the-windows-forms-monthcalendar-controls-appearance"></a>Instrukcje: zmienianie wyglądu kontrolki MonthCalendar formularzy systemu Windows
Formant Windows Forms <xref:System.Windows.Forms.MonthCalendar> umożliwia dostosowanie wyglądu kalendarza na wiele sposobów. Na przykład można ustawić schemat kolorów i wybrać opcję wyświetlania lub ukrywania numerów tygodni i bieżącej daty.  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>Aby zmienić schemat kolorów kalendarza miesięcznego  
  
- Ustaw właściwości, takie <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>jak <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A> , <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>i. <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> Właściwość określa również kolor czcionki dla dni tygodnia. <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> Właściwość określa kolor dat poprzedzających i zgodny z wyświetlanym miesiącem lub miesiącami.  
  
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
    > Począwszy od systemu Windows Vista i w zależności od motywu, ustawienie niektórych właściwości może nie zmieniać wyglądu kalendarza. Na przykład jeśli system Windows jest skonfigurowany do korzystania z motywu Aero, ustawienie <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>właściwości <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>,, lub <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> nie ma żadnego efektu. Wynika to z faktu, że zaktualizowana wersja kalendarza jest renderowana przy użyciu wyglądu, który jest tworzony w czasie wykonywania z bieżącego motywu systemu operacyjnego. Jeśli chcesz użyć tych właściwości i włączyć wcześniejszą wersję kalendarza, możesz wyłączyć style wizualne dla aplikacji. Wyłączenie stylów wizualnych może mieć wpływ na wygląd i zachowanie innych kontrolek w aplikacji. Aby wyłączyć style wizualne w Visual Basic, Otwórz projektanta projektu i usuń zaznaczenie pola wyboru **Włącz style wizualne XP** . Aby wyłączyć style wizualizacji C#w, Otwórz program.cs i Skomentuj `Application.EnableVisualStyles();`. Aby uzyskać więcej informacji na temat stylów wizualizacji, zobacz [Włączanie stylów wizualnych](/windows/desktop/controls/cookbook-overview).  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>Aby wyświetlić bieżącą datę w dolnej części kontrolki  
  
- Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> właściwość `true`. W poniższym przykładzie przełączają się do wyświetlania i pomijania dzisiejszej daty po dwukrotnym kliknięciu formularza.  
  
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
  
- Ustaw <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> właściwość `true`. Tę właściwość można ustawić w kodzie lub w okno Właściwości.  
  
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
- [Instrukcje: Wybierz zakres dat w kontrolce MonthCalendar Windows Forms](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [Instrukcje: Wyświetlaj określone dni pogrubione za pomocą kontrolki MonthCalendar Windows Forms](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [Instrukcje: Wyświetlaj więcej niż jeden miesiąc w formancie Windows Forms MonthCalendar](display-more-than-one-month-wf-monthcalendar-control.md)

---
title: 'Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], setting in DateTimePicker
- DateTimePicker control [Windows Forms], setting and returning dates
- examples [Windows Forms], DateTimePicker control
ms.assetid: a8a48d68-e4b5-426e-9764-51230fc9acd2
ms.openlocfilehash: cc4f0bdf7355cda61e6cb95f5e0b18c4f83aa62b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081544"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy systemu Windows
Aktualnie wybranej daty lub godziny w formularzach Windows Forms <xref:System.Windows.Forms.DateTimePicker> kontrolki jest określany przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości. Możesz ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości przed wyświetleniem formantu (na przykład w czasie projektowania lub w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń) do określenia daty, dla której będzie początkowo zaznaczone w formancie. Domyślnie formant firmy <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiona na bieżącą datę. Jeśli zmienisz formantu <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, formant jest automatycznie aktualizowany na formularz, aby odzwierciedlić nowe ustawienie.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Właściwość zwraca <xref:System.DateTime> struktury jako jego wartość. Istnieje kilka właściwości <xref:System.DateTime> strukturę, która zwraca szczegółowe informacje dotyczące daty wyświetlane. Te właściwości należy używać tylko w celu zwrócenia wartości; nie należy ich używać do ustawiania wartości.  
  
-   W przypadku wartości daty <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, i <xref:System.DateTime.Year%2A> właściwości zwracają wartości całkowite dla tych jednostek czasu od wybranej daty. <xref:System.DateTime.DayOfWeek%2A> Właściwość zwraca wartość wskazującą wybranego dnia tygodnia (możliwe wartości są wymienione w <xref:System.DayOfWeek> wyliczenia).  
  
-   W przypadku wartości czasu <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, i <xref:System.DateTime.Millisecond%2A> właściwości zwracają wartości całkowite dla tych jednostek czasu. Aby skonfigurować formantu, aby wyświetlić czas, zobacz [jak: Wyświetlanie godziny za pomocą formantu DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Aby ustawić wartości daty i godziny formantu  
  
-   Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości wartości daty i godziny.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Zwraca wartość daty i godziny  
  
-   Wywołaj <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwość zwraca całą wartość, jak sformatowane w kontrolce lub wywołać metodę odpowiednią <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości do zwrócenia część wartości. Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A> do konwersji danych na ciąg, który może być wyświetlany użytkownikowi.  
  
    ```vb  
    MessageBox.Show("The selected value is ", DateTimePicker1.Text)  
    MessageBox.Show("The day of the week is ",   
       DateTimePicker1.Value.DayOfWeek.ToString)  
    MessageBox.Show("Millisecond is: ",   
       DateTimePicker1.Value.Millisecond.ToString)  
    ```  
  
    ```csharp  
    MessageBox.Show ("The selected value is " +   
       dateTimePicker1.Text);  
    MessageBox.Show ("The day of the week is " +   
       dateTimePicker1.Value.DayOfWeek.ToString());  
    MessageBox.Show("Millisecond is: " +   
       dateTimePicker1.Value.Millisecond.ToString());  
    ```  
  
    ```cpp  
    MessageBox::Show (String::Concat("The selected value is ",  
       dateTimePicker1->Text));  
    MessageBox::Show (String::Concat("The day of the week is ",  
       dateTimePicker1->Value.DayOfWeek.ToString()));  
    MessageBox::Show(String::Concat("Millisecond is: ",  
       dateTimePicker1->Value.Millisecond.ToString()));  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [DateTimePicker, kontrolka](datetimepicker-control-windows-forms.md)
- [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy systemu Windows](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

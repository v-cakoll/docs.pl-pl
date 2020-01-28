---
title: Ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker
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
ms.openlocfilehash: 1e0aa58e98748ccde9411f0f4871adbae3a5f14d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747100"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows
Aktualnie wybrana data lub godzina w kontrolce <xref:System.Windows.Forms.DateTimePicker> Windows Forms jest określana przez właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A>. Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> można ustawić przed wyświetleniem kontrolki (na przykład w czasie projektowania lub w zdarzeniu <xref:System.Windows.Forms.Form.Load> formularza) w celu określenia, która data będzie początkowo zaznaczona w formancie. Domyślnie <xref:System.Windows.Forms.DateTimePicker.Value%2A> kontrolki jest ustawiana na bieżącą datę. Jeśli zmienisz <xref:System.Windows.Forms.DateTimePicker.Value%2A> formantu w kodzie, formant zostanie automatycznie zaktualizowany w formularzu, aby odzwierciedlić nowe ustawienie.  
  
 Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca strukturę <xref:System.DateTime> jako wartość. Istnieje kilka właściwości struktury <xref:System.DateTime>, które zwracają określone informacje o wyświetlanej dacie. Tych właściwości można użyć tylko do zwrócenia wartości; nie należy używać ich do ustawiania wartości.  
  
- W przypadku wartości dat właściwości <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>i <xref:System.DateTime.Year%2A> zwracają wartości całkowite dla tych jednostek czasu dla wybranej daty. Właściwość <xref:System.DateTime.DayOfWeek%2A> zwraca wartość wskazującą wybrany dzień tygodnia (możliwe wartości są wymienione w wyliczeniu <xref:System.DayOfWeek>).  
  
- W przypadku wartości czasu właściwości <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>i <xref:System.DateTime.Millisecond%2A> zwracają wartości całkowite dla tych jednostek czasu. Aby skonfigurować kontrolkę czas wyświetlania, zobacz [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Aby ustawić datę i godzinę dla formantu  
  
- Ustaw właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> na wartość daty lub godziny.  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a>Aby zwrócić wartość daty i godziny  
  
- Wywołaj Właściwość <xref:System.Windows.Forms.DateTimePicker.Text%2A>, aby zwrócić całą wartość sformatowaną w kontrolce lub wywołać odpowiednią metodę właściwości <xref:System.Windows.Forms.DateTimePicker.Value%2A> w celu zwrócenia części wartości. Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A>, aby przekonwertować informacje na ciąg, który może być wyświetlany użytkownikowi.  
  
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
- [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

---
title: Ustawianie i zwracanie dat za pomocą formantu DateTimePicker
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
ms.openlocfilehash: f958097640316715b38828e72107ab5bdb9389aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141916"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows
Aktualnie wybrana data lub godzina <xref:System.Windows.Forms.DateTimePicker> w formancie Windows Forms jest określana przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość. Można ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość przed wyświetleniem formantu (na przykład w <xref:System.Windows.Forms.Form.Load> czasie projektowania lub w zdarzeniu formularza), aby określić, która data zostanie początkowo wybrana w formancie. Domyślnie formant <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiony na bieżącą datę. Jeśli zmienisz formant <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, formant jest automatycznie aktualizowany w formularzu, aby odzwierciedlić nowe ustawienie.  
  
 Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca <xref:System.DateTime> strukturę jako jej wartość. Istnieje kilka właściwości <xref:System.DateTime> struktury, które zwracają określone informacje o wyświetlanej dacie. Te właściwości mogą służyć tylko do zwracania wartości; nie należy ich używać do ustawiania wartości.  
  
- W przypadku wartości <xref:System.DateTime.Month%2A> <xref:System.DateTime.Day%2A>daty <xref:System.DateTime.Year%2A> , i właściwości zwracają wartości całkowite dla tych jednostek czasu wybranej daty. Właściwość <xref:System.DateTime.DayOfWeek%2A> zwraca wartość wskazującą wybrany dzień tygodnia (możliwe wartości <xref:System.DayOfWeek> są wymienione w wyliczeniu).  
  
- W przypadku wartości <xref:System.DateTime.Hour%2A> <xref:System.DateTime.Minute%2A>czasu <xref:System.DateTime.Second%2A>, <xref:System.DateTime.Millisecond%2A> , i właściwości zwracają wartości całkowite dla tych jednostek czasu. Aby skonfigurować formant do wyświetlania czasów, zobacz [Jak: Wyświetl czas za pomocą formantu DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Aby ustawić wartość daty i godziny formantu  
  
- Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość na wartość daty lub godziny.  
  
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
  
- Wywołanie <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwości, aby zwrócić całą wartość sformatowaną w formancie lub wywołać odpowiednią metodę <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości, aby zwrócić część wartości. Służy <xref:System.Windows.Forms.DateTimePicker.ToString%2A> do konwertowania informacji na ciąg, który może być wyświetlany użytkownikowi.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [DateTimePicker, kontrolka](datetimepicker-control-windows-forms.md)
- [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

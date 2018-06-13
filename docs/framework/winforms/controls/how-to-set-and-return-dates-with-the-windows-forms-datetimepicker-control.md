---
title: 'Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows'
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
ms.openlocfilehash: 017224aa493bfe0cd519df482a4d00e16f889a1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535672"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a>Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows
Aktualnie zaznaczona data lub godzina w formularzach systemu Windows <xref:System.Windows.Forms.DateTimePicker> kontroli jest określany przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości. Można ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości przed wyświetleniem formantu (na przykład w czasie projektowania lub w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń) do określenia daty, dla której będzie początkowo zaznaczone w formancie. Domyślnie formantu w <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiona na bieżącą datę. Jeśli zmienisz formantu <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, kontrolka jest automatycznie aktualizowany na formularzu, aby uwzględnić nowe ustawienie.  
  
 <xref:System.Windows.Forms.DateTimePicker.Value%2A> Zwraca <xref:System.DateTime> struktury jako jego wartość. Istnieje kilka właściwości <xref:System.DateTime> struktury, która zwraca określone informacje na temat wyświetlane data. Te właściwości mogą służyć tylko do zwrócić wartość; nie należy używać ich do ustawiania wartości.  
  
-   W przypadku wartości daty <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, i <xref:System.DateTime.Year%2A> właściwości zwracają wartości będące liczbami całkowitymi tych jednostek czasu wybraną datą. <xref:System.DateTime.DayOfWeek%2A> Właściwość zwraca wartość wskazującą wybranego dnia tygodnia (możliwe wartości są wymienione w <xref:System.DayOfWeek> wyliczenie).  
  
-   Dla wartości czasu <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, i <xref:System.DateTime.Millisecond%2A> właściwości zwracają wartości całkowite dla tych jednostki czasu. Aby skonfigurować formantu, aby wyświetlić razy, zobacz [porady: wyświetlanie czasu za pomocą formantu DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a>Aby ustawić wartość daty i godziny formantu  
  
-   Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości na wartość daty i godziny.  
  
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
  
-   Wywołanie <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwości zwrócić całą wartość jako sformatowane w formancie lub wywołać metodę odpowiednie <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca część wartości dla właściwości. Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A> przekonwertować danych na ciąg, który może być wyświetlana użytkownikowi.  
  
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
 [DateTimePicker, kontrolka](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

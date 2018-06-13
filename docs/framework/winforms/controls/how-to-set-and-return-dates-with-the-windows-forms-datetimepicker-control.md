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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="53bb7-102">Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="53bb7-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="53bb7-103">Aktualnie zaznaczona data lub godzina w formularzach systemu Windows <xref:System.Windows.Forms.DateTimePicker> kontroli jest określany przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="53bb7-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="53bb7-104">Można ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości przed wyświetleniem formantu (na przykład w czasie projektowania lub w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń) do określenia daty, dla której będzie początkowo zaznaczone w formancie.</span><span class="sxs-lookup"><span data-stu-id="53bb7-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="53bb7-105">Domyślnie formantu w <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiona na bieżącą datę.</span><span class="sxs-lookup"><span data-stu-id="53bb7-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="53bb7-106">Jeśli zmienisz formantu <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, kontrolka jest automatycznie aktualizowany na formularzu, aby uwzględnić nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="53bb7-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="53bb7-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> Zwraca <xref:System.DateTime> struktury jako jego wartość.</span><span class="sxs-lookup"><span data-stu-id="53bb7-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="53bb7-108">Istnieje kilka właściwości <xref:System.DateTime> struktury, która zwraca określone informacje na temat wyświetlane data.</span><span class="sxs-lookup"><span data-stu-id="53bb7-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="53bb7-109">Te właściwości mogą służyć tylko do zwrócić wartość; nie należy używać ich do ustawiania wartości.</span><span class="sxs-lookup"><span data-stu-id="53bb7-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="53bb7-110">W przypadku wartości daty <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, i <xref:System.DateTime.Year%2A> właściwości zwracają wartości będące liczbami całkowitymi tych jednostek czasu wybraną datą.</span><span class="sxs-lookup"><span data-stu-id="53bb7-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="53bb7-111"><xref:System.DateTime.DayOfWeek%2A> Właściwość zwraca wartość wskazującą wybranego dnia tygodnia (możliwe wartości są wymienione w <xref:System.DayOfWeek> wyliczenie).</span><span class="sxs-lookup"><span data-stu-id="53bb7-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="53bb7-112">Dla wartości czasu <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, i <xref:System.DateTime.Millisecond%2A> właściwości zwracają wartości całkowite dla tych jednostki czasu.</span><span class="sxs-lookup"><span data-stu-id="53bb7-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="53bb7-113">Aby skonfigurować formantu, aby wyświetlić razy, zobacz [porady: wyświetlanie czasu za pomocą formantu DateTimePicker](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="53bb7-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](../../../../docs/framework/winforms/controls/how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="53bb7-114">Aby ustawić wartość daty i godziny formantu</span><span class="sxs-lookup"><span data-stu-id="53bb7-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="53bb7-115">Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości na wartość daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="53bb7-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="53bb7-116">Zwraca wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="53bb7-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="53bb7-117">Wywołanie <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwości zwrócić całą wartość jako sformatowane w formancie lub wywołać metodę odpowiednie <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca część wartości dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="53bb7-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="53bb7-118">Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A> przekonwertować danych na ciąg, który może być wyświetlana użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="53bb7-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53bb7-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53bb7-119">See Also</span></span>  
 [<span data-ttu-id="53bb7-120">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="53bb7-120">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="53bb7-121">Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="53bb7-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

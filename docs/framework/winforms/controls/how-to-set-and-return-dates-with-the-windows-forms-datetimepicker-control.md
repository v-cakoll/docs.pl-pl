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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="83fb9-102">Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83fb9-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="83fb9-103">Aktualnie wybrana data lub godzina w kontrolce <xref:System.Windows.Forms.DateTimePicker> Windows Forms jest określana przez właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="83fb9-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="83fb9-104">Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> można ustawić przed wyświetleniem kontrolki (na przykład w czasie projektowania lub w zdarzeniu <xref:System.Windows.Forms.Form.Load> formularza) w celu określenia, która data będzie początkowo zaznaczona w formancie.</span><span class="sxs-lookup"><span data-stu-id="83fb9-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="83fb9-105">Domyślnie <xref:System.Windows.Forms.DateTimePicker.Value%2A> kontrolki jest ustawiana na bieżącą datę.</span><span class="sxs-lookup"><span data-stu-id="83fb9-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="83fb9-106">Jeśli zmienisz <xref:System.Windows.Forms.DateTimePicker.Value%2A> formantu w kodzie, formant zostanie automatycznie zaktualizowany w formularzu, aby odzwierciedlić nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="83fb9-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="83fb9-107">Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca strukturę <xref:System.DateTime> jako wartość.</span><span class="sxs-lookup"><span data-stu-id="83fb9-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="83fb9-108">Istnieje kilka właściwości struktury <xref:System.DateTime>, które zwracają określone informacje o wyświetlanej dacie.</span><span class="sxs-lookup"><span data-stu-id="83fb9-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="83fb9-109">Tych właściwości można użyć tylko do zwrócenia wartości; nie należy używać ich do ustawiania wartości.</span><span class="sxs-lookup"><span data-stu-id="83fb9-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="83fb9-110">W przypadku wartości dat właściwości <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>i <xref:System.DateTime.Year%2A> zwracają wartości całkowite dla tych jednostek czasu dla wybranej daty.</span><span class="sxs-lookup"><span data-stu-id="83fb9-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="83fb9-111">Właściwość <xref:System.DateTime.DayOfWeek%2A> zwraca wartość wskazującą wybrany dzień tygodnia (możliwe wartości są wymienione w wyliczeniu <xref:System.DayOfWeek>).</span><span class="sxs-lookup"><span data-stu-id="83fb9-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="83fb9-112">W przypadku wartości czasu właściwości <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>i <xref:System.DateTime.Millisecond%2A> zwracają wartości całkowite dla tych jednostek czasu.</span><span class="sxs-lookup"><span data-stu-id="83fb9-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="83fb9-113">Aby skonfigurować kontrolkę czas wyświetlania, zobacz [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="83fb9-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="83fb9-114">Aby ustawić datę i godzinę dla formantu</span><span class="sxs-lookup"><span data-stu-id="83fb9-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="83fb9-115">Ustaw właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> na wartość daty lub godziny.</span><span class="sxs-lookup"><span data-stu-id="83fb9-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="83fb9-116">Aby zwrócić wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="83fb9-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="83fb9-117">Wywołaj Właściwość <xref:System.Windows.Forms.DateTimePicker.Text%2A>, aby zwrócić całą wartość sformatowaną w kontrolce lub wywołać odpowiednią metodę właściwości <xref:System.Windows.Forms.DateTimePicker.Value%2A> w celu zwrócenia części wartości.</span><span class="sxs-lookup"><span data-stu-id="83fb9-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="83fb9-118">Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A>, aby przekonwertować informacje na ciąg, który może być wyświetlany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="83fb9-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83fb9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83fb9-119">See also</span></span>

- [<span data-ttu-id="83fb9-120">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="83fb9-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="83fb9-121">Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="83fb9-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

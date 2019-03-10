---
title: 'Instrukcje: Ustaw i zwracają dat za pomocą formantu DateTimePicker formularzy Windows'
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
ms.openlocfilehash: 73c40a48a75955d1ba44decae6b50ca641a63f7b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703221"
---
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="36790-102">Instrukcje: Ustaw i zwracają dat za pomocą formantu DateTimePicker formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="36790-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="36790-103">Aktualnie wybranej daty lub godziny w formularzach Windows Forms <xref:System.Windows.Forms.DateTimePicker> kontrolki jest określany przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="36790-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="36790-104">Możesz ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości przed wyświetleniem formantu (na przykład w czasie projektowania lub w postaci <xref:System.Windows.Forms.Form.Load> zdarzeń) do określenia daty, dla której będzie początkowo zaznaczone w formancie.</span><span class="sxs-lookup"><span data-stu-id="36790-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="36790-105">Domyślnie formant firmy <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiona na bieżącą datę.</span><span class="sxs-lookup"><span data-stu-id="36790-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="36790-106">Jeśli zmienisz formantu <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, formant jest automatycznie aktualizowany na formularz, aby odzwierciedlić nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="36790-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="36790-107"><xref:System.Windows.Forms.DateTimePicker.Value%2A> Właściwość zwraca <xref:System.DateTime> struktury jako jego wartość.</span><span class="sxs-lookup"><span data-stu-id="36790-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="36790-108">Istnieje kilka właściwości <xref:System.DateTime> strukturę, która zwraca szczegółowe informacje dotyczące daty wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="36790-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="36790-109">Te właściwości należy używać tylko w celu zwrócenia wartości; nie należy ich używać do ustawiania wartości.</span><span class="sxs-lookup"><span data-stu-id="36790-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
-   <span data-ttu-id="36790-110">W przypadku wartości daty <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, i <xref:System.DateTime.Year%2A> właściwości zwracają wartości całkowite dla tych jednostek czasu od wybranej daty.</span><span class="sxs-lookup"><span data-stu-id="36790-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="36790-111"><xref:System.DateTime.DayOfWeek%2A> Właściwość zwraca wartość wskazującą wybranego dnia tygodnia (możliwe wartości są wymienione w <xref:System.DayOfWeek> wyliczenia).</span><span class="sxs-lookup"><span data-stu-id="36790-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
-   <span data-ttu-id="36790-112">W przypadku wartości czasu <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, i <xref:System.DateTime.Millisecond%2A> właściwości zwracają wartości całkowite dla tych jednostek czasu.</span><span class="sxs-lookup"><span data-stu-id="36790-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="36790-113">Aby skonfigurować formantu, aby wyświetlić czas, zobacz [jak: Wyświetlanie godziny za pomocą formantu DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="36790-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="36790-114">Aby ustawić wartości daty i godziny formantu</span><span class="sxs-lookup"><span data-stu-id="36790-114">To set the date and time value of the control</span></span>  
  
-   <span data-ttu-id="36790-115">Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości wartości daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="36790-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="36790-116">Zwraca wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="36790-116">To return the date and time value</span></span>  
  
-   <span data-ttu-id="36790-117">Wywołaj <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwość zwraca całą wartość, jak sformatowane w kontrolce lub wywołać metodę odpowiednią <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości do zwrócenia część wartości.</span><span class="sxs-lookup"><span data-stu-id="36790-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="36790-118">Użyj <xref:System.Windows.Forms.DateTimePicker.ToString%2A> do konwersji danych na ciąg, który może być wyświetlany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="36790-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36790-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36790-119">See also</span></span>
- [<span data-ttu-id="36790-120">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="36790-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="36790-121">Instrukcje: Wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="36790-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

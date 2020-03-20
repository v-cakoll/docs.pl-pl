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
# <a name="how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="ad5ae-102">Porady: ustawianie i zwracanie dat za pomocą formantu DateTimePicker formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ad5ae-102">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="ad5ae-103">Aktualnie wybrana data lub godzina <xref:System.Windows.Forms.DateTimePicker> w formancie Windows Forms jest określana przez <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-103">The currently selected date or time in the Windows Forms <xref:System.Windows.Forms.DateTimePicker> control is determined by the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property.</span></span> <span data-ttu-id="ad5ae-104">Można ustawić <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość przed wyświetleniem formantu (na przykład w <xref:System.Windows.Forms.Form.Load> czasie projektowania lub w zdarzeniu formularza), aby określić, która data zostanie początkowo wybrana w formancie.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-104">You can set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property before the control is displayed (for example, at design time or in the form's <xref:System.Windows.Forms.Form.Load> event) to determine which date will be initially selected in the control.</span></span> <span data-ttu-id="ad5ae-105">Domyślnie formant <xref:System.Windows.Forms.DateTimePicker.Value%2A> jest ustawiony na bieżącą datę.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-105">By default, the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> is set to the current date.</span></span> <span data-ttu-id="ad5ae-106">Jeśli zmienisz formant <xref:System.Windows.Forms.DateTimePicker.Value%2A> w kodzie, formant jest automatycznie aktualizowany w formularzu, aby odzwierciedlić nowe ustawienie.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-106">If you change the control's <xref:System.Windows.Forms.DateTimePicker.Value%2A> in code, the control is automatically updated on the form to reflect the new setting.</span></span>  
  
 <span data-ttu-id="ad5ae-107">Właściwość <xref:System.Windows.Forms.DateTimePicker.Value%2A> zwraca <xref:System.DateTime> strukturę jako jej wartość.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-107">The <xref:System.Windows.Forms.DateTimePicker.Value%2A> property returns a <xref:System.DateTime> structure as its value.</span></span> <span data-ttu-id="ad5ae-108">Istnieje kilka właściwości <xref:System.DateTime> struktury, które zwracają określone informacje o wyświetlanej dacie.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-108">There are several properties of the <xref:System.DateTime> structure that return specific information about the displayed date.</span></span> <span data-ttu-id="ad5ae-109">Te właściwości mogą służyć tylko do zwracania wartości; nie należy ich używać do ustawiania wartości.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-109">These properties can only be used to return a value; do not use them to set a value.</span></span>  
  
- <span data-ttu-id="ad5ae-110">W przypadku wartości <xref:System.DateTime.Month%2A> <xref:System.DateTime.Day%2A>daty <xref:System.DateTime.Year%2A> , i właściwości zwracają wartości całkowite dla tych jednostek czasu wybranej daty.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-110">For date values, the <xref:System.DateTime.Month%2A>, <xref:System.DateTime.Day%2A>, and <xref:System.DateTime.Year%2A> properties return integer values for those time units of the selected date.</span></span> <span data-ttu-id="ad5ae-111">Właściwość <xref:System.DateTime.DayOfWeek%2A> zwraca wartość wskazującą wybrany dzień tygodnia (możliwe wartości <xref:System.DayOfWeek> są wymienione w wyliczeniu).</span><span class="sxs-lookup"><span data-stu-id="ad5ae-111">The <xref:System.DateTime.DayOfWeek%2A> property returns a value indicating the selected day of the week (possible values are listed in the <xref:System.DayOfWeek> enumeration).</span></span>  
  
- <span data-ttu-id="ad5ae-112">W przypadku wartości <xref:System.DateTime.Hour%2A> <xref:System.DateTime.Minute%2A>czasu <xref:System.DateTime.Second%2A>, <xref:System.DateTime.Millisecond%2A> , i właściwości zwracają wartości całkowite dla tych jednostek czasu.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-112">For time values, the <xref:System.DateTime.Hour%2A>, <xref:System.DateTime.Minute%2A>, <xref:System.DateTime.Second%2A>, and <xref:System.DateTime.Millisecond%2A> properties return integer values for those time units.</span></span> <span data-ttu-id="ad5ae-113">Aby skonfigurować formant do wyświetlania czasów, zobacz [Jak: Wyświetl czas za pomocą formantu DateTimePicker](how-to-display-time-with-the-datetimepicker-control.md).</span><span class="sxs-lookup"><span data-stu-id="ad5ae-113">To configure the control to display times, see [How to: Display Time with the DateTimePicker Control](how-to-display-time-with-the-datetimepicker-control.md).</span></span>  
  
### <a name="to-set-the-date-and-time-value-of-the-control"></a><span data-ttu-id="ad5ae-114">Aby ustawić wartość daty i godziny formantu</span><span class="sxs-lookup"><span data-stu-id="ad5ae-114">To set the date and time value of the control</span></span>  
  
- <span data-ttu-id="ad5ae-115">Ustaw <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwość na wartość daty lub godziny.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-115">Set the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to a date or time value.</span></span>  
  
    ```vb  
    DateTimePicker1.Value = New DateTime(2001, 10, 20)  
    ```  
  
    ```csharp  
    dateTimePicker1.Value = new DateTime(2001, 10, 20);  
    ```  
  
    ```cpp  
    dateTimePicker1->Value = DateTime(2001, 10, 20);  
    ```  
  
### <a name="to-return-the-date-and-time-value"></a><span data-ttu-id="ad5ae-116">Aby zwrócić wartość daty i godziny</span><span class="sxs-lookup"><span data-stu-id="ad5ae-116">To return the date and time value</span></span>  
  
- <span data-ttu-id="ad5ae-117">Wywołanie <xref:System.Windows.Forms.DateTimePicker.Text%2A> właściwości, aby zwrócić całą wartość sformatowaną w formancie lub wywołać odpowiednią metodę <xref:System.Windows.Forms.DateTimePicker.Value%2A> właściwości, aby zwrócić część wartości.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-117">Call the <xref:System.Windows.Forms.DateTimePicker.Text%2A> property to return the entire value as formatted in the control, or call the appropriate method of the <xref:System.Windows.Forms.DateTimePicker.Value%2A> property to return a part of the value.</span></span> <span data-ttu-id="ad5ae-118">Służy <xref:System.Windows.Forms.DateTimePicker.ToString%2A> do konwertowania informacji na ciąg, który może być wyświetlany użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="ad5ae-118">Use <xref:System.Windows.Forms.DateTimePicker.ToString%2A> to convert the information into a string that can be displayed to the user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ad5ae-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad5ae-119">See also</span></span>

- [<span data-ttu-id="ad5ae-120">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ad5ae-120">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="ad5ae-121">Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad5ae-121">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>](display-a-date-in-a-custom-format-with-wf-datetimepicker-control.md)

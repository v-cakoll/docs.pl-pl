---
title: 'Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
ms.openlocfilehash: 2f563b5de9b80dab2af00290e8a6b3b309410a9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526012"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="a81c9-102">Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a81c9-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="a81c9-103">Formularze systemu Windows <xref:System.Windows.Forms.DateTimePicker> kontroli zapewnia elastyczność w formatowaniu wyświetlanie daty i godziny w formancie.</span><span class="sxs-lookup"><span data-stu-id="a81c9-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="a81c9-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwości umożliwia wybranie ze wstępnie zdefiniowanych formatów, na liście <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="a81c9-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="a81c9-105">Jeśli żaden z tych nie jest odpowiedni do własnych celów, można utworzyć własny styl formatu przy użyciu znaków format na liście <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="a81c9-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="a81c9-106">Aby wyświetlić formatu niestandardowego</span><span class="sxs-lookup"><span data-stu-id="a81c9-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="a81c9-107">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="a81c9-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="a81c9-108">Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> właściwości ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="a81c9-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="a81c9-109">Aby dodać tekst sformatowany wartości</span><span class="sxs-lookup"><span data-stu-id="a81c9-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="a81c9-110">Użyj pojedynczy znaki cudzysłowu należy ująć dowolny znak, który nie jest znak format, takich jak "M" lub ogranicznik, takich jak ":".</span><span class="sxs-lookup"><span data-stu-id="a81c9-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="a81c9-111">Na przykład poniższy ciąg formatu wyświetla bieżącą datę w formacie "obecnie jest: 05:30:31 piątek, 02 marca 2012" w języku angielskim (Stany Zjednoczone) kultury.</span><span class="sxs-lookup"><span data-stu-id="a81c9-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     <span data-ttu-id="a81c9-112">W zależności od ustawienia kulturowe znaków, nie jest ujęta w znaki apostrofu może zostać zmieniona.</span><span class="sxs-lookup"><span data-stu-id="a81c9-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="a81c9-113">Na przykład ciąg formatu powyżej Wyświetla bieżącą datę w formacie "obecnie jest: 05:30:31 piątek, 02 marca 2012" w języku angielskim (Stany Zjednoczone) kultury.</span><span class="sxs-lookup"><span data-stu-id="a81c9-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="a81c9-114">Należy pamiętać, że pierwszy dwukropkiem jest ujęta w pojedynczy cudzysłów, ponieważ nie ma ona być znaki rozdzielające, ponieważ jest on "hh: mm:".</span><span class="sxs-lookup"><span data-stu-id="a81c9-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="a81c9-115">W innym kultury, format mogą być wyświetlane jako "obecnie jest: 05.30.31 piątek, 02 marca 2012".</span><span class="sxs-lookup"><span data-stu-id="a81c9-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a81c9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a81c9-116">See Also</span></span>  
 [<span data-ttu-id="a81c9-117">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a81c9-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [<span data-ttu-id="a81c9-118">Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a81c9-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

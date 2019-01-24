---
title: 'Instrukcje: Wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy Windows'
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
ms.openlocfilehash: 489a31474b8ae3e56ba69e59f6d613ecf892a93c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531294"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="6bc2e-102">Instrukcje: Wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="6bc2e-102">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="6bc2e-103">Formularze Windows <xref:System.Windows.Forms.DateTimePicker> kontrola zapewnia elastyczność do formatowania wyświetlania daty i godziny w formancie.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-103">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="6bc2e-104"><xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwości umożliwia wybranie z wstępnie zdefiniowane formaty, na liście <xref:System.Windows.Forms.DateTimePickerFormat>.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-104">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="6bc2e-105">Jeśli żadna z nich jest odpowiedni do własnych celów, możesz utworzyć własny styl formatu przy użyciu formatu znaków, na liście <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-105">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="6bc2e-106">Aby wyświetlić format niestandardowy</span><span class="sxs-lookup"><span data-stu-id="6bc2e-106">To display a custom format</span></span>  
  
1.  <span data-ttu-id="6bc2e-107">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwość `DateTimePickerFormat.Custom`.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2.  <span data-ttu-id="6bc2e-108">Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> właściwość ciągu formatu.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-108">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="6bc2e-109">Aby dodać tekst sformatowany wartość</span><span class="sxs-lookup"><span data-stu-id="6bc2e-109">To add text to the formatted value</span></span>  
  
1.  <span data-ttu-id="6bc2e-110">Użyj pojedynczego cudzysłowu, aby ująć dowolny znak, który nie jest znakiem formacie, takich jak "M" lub ogranicznik, takie jak ":".</span><span class="sxs-lookup"><span data-stu-id="6bc2e-110">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="6bc2e-111">Na przykład, poniższy ciąg formatu zawiera bieżącą datę w formacie "dziś jest: 05:30:31 marca piątek 02, 2012" w kulturze języka angielskiego (Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="6bc2e-111">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="6bc2e-112">W zależności od ustawienia kulturowe żadnych znaków, nie jest ujęta w znaki pojedynczego cudzysłowu mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="6bc2e-112">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="6bc2e-113">Na przykład ciąg formatu powyżej Wyświetla bieżącą datę w formacie "dziś jest: 05:30:31 marca piątek 02, 2012" w kulturze języka angielskiego (Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="6bc2e-113">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="6bc2e-114">Należy pamiętać, że pierwszym dwukropkiem jest ujęty w znaki pojedynczego cudzysłowu, ponieważ nie jest on przeznaczony jako ogranicznika, ponieważ jest ona "gg".</span><span class="sxs-lookup"><span data-stu-id="6bc2e-114">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="6bc2e-115">W innej kulturze format mogą być wyświetlane jako "dziś jest: 05.30.31 piątek marzec 02, 2012".</span><span class="sxs-lookup"><span data-stu-id="6bc2e-115">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc2e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bc2e-116">See also</span></span>
- [<span data-ttu-id="6bc2e-117">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6bc2e-117">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="6bc2e-118">Instrukcje: Ustaw i zwracają dat za pomocą formantu DateTimePicker formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="6bc2e-118">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

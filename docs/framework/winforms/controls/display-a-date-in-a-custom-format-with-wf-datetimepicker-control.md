---
title: Wyświetlanie daty w formacie niestandardowym z kontrolką DateTimePicker
description: Dowiedz się, jak używać kontrolki DateTimePicker Windows Forms do formatowania wyświetlania dat i godzin w formancie.
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
ms.openlocfilehash: 773070136e4fd43ab1bf510ebcaf6b0aa6a7ba8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325829"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a><span data-ttu-id="a4cf9-103">Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a4cf9-103">How to: Display a Date in a Custom Format with the Windows Forms DateTimePicker Control</span></span>
<span data-ttu-id="a4cf9-104">Formant Windows Forms <xref:System.Windows.Forms.DateTimePicker> zapewnia elastyczność formatowania wyświetlania dat i godzin w formancie.</span><span class="sxs-lookup"><span data-stu-id="a4cf9-104">The Windows Forms <xref:System.Windows.Forms.DateTimePicker> control gives you flexibility in formatting the display of dates and times in the control.</span></span> <span data-ttu-id="a4cf9-105"><xref:System.Windows.Forms.DateTimePicker.Format%2A>Właściwość umożliwia wybranie ze wstępnie zdefiniowanych formatów wymienionych w temacie <xref:System.Windows.Forms.DateTimePickerFormat> .</span><span class="sxs-lookup"><span data-stu-id="a4cf9-105">The <xref:System.Windows.Forms.DateTimePicker.Format%2A> property allows you to select from predefined formats, listed in the <xref:System.Windows.Forms.DateTimePickerFormat>.</span></span> <span data-ttu-id="a4cf9-106">Jeśli żadna z tych elementów nie jest odpowiednia do celów, możesz utworzyć własny styl formatu, używając znaków formatowania wymienionych w <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .</span><span class="sxs-lookup"><span data-stu-id="a4cf9-106">If none of these is adequate for your purposes, you can create your own format style using format characters listed in <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.</span></span>  
  
### <a name="to-display-a-custom-format"></a><span data-ttu-id="a4cf9-107">Aby wyświetlić niestandardowy format</span><span class="sxs-lookup"><span data-stu-id="a4cf9-107">To display a custom format</span></span>  
  
1. <span data-ttu-id="a4cf9-108">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwość na wartość `DateTimePickerFormat.Custom` .</span><span class="sxs-lookup"><span data-stu-id="a4cf9-108">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to `DateTimePickerFormat.Custom`.</span></span>  
  
2. <span data-ttu-id="a4cf9-109">Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> Właściwość na ciąg formatu.</span><span class="sxs-lookup"><span data-stu-id="a4cf9-109">Set the <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> property to a format string.</span></span>  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a><span data-ttu-id="a4cf9-110">Aby dodać tekst do sformatowanej wartości</span><span class="sxs-lookup"><span data-stu-id="a4cf9-110">To add text to the formatted value</span></span>  
  
1. <span data-ttu-id="a4cf9-111">Użyj znaków pojedynczego cudzysłowu, aby ująć dowolny znak, który nie jest znakiem formatu takim jak "M" lub ogranicznikiem ":".</span><span class="sxs-lookup"><span data-stu-id="a4cf9-111">Use single quotation marks to enclose any character that is not a format character like "M" or a delimiter like ":".</span></span> <span data-ttu-id="a4cf9-112">Na przykład ciąg formatu poniżej wyświetla bieżącą datę z formatem "dzisiaj jest: 05:30:31 w piątek marca 02, 2012" w kulturze angielskiej (Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="a4cf9-112">For example, the format string below displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span>  
  
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
  
     <span data-ttu-id="a4cf9-113">W zależności od ustawienia kultury wszystkie znaki, które nie są ujęte w znaki pojedynczego cudzysłowu, mogą zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="a4cf9-113">Depending on the culture setting, any characters not enclosed in single quotation marks may be changed.</span></span> <span data-ttu-id="a4cf9-114">Na przykład ciąg formatu powyżej wyświetla bieżącą datę z formatem "dzisiaj jest: 05:30:31 w piątek marca 02, 2012" w kulturze angielskiej (Stany Zjednoczone).</span><span class="sxs-lookup"><span data-stu-id="a4cf9-114">For example, the format string above displays the current date with the format "Today is: 05:30:31 Friday March 02, 2012" in the English (United States) culture.</span></span> <span data-ttu-id="a4cf9-115">Należy zauważyć, że pierwszy dwukropek jest ujęty w znaki pojedynczego cudzysłowu, ponieważ nie jest przeznaczony do ograniczania znaku, ponieważ jest w formacie "gg: mm: SS".</span><span class="sxs-lookup"><span data-stu-id="a4cf9-115">Note that the first colon is enclosed in single quotation marks, because it is not intended to be a delimiting character as it is in "hh:mm:ss".</span></span> <span data-ttu-id="a4cf9-116">W innej kulturze format może wyglądać tak, jakby "dzisiaj jest: 05.30.31 piątek marca 02, 2012".</span><span class="sxs-lookup"><span data-stu-id="a4cf9-116">In another culture, the format might appear as "Today is: 05.30.31 Friday March 02, 2012".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4cf9-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4cf9-117">See also</span></span>

- [<span data-ttu-id="a4cf9-118">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a4cf9-118">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
- [<span data-ttu-id="a4cf9-119">Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a4cf9-119">How to: Set and Return Dates with the Windows Forms DateTimePicker Control</span></span>](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

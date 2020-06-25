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
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows
Formant Windows Forms <xref:System.Windows.Forms.DateTimePicker> zapewnia elastyczność formatowania wyświetlania dat i godzin w formancie. <xref:System.Windows.Forms.DateTimePicker.Format%2A>Właściwość umożliwia wybranie ze wstępnie zdefiniowanych formatów wymienionych w temacie <xref:System.Windows.Forms.DateTimePickerFormat> . Jeśli żadna z tych elementów nie jest odpowiednia do celów, możesz utworzyć własny styl formatu, używając znaków formatowania wymienionych w <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> .  
  
### <a name="to-display-a-custom-format"></a>Aby wyświetlić niestandardowy format  
  
1. Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwość na wartość `DateTimePickerFormat.Custom` .  
  
2. Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> Właściwość na ciąg formatu.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Aby dodać tekst do sformatowanej wartości  
  
1. Użyj znaków pojedynczego cudzysłowu, aby ująć dowolny znak, który nie jest znakiem formatu takim jak "M" lub ogranicznikiem ":". Na przykład ciąg formatu poniżej wyświetla bieżącą datę z formatem "dzisiaj jest: 05:30:31 w piątek marca 02, 2012" w kulturze angielskiej (Stany Zjednoczone).  
  
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
  
     W zależności od ustawienia kultury wszystkie znaki, które nie są ujęte w znaki pojedynczego cudzysłowu, mogą zostać zmienione. Na przykład ciąg formatu powyżej wyświetla bieżącą datę z formatem "dzisiaj jest: 05:30:31 w piątek marca 02, 2012" w kulturze angielskiej (Stany Zjednoczone). Należy zauważyć, że pierwszy dwukropek jest ujęty w znaki pojedynczego cudzysłowu, ponieważ nie jest przeznaczony do ograniczania znaku, ponieważ jest w formacie "gg: mm: SS". W innej kulturze format może wyglądać tak, jakby "dzisiaj jest: 05.30.31 piątek marca 02, 2012".  
  
## <a name="see-also"></a>Zobacz też

- [DateTimePicker, kontrolka](datetimepicker-control-windows-forms.md)
- [Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy Windows Forms](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

---
title: 'Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy systemu Windows'
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
ms.openlocfilehash: 08d5a505229cd434dbf82e8ae4624bb418efd379
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335943"
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Instrukcje: wyświetlanie daty w niestandardowym formacie za pomocą kontrolki DateTimePicker formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.DateTimePicker> kontrola zapewnia elastyczność do formatowania wyświetlania daty i godziny w formancie. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwości umożliwia wybranie z wstępnie zdefiniowane formaty, na liście <xref:System.Windows.Forms.DateTimePickerFormat>. Jeśli żadna z nich jest odpowiedni do własnych celów, możesz utworzyć własny styl formatu przy użyciu formatu znaków, na liście <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Aby wyświetlić format niestandardowy  
  
1. Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwość `DateTimePickerFormat.Custom`.  
  
2. Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> właściwość ciągu formatu.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Aby dodać tekst sformatowany wartość  
  
1. Użyj pojedynczego cudzysłowu, aby ująć dowolny znak, który nie jest znakiem formacie, takich jak "M" lub ogranicznik, takie jak ":". Na przykład, poniższy ciąg formatu zawiera bieżącą datę w formacie "dziś jest: 05:30:31 marca piątek 02, 2012" w kulturze języka angielskiego (Stany Zjednoczone).  
  
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
  
     W zależności od ustawienia kulturowe żadnych znaków, nie jest ujęta w znaki pojedynczego cudzysłowu mogą ulec zmianie. Na przykład ciąg formatu powyżej Wyświetla bieżącą datę w formacie "dziś jest: 05:30:31 marca piątek 02, 2012" w kulturze języka angielskiego (Stany Zjednoczone). Należy pamiętać, że pierwszym dwukropkiem jest ujęty w znaki pojedynczego cudzysłowu, ponieważ nie jest on przeznaczony jako ogranicznika, ponieważ jest ona "gg". W innej kulturze format mogą być wyświetlane jako "dziś jest: 05.30.31 piątek marzec 02, 2012".  
  
## <a name="see-also"></a>Zobacz także

- [DateTimePicker, kontrolka](datetimepicker-control-windows-forms.md)
- [Instrukcje: ustawianie i zwracanie dat za pomocą kontrolki DateTimePicker formularzy systemu Windows](how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

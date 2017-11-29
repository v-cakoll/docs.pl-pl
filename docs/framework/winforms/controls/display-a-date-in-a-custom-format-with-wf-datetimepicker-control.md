---
title: "Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Porady: wyświetlanie daty w niestandardowym formacie za pomocą formantu DateTimePicker formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.DateTimePicker> kontroli zapewnia elastyczność w formatowaniu wyświetlanie daty i godziny w formancie. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwości umożliwia wybranie ze wstępnie zdefiniowanych formatów, na liście <xref:System.Windows.Forms.DateTimePickerFormat>. Jeśli żaden z tych nie jest odpowiedni do własnych celów, można utworzyć własny styl formatu przy użyciu znaków format na liście <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Aby wyświetlić formatu niestandardowego  
  
1.  Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> właściwości `DateTimePickerFormat.Custom`.  
  
2.  Ustaw <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> właściwości ciągu formatu.  
  
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
  
### <a name="to-add-text-to-the-formatted-value"></a>Aby dodać tekst sformatowany wartości  
  
1.  Użyj pojedynczy znaki cudzysłowu należy ująć dowolny znak, który nie jest znak format, takich jak "M" lub ogranicznik, takich jak ":". Na przykład poniższy ciąg formatu wyświetla bieżącą datę w formacie "obecnie jest: 05:30:31 piątek, 02 marca 2012" w języku angielskim (Stany Zjednoczone) kultury.  
  
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
  
     W zależności od ustawienia kulturowe znaków, nie jest ujęta w znaki apostrofu może zostać zmieniona. Na przykład ciąg formatu powyżej Wyświetla bieżącą datę w formacie "obecnie jest: 05:30:31 piątek, 02 marca 2012" w języku angielskim (Stany Zjednoczone) kultury. Należy pamiętać, że pierwszy dwukropkiem jest ujęta w pojedynczy cudzysłów, ponieważ nie ma ona być znaki rozdzielające, ponieważ jest on "hh: mm:". W innym kultury, format mogą być wyświetlane jako "obecnie jest: 05.30.31 piątek, 02 marca 2012".  
  
## <a name="see-also"></a>Zobacz też  
 [DateTimePicker — formant](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Porady: Ustawianie i zwracanie dat z systemu Windows formantu DateTimePicker formularzy](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)

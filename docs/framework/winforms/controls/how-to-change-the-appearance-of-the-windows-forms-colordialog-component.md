---
title: Zmień wygląd składnika ColorDialog
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
ms.openlocfilehash: 0402d7f3c03a0771512a03ac54e1b093c9fe6e9b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746638"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows
Można skonfigurować wygląd składnika <xref:System.Windows.Forms.ColorDialog> Windows Forms z liczbą jego właściwości. Okno dialogowe ma dwie sekcje — jedną, która zawiera podstawowe kolory i jeden, który umożliwia użytkownikowi Definiowanie kolorów niestandardowych.  
  
 Większość właściwości ogranicza kolory, które użytkownik może wybrać z okna dialogowego. Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> jest ustawiona na `true`, użytkownik może definiować kolory niestandardowe. Właściwość <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> jest `true`, jeśli okno dialogowe jest rozwinięte w celu zdefiniowania kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiuj kolory niestandardowe". Gdy właściwość <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> jest ustawiona na `true`, w oknie dialogowym są wyświetlane wszystkie dostępne kolory z zestawu kolorów podstawowych. Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> jest ustawiona na `true`, użytkownik nie może wybrać kolorami. tylko pełne kolory są dostępne do wybrania.  
  
 Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> jest ustawiona na `true`, w oknie dialogowym pojawi się przycisk Pomoc. Gdy użytkownik kliknie przycisk Pomoc, zostanie zgłoszone zdarzenie <xref:System.Windows.Forms.CommonDialog.HelpRequest> składnika <xref:System.Windows.Forms.ColorDialog>.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Aby skonfigurować wygląd okna dialogowego koloru  
  
1. Ustaw odpowiednie wartości właściwości <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>i <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A>.  
  
    ```vb  
    ColorDialog1.AllowFullOpen = True  
    ColorDialog1.AnyColor = True  
    ColorDialog1.SolidColorOnly = False  
    ColorDialog1.ShowHelp = True  
    ```  
  
    ```csharp  
    colorDialog1.AllowFullOpen = true;  
    colorDialog1.AnyColor = true;  
    colorDialog1.SolidColorOnly = false;  
    colorDialog1.ShowHelp = true;  
    ```  
  
    ```cpp  
    colorDialog1->AllowFullOpen = true;  
    colorDialog1->AnyColor = true;  
    colorDialog1->SolidColorOnly = false;  
    colorDialog1->ShowHelp = true;  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, składnik](colordialog-component-windows-forms.md)
- [ColorDialog, składnik — omówienie](colordialog-component-overview-windows-forms.md)

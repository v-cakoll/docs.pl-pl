---
title: 'Instrukcje: Zmienianie wyglądu składnika ColorDialog formularzy Windows'
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
ms.openlocfilehash: 6bc59f08d811ef542206b5788f251f30f89af301
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702792"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Instrukcje: Zmienianie wyglądu składnika ColorDialog formularzy Windows
Możesz skonfigurować wygląd interfejsu Windows Forms <xref:System.Windows.Forms.ColorDialog> składnika z liczbą jego właściwości. Okno dialogowe ma dwie sekcje — taki, który przedstawia kolory podstawowe i jedną, która pozwala użytkownikowi na definiowanie kolorów niestandardowych.  
  
 Większość właściwości ograniczyć kolorów, które użytkownik może wybrać w oknie dialogowym. Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `true`, użytkownik może definiowanie kolorów niestandardowych. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Właściwość `true` Jeśli okno dialogowe jest rozwinięty, definiowanie kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiowanie kolorów niestandardowych". Gdy <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> właściwość jest ustawiona na `true`, okno dialogowe wyświetla wszystkie dostępne kolory w zestawie kolory podstawowe. Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory szarych; tylko jednolitymi kolorami są dostępne do wybrania.  
  
 Jeśli <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwość jest ustawiona na `true`, pojawia się w oknie dialogowym przycisk pomocy. Gdy użytkownik kliknie przycisk Pomoc <xref:System.Windows.Forms.ColorDialog> składnika <xref:System.Windows.Forms.CommonDialog.HelpRequest> zdarzenie jest wywoływane.  
  
### <a name="to-configure-the-appearance-of-the-color-dialog-box"></a>Aby skonfigurować wygląd okno dialogowe kolorów  
  
1.  Ustaw <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A>, <xref:System.Windows.Forms.ColorDialog.AnyColor%2A>, <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A>, i <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwości, aby odpowiednie wartości.  
  
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

---
title: "Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows"
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
- ColorDialog component [Windows Forms], examples
- ColorDialog component [Windows Forms], formatting appearance
- color dialog box [Windows Forms], configuring appearance
ms.assetid: bba4e262-1cd7-4f63-89cf-330a36f7b539
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af3a9ec6ba301a27a7940bc752ffaf12f345abec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-colordialog-component"></a>Porady: zmienianie wyglądu składnika ColorDialog formularzy systemu Windows
Możesz skonfigurować wygląd formularzy systemu Windows <xref:System.Windows.Forms.ColorDialog> składnika o liczbie jego właściwości. Okno dialogowe ma dwie sekcje —, który przedstawia kolorów podstawowych i taki, który umożliwia użytkownikowi zdefiniowanie kolorów niestandardowych.  
  
 Większość właściwości ograniczyć kolorów, które użytkownik może wybrać w oknie dialogowym. Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `true`, użytkownik będzie mógł Definiuj kolory niestandardowe. <xref:System.Windows.Forms.ColorDialog.FullOpen%2A> Właściwość jest `true` Jeśli okno dialogowe jest rozwinięty, zdefiniowanie kolorów niestandardowych; w przeciwnym razie użytkownik musi kliknąć przycisk "Definiuj kolory niestandardowe". Gdy <xref:System.Windows.Forms.ColorDialog.AnyColor%2A> właściwość jest ustawiona na `true`, okno dialogowe wyświetla wszystkie dostępne kolory w zestawie kolorów podstawowych. Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory symulowanych; wyłącznie pełnych kolorów są dostępne do wybrania.  
  
 Jeśli <xref:System.Windows.Forms.ColorDialog.ShowHelp%2A> właściwość jest ustawiona na `true`, pojawi się przycisk Pomoc w oknie dialogowym. Gdy użytkownik kliknie przycisk Pomoc, <xref:System.Windows.Forms.ColorDialog> składnika <xref:System.Windows.Forms.CommonDialog.HelpRequest> zdarzenie jest wywoływane.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog, składnik](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [ColorDialog, składnik — omówienie](../../../../docs/framework/winforms/controls/colordialog-component-overview-windows-forms.md)

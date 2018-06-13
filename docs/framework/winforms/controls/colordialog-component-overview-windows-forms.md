---
title: ColorDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9b4fb545a2ed35a9c7bad5e28c28d3ec42870860
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526041"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.ColorDialog> składnik jest wstępnie skonfigurowana okno dialogowe, które umożliwia użytkownikowi wybieranie koloru z palety i dodać do tej palety kolorów niestandardowych. To okno dialogowe tego samego widoczne w innych aplikacji systemu Windows, aby wybrać kolorów. Użyj go w aplikacji systemu Windows jako prostym rozwiązaniem zamiast własne okno dialogowe Konfigurowanie.  
  
 Kolor wybrany w oknie dialogowym jest zwracany w <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości. Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `false`, przycisk "Definiuj kolory niestandardowe" jest wyłączona, a użytkownik jest ograniczony do wstępnie zdefiniowanych kolorów w palecie. Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać symulowanych kolorów. Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog, składnik](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Kontrolki i składniki okien dialogowych](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Instrukcje: zmienianie wyglądu składnika ColorDialog formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)

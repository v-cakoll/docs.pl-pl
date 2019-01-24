---
title: ColorDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 9ef7d667b582d3b227f0f0e8af5e7e0335cd4860
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570112"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.ColorDialog> składnik to wstępnie skonfigurowane okno dialogowe, które pozwala użytkownikowi wybrać kolor z palety i dodać kolorów niestandardowych do tej palety. Jest to ten sam okno dialogowe, które pojawi się w innych aplikacji opartych na Windows do wybierania kolorów. Użyj go w ramach aplikacji opartych na Windows jako proste rozwiązanie audytów Konfigurowanie własnego okno dialogowe.  
  
 Kolor wybrany w oknie dialogowym są zwracane w <xref:System.Windows.Forms.ColorDialog.Color%2A> właściwości. Jeśli <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> właściwość jest ustawiona na `false`, przycisk "Definiowanie kolorów niestandardowych" jest wyłączona, a użytkownik jest ograniczone do wstępnie zdefiniowanych kolorów palety. Jeśli <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> właściwość jest ustawiona na `true`, użytkownik może wybrać kolory szarych. Aby wyświetlić okno dialogowe, należy wywołać jej <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, składnik](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
- [Instrukcje: Zmienianie wyglądu składnika ColorDialog formularzy Windows](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)

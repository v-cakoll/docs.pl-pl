---
title: ColorDialog, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
ms.openlocfilehash: 48d9d5072335908f85e65933dadafb1b69f28528
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736963"
---
# <a name="colordialog-component-overview-windows-forms"></a>ColorDialog — Informacje o składniku (Formularze systemu Windows)
Składnik <xref:System.Windows.Forms.ColorDialog> Windows Forms to wstępnie skonfigurowane okno dialogowe, które umożliwia użytkownikowi wybranie koloru z palety i dodanie niestandardowych kolorów do tej palety. To samo okno dialogowe, które jest wyświetlane w innych aplikacjach opartych na systemie Windows, aby wybrać kolory. Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie zamiast konfigurować własne okno dialogowe.  
  
 Kolor wybrany w oknie dialogowym jest zwracany we właściwości <xref:System.Windows.Forms.ColorDialog.Color%2A>. Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> jest ustawiona na `false`, przycisk "Definiuj kolory niestandardowe" jest wyłączony, a użytkownik jest ograniczony do wstępnie zdefiniowanych kolorów w palecie. Jeśli właściwość <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> jest ustawiona na `true`, użytkownik nie może wybrać kolorami. Aby wyświetlić okno dialogowe, należy wywołać jego metodę <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog, składnik](colordialog-component-windows-forms.md)
- [Kontrolki i składniki okien dialogowych](dialog-box-controls-and-components-windows-forms.md)
- [Instrukcje: zmienianie wyglądu składnika ColorDialog formularzy Windows Forms](how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)

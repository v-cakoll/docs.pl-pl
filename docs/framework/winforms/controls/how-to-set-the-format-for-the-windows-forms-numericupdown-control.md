---
title: 'Porady: ustawienie formatu dla formantu NumericUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 1cb8f8b7d2f86125736c08cd9eadf4eee30063bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Porady: ustawienie formatu dla formantu NumericUpDown formularzy systemu Windows
Można skonfigurować sposób wyświetlania wartości w formularzach systemu Windows <xref:System.Windows.Forms.NumericUpDown> formantu. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Właściwość określa liczby są wyświetlane od punktu dziesiętnego; wartość domyślna to 0. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Właściwość określa, czy separator będzie wstawiany między wszystkimi trójkami cyfr dziesiętnych; wartość domyślna to `false`. Kontrolki można wyświetlić wartości w formacie szesnastkowym zamiast format dziesiętny, jeśli <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość jest ustawiona na `true`; wartość domyślna to `false`.  
  
### <a name="to-format-the-numeric-value"></a>Format wartości liczbowe  
  
-   Wyświetl wartość dziesiętną przez ustawienie <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> właściwości na wartość całkowitą i ustawienie <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> właściwości `true` lub `false`.  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     —lub—  
  
-   Wyświetl wartość szesnastkowa przez ustawienie <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwości `true`.  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywane na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości testowania wartości dziesiętnej.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.NumericUpDown>  
 [NumericUpDown, kontrolka](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [NumericUpDown, kontrolka — omówienie](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)

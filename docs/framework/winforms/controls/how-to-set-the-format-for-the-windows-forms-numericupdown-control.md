---
title: 'Instrukcje: Ustawienie formatu dla formantu NumericUpDown formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5574faf858c32752cfa99b6bf339ddf06cb6b345
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631012"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Instrukcje: Ustawienie formatu dla formantu NumericUpDown formularzy Windows
Można skonfigurować sposób wyświetlania wartości w formularzach Windows Forms <xref:System.Windows.Forms.NumericUpDown> kontroli. <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Właściwość określa, ile pojawiają się po punkcie dziesiętnym; wartość domyślna to 0. <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Właściwość określa, czy separator zostanie wstawione między co trzy cyfry dziesiętne; wartość domyślna to `false`. Formant może wyświetlić wartości w formacie szesnastkowym, zamiast formatu dziesiętnego, jeśli <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość jest ustawiona na `true`; wartość domyślna to `false`.  
  
### <a name="to-format-the-numeric-value"></a>Aby sformatować wartość numeryczną  
  
-   Wyświetlanie wartości dziesiętnej, ustawiając <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> właściwości do liczby całkowitej, a ustawienie <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> właściwości `true` lub `false`.  
  
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
  
-   Wyświetlanie wartości szesnastkowych, ustawiając <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość `true`.  
  
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
    >  Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywania na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwość testowania wartości dziesiętnej.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, kontrolka](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)
- [NumericUpDown, kontrolka — omówienie](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)

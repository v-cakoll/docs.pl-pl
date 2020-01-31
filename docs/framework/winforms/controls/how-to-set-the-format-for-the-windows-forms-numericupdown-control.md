---
title: Ustaw format kontrolki NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5ef1c801e96bef7b92e7e69dc36491144c456eeb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742175"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a>Porady: ustawienie formatu dla formantu NumericUpDown formularzy systemu Windows
Można skonfigurować sposób wyświetlania wartości w kontrolce <xref:System.Windows.Forms.NumericUpDown> Windows Forms. Właściwość <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> określa, ile numerów pojawia się po przecinku dziesiętnym; wartość domyślna to 0. Właściwość <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> określa, czy separator ma być wstawiany między każdą trzema cyframi dziesiętnymi; wartość domyślna to `false`. Kontrolka może wyświetlać wartości w formacie szesnastkowym, a nie dziesiętnym, jeśli właściwość <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> jest ustawiona na `true`; wartość domyślna to `false`.  
  
### <a name="to-format-the-numeric-value"></a>Aby sformatować wartość liczbową  
  
- Wyświetl wartość dziesiętną, ustawiając właściwość <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> na liczbę całkowitą i ustawiając właściwość <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> na `true` lub `false`.  
  
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
  
     lub  
  
- Wyświetl wartość szesnastkową, ustawiając właściwość <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> na `true`.  
  
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
    > Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywane na właściwości <xref:System.Windows.Forms.NumericUpDown.Value%2A> będą testowanie wartości dziesiętnej.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NumericUpDown>
- [NumericUpDown, kontrolka](numericupdown-control-windows-forms.md)
- [NumericUpDown, kontrolka — omówienie](numericupdown-control-overview-windows-forms.md)

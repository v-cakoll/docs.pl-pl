---
title: Ustawianie i zwracanie wartości liczbowych z kontrolką NumericUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: a0b264fec9619b467c293bcb96278c4517775ac3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743023"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Porady: ustawianie i zwracanie wartości liczbowych za pomocą formantu NumericUpDown formularzy systemu Windows
Wartość liczbowa kontrolki <xref:System.Windows.Forms.NumericUpDown> Windows Forms jest określana na podstawie jej właściwości <xref:System.Windows.Forms.NumericUpDown.Value%2A>. Można napisać testy warunkowe dla wartości kontrolki tak samo jak w przypadku każdej innej właściwości. Po ustawieniu właściwości <xref:System.Windows.Forms.NumericUpDown.Value%2A> można dostosować ją bezpośrednio przez napisanie kodu w celu wykonania operacji na nim lub wywołać metody <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
### <a name="to-set-the-numeric-value"></a>Aby ustawić wartość liczbową  
  
1. Przypisz wartość do właściwości <xref:System.Windows.Forms.NumericUpDown.Value%2A> w kodzie lub w okno Właściwości.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     lub  
  
2. Wywołaj metodę <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> lub <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>, aby zwiększyć lub zmniejszyć wartość o kwotę określoną we właściwości <xref:System.Windows.Forms.NumericUpDown.Increment%2A>.  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>Aby zwrócić wartość liczbową  
  
- Uzyskaj dostęp do właściwości <xref:System.Windows.Forms.NumericUpDown.Value%2A> w kodzie.  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [NumericUpDown, kontrolka](numericupdown-control-windows-forms.md)
- [NumericUpDown, kontrolka — omówienie](numericupdown-control-overview-windows-forms.md)

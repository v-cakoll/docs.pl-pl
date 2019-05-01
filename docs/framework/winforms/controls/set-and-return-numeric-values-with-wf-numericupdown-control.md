---
title: 'Instrukcje: ustawianie i zwracanie wartości liczbowych za pomocą kontrolki NumericUpDown formularzy systemu Windows'
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
ms.openlocfilehash: c73200eb1c373f1d723ba82f2e6be5b625496b59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902229"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>Instrukcje: ustawianie i zwracanie wartości liczbowych za pomocą kontrolki NumericUpDown formularzy systemu Windows
Wartość liczbowa formularzy Windows Forms <xref:System.Windows.Forms.NumericUpDown> kontrolki jest określany przez jego <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości. Możesz tworzyć testów warunkowych wartości kontrolki podobnie jak w przypadku wszystkich innych właściwości. Gdy <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwość jest ustawiona, możesz je dostosować bezpośrednio przez napisanie kodu, aby wykonywać operacje na nim lub może wywołać <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metody.  
  
### <a name="to-set-the-numeric-value"></a>Aby ustawić wartość liczbową  
  
1. Przypisanie wartości do <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości w kodzie lub w oknie dialogowym właściwości.  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     —lub—  
  
2. Wywołaj <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> lub <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metodę, aby zwiększyć lub zmniejszyć wartość określoną w <xref:System.Windows.Forms.NumericUpDown.Increment%2A> właściwości.  
  
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
  
- Dostęp do <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości w kodzie.  
  
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

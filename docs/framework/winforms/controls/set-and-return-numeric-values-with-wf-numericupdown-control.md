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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300505"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="95f16-102">Instrukcje: ustawianie i zwracanie wartości liczbowych za pomocą kontrolki NumericUpDown formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95f16-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="95f16-103">Wartość liczbowa formularzy Windows Forms <xref:System.Windows.Forms.NumericUpDown> kontrolki jest określany przez jego <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="95f16-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="95f16-104">Możesz tworzyć testów warunkowych wartości kontrolki podobnie jak w przypadku wszystkich innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="95f16-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="95f16-105">Gdy <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwość jest ustawiona, możesz je dostosować bezpośrednio przez napisanie kodu, aby wykonywać operacje na nim lub może wywołać <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> i <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="95f16-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="95f16-106">Aby ustawić wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="95f16-106">To set the numeric value</span></span>  
  
1. <span data-ttu-id="95f16-107">Przypisanie wartości do <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości w kodzie lub w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="95f16-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="95f16-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="95f16-108">-or-</span></span>  
  
2. <span data-ttu-id="95f16-109">Wywołaj <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> lub <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> metodę, aby zwiększyć lub zmniejszyć wartość określoną w <xref:System.Windows.Forms.NumericUpDown.Increment%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="95f16-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="95f16-110">Aby zwrócić wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="95f16-110">To return the numeric value</span></span>  
  
-   <span data-ttu-id="95f16-111">Dostęp do <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości w kodzie.</span><span class="sxs-lookup"><span data-stu-id="95f16-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="95f16-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95f16-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [<span data-ttu-id="95f16-113">NumericUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="95f16-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="95f16-114">NumericUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="95f16-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)

---
title: 'Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5957a44c7b07aa1b8d8df32667f023c0873ec1de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013195"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="a0de1-102">Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a0de1-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="a0de1-103">Można skonfigurować sposób wyświetlania wartości w formularzach Windows Forms <xref:System.Windows.Forms.NumericUpDown> kontroli.</span><span class="sxs-lookup"><span data-stu-id="a0de1-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="a0de1-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Właściwość określa, ile pojawiają się po punkcie dziesiętnym; wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="a0de1-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="a0de1-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Właściwość określa, czy separator zostanie wstawione między co trzy cyfry dziesiętne; wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a0de1-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="a0de1-106">Formant może wyświetlić wartości w formacie szesnastkowym, zamiast formatu dziesiętnego, jeśli <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość jest ustawiona na `true`; wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="a0de1-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="a0de1-107">Aby sformatować wartość numeryczną</span><span class="sxs-lookup"><span data-stu-id="a0de1-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="a0de1-108">Wyświetlanie wartości dziesiętnej, ustawiając <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> właściwości do liczby całkowitej, a ustawienie <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> właściwości `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="a0de1-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="a0de1-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="a0de1-109">-or-</span></span>  
  
- <span data-ttu-id="a0de1-110">Wyświetlanie wartości szesnastkowych, ustawiając <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="a0de1-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="a0de1-111">Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywania na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwość testowania wartości dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="a0de1-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0de1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0de1-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="a0de1-113">NumericUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a0de1-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="a0de1-114">NumericUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a0de1-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)

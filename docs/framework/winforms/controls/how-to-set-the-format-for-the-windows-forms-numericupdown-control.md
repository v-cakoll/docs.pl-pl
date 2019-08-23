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
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949160"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="1ca70-102">Instrukcje: ustawienie formatu dla kontrolki NumericUpDown formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1ca70-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="1ca70-103">Można skonfigurować sposób wyświetlania wartości w kontrolce Windows Forms <xref:System.Windows.Forms.NumericUpDown> .</span><span class="sxs-lookup"><span data-stu-id="1ca70-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="1ca70-104">Właściwość <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> określa, ile liczb pojawia się po przecinku dziesiętnym; wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="1ca70-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="1ca70-105">Właściwość <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> określa, czy separator zostanie wstawiony między każdą trzema cyframi dziesiętnymi; wartość domyślna `false`to.</span><span class="sxs-lookup"><span data-stu-id="1ca70-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="1ca70-106">Kontrolka może wyświetlać wartości w formacie szesnastkowym, a nie dziesiętnym <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> , jeśli właściwość jest `true`ustawiona na; wartość `false`domyślna to.</span><span class="sxs-lookup"><span data-stu-id="1ca70-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="1ca70-107">Aby sformatować wartość liczbową</span><span class="sxs-lookup"><span data-stu-id="1ca70-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="1ca70-108">Wyświetl wartość dziesiętną <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> , ustawiając właściwość na liczbę całkowitą i <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> ustawiając właściwość na `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="1ca70-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="1ca70-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="1ca70-109">-or-</span></span>  
  
- <span data-ttu-id="1ca70-110">Wyświetl wartość szesnastkową, ustawiając <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość na. `true`</span><span class="sxs-lookup"><span data-stu-id="1ca70-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="1ca70-111">Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywane na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości będą testowanie wartości dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="1ca70-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca70-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ca70-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="1ca70-113">NumericUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1ca70-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="1ca70-114">NumericUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1ca70-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)

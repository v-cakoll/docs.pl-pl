---
title: 'Porady: ustawienie formatu dla formantu NumericUpDown formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4ff6d8e584e65482285012af351ebd1a669b806
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="ce356-102">Porady: ustawienie formatu dla formantu NumericUpDown formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ce356-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="ce356-103">Można skonfigurować sposób wyświetlania wartości w formularzach systemu Windows <xref:System.Windows.Forms.NumericUpDown> formantu.</span><span class="sxs-lookup"><span data-stu-id="ce356-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="ce356-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> Właściwość określa liczby są wyświetlane od punktu dziesiętnego; wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="ce356-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="ce356-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> Właściwość określa, czy separator będzie wstawiany między wszystkimi trójkami cyfr dziesiętnych; wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ce356-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="ce356-106">Kontrolki można wyświetlić wartości w formacie szesnastkowym zamiast format dziesiętny, jeśli <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwość jest ustawiona na `true`; wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="ce356-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="ce356-107">Format wartości liczbowe</span><span class="sxs-lookup"><span data-stu-id="ce356-107">To format the numeric value</span></span>  
  
-   <span data-ttu-id="ce356-108">Wyświetl wartość dziesiętną przez ustawienie <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> właściwości na wartość całkowitą i ustawienie <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> właściwości `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="ce356-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="ce356-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="ce356-109">-or-</span></span>  
  
-   <span data-ttu-id="ce356-110">Wyświetl wartość szesnastkowa przez ustawienie <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="ce356-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="ce356-111">Nawet jeśli wartość jest wyświetlana w postaci szesnastkowej, wszystkie testy wykonywane na <xref:System.Windows.Forms.NumericUpDown.Value%2A> właściwości testowania wartości dziesiętnej.</span><span class="sxs-lookup"><span data-stu-id="ce356-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce356-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce356-112">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 [<span data-ttu-id="ce356-113">NumericUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="ce356-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="ce356-114">NumericUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="ce356-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)

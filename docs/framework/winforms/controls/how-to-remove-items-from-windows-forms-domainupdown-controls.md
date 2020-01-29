---
title: Usuń elementy z kontrolek DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: e52af5c5add4fda93e2b51c8afdb90c92e8d2f62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735772"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="a4f1a-102">Porady: dodawanie i usuwanie elementów za pomocą formantu DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a4f1a-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="a4f1a-103">Elementy można usunąć z kontrolki <xref:System.Windows.Forms.DomainUpDown> Windows Forms, wywołując metodę <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> klasy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>.</span><span class="sxs-lookup"><span data-stu-id="a4f1a-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="a4f1a-104">Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> usuwa określony element, podczas gdy metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> usuwa element według jego położenia.</span><span class="sxs-lookup"><span data-stu-id="a4f1a-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="a4f1a-105">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="a4f1a-105">To remove an item</span></span>  
  
- <span data-ttu-id="a4f1a-106">Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> klasy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>, aby usunąć element według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a4f1a-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="a4f1a-107">lub</span><span class="sxs-lookup"><span data-stu-id="a4f1a-107">-or-</span></span>  
  
- <span data-ttu-id="a4f1a-108">Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>, aby usunąć element według jego położenia.</span><span class="sxs-lookup"><span data-stu-id="a4f1a-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
    ```vb  
    ' Removes the first item in the list.  
    DomainUpDown1.Items.RemoveAt(0)  
    ```  
  
    ```csharp  
    // Removes the first item in the list.  
    domainUpDown1.Items.RemoveAt(0);  
    ```  
  
    ```cpp  
    // Removes the first item in the list.  
    domainUpDown1->Items->RemoveAt(0);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a4f1a-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4f1a-109">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a4f1a-110">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a4f1a-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="a4f1a-111">DomainUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a4f1a-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)

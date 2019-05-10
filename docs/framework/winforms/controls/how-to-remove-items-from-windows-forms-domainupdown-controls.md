---
title: 'Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki DomainUpDown'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: f56bc2b7b7b8a783ac298b220c83281f38da29da
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662349"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="a69d9-102">Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="a69d9-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="a69d9-103">Możesz usunąć elementy z formularzy Windows <xref:System.Windows.Forms.DomainUpDown> kontroli przez wywołanie metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="a69d9-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="a69d9-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda usuwa określony element, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda usuwa element według ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="a69d9-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="a69d9-105">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="a69d9-105">To remove an item</span></span>  
  
- <span data-ttu-id="a69d9-106">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy, aby usunąć element według nazwy.</span><span class="sxs-lookup"><span data-stu-id="a69d9-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="a69d9-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="a69d9-107">-or-</span></span>  
  
- <span data-ttu-id="a69d9-108">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodę, aby usunąć element według ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="a69d9-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a69d9-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a69d9-109">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a69d9-110">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a69d9-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="a69d9-111">DomainUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a69d9-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)

---
title: 'Instrukcje: Usuwanie elementów z kontrolki DomainUpDown formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
ms.openlocfilehash: 58c93f478414d24c2fdda0f9662936a8b520e381
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708967"
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="abbac-102">Instrukcje: Usuwanie elementów z kontrolki DomainUpDown formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="abbac-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="abbac-103">Możesz usunąć elementy z formularzy Windows <xref:System.Windows.Forms.DomainUpDown> kontroli przez wywołanie metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="abbac-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="abbac-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda usuwa określony element, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda usuwa element według ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="abbac-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="abbac-105">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="abbac-105">To remove an item</span></span>  
  
-   <span data-ttu-id="abbac-106">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy, aby usunąć element według nazwy.</span><span class="sxs-lookup"><span data-stu-id="abbac-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="abbac-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="abbac-107">-or-</span></span>  
  
-   <span data-ttu-id="abbac-108">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodę, aby usunąć element według ich pozycji.</span><span class="sxs-lookup"><span data-stu-id="abbac-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="abbac-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abbac-109">See also</span></span>
- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [<span data-ttu-id="abbac-110">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="abbac-110">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="abbac-111">DomainUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="abbac-111">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)

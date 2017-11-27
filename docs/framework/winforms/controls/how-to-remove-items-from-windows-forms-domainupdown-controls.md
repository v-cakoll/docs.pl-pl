---
title: "Porady: dodawanie i usuwanie elementów za pomocą formantu DomainUpDown"
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
- DomainUpDown control [Windows Forms], removing items from
- spin button control [Windows Forms], removing items
ms.assetid: e70f5cbc-b497-41a9-975a-344c00e56ed2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cab9bf4445c7322c1b4824f26c0821de8c58657
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a><span data-ttu-id="2dd4c-102">Porady: dodawanie i usuwanie elementów za pomocą formantu DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="2dd4c-102">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>
<span data-ttu-id="2dd4c-103">Należy usunąć elementy z formularzy systemu Windows <xref:System.Windows.Forms.DomainUpDown> kontroli przez wywołanie metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="2dd4c-103">You can remove items from the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control by calling the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class.</span></span> <span data-ttu-id="2dd4c-104"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda usuwa określony element, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda usuwa element przez jego położenie.</span><span class="sxs-lookup"><span data-stu-id="2dd4c-104">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method removes a specific item, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method removes an item by its position.</span></span>  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="2dd4c-105">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="2dd4c-105">To remove an item</span></span>  
  
-   <span data-ttu-id="2dd4c-106">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy, aby usunąć element według nazwy.</span><span class="sxs-lookup"><span data-stu-id="2dd4c-106">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to remove an item by name.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     <span data-ttu-id="2dd4c-107">—lub—</span><span class="sxs-lookup"><span data-stu-id="2dd4c-107">-or-</span></span>  
  
-   <span data-ttu-id="2dd4c-108">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodę, aby usunąć element przez jego położenie.</span><span class="sxs-lookup"><span data-stu-id="2dd4c-108">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> method to remove an item by its position.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2dd4c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dd4c-109">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="2dd4c-110">DomainUpDown — formant</span><span class="sxs-lookup"><span data-stu-id="2dd4c-110">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [<span data-ttu-id="2dd4c-111">Informacje o formancie DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="2dd4c-111">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)

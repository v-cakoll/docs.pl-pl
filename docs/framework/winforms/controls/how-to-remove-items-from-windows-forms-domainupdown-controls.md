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
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu DomainUpDown
Należy usunąć elementy z formularzy systemu Windows <xref:System.Windows.Forms.DomainUpDown> kontroli przez wywołanie metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> Metoda usuwa określony element, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metoda usuwa element przez jego położenie.  
  
### <a name="to-remove-an-item"></a>Aby usunąć element  
  
-   Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy, aby usunąć element według nazwy.  
  
    ```vb  
    DomainUpDown1.Items.Remove("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Remove("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Remove("noodles");  
    ```  
  
     —lub—  
  
-   Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> metodę, aby usunąć element przez jego położenie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>  
 [DomainUpDown — formant](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [Informacje o formancie DomainUpDown](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)

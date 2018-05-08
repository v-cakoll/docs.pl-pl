---
title: 'Porady: dodawanie w sposób programowy elementów do formantu DomainUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 7359310b092e84b250c09153ef86d44c70d413fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Porady: dodawanie w sposób programowy elementów do formantu DomainUpDown formularzy systemu Windows
Można dodać elementy do formularzy systemu Windows <xref:System.Windows.Forms.DomainUpDown> kontroli w kodzie. Wywołanie <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy do dodawania elementów do formantu <xref:System.Windows.Forms.DomainUpDown.Items%2A> właściwości. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metody dodaje element do końca kolekcji, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metody dodaje element na określonej pozycji.  
  
### <a name="to-add-a-new-item"></a>Aby dodać nowy element  
  
1.  Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> metodę, aby dodać element na końcu listy elementów.  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     —lub—  
  
2.  Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metody, aby wstawić element na liście w określonej pozycji.  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DomainUpDown>  
 <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>  
 <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>  
 [DomainUpDown, kontrolka](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)  
 [DomainUpDown, kontrolka — omówienie](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)

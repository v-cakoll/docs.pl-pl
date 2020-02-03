---
title: Programowanie dodawanie elementów do kontrolki DomainUpDown
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 2e9f51fa051bf9b62e95f289db97bffd83450036
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745583"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Porady: dodawanie w sposób programowy elementów do formantu DomainUpDown formularzy systemu Windows
Możesz dodać elementy do kontrolki <xref:System.Windows.Forms.DomainUpDown> Windows Forms w kodzie. Wywołaj metodę <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> klasy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>, aby dodać elementy do właściwości <xref:System.Windows.Forms.DomainUpDown.Items%2A> kontrolki. Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> dodaje element na końcu kolekcji, podczas gdy metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> dodaje element w określonej pozycji.  
  
### <a name="to-add-a-new-item"></a>Aby dodać nowy element  
  
1. Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A>, aby dodać element na końcu listy elementów.  
  
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
  
2. Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A>, aby wstawić element do listy w określonym położeniu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [DomainUpDown, kontrolka](domainupdown-control-windows-forms.md)
- [DomainUpDown, kontrolka — omówienie](domainupdown-control-overview-windows-forms.md)

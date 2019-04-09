---
title: 'Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 32f58dc8b8b96a3d8660550d8ce7696839587ddc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080673"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a>Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy systemu Windows
Można dodać elementy do formularzy Windows Forms <xref:System.Windows.Forms.DomainUpDown> kontrolki w kodzie. Wywołaj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy do dodawania elementów do formantu <xref:System.Windows.Forms.DomainUpDown.Items%2A> właściwości. <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metoda dodaje element do końca kolekcji, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda dodaje element na określonej pozycji.  
  
### <a name="to-add-a-new-item"></a>Aby dodać nowy element  
  
1.  Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> metodę, aby dodać element do końca listy elementów.  
  
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
  
2.  Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodę, aby wstawić element do listy na określonej pozycji.  
  
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

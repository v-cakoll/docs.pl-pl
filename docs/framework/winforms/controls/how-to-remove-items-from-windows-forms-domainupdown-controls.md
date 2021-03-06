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
# <a name="how-to-remove-items-from-windows-forms-domainupdown-controls"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu DomainUpDown
Elementy można usunąć z kontrolki <xref:System.Windows.Forms.DomainUpDown> Windows Forms, wywołując metodę <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> klasy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>. Metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> usuwa określony element, podczas gdy metoda <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A> usuwa element według jego położenia.  
  
### <a name="to-remove-an-item"></a>Aby usunąć element  
  
- Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A> klasy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection>, aby usunąć element według nazwy.  
  
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
  
- Użyj metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A>, aby usunąć element według jego położenia.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.RemoveAt%2A?displayProperty=nameWithType>
- [DomainUpDown, kontrolka](domainupdown-control-windows-forms.md)
- [DomainUpDown, kontrolka — omówienie](domainupdown-control-overview-windows-forms.md)

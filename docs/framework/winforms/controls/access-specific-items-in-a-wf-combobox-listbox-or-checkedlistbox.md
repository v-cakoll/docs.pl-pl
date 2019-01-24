---
title: 'Instrukcje: Uzyskiwanie dostępu do określonych elementów w Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ComboBox control [Windows Forms], accessing items
- ListBox control [Windows Forms], returning item information
- list boxes [Windows Forms], accessing items
- ListBox control [Windows Forms], accessing items
- combo boxes [Windows Forms], accessing items
- CheckedListBox control [Windows Forms], accessing items
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
ms.openlocfilehash: b6478c24550f9f32ea75899521f7aa610ef12955
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656703"
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Instrukcje: Uzyskiwanie dostępu do określonych elementów w Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka
Uzyskiwanie dostępu do określonych elementów w pole kombi Windows Forms, pole listy lub pole listy zaznaczone jest zadaniem podstawowych. Umożliwia programowe wyznaczanie, co to jest na liście w poszczególnych pozycji.  
  
### <a name="to-access-a-specific-item"></a>Aby dostęp do określonego elementu  
  
1.  Zapytanie `Items` kolekcji przy użyciu indeksu konkretny element:  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

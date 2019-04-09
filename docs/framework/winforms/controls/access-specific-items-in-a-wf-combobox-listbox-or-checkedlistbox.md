---
title: 'Instrukcje: uzyskiwanie dostępu do określonych elementów w kontrolkach ComboBox, ListBox lub CheckedListBox formularzy systemu Windows'
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
ms.openlocfilehash: 3d61a9b38f809d16e95b485893acaadcf04d826f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077215"
---
# <a name="how-to-access-specific-items-in-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="b3366-102">Instrukcje: uzyskiwanie dostępu do określonych elementów w kontrolkach ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b3366-102">How to: Access Specific Items in a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="b3366-103">Uzyskiwanie dostępu do określonych elementów w pole kombi Windows Forms, pole listy lub pole listy zaznaczone jest zadaniem podstawowych.</span><span class="sxs-lookup"><span data-stu-id="b3366-103">Accessing specific items in a Windows Forms combo box, list box, or checked list box is an essential task.</span></span> <span data-ttu-id="b3366-104">Umożliwia programowe wyznaczanie, co to jest na liście w poszczególnych pozycji.</span><span class="sxs-lookup"><span data-stu-id="b3366-104">It enables you to programmatically determine what is in a list, at any given position.</span></span>  
  
### <a name="to-access-a-specific-item"></a><span data-ttu-id="b3366-105">Aby dostęp do określonego elementu</span><span class="sxs-lookup"><span data-stu-id="b3366-105">To access a specific item</span></span>  
  
1.  <span data-ttu-id="b3366-106">Zapytanie `Items` kolekcji przy użyciu indeksu konkretny element:</span><span class="sxs-lookup"><span data-stu-id="b3366-106">Query the `Items` collection using the index of the specific item:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3366-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3366-107">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="b3366-108">Formanty formularzy systemu Windows używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="b3366-108">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

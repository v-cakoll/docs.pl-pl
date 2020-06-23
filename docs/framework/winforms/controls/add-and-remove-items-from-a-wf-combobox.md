---
title: Dodawanie i usuwanie elementów z kontrolki ComboBox, ListBox lub CheckedListBox
ms.date: 03/30/2017
description: Dowiedz się, jak dodawać i usuwać Windows Forms kontrolki ComboBox, ListBox i CheckedListBox po prostu i bez powiązania danych.
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
ms.openlocfilehash: f3701257bbe410bf03c4c21700705e87b581bf2e
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904445"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="1595f-103">Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1595f-103">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="1595f-104">Elementy można dodawać do pola kombi Windows Forms, pola listy lub pola listy zaznaczonej na różne sposoby, ponieważ te formanty mogą być powiązane z różnymi źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="1595f-104">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="1595f-105">Jednak w tym temacie przedstawiono najprostszą metodę i nie wymaga powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="1595f-105">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="1595f-106">Wyświetlane elementy są zwykle ciągami; można jednak użyć dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1595f-106">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="1595f-107">Tekst wyświetlany w kontrolce jest wartością zwracaną przez `ToString` metodę obiektu.</span><span class="sxs-lookup"><span data-stu-id="1595f-107">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="1595f-108">Aby dodać elementy</span><span class="sxs-lookup"><span data-stu-id="1595f-108">To add items</span></span>  
  
1. <span data-ttu-id="1595f-109">Dodaj ciąg lub obiekt do listy przy użyciu `Add` metody `ObjectCollection` klasy.</span><span class="sxs-lookup"><span data-stu-id="1595f-109">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="1595f-110">Odwołuje się do kolekcji przy użyciu `Items` Właściwości:</span><span class="sxs-lookup"><span data-stu-id="1595f-110">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="1595f-111">oraz</span><span class="sxs-lookup"><span data-stu-id="1595f-111">or -</span></span>  
  
2. <span data-ttu-id="1595f-112">Wstaw ciąg lub obiekt w żądanym punkcie listy za pomocą `Insert` metody:</span><span class="sxs-lookup"><span data-stu-id="1595f-112">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="1595f-113">oraz</span><span class="sxs-lookup"><span data-stu-id="1595f-113">or -</span></span>  
  
3. <span data-ttu-id="1595f-114">Przypisz całą tablicę do `Items` kolekcji:</span><span class="sxs-lookup"><span data-stu-id="1595f-114">Assign an entire array to the `Items` collection:</span></span>  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="1595f-115">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="1595f-115">To remove an item</span></span>  
  
1. <span data-ttu-id="1595f-116">Wywołaj `Remove` metodę lub, `RemoveAt` Aby usunąć elementy.</span><span class="sxs-lookup"><span data-stu-id="1595f-116">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="1595f-117">`Remove`ma jeden argument, który określa element do usunięcia.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="1595f-117">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="1595f-118">Usuwa element o określonym numerze indeksu.</span><span class="sxs-lookup"><span data-stu-id="1595f-118">removes the item with the specified index number.</span></span>  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a><span data-ttu-id="1595f-119">Aby usunąć wszystkie elementy</span><span class="sxs-lookup"><span data-stu-id="1595f-119">To remove all items</span></span>  
  
1. <span data-ttu-id="1595f-120">Wywołaj `Clear` metodę, aby usunąć wszystkie elementy z kolekcji:</span><span class="sxs-lookup"><span data-stu-id="1595f-120">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1595f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1595f-121">See also</span></span>

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="1595f-122">Porady: sortowanie zawartości formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1595f-122">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="1595f-123">Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="1595f-123">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="1595f-124">Formanty formularzy systemu Windows używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="1595f-124">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

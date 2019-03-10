---
title: 'Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka'
ms.date: 03/30/2017
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
ms.openlocfilehash: 1430975a48fb0755c6b08d6d5c183d8f29434f55
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710449"
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="d1b44-102">Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d1b44-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="d1b44-103">Elementy mogą być dodawane do pola kombi Windows Forms, pole listy lub sprawdzić pola listy w na różne sposoby, ponieważ te kontrolki mogą być powiązane z różnymi źródłami danych.</span><span class="sxs-lookup"><span data-stu-id="d1b44-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="d1b44-104">Jednak w tym temacie przedstawiono najprostszą metodą i wymaga żadne wiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="d1b44-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="d1b44-105">Elementy wyświetlane są zwykle ciągów; Jednak każdy obiekt może być używany.</span><span class="sxs-lookup"><span data-stu-id="d1b44-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="d1b44-106">Tekst, który jest wyświetlany w kontrolce jest wartość zwrócona przez obiekt `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="d1b44-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="d1b44-107">Aby dodać elementy</span><span class="sxs-lookup"><span data-stu-id="d1b44-107">To add items</span></span>  
  
1.  <span data-ttu-id="d1b44-108">Dodaj ciąg lub obiekt do listy przy użyciu `Add` metody `ObjectCollection` klasy.</span><span class="sxs-lookup"><span data-stu-id="d1b44-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="d1b44-109">Kolekcja jest wskazywane za pomocą `Items` właściwości:</span><span class="sxs-lookup"><span data-stu-id="d1b44-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="d1b44-110">lub —</span><span class="sxs-lookup"><span data-stu-id="d1b44-110">or -</span></span>  
  
2.  <span data-ttu-id="d1b44-111">Wstaw ciąg lub obiekt w żądany moment na liście z `Insert` metody:</span><span class="sxs-lookup"><span data-stu-id="d1b44-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="d1b44-112">lub —</span><span class="sxs-lookup"><span data-stu-id="d1b44-112">or -</span></span>  
  
3.  <span data-ttu-id="d1b44-113">Przypisz całej tablicy, aby `Items` kolekcji:</span><span class="sxs-lookup"><span data-stu-id="d1b44-113">Assign an entire array to the `Items` collection:</span></span>  
  
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
  
### <a name="to-remove-an-item"></a><span data-ttu-id="d1b44-114">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="d1b44-114">To remove an item</span></span>  
  
1.  <span data-ttu-id="d1b44-115">Wywołaj `Remove` lub `RemoveAt` metodę, aby usunąć elementy.</span><span class="sxs-lookup"><span data-stu-id="d1b44-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="d1b44-116">`Remove` ma jeden argument, który określa element do usunięcia.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="d1b44-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="d1b44-117">Usuwa element o określonym indeksie.</span><span class="sxs-lookup"><span data-stu-id="d1b44-117">removes the item with the specified index number.</span></span>  
  
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
  
### <a name="to-remove-all-items"></a><span data-ttu-id="d1b44-118">Aby usunąć wszystkie elementy</span><span class="sxs-lookup"><span data-stu-id="d1b44-118">To remove all items</span></span>  
  
1.  <span data-ttu-id="d1b44-119">Wywołaj `Clear` metodę, aby usunąć wszystkie elementy z kolekcji:</span><span class="sxs-lookup"><span data-stu-id="d1b44-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d1b44-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1b44-120">See also</span></span>
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [<span data-ttu-id="d1b44-121">Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="d1b44-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [<span data-ttu-id="d1b44-122">Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="d1b44-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [<span data-ttu-id="d1b44-123">Kontrolki formularzy Windows Forms używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="d1b44-123">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

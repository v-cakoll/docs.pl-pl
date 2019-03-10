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
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Instrukcje: Dodawanie i usuwanie elementów z Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka
Elementy mogą być dodawane do pola kombi Windows Forms, pole listy lub sprawdzić pola listy w na różne sposoby, ponieważ te kontrolki mogą być powiązane z różnymi źródłami danych. Jednak w tym temacie przedstawiono najprostszą metodą i wymaga żadne wiązanie danych. Elementy wyświetlane są zwykle ciągów; Jednak każdy obiekt może być używany. Tekst, który jest wyświetlany w kontrolce jest wartość zwrócona przez obiekt `ToString` metody.  
  
### <a name="to-add-items"></a>Aby dodać elementy  
  
1.  Dodaj ciąg lub obiekt do listy przy użyciu `Add` metody `ObjectCollection` klasy. Kolekcja jest wskazywane za pomocą `Items` właściwości:  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - lub —  
  
2.  Wstaw ciąg lub obiekt w żądany moment na liście z `Insert` metody:  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - lub —  
  
3.  Przypisz całej tablicy, aby `Items` kolekcji:  
  
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
  
### <a name="to-remove-an-item"></a>Aby usunąć element  
  
1.  Wywołaj `Remove` lub `RemoveAt` metodę, aby usunąć elementy.  
  
     `Remove` ma jeden argument, który określa element do usunięcia.`RemoveAt` Usuwa element o określonym indeksie.  
  
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
  
### <a name="to-remove-all-items"></a>Aby usunąć wszystkie elementy  
  
1.  Wywołaj `Clear` metodę, aby usunąć wszystkie elementy z kolekcji:  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Instrukcje: Sortowanie zawartości Windows Forms ComboBox, ListBox lub CheckedListBox, kontrolka](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Kontrolki formularzy Windows Forms używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)

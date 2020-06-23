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
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows
Elementy można dodawać do pola kombi Windows Forms, pola listy lub pola listy zaznaczonej na różne sposoby, ponieważ te formanty mogą być powiązane z różnymi źródłami danych. Jednak w tym temacie przedstawiono najprostszą metodę i nie wymaga powiązania danych. Wyświetlane elementy są zwykle ciągami; można jednak użyć dowolnego obiektu. Tekst wyświetlany w kontrolce jest wartością zwracaną przez `ToString` metodę obiektu.  
  
### <a name="to-add-items"></a>Aby dodać elementy  
  
1. Dodaj ciąg lub obiekt do listy przy użyciu `Add` metody `ObjectCollection` klasy. Odwołuje się do kolekcji przy użyciu `Items` Właściwości:  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - oraz  
  
2. Wstaw ciąg lub obiekt w żądanym punkcie listy za pomocą `Insert` metody:  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - oraz  
  
3. Przypisz całą tablicę do `Items` kolekcji:  
  
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
  
1. Wywołaj `Remove` metodę lub, `RemoveAt` Aby usunąć elementy.  
  
     `Remove`ma jeden argument, który określa element do usunięcia.`RemoveAt` Usuwa element o określonym numerze indeksu.  
  
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
  
1. Wywołaj `Clear` metodę, aby usunąć wszystkie elementy z kolekcji:  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Porady: sortowanie zawartości formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [Kiedy należy używać kontrolki ComboBox formularzy Windows Forms zamiast ListBox](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [Formanty formularzy systemu Windows używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)

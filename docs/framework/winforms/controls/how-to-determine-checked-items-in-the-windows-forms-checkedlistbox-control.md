---
title: 'Instrukcje: określanie elementów jako zaznaczone w kontrolce CheckedListBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 0cfb34d058486c44ffb01e6c105134e3ca4c2175
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184681"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Instrukcje: określanie elementów jako zaznaczone w kontrolce CheckedListBox formularzy systemu Windows
Podczas wyświetlania danych w formularzach Windows <xref:System.Windows.Forms.CheckedListBox> kontrolki, można albo wykonać iterację kolekcji, przechowywane w <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> właściwości lub krok po kroku używając listy <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodę pozwala ustalić, które elementy są zaznaczone. <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> Metoda pobiera element o indeksie jako argument i zwraca `true` lub `false`. Sprzecznie może oczekiwań <xref:System.Windows.Forms.ListBox.SelectedItems%2A> i <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> właściwości nie może określić elementy, które są sprawdzane; ustalają one, elementy, które są wyróżnione.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Aby określić elementów jako zaznaczone w formancie CheckedListBox  
  
1.  Iteracyjne przeglądanie <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekcji, począwszy od 0, ponieważ kolekcja jest liczony od zera. Należy pamiętać, że ta metoda zapewni numer na liście elementów jako zaznaczone, listy ogólnej. Więc jeśli pierwszy element na liście nie jest zaznaczone, a drugi element jest wyewidencjonowany, poniższy kod będzie wyświetlany tekst, takich jak "zaznaczony element 1 = MyListItem2".  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x < checkedListBox1.CheckedItems.Count ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
       MessageBox.Show(s);  
    }  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x < checkedListBox1->CheckedItems->Count; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     - lub —  
  
2.  Krok po kroku <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekcji, począwszy od 0, ponieważ kolekcja jest liczony od zera, a wywołanie <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metody dla każdego elementu. Należy pamiętać, że ta metoda zapewni numer na liście ogólne, jeśli pierwszy element w liście nie jest zaznaczone i drugi element jest wyewidencjonowany wyświetli podobny do "element 2 = MyListItem2".  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Formanty formularzy systemu Windows używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)

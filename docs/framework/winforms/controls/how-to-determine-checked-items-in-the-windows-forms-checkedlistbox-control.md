---
title: Określanie zaznaczonych elementów w formancie CheckedListBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 5d93a63e9c1c6aae91ecfe83590c59450a565afe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182188"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Porady: określanie elementów jako zaznaczone w formancie CheckedListBox formularzy systemu Windows
Podczas prezentacji danych w <xref:System.Windows.Forms.CheckedListBox> formancie Windows Forms można iterować za <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> pośrednictwem kolekcji przechowywanej <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> we właściwości lub krok po kroku przy użyciu metody, aby określić, które elementy są sprawdzane. Metoda <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> przyjmuje numer indeksu towaru `true` jako `false`argument i zwraca lub . W przeciwieństwie do tego, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> czego <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> można się spodziewać, właściwości i nie określają, które elementy są sprawdzane; określają one, które elementy są wyróżnione.  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>Aby określić zaznaczone elementy w formancie CheckedListBox  
  
1. Iteracja za <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> pośrednictwem kolekcji, począwszy od 0, ponieważ kolekcja jest oparta na wartości zero. Należy zauważyć, że ta metoda daje numer towaru na liście zaznaczonych elementów, a nie na ogólnej liście. Jeśli więc pierwszy element na liście nie jest zaznaczony, a drugi element jest zaznaczony, poniższy kod wyświetli tekst w stylu "Zaznaczony element 1 = MyListItem2".  
  
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
  
     - lub -  
  
2. Krok po <xref:System.Windows.Forms.CheckedListBox.Items%2A> kroku kolekcji, począwszy od 0, ponieważ <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> kolekcja jest od zera i wywołać metodę dla każdego elementu. Należy zauważyć, że ta metoda daje numer elementu na ogólnej liście, więc jeśli pierwszy element na liście nie jest zaznaczone, a drugi element jest zaznaczony, wyświetli się coś w stylu "Element 2 = MyListItem2".  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Formanty formularzy systemu Windows używane do obsługi opcji list](windows-forms-controls-used-to-list-options.md)

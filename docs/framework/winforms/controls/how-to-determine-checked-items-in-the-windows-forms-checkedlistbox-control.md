---
title: 'Porady: określanie elementów jako zaznaczone w formancie CheckedListBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 70884051ba440c5d0f9d282b7edf189c8f52807e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505442"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>Porady: określanie elementów jako zaznaczone w formancie CheckedListBox formularzy systemu Windows
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
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)

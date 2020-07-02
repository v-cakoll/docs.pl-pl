---
title: Określanie elementów zaewidencjonowanych w kontrolce CheckedListBox
description: Dowiedz się, jak określić zaznaczone elementy w kontrolce Windows Forms CheckedListBox przez iterację kolekcji przechowywanej we właściwości CheckedItems.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: fd8845ef83da7406ff4f1468506a23e3f4d386a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618353"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="1e5fb-103">Porady: określanie elementów jako zaznaczone w formancie CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1e5fb-103">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="1e5fb-104">Podczas prezentowania danych w <xref:System.Windows.Forms.CheckedListBox> kontrolce Windows Forms można wykonać iterację kolekcji przechowywanej we <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> właściwości lub przejść przez listę przy użyciu <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metody, aby określić, które elementy są sprawdzane.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-104">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="1e5fb-105"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>Metoda przyjmuje jako argument numer indeksu elementu i zwraca `true` lub `false` .</span><span class="sxs-lookup"><span data-stu-id="1e5fb-105">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="1e5fb-106">W przeciwieństwie do tego, czego można oczekiwać, <xref:System.Windows.Forms.ListBox.SelectedItems%2A> <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> właściwości i nie określają, które elementy są sprawdzane. określają elementy, które są wyróżnione.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-106">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="1e5fb-107">Aby określić elementy zaznaczone w kontrolce CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="1e5fb-107">To determine checked items in a CheckedListBox control</span></span>  
  
1. <span data-ttu-id="1e5fb-108">Wykonaj iterację <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> kolekcji, rozpoczynając od 0, ponieważ kolekcja nie jest zależna od zera.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-108">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="1e5fb-109">Należy zauważyć, że ta metoda spowoduje udostępnienie numeru elementu na liście zaznaczonych elementów, a nie listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-109">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="1e5fb-110">Jeśli więc pierwszy element na liście nie jest zaznaczony, a drugi element jest zaznaczone, poniższy kod wyświetli tekst, taki jak "Checked Item 1 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="1e5fb-110">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="1e5fb-111">oraz</span><span class="sxs-lookup"><span data-stu-id="1e5fb-111">or -</span></span>  
  
2. <span data-ttu-id="1e5fb-112">Przejdź do <xref:System.Windows.Forms.CheckedListBox.Items%2A> kolekcji, rozpoczynając od 0, ponieważ kolekcja jest oparta na zero, i Wywołaj <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> metodę dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-112">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="1e5fb-113">Należy zauważyć, że ta metoda spowoduje udostępnienie numeru elementu na liście ogólnej, więc jeśli pierwszy element na liście nie zostanie zaznaczony i zostanie sprawdzony drugi element, będzie on wyświetlany podobnie jak "Item 2 = MyListItem2".</span><span class="sxs-lookup"><span data-stu-id="1e5fb-113">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e5fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e5fb-114">See also</span></span>

- [<span data-ttu-id="1e5fb-115">Formanty formularzy systemu Windows używane do obsługi opcji list</span><span class="sxs-lookup"><span data-stu-id="1e5fb-115">Windows Forms Controls Used to List Options</span></span>](windows-forms-controls-used-to-list-options.md)

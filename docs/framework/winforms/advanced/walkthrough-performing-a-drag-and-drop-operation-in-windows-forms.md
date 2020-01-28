---
title: 'Przewodnik: wykonywanie operacji przeciągania i upuszczania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 265e6d4f9e3370d28a18b86dea983bb0b556be41
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746793"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows
Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych na systemie Windows, musisz obsługiwać szereg zdarzeń, w szczególności zdarzenia <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>i <xref:System.Windows.Forms.Control.DragDrop>. Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić wykonywanie operacji przeciągania i upuszczania.  
  
## <a name="dragging-data"></a>Przeciąganie danych  
 Wszystkie operacje przeciągania i upuszczania zaczynają się od przeciągania. Funkcja umożliwiająca zbieranie danych po rozpoczęciu przeciągania jest zaimplementowana w metodzie <xref:System.Windows.Forms.Control.DoDragDrop%2A>.  
  
 W poniższym przykładzie zdarzenie <xref:System.Windows.Forms.Control.MouseDown> służy do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania zaczyna się od naciśnięcia przycisku myszy. Należy jednak pamiętać, że dowolnego zdarzenia można użyć do zainicjowania procedury przeciągania i upuszczania.  
  
> [!NOTE]
> Niektóre kontrolki mają niestandardowe zdarzenia dotyczące przeciągania. Kontrolki <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView>, na przykład, mają zdarzenie <xref:System.Windows.Forms.TreeView.ItemDrag>.  
  
#### <a name="to-start-a-drag-operation"></a>Aby rozpocząć operację przeciągania  
  
1. W zdarzeniu <xref:System.Windows.Forms.Control.MouseDown> dla kontrolki, w której rozpocznie się przeciąganie, użyj metody `DoDragDrop`, aby ustawić przeciąganie i dozwolony efekt przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Poniższy przykład pokazuje, jak zainicjować operację przeciągania. Kontrolka, w której rozpoczyna się przeciąganie, jest kontrolką <xref:System.Windows.Forms.Button>, przeciągane dane są ciągiem reprezentującym Właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> i dozwolone efekty są kopiowane lub przenoszone.  
  
    ```vb  
    Private Sub Button1_MouseDown(ByVal sender As Object, ByVal e As System.Windows.Forms.MouseEventArgs) Handles Button1.MouseDown  
       Button1.DoDragDrop(Button1.Text, DragDropEffects.Copy Or DragDropEffects.Move)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_MouseDown(object sender,   
    System.Windows.Forms.MouseEventArgs e)  
    {  
       button1.DoDragDrop(button1.Text, DragDropEffects.Copy |   
          DragDropEffects.Move);  
    }  
    ```  
  
    > [!NOTE]
    > Wszystkie dane mogą być używane jako parametr w metodzie `DoDragDrop`; w powyższym przykładzie użyto właściwości <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.Button> (zamiast kodowania wartości lub pobierania danych z zestawu danych), ponieważ właściwość została powiązana z lokalizacją, z której jest przeciągany (kontrolka <xref:System.Windows.Forms.Button>). Należy pamiętać o uwzględnieniu operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.  
  
 Podczas operacji przeciągania można obsłużyć zdarzenie <xref:System.Windows.Forms.Control.QueryContinueDrag>, które "prosi o uprawnienia" systemu do kontynuowania operacji przeciągania. Podczas obsługi tej metody jest również odpowiednim punktem, aby wywołać metody, które będą miały wpływ na operację przeciągania, na przykład rozszerzając <xref:System.Windows.Forms.TreeNode> w kontrolce <xref:System.Windows.Forms.TreeView>, gdy kursor znajduje się nad nim.  
  
## <a name="dropping-data"></a>Usuwanie danych  
 Po rozpoczęciu przeciągania danych z lokalizacji w formularzu lub kontrolce systemu Windows można w naturalny sposób upuścić je w dowolnym miejscu. Kursor zmieni się po przekroczeniu obszaru formularza lub kontrolki, która jest prawidłowo skonfigurowana do upuszczania danych. Każdy obszar w formularzu lub kontrolce systemu Windows można wprowadzić w celu zaakceptowania porzuconych danych przez ustawienie właściwości <xref:System.Windows.Forms.Control.AllowDrop%2A> i obsługę zdarzeń <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop>.  
  
#### <a name="to-perform-a-drop"></a>Aby wykonać upuszczanie  
  
1. Ustaw właściwość <xref:System.Windows.Forms.Control.AllowDrop%2A> na wartość true.  
  
2. W zdarzeniu `DragEnter` dla kontrolki, w której nastąpi upuszczenie, upewnij się, że przeciągane dane mają akceptowalny typ (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>). Następnie kod ustawia efekt, który zostanie wykonany, gdy porzucanie zostanie wykonane do wartości w wyliczeniu <xref:System.Windows.Forms.DragDropEffects>. Aby uzyskać więcej informacji, zobacz temat <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
    ```vb  
    Private Sub TextBox1_DragEnter(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
         e.Effect = DragDropEffects.Copy  
       Else  
         e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    > [!NOTE]
    > Możesz zdefiniować własne <xref:System.Windows.Forms.DataFormats>, określając własny obiekt jako parametr <xref:System.Object> metody <xref:System.Windows.Forms.DataObject.SetData%2A>. Upewnij się, że w tym przypadku obiekt jest możliwy do serializacji. Aby uzyskać więcej informacji, zobacz temat <xref:System.Runtime.Serialization.ISerializable>.  
  
3. W zdarzeniu <xref:System.Windows.Forms.Control.DragDrop> dla kontrolki, w której nastąpi upuszczenie, użyj metody <xref:System.Windows.Forms.DataObject.GetData%2A>, aby pobrać przeciągane dane. Aby uzyskać więcej informacji, zobacz temat <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     W poniższym przykładzie formant <xref:System.Windows.Forms.TextBox> jest przeciągany do (w którym wystąpił spadek). Kod ustawia właściwość <xref:System.Windows.Forms.Control.Text%2A> kontrolki <xref:System.Windows.Forms.TextBox> równej przeciąganym danym.  
  
    ```vb  
    Private Sub TextBox1_DragDrop(ByVal sender As Object, ByVal e As System.Windows.Forms.DragEventArgs) Handles TextBox1.DragDrop  
       TextBox1.Text = e.Data.GetData(DataFormats.Text).ToString  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       textBox1.Text = e.Data.GetData(DataFormats.Text).ToString();  
    }  
    ```  
  
    > [!NOTE]
    > Ponadto można korzystać z właściwości <xref:System.Windows.Forms.DragEventArgs.KeyState%2A>, dzięki czemu w zależności od kluczy podczas operacji przeciągania i upuszczania pojawiają się pewne efekty (na przykład standardowe do kopiowania przeciąganych danych po naciśnięciu klawisza CTRL).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: dodawanie danych do schowka](how-to-add-data-to-the-clipboard.md)
- [Instrukcje: pobieranie danych ze schowka](how-to-retrieve-data-from-the-clipboard.md)
- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)

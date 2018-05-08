---
title: 'Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 6c78a06e37de491e95d56d29c9d2f3e60b88e8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows
Wykonywanie operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows musi obsługiwać szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia. Praca z informacji dostępnych w przypadku argumentów te zdarzenia, można łatwo ułatwienia operacji przeciągania i upuszczania.  
  
## <a name="dragging-data"></a>Przeciąganie danych  
 Wszystkie operacje przeciągania i upuszczania zaczynać przeciągania. Funkcje umożliwiające podczas przeciągania rozpoczyna zbieranie danych jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.  
  
 W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenia są używane do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjnego (Większość akcji przeciągania i upuszczania zaczynać się przycisk myszy jest wciśnięty). Należy jednak pamiętać, że wszystkie zdarzenia może posłużyć do zainicjowania procedury przeciągania i upuszczania.  
  
> [!NOTE]
>  Niektóre formanty ma niestandardowych zdarzeń specyficznych dla przeciągania. <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolki, na przykład mieć <xref:System.Windows.Forms.TreeView.ItemDrag> zdarzeń.  
  
#### <a name="to-start-a-drag-operation"></a>Aby uruchomić operację przeciągania  
  
1.  W <xref:System.Windows.Forms.Control.MouseDown> zdarzeń dla formantu, gdzie rozpocznie przeciąganie, użyj `DoDragDrop` ma metodę, aby ustawić dane do przeciąganych i dozwolonym efektem przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Poniższy przykład pokazuje, jak zainicjować operacji przeciągania. Formant, gdzie zaczyna się przeciągania jest <xref:System.Windows.Forms.Button> kontroli, dane przeciągane jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> kontroli i dozwolone efekty są kopiowania lub przenoszenia.  
  
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
    >  Wszystkie dane mogą być używane jako parametru w `DoDragDrop` — metoda; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formant został użyty (zamiast kodować wartość lub pobieranie danych z zestawu danych) ponieważ właściwość nie została powiązana z przeciąganie z lokalizacji ( <xref:System.Windows.Forms.Button> kontroli). Należy to pamiętać, jak zastosować operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.  
  
 Podczas operacji przeciągania jest włączone, można obsługiwać <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "prosi o uprawnienie" systemu, aby kontynuować operację przeciągania. Podczas przetwarzania tej metody, jest również odpowiedniego punktu można wywoływać metod, które będą miały wpływu na operację przeciągania, takich jak rozszerzanie <xref:System.Windows.Forms.TreeNode> w <xref:System.Windows.Forms.TreeView> kontroli, gdy kursor znajduje się nad nim.  
  
## <a name="dropping-data"></a>Usuwanie danych  
 Po rozpoczęciu przeciąganie danych z lokalizacji w formularzu systemu Windows lub kontrolki, należy naturalny Porzuć go innym. Kursor ulegnie zmianie po jego przecina obszaru formularz lub formant, który jest poprawnie skonfigurowany dla usunięcie danych. Każdy obszar w formularzu systemu Windows lub formant może również akceptować dane porzuconych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości i obsługa <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.  
  
#### <a name="to-perform-a-drop"></a>Aby wykonać spadek  
  
1.  Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości na wartość true.  
  
2.  W `DragEnter` zdarzeń dla formantu, gdy nastąpi spadek Sprawdź, czy dane przeciągane jest dopuszczalne typu (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>). Kod następnie ustawia efekt, który nastąpi po wartości w polu listy <xref:System.Windows.Forms.DragDropEffects> wyliczenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Można definiować własnych <xref:System.Windows.Forms.DataFormats> , określając obiektu jako <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Upewnij się, gdy spowoduje to, że określony obiekt jest możliwy do serializacji. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  W <xref:System.Windows.Forms.Control.DragDrop> zdarzeń dla formantu, gdzie nastąpi spadek użyj <xref:System.Windows.Forms.DataObject.GetData%2A> metody do pobierania danych przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.TextBox> formant jest formantem przeciąganego (listy będą mieć miejsce). Ustawia kod <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontrolować równa dane przeciągane.  
  
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
    >  Ponadto możesz pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwości, dzięki czemu w zależności od klucze wciśnięty podczas operacji przeciągania i upuszczania niektórych występują skutki (na przykład jest standard, aby skopiować dane przeciąganego, gdy zostanie naciśnięty klawisz CTRL).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dodawanie danych do schowka](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Instrukcje: pobieranie danych ze schowka](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operacje przeciągania i upuszczania oraz obsługa schowka](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)

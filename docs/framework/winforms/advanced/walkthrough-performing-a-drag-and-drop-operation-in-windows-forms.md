---
title: 'Instruktaż: Wykonywanie operacji przeciągania i upuszczania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: b5e4bf753733cb9bd010672f40e8fbeb0cf036bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182440"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows
Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych <xref:System.Windows.Forms.Control.DragEnter>na <xref:System.Windows.Forms.Control.DragLeave>systemie <xref:System.Windows.Forms.Control.DragDrop> Windows, należy obsługiwać serię zdarzeń, w szczególności , i zdarzenia. Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić operacje przeciągania i upuszczania.  
  
## <a name="dragging-data"></a>Przeciąganie danych  
 Wszystkie operacje przeciągania i upuszczania rozpoczynają się od przeciągania. Funkcja umożliwiająca zbieranie danych podczas przeciągania rozpoczyna się <xref:System.Windows.Forms.Control.DoDragDrop%2A> zaimplementowana w metodzie.  
  
 W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenie jest używane do rozpoczęcia operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania rozpoczyna się od wciśnięciu przycisku myszy). Należy jednak pamiętać, że każde zdarzenie może służyć do inicjowania procedury przeciągania i upuszczania.  
  
> [!NOTE]
> Niektóre formanty mają niestandardowe zdarzenia specyficzne dla przeciągania. I <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> formanty, na <xref:System.Windows.Forms.TreeView.ItemDrag> przykład, mają zdarzenie.  
  
#### <a name="to-start-a-drag-operation"></a>Aby rozpocząć operację przeciągania  
  
1. W <xref:System.Windows.Forms.Control.MouseDown> przypadku formantu, w którym rozpocznie `DoDragDrop` się przeciąganie, użyj metody, aby ustawić dane do przeciągania i będzie miało dozwolony efekt przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     W poniższym przykładzie pokazano, jak zainicjować operację przeciągania. Formant, w którym <xref:System.Windows.Forms.Button> rozpoczyna się przeciąganie jest formantem, dane przeciągane jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formantu, a dozwolone efekty są kopiowanie lub przenoszenie.  
  
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
    > Wszelkie dane mogą być używane `DoDragDrop` jako parametr w metodzie; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> użyto właściwości <xref:System.Windows.Forms.Button> formantu (zamiast twardego kodowania wartości lub pobierania danych z zestawu danych), ponieważ właściwość <xref:System.Windows.Forms.Button> była powiązana z lokalizacją przeciąganą z (formant). Należy o tym pamiętać, włączanie operacji przeciągania i upuszczania do aplikacji opartych na systemie Windows.  
  
 Podczas operacji przeciągania jest w <xref:System.Windows.Forms.Control.QueryContinueDrag> życie, można obsłużyć zdarzenie, które "prosi uprawnienia" systemu, aby kontynuować operację przeciągania. Podczas obsługi tej metody, jest również odpowiedni punkt do wywołania metod, które będą miały <xref:System.Windows.Forms.TreeNode> wpływ <xref:System.Windows.Forms.TreeView> na operację przeciągania, takich jak rozwijanie w formancie, gdy kursor najeżdża nad nim.  
  
## <a name="dropping-data"></a>Upuszczanie danych  
 Po rozpoczęciu przeciągania danych z lokalizacji w formularzu systemu Windows lub formancie, naturalnie chcesz go gdzieś upuścić. Kursor zmieni się po przekroczeniu obszaru formularza lub formantu, który jest poprawnie skonfigurowany do upuszczania danych. Każdy obszar w formularzu systemu Windows lub formantu <xref:System.Windows.Forms.Control.AllowDrop%2A> można dokonać, aby zaakceptować porzucone dane, ustawiając właściwość i obsługi <xref:System.Windows.Forms.Control.DragEnter> zdarzeń. <xref:System.Windows.Forms.Control.DragDrop>  
  
#### <a name="to-perform-a-drop"></a>Aby wykonać upuszczenie  
  
1. Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwość na true.  
  
2. W `DragEnter` przypadku formantu, w którym nastąpi upuszczenie, upewnij się, że przeciągane dane są akceptowalnym typem (w tym przypadku). <xref:System.Windows.Forms.Control.Text%2A> Kod następnie ustawia efekt, który nastąpi, gdy spadek <xref:System.Windows.Forms.DragDropEffects> wystąpi do wartości w wyliczeniu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Można zdefiniować <xref:System.Windows.Forms.DataFormats> własne, określając własny obiekt <xref:System.Object> jako <xref:System.Windows.Forms.DataObject.SetData%2A> parametr metody. Upewnij się, że podczas wykonywania tej pracy, że obiekt określony jest serializable. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.  
  
3. W <xref:System.Windows.Forms.Control.DragDrop> przypadku formantu, w którym nastąpi <xref:System.Windows.Forms.DataObject.GetData%2A> upuszczenie, użyj metody, aby pobrać przeciągane dane. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     W poniższym przykładzie formant <xref:System.Windows.Forms.TextBox> jest formant przeciągany do (gdzie nastąpi spadek). Kod ustawia <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> formantu równa przeciąganych danych.  
  
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
    > Ponadto można pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwością, dzięki czemu, w zależności od klawiszy wciśnięty podczas operacji przeciągania i upuszczania, pewne efekty występują (na przykład jest standardem kopiowania przeciągniętych danych po naciśnięciu klawisza CTRL).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: dodawanie danych do schowka](how-to-add-data-to-the-clipboard.md)
- [Instrukcje: pobieranie danych ze schowka](how-to-retrieve-data-from-the-clipboard.md)
- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)

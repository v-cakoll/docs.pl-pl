---
title: 'Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: e9b21d7bfa188ebb053f36e2637ffce5d6fa0dd7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189030"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows
Wykonywanie operacji przeciągania i upuszczania w aplikacji systemu Windows musi obsługiwać szereg zdarzeń, głównie <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia. Praca z dostępnych informacji w zdarzeniu argumenty te zdarzenia, można łatwo ułatwić operacji przeciągania i upuszczania.  
  
## <a name="dragging-data"></a>Przeciąganie danych  
 Wszystkie operacje przeciągania i upuszczania rozpoczynają się od przeciągania. Funkcje umożliwiające podczas przeciągania rozpoczyna się zbieranie danych jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metody.  
  
 W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenia są używane do uruchamiania operacji przeciągania, ponieważ jest on w najbardziej intuicyjnej (Większość akcji przeciągania i upuszczania zaczynają się od przycisk myszy jest wciśnięty). Należy jednak pamiętać, że dowolne zdarzenie, może służyć do zainicjowania procedury przeciągania i upuszczania.  
  
> [!NOTE]
>  Niektóre formanty mają niestandardowych zdarzeń specyficznych dla przeciągania. <xref:System.Windows.Forms.ListView> i <xref:System.Windows.Forms.TreeView> kontrolki, na przykład mieć <xref:System.Windows.Forms.TreeView.ItemDrag> zdarzeń.  
  
#### <a name="to-start-a-drag-operation"></a>Aby rozpocząć operację przeciągania  
  
1.  W <xref:System.Windows.Forms.Control.MouseDown> zdarzeń dla formantu, gdy rozpocznie się przeciąganie, użyj `DoDragDrop` metodę, aby ustawić dane, które mają być przeciągane i dozwolonym efektem przeciąganie będą mieć. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Poniższy przykład pokazuje, jak zainicjować operacji przeciągania. Kontrolka, gdzie rozpoczyna się przeciągania jest <xref:System.Windows.Forms.Button> kontroli danych przeciąganie jest ciąg reprezentujący <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> kontroli i dozwolone efekty są kopiowania lub przenoszenia.  
  
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
    >  Wszystkie dane mogą być używane jako parametr w `DoDragDrop` metoda; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.Button> formant został użyty (a nie zakodowane na stałe wartości lub pobieranie danych z zestawu danych), ponieważ właściwość był powiązany z przeciąganie z lokalizacji ( <xref:System.Windows.Forms.Button> kontroli). Miej to na uwadze, jak włączenie operacji przeciągania i upuszczania do aplikacji z systemem Windows.  
  
 Operacja przeciągania w czasie działania, które ułatwią Ci obsługę <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "żąda uprawnienia" systemu, aby kontynuować operację przeciągania. Podczas obsługi tej metody, jest również odpowiedni punkt wywoływać metody mające wpływ na operacji przeciągania, takich jak rozwijanie <xref:System.Windows.Forms.TreeNode> w <xref:System.Windows.Forms.TreeView> kontroli, gdy kursor znajduje się nad nią.  
  
## <a name="dropping-data"></a>Usuwanie danych  
 Po rozpoczęciu przeciągając danych z lokalizacji Windows formularza lub formantu, naturalnie można je gdzieś umieścić. Kursor zmieni się na jej przecina obszaru formularza lub formantu, który jest poprawnie skonfigurowany dla porzucenie danych. Każdy obszar w Windows formularza lub formantu można wprowadzić na akceptowanie danych porzuconych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości i obsługa <xref:System.Windows.Forms.Control.DragEnter> i <xref:System.Windows.Forms.Control.DragDrop> zdarzenia.  
  
#### <a name="to-perform-a-drop"></a>Aby wykonać zrzutu  
  
1.  Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości na wartość true.  
  
2.  W `DragEnter` zdarzeń dla formantu, gdy nastąpi spadek, upewnij się, że dane przeciąganie typu dopuszczalnych (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A>). Kod następnie ustawia wpływ, jaki nastąpi wartości w przypadku listy <xref:System.Windows.Forms.DragDropEffects> wyliczenia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    >  Definiowanie swoich własnych <xref:System.Windows.Forms.DataFormats> , określając obiektu jako <xref:System.Object> parametru <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Upewnij się, w trakcie tego, czy określony obiekt jest możliwy do serializacji. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.  
  
3.  W <xref:System.Windows.Forms.Control.DragDrop> zdarzeń dla formantu, gdzie nastąpi spadek, użyj <xref:System.Windows.Forms.DataObject.GetData%2A> metody do pobierania danych przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.TextBox> jest kontrolka przeciąganego (gdzie listy nastąpi). Zestawy kodów <xref:System.Windows.Forms.Control.Text%2A> właściwość <xref:System.Windows.Forms.TextBox> kontrolować równa danych przeciągania.  
  
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
    >  Ponadto można pracować z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwość tak, aby w zależności od klucze obniżone podczas operacji przeciągania i upuszczania pewne efekty wystąpić (na przykład jest standard, aby skopiować dane przeciąganego, po naciśnięciu klawisza CTRL).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dodawanie danych do schowka](how-to-add-data-to-the-clipboard.md)
- [Instrukcje: Pobieranie danych ze schowka](how-to-retrieve-data-from-the-clipboard.md)
- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)

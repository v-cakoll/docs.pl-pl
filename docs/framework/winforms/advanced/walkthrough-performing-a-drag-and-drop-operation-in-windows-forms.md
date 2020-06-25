---
title: 'Przewodnik: wykonywanie operacji przeciągania i upuszczania'
description: Informacje na temat wykonywania operacji przeciągania i upuszczania w Windows Forms przez obsługę serii zdarzeń, w szczególności zdarzeń DragEnter, zdarzenie DragLeave i DragDrop.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drag and drop operations
- drag and drop [Windows Forms], Windows Forms
ms.assetid: eb66f6bf-4a7d-4c2d-b276-40fefb2d3b6c
ms.openlocfilehash: 83bfda875e2fdec3981bbcb8f8f7be00db342440
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325819"
---
# <a name="walkthrough-performing-a-drag-and-drop-operation-in-windows-forms"></a>Wskazówki: wykonywanie operacji przeciągania i upuszczania w formularzach systemu Windows
Aby wykonać operacje przeciągania i upuszczania w aplikacjach opartych na systemie Windows, musisz obsługiwać serie zdarzeń, w szczególności <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragLeave> <xref:System.Windows.Forms.Control.DragDrop> zdarzenia. Pracując z informacjami dostępnymi w argumentach zdarzeń tych zdarzeń, można łatwo ułatwić wykonywanie operacji przeciągania i upuszczania.  
  
## <a name="dragging-data"></a>Przeciąganie danych  
 Wszystkie operacje przeciągania i upuszczania zaczynają się od przeciągania. Funkcja umożliwiająca zbieranie danych po rozpoczęciu przeciągania jest zaimplementowana w <xref:System.Windows.Forms.Control.DoDragDrop%2A> metodzie.  
  
 W poniższym przykładzie <xref:System.Windows.Forms.Control.MouseDown> zdarzenie jest używane do uruchamiania operacji przeciągania, ponieważ jest najbardziej intuicyjne (większość akcji przeciągania i upuszczania zaczyna się od naciśnięcia przycisku myszy). Należy jednak pamiętać, że dowolnego zdarzenia można użyć do zainicjowania procedury przeciągania i upuszczania.  
  
> [!NOTE]
> Niektóre kontrolki mają niestandardowe zdarzenia dotyczące przeciągania. <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.TreeView> Na przykład kontrolki i mają <xref:System.Windows.Forms.TreeView.ItemDrag> zdarzenie.  
  
#### <a name="to-start-a-drag-operation"></a>Aby rozpocząć operację przeciągania  
  
1. W <xref:System.Windows.Forms.Control.MouseDown> przypadku kontrolki, w której rozpocznie się przeciąganie, użyj metody, aby ustawić przeciąganie `DoDragDrop` i dozwolony efekt przeciągania. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Data%2A> i <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A>.  
  
     Poniższy przykład pokazuje, jak zainicjować operację przeciągania. Formant, w którym rozpoczyna się przeciąganie <xref:System.Windows.Forms.Button> , jest formantem, przeciągane dane są ciągiem reprezentującym <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.Button> kontrolki, a dozwolone efekty są kopiowane lub przenoszone.  
  
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
    > Wszystkie dane mogą być używane jako parametr w `DoDragDrop` metodzie; w powyższym przykładzie <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.Button> kontrolki została użyta (zamiast kodowania wartości lub pobierania danych z zestawu danych), ponieważ właściwość została powiązana z lokalizacją przeciągniętej z ( <xref:System.Windows.Forms.Button> kontrolka). Należy pamiętać o uwzględnieniu operacji przeciągania i upuszczania w aplikacjach opartych na systemie Windows.  
  
 Podczas operacji przeciągania można obsłużyć <xref:System.Windows.Forms.Control.QueryContinueDrag> zdarzenie, które "Zażądaj uprawnienia" systemu do kontynuowania operacji przeciągania. W przypadku obsługi tej metody jest również odpowiednim punktem, aby wywołać metody, które będą miały wpływ na operację przeciągania, na przykład rozszerzając element <xref:System.Windows.Forms.TreeNode> w <xref:System.Windows.Forms.TreeView> kontrolce, gdy kursor znajduje się nad nim.  
  
## <a name="dropping-data"></a>Usuwanie danych  
 Po rozpoczęciu przeciągania danych z lokalizacji w formularzu lub kontrolce systemu Windows można w naturalny sposób upuścić je w dowolnym miejscu. Kursor zmieni się po przekroczeniu obszaru formularza lub kontrolki, która jest prawidłowo skonfigurowana do upuszczania danych. Każdy obszar w formularzu lub kontrolce systemu Windows można wprowadzić w celu zaakceptowania porzuconych danych przez ustawienie <xref:System.Windows.Forms.Control.AllowDrop%2A> właściwości i obsługę <xref:System.Windows.Forms.Control.DragEnter> <xref:System.Windows.Forms.Control.DragDrop> zdarzeń i.  
  
#### <a name="to-perform-a-drop"></a>Aby wykonać upuszczanie  
  
1. Ustaw <xref:System.Windows.Forms.Control.AllowDrop%2A> Właściwość na wartość true.  
  
2. W `DragEnter` przypadku kontrolki, w której nastąpi upuszczenie, upewnij się, że przeciągane dane mają akceptowalny typ (w tym przypadku <xref:System.Windows.Forms.Control.Text%2A> ). Następnie kod ustawia efekt, który zostanie wykonany, gdy porzucanie będzie miało wartość w <xref:System.Windows.Forms.DragDropEffects> wyliczeniu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DragEventArgs.Effect%2A>.  
  
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
    > Można zdefiniować własne <xref:System.Windows.Forms.DataFormats> , określając własny obiekt jako <xref:System.Object> parametr <xref:System.Windows.Forms.DataObject.SetData%2A> metody. Upewnij się, że w tym przypadku obiekt jest możliwy do serializacji. Aby uzyskać więcej informacji, zobacz <xref:System.Runtime.Serialization.ISerializable>.  
  
3. W <xref:System.Windows.Forms.Control.DragDrop> przypadku kontrolki, w której nastąpi upuszczenie, użyj <xref:System.Windows.Forms.DataObject.GetData%2A> metody, aby pobrać przeciągane dane. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Cryptography.Xml.DataObject.Data%2A>.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.TextBox> formant jest przeciągany do (w którym wystąpił spadek). Kod ustawia <xref:System.Windows.Forms.Control.Text%2A> Właściwość <xref:System.Windows.Forms.TextBox> kontrolki równej przeciąganym danym.  
  
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
    > Ponadto można korzystać z <xref:System.Windows.Forms.DragEventArgs.KeyState%2A> właściwości, tak aby w zależności od kluczy podczas operacji przeciągania i upuszczania wystąpił pewne efekty (na przykład standardowe do kopiowania przeciąganych danych po naciśnięciu klawisza Ctrl).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: dodawanie danych do schowka](how-to-add-data-to-the-clipboard.md)
- [Instrukcje: pobieranie danych ze schowka](how-to-retrieve-data-from-the-clipboard.md)
- [Operacje przeciągania i upuszczania oraz obsługa schowka](drag-and-drop-operations-and-clipboard-support.md)

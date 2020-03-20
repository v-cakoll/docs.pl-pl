---
title: 'Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182290"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania
Typowe zadania w tworzeniu aplikacji są dodawanie formantów i usuwanie formantów z dowolnego formantu kontenera w formularzach (takich jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> formantu, a nawet sam formularz). W czasie projektowania formanty mogą być przeciągane bezpośrednio na pole panelu lub grupy. W czasie wykonywania te `Controls` formanty obsługi kolekcji, która śledzi, jakie formanty są umieszczane na nich.  
  
> [!NOTE]
> Poniższy przykład kodu ma zastosowanie do dowolnego formantu, który utrzymuje kolekcję formantów w nim.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Aby programowo dodać formant do kolekcji  
  
1. Utwórz wystąpienie formantu, które ma zostać dodane.  
  
2. Ustaw właściwości nowego formantu.  
  
3. Dodaj formant `Controls` do kolekcji formantu nadrzędnego.  
  
     Poniższy przykład kodu pokazuje, jak <xref:System.Windows.Forms.Button> utworzyć wystąpienie formantu. Wymaga formularza z <xref:System.Windows.Forms.Panel> formantem i że metoda obsługi zdarzeń `NewPanelButton_Click`dla tworzonego przycisku , już istnieje.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Aby programowo usunąć formanty z kolekcji  
  
1. Usuń program obsługi zdarzeń ze zdarzenia. W języku Visual Basic użyj słowa kluczowego [RemoveHandler Statement;](../../../visual-basic/language-reference/statements/removehandler-statement.md) w języku C#, użyj [operatora -=](../../../csharp/language-reference/operators/subtraction-operator.md).  
  
2. Użyj `Remove` metody, aby usunąć żądany formant z kolekcji `Controls` panelu.  
  
3. Wywołanie <xref:System.Windows.Forms.Control.Dispose%2A> metody, aby zwolnić wszystkie zasoby używane przez formant.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.Panel>
- [Panel — Formant](panel-control-windows-forms.md)

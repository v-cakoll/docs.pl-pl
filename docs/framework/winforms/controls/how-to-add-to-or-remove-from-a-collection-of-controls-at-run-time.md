---
title: 'Instrukcje: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
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
ms.openlocfilehash: 5c963976dd787b40c3e5c6180538051cfe419540
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143146"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Instrukcje: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania
Typowe zadania podczas tworzenia aplikacji są dodawanie formantów do i usuwanie kontrolek z dowolną kontrolkę kontenera na formularzach (takie jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> formantu lub nawet formularza). W czasie projektowania formanty można przeciągać bezpośrednio okno panel lub grupę. W czasie wykonywania, obsługa tych formantów `Controls` kolekcji, która przechowuje informacje o kontrolki są umieszczane na nich.  
  
> [!NOTE]
>  Poniższy przykładowy kod stosuje się do żadnego formantu, który przechowuje kolekcję zawarte w niej kontrolki.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Aby programowo dodać formant do kolekcji  
  
1.  Utwórz wystąpienie kontrolki, które mają zostać dodane.  
  
2.  Ustaw właściwości nowego formantu.  
  
3.  Dodać formant do `Controls` kolekcji do kontrolki nadrzędnej.  
  
     Poniższy przykład kodu pokazuje, jak utworzyć wystąpienie <xref:System.Windows.Forms.Button> kontroli. Wymaga formularza z <xref:System.Windows.Forms.Panel> kontroli i że trwa tworzenie metody obsługi zdarzeń dla przycisku, `NewPanelButton_Click`, już istnieje.  
  
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
  
1.  Usuń obsługi zdarzenia ze zdarzenia. W języku Visual Basic należy używać [RemoveHandler — instrukcja](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) — słowo kluczowe; w elemencie wizualnym C#, użyj [-= — Operator (C# odwołania)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Użyj `Remove` metodę, aby usunąć żądanego formant na panelu `Controls` kolekcji.  
  
3.  Wywołaj <xref:System.Windows.Forms.Control.Dispose%2A> metodę, aby zwolnić wszystkie zasoby, które są używane przez kontrolkę.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Panel>
- [Panel, kontrolka](panel-control-windows-forms.md)

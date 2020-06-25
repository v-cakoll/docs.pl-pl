---
title: 'Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
description: Dowiedz się, jak dodać kontrolki do i usunąć kontrolki z dowolnego formantu kontenera w formularzach, takie jak panel lub kontrolka grupy, a nawet sam formularz.
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
ms.openlocfilehash: 6c3f2d1f42b130de4d808871265b50510cfb8f47
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325875"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania
Typowe zadania związane z tworzeniem aplikacji to dodawanie kontrolek do i usuwanie kontrolek z dowolnych kontrolek kontenera w formularzach (takich jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> kontrolka, a nawet do samego formularza). W czasie projektowania formanty mogą być przeciągane bezpośrednio do panelu lub pola grupy. W czasie wykonywania te kontrolki utrzymują `Controls` kolekcję, która śledzi umieszczanie na nich formantów.  
  
> [!NOTE]
> Poniższy przykład kodu ma zastosowanie do każdej kontrolki, która zachowuje kolekcję kontrolek.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Aby programowo dodać kontrolkę do kolekcji  
  
1. Utwórz wystąpienie kontrolki, która ma zostać dodana.  
  
2. Ustaw właściwości nowej kontrolki.  
  
3. Dodaj kontrolkę do `Controls` kolekcji kontrolki nadrzędnej.  
  
     Poniższy przykład kodu pokazuje, jak utworzyć wystąpienie <xref:System.Windows.Forms.Button> kontrolki. Wymaga formularza z <xref:System.Windows.Forms.Panel> kontrolką i że metoda obsługi zdarzeń dla tworzonego przycisku `NewPanelButton_Click` już istnieje.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Aby programowo usunąć kontrolki z kolekcji  
  
1. Usuń procedurę obsługi zdarzeń ze zdarzenia. W Visual Basic, użyj słowa kluczowego [RemoveHandler instrukcji](../../../visual-basic/language-reference/statements/removehandler-statement.md) ; w języku C# Użyj [operatora-=](../../../csharp/language-reference/operators/subtraction-operator.md).  
  
2. Użyj `Remove` metody, aby usunąć żądany formant z `Controls` kolekcji panelu.  
  
3. Wywołaj <xref:System.Windows.Forms.Control.Dispose%2A> metodę, aby zwolnić wszystkie zasoby używane przez formant.  
  
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

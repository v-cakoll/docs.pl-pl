---
title: 'Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b34863e7846f75c5dc9a8af24591522e37252f4c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Porady: dodawanie do lub usuwanie z kolekcji kontrolek w czasie wykonywania
Typowe zadania w projektowanie aplikacji są dodawanie formantów do oraz usuwanie kontrolek z dowolnego formantu kontenera na formularzach (takich jak <xref:System.Windows.Forms.Panel> lub <xref:System.Windows.Forms.GroupBox> formant lub nawet formularza). W czasie projektowania formantów może być przeciągnięte bezpośrednio na panelu lub grupy. W czasie wykonywania, obsługa tych kontrolek `Controls` kolekcji, która przechowuje informacje o kontrolki są umieszczane na nich.  
  
> [!NOTE]
>  Poniższy przykład kodu dotyczy żadnego formantu, który obsługuje kolekcji formantów w niej.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Aby dodać kontrolkę programistycznie do kolekcji  
  
1.  Utwórz wystąpienie formantu ma zostać dodana.  
  
2.  Ustaw właściwości nowej kontrolki.  
  
3.  Dodawanie formantu do `Controls` kolekcji kontrolki nadrzędnej.  
  
     W poniższym przykładzie przedstawiono sposób tworzenia wystąpienia <xref:System.Windows.Forms.Button> formantu. Wymaga to formularza z <xref:System.Windows.Forms.Panel> kontroli, a metoda obsługi zdarzeń dla przycisku tworzone `NewPanelButton_Click`, już istnieje.  
  
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
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Aby usunąć formanty programowo z kolekcji  
  
1.  Usuń program obsługi zdarzeń z zdarzenia. W języku Visual Basic, użyj [RemoveHandler — instrukcja](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) słowo kluczowe języka Visual C#, użyj [-= — Operator (odwołanie w C#)](~/docs/csharp/language-reference/operators/subtraction-assignment-operator.md).  
  
2.  Użyj `Remove` do usunięcia z poziomu Panelu sterowania żądaną `Controls` kolekcji.  
  
3.  Wywołanie <xref:System.Windows.Forms.Control.Dispose%2A> metodę, aby zwolnić wszystkie zasoby używane przez formant.  
  
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
 <xref:System.Windows.Forms.Panel>  
 [Panel, kontrolka](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)

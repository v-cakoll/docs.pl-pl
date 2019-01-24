---
title: 'Instrukcje: Dodawanie formantów do formularzy Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 6290fdac63bb22b878035c0cc27bba97300899de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611361"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Instrukcje: Dodawanie formantów do formularzy Windows Forms
Większość formularzy poprzez dodawanie formantów do powierzchni formularza do definiowania interfejsu użytkownika (UI). A *kontroli* jest składnikiem w formularzu, używane do wyświetlania informacji i akceptuje dane wejściowe użytkownika. Aby uzyskać więcej informacji na temat formantów, zobacz [kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-control-on-a-form"></a>Narysuj kontrolkę w formularzu  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, kliknij kontrolkę, którą chcesz dodać do formularza.  
  
3.  W formularzu kliknij w miejscu lewego górnego rogu kontrolki można znaleźć i przeciągnij w odpowiednie miejsce prawym dolnym rogu formantu w zlokalizowanym.  
  
     Formant jest dodawany do formularza z określonej lokalizacji i rozmiaru.  
  
    > [!NOTE]
    >  Każda kontrolka ma domyślny rozmiar zdefiniowany. Można dodać formant do formularza w formantu domyślny rozmiar, przeciągając go z **przybornika** do formularza.  
  
### <a name="to-drag-a-control-to-a-form"></a>Przeciągnij formant do formularza  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formularzy Windows w Projektancie](https://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, ma miejsce kliknięcie kontrolki i przeciągnij je do formularza.  
  
     Formant jest dodawany do formularza w określonej lokalizacji w jej domyślny rozmiar.  
  
    > [!NOTE]
    >  Możesz kliknąć dwukrotnie formant w **przybornika** Aby dodać go do lewego górnego rogu formularza w jej domyślny rozmiar.  
  
     Możesz również dodać formanty dynamicznie do formularza w czasie wykonywania. W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formant zostanie dodany do formularza, gdy <xref:System.Windows.Forms.Button> kliknięciu formantu.  
  
    > [!NOTE]
    >  Poniższa procedura wymaga istnienia formularza z **przycisk** kontroli `Button1`, już umieszczony na nim.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Aby programowo dodać formant do formularza  
  
1.  W metodzie, która obsługuje przycisku `Click` zdarzenia w obrębie klasy formularza, Wstaw kod podobne do następujących czynności, aby dodać odwołanie do zmiennej kontrolki, ustaw dla formantu `Location`i Dodaj formant.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  Można również dodać kod do zainicjowania inne właściwości formantu.  
  
    > [!IMPORTANT]
    >  Na komputerze lokalnym to zagrożenie bezpieczeństwa, za pośrednictwem sieci można uwidocznić, odwołując się do złośliwych `UserControl`. Powinien to być jedynie kwestią w przypadku złośliwe osoby tworzącej szkodliwe kontrolka niestandardowa, a następnie przez Ciebie przez pomyłkę dodawania do projektu.  
  
## <a name="see-also"></a>Zobacz także
- [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
- [Instrukcje: Zmiana rozmiaru formantów na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)
- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)

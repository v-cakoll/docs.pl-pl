---
title: 'Porady: dodawanie formantów do formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 2dd048fb074d1ec5bb7bc0a67f196d5d51281545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528480"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Porady: dodawanie formantów do formularzy systemu Windows
Większość formularzy przez dodawanie formantów do powierzchni formularza do definiowania interfejsu użytkownika (UI). A *kontroli* jest składnikiem w formularzu używane do wyświetlania informacji i akceptowanie danych wejściowych użytkownika. Aby uzyskać więcej informacji na temat formantów, zobacz [formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-draw-a-control-on-a-form"></a>Aby narysować kontrolkę w formularzu  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, kliknij przycisk formantu ma zostać dodany do formularza.  
  
3.  Na formularzu kliknij w miejscu górnego lewego rogu formantu znajdował się i przeciągnij, aby miejsce prawym dolnym rogu formantu można znaleźć.  
  
     Formant został dodany do formularza z określonej lokalizacji i rozmiaru.  
  
    > [!NOTE]
    >  Każdy formant ma domyślny rozmiar zdefiniowany. Można dodać kontrolkę do formularza w formantu domyślny rozmiar, przeciągając je z **przybornika** do formularza.  
  
### <a name="to-drag-a-control-to-a-form"></a>Przeciągnij formant do formularza  
  
1.  Otwórz formularz. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formularzy systemu Windows w Projektancie](http://msdn.microsoft.com/library/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  W **przybornika**, kliknij i przeciągnij go do formularza formantu.  
  
     Formant został dodany do formularza w określonej lokalizacji w jego domyślny rozmiar.  
  
    > [!NOTE]
    >  Możesz kliknąć dwukrotnie formantu w **przybornika** Aby dodać go do lewego górnego rogu formularza w jego domyślny rozmiar.  
  
     Można również dodawać formanty dynamicznie do formularza w czasie wykonywania. W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formantu zostanie dodany do formularza po <xref:System.Windows.Forms.Button> formant zostanie kliknięty.  
  
    > [!NOTE]
    >  Poniższa procedura wymaga istnienia formularza z **przycisk** kontroli, `Button1`, już umieszczony na nim.  
  
### <a name="to-add-a-control-to-a-form-programmatically"></a>Aby programowo Dodawanie formantu do formularza  
  
1.  W metodzie, który obsługuje przycisku `Click` zdarzenia w klasie formularza, Wstaw kod podobne do następujących czynności, aby dodać odwołanie do zmiennej formantu użytkownika Ustawianie formantu `Location`i Dodaj formant.  
  
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
    >  Na komputerze lokalnym zagrożenie bezpieczeństwa w sieci może udostępniać za pomocą odwołań do złośliwych `UserControl`. Tylko będzie to problemem w przypadku złośliwe osoby tworzenie kontrolkę niestandardową szkodliwy, następuje można przez pomyłkę dodanie go do projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Instrukcje: zmienianie rozmiaru kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)  
 [Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)

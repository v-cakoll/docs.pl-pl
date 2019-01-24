---
title: 'Przewodnik: Praca z formantem MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: a81a715578e3cbbe576f1513770ff86f08807fdf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615088"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Przewodnik: Praca z formantem MaskedTextBox
Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Inicjowanie <xref:System.Windows.Forms.MaskedTextBox> kontroli  
  
-   Za pomocą <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> program obsługi zdarzeń, aby ostrzec użytkownika, jeśli znak nie jest zgodny z maską  
  
-   Przypisywanie typu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości i za pomocą <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> program obsługi zdarzeń, aby ostrzec użytkownika, gdy wartości są próby przekazania jest nieprawidłowy dla typu  
  
## <a name="creating-the-project-and-adding-a-control"></a>Tworzenie projektu i dodawanie kontrolki  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Aby dodać maskedtextbox — formant do formularza  
  
1.  Otwórz formularz, na którym chcesz umieścić <xref:System.Windows.Forms.MaskedTextBox> kontroli.  
  
2.  Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> z kontrolować **przybornika** do formularza.  
  
3.  Kliknij prawym przyciskiem myszy formant, a następnie wybierz **właściwości**. W **właściwości** wybierz **maski** właściwości i kliknij przycisk **...**  (wielokropek) przycisk znajdujący się obok nazwy właściwości.  
  
4.  W **maska wprowadzania** okno dialogowe, wybierz opcję **daty krótkiej** maski, a następnie kliknij przycisk **OK**.  
  
5.  W **właściwości** zestaw okna <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> właściwość `true`. Tej właściwości powoduje, że sygnał dźwiękowy krótki dźwięk za każdym razem, gdy użytkownik próbuje Wprowadź znak, który narusza definicję maski.  
  
 Podsumowanie znaków, które obsługuje właściwość maska, zobacz sekcję Uwagi <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
## <a name="alert-the-user-to-input-errors"></a>Ostrzegać użytkowników o danych wejściowych błędy  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Dodaj dymku dla odrzuconych maska wprowadzania  
  
1.  Wróć do **przybornika** i Dodaj <xref:System.Windows.Forms.ToolTip> do formularza.  
  
2.  Utwórz procedurę obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> zdarzeń, która wywołuje <xref:System.Windows.Forms.ToolTip> gdy wystąpi błąd danych wejściowych. Dymku pozostają widoczne na pięć sekund, lub użytkownik go kliknie.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Ostrzegać użytkowników do typu, który jest nieprawidłowy  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Dodaj poradę dotyczącą dymku dla typów nieprawidłowe dane  
  
1.  Do formularza <xref:System.Windows.Forms.Form.Load> procedura obsługi zdarzeń, Przypisz <xref:System.Type> obiekt reprezentujący <xref:System.DateTime> typ <xref:System.Windows.Forms.MaskedTextBox> kontrolki <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości:  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  Dodawanie obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> zdarzeń:  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox, kontrolka](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)

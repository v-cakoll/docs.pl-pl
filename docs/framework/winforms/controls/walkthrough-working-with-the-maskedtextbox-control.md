---
title: 'Wskazówki: praca z formantem MaskedTextBox'
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
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182046"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Wskazówki: praca z formantem MaskedTextBox
Zadania zilustrowane w tym przewodniku obejmują:  
  
- Inicjowanie <xref:System.Windows.Forms.MaskedTextBox> formantu  
  
- Za <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> pomocą programu obsługi zdarzeń, aby ostrzec użytkownika, gdy znak nie jest zgodny z maską  
  
- Przypisywanie typu do <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości i <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> używanie programu obsługi zdarzeń do ostrzegania użytkownika, gdy wartość, którą próbują zatwierdzić, jest nieprawidłowa dla tego typu  
  
## <a name="creating-the-project-and-adding-a-control"></a>Tworzenie projektu i dodawanie formantu  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Aby dodać formant MaskedTextBox do formularza  
  
1. Otwórz formularz, w którym chcesz <xref:System.Windows.Forms.MaskedTextBox> umieścić formant.  
  
2. Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> formant z **przybornika** do formularza.  
  
3. Kliknij prawym przyciskiem myszy formant i wybierz polecenie **Właściwości**. W oknie **Właściwości** wybierz właściwość **Mask i** kliknij przycisk **...** (wielokropek) obok nazwy właściwości.  
  
4. W oknie **dialogowym Maska wprowadzania** zaznacz maskę **Data krótka** i kliknij przycisk **OK**.  
  
5. W oknie **Właściwości** ustaw <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> właściwość na `true`. Ta właściwość powoduje, że krótki sygnał dźwiękowy do dźwięku za każdym razem, gdy użytkownik próbuje wprowadzić znak, który narusza definicję maski.  
  
 Aby uzyskać podsumowanie znaków, które maskuje właściwość, zobacz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> uwagi sekcji właściwości.  
  
## <a name="alert-the-user-to-input-errors"></a>Ostrzeganie użytkownika o błędach wprowadzania  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Dodawanie końcówki dymka dla odrzuconego wprowadzania maski  
  
1. Wróć do **przybornika** <xref:System.Windows.Forms.ToolTip> i dodaj go do formularza.  
  
2. Utwórz program obsługi <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> zdarzeń dla <xref:System.Windows.Forms.ToolTip> zdarzenia, które podnosi, gdy wystąpi błąd wejściowy. Końcówka dymka pozostaje widoczna przez pięć sekund lub do momentu kliknięcia przez użytkownika.  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Ostrzeganie użytkownika o typie, który jest nieprawidłowy  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Dodawanie końcówki dymka dla nieprawidłowych typów danych  
  
1. W programie obsługi <xref:System.Windows.Forms.Form.Load> zdarzeń formularza <xref:System.Type> przypisz obiekt <xref:System.DateTime> reprezentujący <xref:System.Windows.Forms.MaskedTextBox> typ <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> do właściwości formantu:  
  
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
  
2. Dodaj program obsługi <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> zdarzeń dla zdarzenia:  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox, kontrolka](maskedtextbox-control-windows-forms.md)

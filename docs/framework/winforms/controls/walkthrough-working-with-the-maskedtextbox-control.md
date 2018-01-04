---
title: "Wskazówki: praca z formantem MaskedTextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 006dafe88c5db7cb1499d7c1902d295841bfb5ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Wskazówki: praca z formantem MaskedTextBox
Zadania przedstawione w tym przewodniku obejmują:  
  
-   Inicjowanie <xref:System.Windows.Forms.MaskedTextBox> formantu  
  
-   Przy użyciu <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> obsługi zdarzeń, aby ostrzec użytkownika, gdy znak jest niezgodna z maską  
  
-   Typ do przypisywania <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości i przy użyciu <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> obsługi zdarzeń, aby ostrzec użytkownika, gdy wartość one próby przekazania nie jest prawidłowa dla typu  
  
## <a name="creating-the-project-and-adding-a-control"></a>Tworzenie projektu i dodawanie formantu  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Aby dodać do formularza maskedtextbox — formant  
  
1.  Otwórz formularz, na którym chcesz umieścić <xref:System.Windows.Forms.MaskedTextBox> formantu.  
  
2.  Przeciągnij <xref:System.Windows.Forms.MaskedTextBox> kontrolować z **przybornika** do formularza.  
  
3.  Kliknij prawym przyciskiem myszy formantu i wybierz polecenie **właściwości**. W **właściwości** wybierz **maski** właściwości i kliknij przycisk **...**  (wielokropkiem) obok nazwy właściwości.  
  
4.  W **maska wprowadzania** okno dialogowe, wybierz opcję **Data krótka** maski, a następnie kliknij przycisk **OK**.  
  
5.  W **właściwości** zestaw okna <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> właściwości `true`. Ta właściwość powoduje, że krótkich dźwiękowego dźwięk za każdym razem, gdy użytkownik próbuje znak, który narusza definicję maski wprowadzania.  
  
 Podsumowanie znaki, które obsługuje właściwość maska, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
## <a name="alert-the-user-to-input-errors"></a>Błędy wejściowych użytkownika  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Dodaj etykieta dymka dla odrzucone maska wprowadzania  
  
1.  Wróć do **przybornika** i Dodaj <xref:System.Windows.Forms.ToolTip> do formularza.  
  
2.  Tworzenie procedury obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> zdarzeń, który wywołuje <xref:System.Windows.Forms.ToolTip> gdy wystąpi błąd danych wejściowych. Etykieta dymka pozostanie widoczny przez pięć sekund, lub kliknięciu przez użytkownika.  
  
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
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Użytkownika typu, który jest nieprawidłowy  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Dodaj etykieta dymka dla typów nieprawidłowe dane  
  
1.  Do formularza <xref:System.Windows.Forms.Form.Load> program obsługi zdarzeń, Przypisz <xref:System.Type> reprezentujący obiekt <xref:System.DateTime> typ <xref:System.Windows.Forms.MaskedTextBox> formantu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości:  
  
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
  
2.  Dodaj program obsługi zdarzeń dla <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> zdarzeń:  
  
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
 <xref:System.Windows.Forms.MaskedTextBox>  
 [MaskedTextBox, kontrolka](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)

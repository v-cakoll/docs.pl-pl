---
title: Dodawanie kontrolek
description: Dowiedz się, jak narysować kontrolkę w formularzu systemu Windows. Kontrolka jest składnikiem formularza, którego można użyć do wyświetlania informacji lub akceptowania danych wejściowych użytkownika.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: d9ab0d78fa0153cce20fb17d22f6e9e781229ece
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325887"
---
# <a name="how-to-add-controls-to-windows-forms"></a>Porady: dodawanie formantów do formularzy systemu Windows

Większość formularzy służy do dodawania kontrolek do powierzchni formularza w celu zdefiniowania interfejsu użytkownika. *Kontrolka* to składnik formularza służący do wyświetlania informacji lub akceptowania danych wejściowych użytkownika. Aby uzyskać więcej informacji na temat kontrolek, zobacz [Windows Forms Controls](index.md).

## <a name="to-draw-a-control-on-a-form"></a>Aby narysować kontrolkę w formularzu

1. Otwórz formularz. Aby uzyskać więcej informacji, zobacz [How to: Display Windows Forms in a Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. W **przyborniku**kliknij kontrolkę, którą chcesz dodać do formularza.

3. Na formularzu kliknij miejsce w lewym górnym rogu kontrolki, a następnie przeciągnij do miejsca, w którym ma się znajdować prawy dolny róg kontrolki.

    Kontrolka zostanie dodana do formularza z określoną lokalizacją i rozmiarem.

    > [!NOTE]
    > Każdy formant ma zdefiniowany rozmiar domyślny. Możesz dodać formant do formularza w domyślnym rozmiarze kontrolki, przeciągając go z **przybornika** do formularza.

## <a name="to-drag-a-control-to-a-form"></a>Aby przeciągnąć formant do formularza

1. Otwórz formularz. Aby uzyskać więcej informacji, zobacz [How to: Display Windows Forms in a Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100)).

2. W **przyborniku**kliknij żądany formant i przeciągnij go do formularza.

    Kontrolka jest dodawana do formularza w określonej lokalizacji w domyślnym rozmiarze.

    > [!NOTE]
    > Możesz dwukrotnie kliknąć kontrolkę w **przyborniku** , aby dodać ją do lewego górnego rogu formularza w domyślnym rozmiarze.

    Kontrolki można także dynamicznie dodawać do formularza w czasie wykonywania. W poniższym przykładzie kodu <xref:System.Windows.Forms.TextBox> formant zostanie dodany do formularza, gdy zostanie <xref:System.Windows.Forms.Button> kliknięty formant.

    > [!NOTE]
    > Poniższa procedura wymaga istnienia formularza z kontrolką **przycisku** , która jest `Button1` już umieszczona w nim.

## <a name="to-add-a-control-to-a-form-programmatically"></a>Aby programowo dodać formant do formularza

1. W metodzie, która obsługuje zdarzenie przycisku `Click` w klasie formularza, Wstaw kod podobny do poniższego, aby dodać odwołanie do zmiennej kontroli, ustaw kontrolkę `Location` i Dodaj kontrolkę.

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
    > Możesz również dodać kod, aby zainicjować inne właściwości formantu.

    > [!IMPORTANT]
    > Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do złośliwej `UserControl` . Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.

## <a name="see-also"></a>Zobacz też

- [Kontrolki Windows Forms](index.md)
- [Porady: zmienianie rozmiaru formantów na formularzach systemu Windows](how-to-resize-controls-on-windows-forms.md)
- [Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)

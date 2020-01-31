---
title: Dodawanie kontrolek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, adding to form
- controls [Windows Forms], adding
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
ms.openlocfilehash: 560089a23fbcccb0f0d5683a95ad06dd9c59556d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743957"
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

    Kontrolki można także dynamicznie dodawać do formularza w czasie wykonywania. W poniższym przykładzie kodu formant <xref:System.Windows.Forms.TextBox> zostanie dodany do formularza po kliknięciu kontrolki <xref:System.Windows.Forms.Button>.

    > [!NOTE]
    > Poniższa procedura wymaga istnienia formularza z kontrolką **przycisku** , `Button1`już umieszczona na nim.

## <a name="to-add-a-control-to-a-form-programmatically"></a>Aby programowo dodać formant do formularza

1. W metodzie, która obsługuje zdarzenie `Click` przycisku w klasie formularza, Wstaw kod podobny do poniższego, aby dodać odwołanie do zmiennej kontroli, ustaw `Location`kontrolki i Dodaj kontrolkę.

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
    > Komputer lokalny może być narażony na zagrożenia bezpieczeństwa przez sieć, odwołując się do złośliwego `UserControl`. Może to stanowić problem tylko w przypadku złośliwej osoby, która tworzy szkodliwą kontrolkę niestandardową, a następnie nie dodawaj jej do projektu.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Instrukcje: zmienianie rozmiaru kontrolek na formularzach Windows Forms](how-to-resize-controls-on-windows-forms.md)
- [Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)

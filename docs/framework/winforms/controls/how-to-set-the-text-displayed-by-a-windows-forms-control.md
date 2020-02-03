---
title: Ustawianie tekstu wyświetlanego przez kontrolkę
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: eb02cbc3b335b0d5856f786b21d1d202cf444211
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738424"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms

Kontrolki Windows Forms zwykle wyświetlają tekst, który jest powiązany z podstawową funkcją formantu. Na przykład kontrolka <xref:System.Windows.Forms.Button> zwykle wyświetla napis wskazujący, jaka akcja zostanie wykonana po kliknięciu przycisku. Dla wszystkich kontrolek można ustawić lub zwrócić tekst przy użyciu właściwości <xref:System.Windows.Forms.Control.Text%2A>. Można zmienić czcionkę przy użyciu właściwości <xref:System.Windows.Forms.Control.Font%2A>.

Możesz również ustawić tekst za pomocą [projektanta](#designer).

## <a name="programmatic"></a>Programowa

1. Ustaw właściwość <xref:System.Windows.Forms.Control.Text%2A> na ciąg.

   Aby utworzyć podkreślony klucz dostępu, program zawiera znak handlowego "i" (&) przed literą, która będzie kluczem dostępu.

2. Ustaw właściwość <xref:System.Windows.Forms.Control.Font%2A> na obiekt typu <xref:System.Drawing.Font>.

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > Możesz użyć znaku ucieczki, aby wyświetlić specjalny znak w elementach interfejsu użytkownika, które zwykle interpretują je inaczej, takich jak elementy menu. Na przykład poniższy wiersz kodu ustawia tekst elementu menu do odczytania "& teraz dla czegoś zupełnie innego":

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Projektant

1. W oknie **Właściwości** w programie Visual Studio ustaw właściwość **Text** kontrolki na odpowiedni ciąg.

   Aby utworzyć podkreślony klawisz skrótu, program zawiera znak handlowego "i" (&) przed literą, która będzie klawiszem skrótu.

2. W oknie **Właściwości** wybierz przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/visual-studio-ellipsis-button.png)) obok właściwości **Font** .

   W oknie dialogowym Czcionka standardowa wybierz czcionkę, styl czcionki, rozmiar, efekty (na przykład przekreślenie lub podkreślenie) i skrypt, którego chcesz użyć.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)

---
title: Międzynarodowe czcionki w formularzach i kontrolkach
ms.date: 03/30/2017
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
dev_langs:
- csharp
- vb
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
ms.openlocfilehash: 59dde6bb384d644321a8ff5674d735f8e6d36fd0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743521"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Międzynarodowe czcionki w Windows Forms i kontrolki

W aplikacjach międzynarodowych zalecaną metodą wybierania czcionek jest użycie opcji powrotu do czcionki wszędzie tam, gdzie jest to możliwe. Powrót do czcionki oznacza, że system Określa, do jakiego skryptu należy znak.

## <a name="using-font-fallback"></a>Używanie powrotu do czcionek

Aby skorzystać z tej funkcji, nie ustawiaj właściwości <xref:System.Drawing.Font> dla formularza ani innego elementu. Aplikacja automatycznie użyje domyślnej czcionki systemowej, która różni się od jednego zlokalizowanego języka systemu operacyjnego do innego. Gdy aplikacja zostanie uruchomiona, system automatycznie poda poprawną czcionkę dla kultury wybranej w systemie operacyjnym.

Istnieje wyjątek od reguły, która nie ustawia czcionki, która umożliwia zmianę stylu czcionki. Może to być ważne w przypadku aplikacji, w której użytkownik klika przycisk, aby tekst w polu tekstowym był wyświetlany jako pogrubiony. W tym celu należy napisać funkcję, aby zmienić styl czcionki pola tekstowego na pogrubioną, w zależności od rodzaju czcionki formularza. Ważne jest, aby wywołać tę funkcję w dwóch miejscach: w obsłudze zdarzeń <xref:System.Windows.Forms.Control.Click> przycisku i w obsłudze zdarzeń <xref:System.Windows.Forms.Control.FontChanged>. Jeśli funkcja jest wywoływana tylko w programie obsługi zdarzeń <xref:System.Windows.Forms.Control.Click> i niektóre inne fragmenty kodu zmieniają rodzinę czcionek całego formularza, pole tekstowe nie zmieni się w resztę formularza.

```vb
Private Sub MakeBold()
   ' Change the TextBox to a bold version of the form font
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)
End Sub

Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click
   ' Clicking this button makes the TextBox bold
   MakeBold()
End Sub

Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged
   ' If the TextBox is already bold and the form's font changes,
   ' change the TextBox to a bold version of the new form font
   If (TextBox1.Font.Style = FontStyle.Bold) Then
      MakeBold()
   End If
End Sub
```

```csharp
private void button1_Click(object sender, System.EventArgs e)
{
   // Clicking this button makes the TextBox bold
   MakeBold();
}

private void MakeBold()
{
   // Change the TextBox to a bold version of the form's font
   textBox1.Font = new Font(this.Font, FontStyle.Bold);
}

private void Form1_FontChanged(object sender, System.EventArgs e)
{
   // If the TextBox is already bold and the form's font changes,
   // change the TextBox to a bold version of the new form font
   if (textBox1.Font.Style == FontStyle.Bold)
   {
      MakeBold();
   }
}
```

Jednak podczas lokalizowania aplikacji czcionka pogrubiona może być wyświetlana w niewłaściwy sposób w przypadku niektórych języków. Jeśli jest to problem, chcemy, aby lokalizatory miały możliwość przełączania czcionki z pogrubionej do zwykłego tekstu. Ponieważ lokalizatory zazwyczaj nie są deweloperami i nie mają dostępu do kodu źródłowego, tylko w przypadku plików zasobów, ta opcja musi być ustawiona w plikach zasobów. W tym celu należy ustawić właściwość <xref:System.Drawing.Font.Bold%2A> na `true`. Powoduje to zapisanie ustawienia czcionki do plików zasobów, gdzie lokalizatory mogą go edytować. Następnie napiszesz kod po metodzie `InitializeComponent`, aby zresetować czcionkę w oparciu o zawartość czcionki formularza, ale przy użyciu stylu czcionki określonego w pliku zasobów.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Zobacz także

- [Używanie czcionek i tekstu](using-fonts-and-text.md)

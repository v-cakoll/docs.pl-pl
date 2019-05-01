---
title: Międzynarodowe czcionki w formularzach Windows i kontrolek
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
ms.openlocfilehash: 1f9afd575e2de04e0b11556ad34436839e13d968
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942899"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Międzynarodowe czcionki w formularzach Windows i kontrolek

W aplikacjach międzynarodowych wybierania czcionek zaleca się użyć rezerwa czcionek, tam gdzie to możliwe. Czcionka rezerwowego oznacza, że system określi, co skrypt znak należy do.

## <a name="using-font-fallback"></a>Przy użyciu czcionki rezerwowe

Aby móc korzystać z tej funkcji, nie należy ustawiać <xref:System.Drawing.Font> właściwości dla formularza lub innego elementu. Aplikacja będzie automatycznie używać domyślnej czcionki systemowej, która różni się od jednego zlokalizowanego języka systemu operacyjnego do innego. Gdy aplikacja zostanie uruchomiona, system automatycznie zapewnić poprawną czcionkę dla kultury wybrane w systemie operacyjnym.

Występuje wyjątek do reguły nie ustawienia czcionki, której dotyczy zmiana styl czcionki. Może to być ważne dla aplikacji, w którym użytkownik kliknie przycisk, aby tekst w polu tekstowym, są wyświetlane pogrubioną czcionką. Aby to zrobić, należy napisać funkcję, aby zmienić styl czcionki pole tekstowe do pogrubienie, oparciu o dowolnej formie czcionki. Ważne jest, aby wywołać tę funkcję w dwóch miejscach: przycisku <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń i <xref:System.Windows.Forms.Control.FontChanged> programu obsługi zdarzeń. Jeśli funkcja jest wywoływana tylko w <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń i innych fragment kodu zmienia rodzinę czcionek cały formularz, pole tekstowe nie zmienia się w pozostałej części formularza.

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

Jednak gdy możesz zlokalizować aplikację, pogrubioną czcionką mogą być wyświetlane nieprawidłowo w przypadku niektórych języków. Jeśli jest to niepożądane, chcesz lokalizatorzy dostępna będzie opcja przełączania czcionki pogrubioną czcionką na zwykły tekst. Ponieważ lokalizatorzy nie są zwykle deweloperzy i nie mają dostępu do kodu źródłowego, tylko do plików zasobów, ta opcja musi być ustawiona w plikach zasobów. Aby to zrobić, należy ustawić <xref:System.Drawing.Font.Bold%2A> właściwość `true`. Powoduje to ustawienie czcionki, są zapisywane w plikach zasobów, w którym lokalizatorzy można go edytować. Następnie napisać kod po `InitializeComponent` metodę, aby zresetować czcionki na podstawie informacji o dowolnej formie czcionki, ale za pomocą styl czcionki określonych w pliku zasobów.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Zobacz także

- [Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)
- [Używanie czcionek i tekstu](using-fonts-and-text.md)

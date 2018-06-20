---
title: Międzynarodowe czcionki w formularzach systemu Windows i formantów
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
ms.openlocfilehash: b2738f174c9837a2ba83c1306f4617f39ce17de1
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208457"
---
# <a name="international-fonts-in-windows-forms-and-controls"></a>Międzynarodowe czcionki w formularzach systemu Windows i formantów

W aplikacjach międzynarodowych wybranie czcionki zalecaną metodą jest użycie rezerwa czcionek, tam gdzie to możliwe. Czcionka rezerwowy oznacza, że system sprawdza, co skryptu znak należy do.

## <a name="using-font-fallback"></a>Przy użyciu rezerwa czcionek

Aby móc korzystać z tej funkcji, nie należy ustawiać <xref:System.Drawing.Font> właściwość formularza lub innego elementu. Aplikacja będzie automatycznie używać domyślnej czcionki systemowej, która różni się od zlokalizowanego języka systemu operacyjnego do innego. Po uruchomieniu aplikacji, system automatycznie Podaj poprawną czcionkę dla kultury wybrane w systemie operacyjnym.

Brak wyjątek do reguły nie ustawienie czcionki, który jest zmiany stylu czcionki. Może to być istotne dla aplikacji, w którym użytkownik kliknie przycisk, aby tekst w polu tekstowym wyświetlone pogrubioną czcionką. W tym celu piszesz funkcji, aby zmienić styl czcionki w polu tekstowym mają zostać pogrubione, oparte na czcionka niezależnie od formularza jest. Ważne jest, aby wywołanie tej funkcji w dwóch miejscach: w przycisku <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń i <xref:System.Windows.Forms.Control.FontChanged> obsługi zdarzeń. Jeśli funkcja jest wywoływana tylko w <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń i inne części kodu zmienia rodziny czcionek całego formularza, pole tekstowe nie zmienia się w pozostałej części formularza.

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

Jednak gdy lokalizowanie aplikacji, pogrubioną czcionką mogą być wyświetlane nieprawidłowo określonych języków. W przypadku wątpliwości dotyczących ma wiadomość dla lokalizatorów dostępna będzie opcja przełączania czcionki czcionką na zwykły tekst. Ponieważ wiadomość dla lokalizatorów nie są zwykle deweloperzy i nie mają dostępu do kodu źródłowego, tylko do plików zasobów, ta opcja musi być ustawiona w plikach zasobów. Aby to zrobić, należy ustawić <xref:System.Drawing.Font.Bold%2A> właściwości `true`. Powoduje to ustawienie czcionki zapisaniem plików zasobów, gdy wiadomość dla lokalizatorów można go edytować. Następnie napiszesz kod po `InitializeComponent` metoda czcionki oparte na jest bez względu na rodzaj czcionki, ale przy użyciu stylów czcionek określone w pliku zasobów.

```vb
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)
```

```csharp
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);
```
  
## <a name="see-also"></a>Zobacz także

[Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)  
[Używanie czcionek i tekstu](using-fonts-and-text.md)
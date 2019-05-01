---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644555"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Dodaj właściwość publiczną SelectionTextBrush do pola tekstowego/PasswordBox — moduł definiowania układu zaznaczenia

|   |   |
|---|---|
|Szczegóły|W aplikacji WPF przy użyciu [bez definiowania układu na podstawie zaznaczonego tekstu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox>, deweloperzy mogą teraz ustawić nowo dodanej właściwości SelectionTextBrush aby można było zmienić renderowania zaznaczonego tekstu.  Domyślnie ten kolor zmienia się przy użyciu <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Jeśli na podstawie innego niż moduł definiowania układu zaznaczony tekst nie jest włączona, nie robi nic, ta właściwość.|
|Sugestia|Gdy na podstawie innego niż moduł definiowania układu zaznaczonego tekstu jest włączona, można użyć <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> i <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> właściwości, aby zmienić wygląd zaznaczonego tekstu. Można to osiągnąć przy użyciu XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

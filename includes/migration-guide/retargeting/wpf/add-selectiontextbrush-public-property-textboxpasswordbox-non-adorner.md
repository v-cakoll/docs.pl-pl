---
ms.openlocfilehash: e04134ec731c5e7bede3388621078c6518805ec2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803544"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Dodaj SelectionTextBrush właściwość publiczna do textbox /PasswordBox non-adorner wyboru

|   |   |
|---|---|
|Szczegóły|W aplikacjach WPF przy użyciu [nie-adorner na podstawie wyboru tekstu](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox>deweloperzy mogą teraz ustawić nowo dodane SelectionTextBrush właściwości w celu zmiany renderowania zaznaczonego tekstu.  Domyślnie ten kolor <xref:System.Windows.SystemColors.HighlightTextBrushKey>zmienia się wraz z programem .  Jeśli nie-adorner na podstawie wyboru tekstu nie jest włączona, ta właściwość nie robi nic.|
|Sugestia|Po włączeniu zaznaczenia tekstu opartego na adornerze można użyć <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> właściwości i <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> właściwości, aby zmienić wygląd zaznaczonego tekstu. Można to osiągnąć za pomocą XAML:<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Zakres|Duży|
|Wersja|4.8|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[Pole systemowe system.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

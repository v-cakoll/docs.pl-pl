---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616310"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Dodaj właściwość publiczną SelectionTextBrush do zaznaczenia pola tekstowego/PasswordBox bez modułu definiowania układu

#### <a name="details"></a>Szczegóły

W aplikacjach WPF korzystających z [tekstu innego niż moduł definiowania](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) układu dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> , deweloperzy mogą teraz ustawić nowo dodaną Właściwość SelectionTextBrush, aby zmienić renderowanie zaznaczonego tekstu.  Domyślnie ten kolor zmienia się z <xref:System.Windows.SystemColors.HighlightTextBrushKey> .  Jeśli zaznaczenie tekstu bez modułu definiowania układu nie jest włączone, ta właściwość nie wykonuje żadnych operacji.

#### <a name="suggestion"></a>Sugestia

Po włączeniu zaznaczania tekstu, który nie jest oparty na programie do definiowania układu, można użyć <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> właściwości i, <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> Aby zmienić wygląd zaznaczonego tekstu. Można to osiągnąć przy użyciu języka XAML:

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Duży       |
| Wersja | 4,8         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [System. Windows. Controls. TextBox](xref:System.Windows.Controls.TextBox)
- [System. Windows. Controls. PasswordBox](xref:System.Windows.Controls.PasswordBox)

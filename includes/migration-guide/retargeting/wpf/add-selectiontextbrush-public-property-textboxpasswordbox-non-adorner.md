---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616310"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="be0ea-101">Dodaj właściwość publiczną SelectionTextBrush do zaznaczenia pola tekstowego/PasswordBox bez modułu definiowania układu</span><span class="sxs-lookup"><span data-stu-id="be0ea-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="be0ea-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="be0ea-102">Details</span></span>

<span data-ttu-id="be0ea-103">W aplikacjach WPF korzystających z [tekstu innego niż moduł definiowania](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) układu dla <xref:System.Windows.Controls.TextBox> i <xref:System.Windows.Controls.PasswordBox> , deweloperzy mogą teraz ustawić nowo dodaną Właściwość SelectionTextBrush, aby zmienić renderowanie zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="be0ea-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="be0ea-104">Domyślnie ten kolor zmienia się z <xref:System.Windows.SystemColors.HighlightTextBrushKey> .</span><span class="sxs-lookup"><span data-stu-id="be0ea-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="be0ea-105">Jeśli zaznaczenie tekstu bez modułu definiowania układu nie jest włączone, ta właściwość nie wykonuje żadnych operacji.</span><span class="sxs-lookup"><span data-stu-id="be0ea-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="be0ea-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="be0ea-106">Suggestion</span></span>

<span data-ttu-id="be0ea-107">Po włączeniu zaznaczania tekstu, który nie jest oparty na programie do definiowania układu, można użyć <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> właściwości i, <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> Aby zmienić wygląd zaznaczonego tekstu.</span><span class="sxs-lookup"><span data-stu-id="be0ea-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="be0ea-108">Można to osiągnąć przy użyciu języka XAML:</span><span class="sxs-lookup"><span data-stu-id="be0ea-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="be0ea-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="be0ea-109">Name</span></span>    | <span data-ttu-id="be0ea-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="be0ea-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="be0ea-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="be0ea-111">Scope</span></span>   | <span data-ttu-id="be0ea-112">Duży</span><span class="sxs-lookup"><span data-stu-id="be0ea-112">Major</span></span>       |
| <span data-ttu-id="be0ea-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="be0ea-113">Version</span></span> | <span data-ttu-id="be0ea-114">4,8</span><span class="sxs-lookup"><span data-stu-id="be0ea-114">4.8</span></span>         |
| <span data-ttu-id="be0ea-115">Typ</span><span class="sxs-lookup"><span data-stu-id="be0ea-115">Type</span></span>    | <span data-ttu-id="be0ea-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="be0ea-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="be0ea-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="be0ea-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="be0ea-118">System. Windows. Controls. TextBox</span><span class="sxs-lookup"><span data-stu-id="be0ea-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="be0ea-119">System. Windows. Controls. PasswordBox</span><span class="sxs-lookup"><span data-stu-id="be0ea-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)

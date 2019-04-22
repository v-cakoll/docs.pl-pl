---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774421"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Właściwość WPF TextBox.Text może być niezsynchronizowana z powodu powiązania danych

|   |   |
|---|---|
|Szczegóły|W niektórych przypadkach właściwość <xref:System.Windows.Controls.TextBox.Text> odzwierciedla poprzednią wartość właściwości związanej z danymi, jeśli ta właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.|
|Sugestia|Nie powinno to mieć żadnego negatywnego wpływu. Jednakże można przywrócić poprzednie zachowanie przez ustawienie właściwości <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType></li></ul>|

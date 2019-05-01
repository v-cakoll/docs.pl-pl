---
ms.openlocfilehash: 8b0617d8f021a9534289fd7ae8539cd054684862
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62091710"
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

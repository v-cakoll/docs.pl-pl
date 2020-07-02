---
ms.openlocfilehash: d0de1a262d57c67dd4dfb258d5ac013af5d8783d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617294"
---
### <a name="wpf-textboxtext-can-be-out-of-sync-with-databinding"></a>Właściwość WPF TextBox.Text może być niezsynchronizowana z powodu powiązania danych

#### <a name="details"></a>Szczegóły

W niektórych przypadkach właściwość <xref:System.Windows.Controls.TextBox.Text> odzwierciedla poprzednią wartość właściwości związanej z danymi, jeśli ta właściwość jest modyfikowana podczas operacji zapisu z wiązaniem danych.

#### <a name="suggestion"></a>Sugestia

Nie powinno to mieć żadnego negatywnego wpływu. Jednakże można przywrócić poprzednie zachowanie przez ustawienie właściwości <xref:System.Windows.FrameworkCompatibilityPreferences.KeepTextBoxDisplaySynchronizedWithTextProperty> na `false`.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.5         |
|Typ|Przekierowanie

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType>

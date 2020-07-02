---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620466"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Zaznaczony tekst pola tekstowego WPF jest wyświetlany w innym kolorze, gdy pole tekstowe jest nieaktywne

#### <a name="details"></a>Szczegóły

W .NET Framework 4,5, gdy kontrolka pola tekstowego WPF jest nieaktywna (nie ma fokusu), zaznaczony tekst wewnątrz pola będzie wyglądać inaczej, niż w przypadku, gdy formant jest aktywny.

#### <a name="suggestion"></a>Sugestia

Zachowanie poprzedniego (.NET Framework 4,0) może zostać przywrócone przez ustawienie <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwości na <code>false</code> .

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   |Brzeg|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe

#### <a name="affected-apis"></a>Dotyczy interfejsów API

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

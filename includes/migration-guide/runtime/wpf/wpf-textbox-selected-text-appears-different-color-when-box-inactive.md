---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804738"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>TextBox WPF zaznaczony tekst jest wyświetlany inny kolor, gdy pole tekstowe jest nieaktywny

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5, gdy formant pola tekstowego WPF jest nieaktywny (nie ma fokusu), zaznaczony tekst wewnątrz pola będą wyświetlane w innym kolorze niż gdy kontrolka jest aktywny.|
|Sugestia|Poprzednie zachowanie (.NET Framework 4.0) mogą zostać przywrócone, ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwość <code>false</code>.|
|Zakres|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

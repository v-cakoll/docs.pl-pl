---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379688"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>TextBox WPF zaznaczony tekst jest wyświetlany inny kolor, gdy pole tekstowe jest nieaktywny

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.5, gdy formant pola tekstowego WPF jest nieaktywny (nie ma fokusu), zaznaczony tekst wewnątrz pola będą wyświetlane w innym kolorze niż gdy kontrolka jest aktywny.|
|Sugestia|Poprzednie zachowanie (.NET Framework 4.0) mogą zostać przywrócone, ustawiając <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> właściwość <code>false</code>.|
|Scope|Krawędź|
|Wersja|4.5|
|Typ|Środowisko uruchomieniowe|
|Dotyczy interfejsów API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644034"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a>Przełącznik. System. Windows. Forms. UseLegacyImages nie jest obsługiwany.

Przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages`, który został wprowadzony w .NET Framework 4,8, nie jest obsługiwany w Windows Forms na platformie .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4,8, przełącznik zgodności `Switch.System.Windows.Forms.UseLegacyImages` zapoznajł możliwe problemy z skalowaniem obrazu w scenariuszach ClickOnce w środowiskach o wysokiej rozdzielczości DPI. Gdy ustawiona na `true`, przełącznik zezwala użytkownikowi na przywracanie starszego skalowania obrazów na wyświetlaczach o wysokiej rozdzielczości DPI, których Skala jest ustawiona na wartość większą niż 100%. Aby uzyskać więcej informacji, zobacz [Informacje o wersji .NET Framework 4,8](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) w witrynie GitHub.

W programie .NET Core przełącznik `Switch.System.Windows.Forms.UseLegacyImages` nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3,0 wersja zapoznawcza 9

#### <a name="recommended-action"></a>Zalecane działanie

Usuń przełącznik. Przełącznik nie jest obsługiwany i żadna alternatywna funkcja nie jest dostępna.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

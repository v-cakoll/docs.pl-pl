---
ms.openlocfilehash: 3eab49acd3eaa5b6d5802af5f4e6f0fe2699ee97
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937120"
---
### <a name="uselegacyimages-compatibility-switch-not-supported"></a>Przełącznik zgodności UseLegacyImages nie jest obsługiwany

Przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności, który został wprowadzony w programie .NET Framework 4.8, nie jest obsługiwany w formularzach systemu Windows w programie .NET Core 3.0.

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Framework 4.8, przełącznik `Switch.System.Windows.Forms.UseLegacyImages` zgodności rozwiązać możliwe problemy ze skalowaniem obrazu w scenariuszach ClickOnce w środowiskach o wysokiej dpi. Po ustawieniu przełącznik `true`umożliwia użytkownikowi przywrócenie starszego skalowania obrazu na wyświetlaczach o wysokiej jakości dpi, których skala jest ustawiona na więcej niż 100%. Aby uzyskać więcej informacji, zobacz [.NET Framework 4.8 Informacje o wersji](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) w usiulach usługi GitHub.

W .NET Core `Switch.System.Windows.Forms.UseLegacyImages` przełącznik nie jest obsługiwany.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 9

#### <a name="recommended-action"></a>Zalecana akcja

Wyjmij przełącznik. Przełącznik nie jest obsługiwany i nie jest dostępna żadna alternatywna funkcjonalność.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- Brak

<!-- 

### Affected APIs

- Not detectable via API analysis

-->

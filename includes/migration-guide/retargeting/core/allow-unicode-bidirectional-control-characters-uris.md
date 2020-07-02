---
ms.openlocfilehash: 53d74db1a77e62cc64250658281fd3e4706fe494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614634"
---
### <a name="allow-unicode-bidirectional-control-characters-in-uris"></a>Zezwalaj na znaki kontrolne dwukierunkowej Unicode w identyfikatorach URI

#### <a name="details"></a>Szczegóły

Unicode określa kilka specjalnych znaków sterujących używanych do określania orientacji tekstu. W poprzednich wersjach .NET Framework te znaki zostały nieprawidłowo usunięte ze wszystkich identyfikatorów URI, nawet jeśli były obecne w postaci kodowanej według wartości procentowej. W celu lepszego przestrzegania [specyfikacji RFC 3987](https://tools.ietf.org/html/rfc3987)zezwalamy teraz na te znaki w identyfikatorach URI. W przypadku znalezienia niezaszyfrowanego identyfikatora URI są one kodowane według wartości procentowej. W przypadku znalezienia zakodowanej procentowo są one pozostawione jako-is.

#### <a name="suggestion"></a>Sugestia

W przypadku aplikacji przeznaczonych dla wersji .NET Framework począwszy od 4.7.2, obsługa znaków dwukierunkowych Unicode jest domyślnie włączona. Jeśli ta zmiana jest niepożądana, można ją wyłączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=true" />
</runtime>
```

W przypadku aplikacji przeznaczonych dla wcześniejszych wersji .NET Framework, które są uruchamiane w ramach wersji zaczynających się od .NET Framework 4.7.2, obsługa znaków dwukierunkowych Unicode jest domyślnie wyłączona. Można ją włączyć, dodając następujący przełącznik [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.Uri.DontKeepUnicodeBidiFormattingCharacters=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.7.2       |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Uri?displayProperty=nameWithType>

---
ms.openlocfilehash: d57cd5a9d41a7d2d93f03216d534f14831bcefe0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804764"
---
### <a name="changes-in-path-normalization"></a>Zmiany w ścieżce normalizacji

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji środowiska .NET Framework 4.6.2, zmienił się sposób, w której środowisko uruchomieniowe normalizuje ścieżki. Normalizowanie ścieżką obejmuje modyfikuje ciąg, który identyfikuje pliku lub ścieżki, tak aby odpowiada prawidłowej ścieżki, na docelowy system operacyjny. Normalizacja zwykle obejmuje:<ul><li>Przekształcania w formę kanoniczną separatory składnika i katalog.</li><li>Stosowanie bieżący katalog do ścieżki względnej.</li><li>Ocena względna katalogu (.) lub katalogu nadrzędnego (.) w ścieżce.</li><li>Przycinanie określonych znaków.</li></ul>Począwszy od aplikacji środowiska .NET Framework 4.6.2, następujące zmiany w ścieżce normalizacji są domyślnie włączone:<ul><li>Środowisko uruchomieniowe różni się w systemie operacyjnym [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) funkcję, aby znormalizować ścieżki.</li><li>Nie jest już normalizacji obejmuje przycinania koniec segmentów katalogu (np. miejsce na końcu nazwy katalogu).</li><li>Obsługa składnia ścieżki urządzenia w trybie pełnego zaufania, w tym `\\.\` a w przypadku plikowych interfejsów API we/wy w mscorlib.dll, `\\?\`.</li><li>Środowisko wykonawcze nie można zweryfikować ścieżki składni urządzeń.</li><li>Użycie składni urządzenia do uzyskania dostępu alternatywne strumienie danych jest obsługiwane.</li></ul>Te zmiany poprawić wydajność, podczas gdy metody dostępu do ścieżki niedostępnych wcześniej. Aplikacje, które przeznaczony dla platformy .NET Framework 4.6.1 oraz wcześniejszymi wersjami, ale działają na platformie .NET Framework 4.6.2 lub nowszej nie ma wpływu na tę zmianę.|
|Sugestia|Aplikacje, które obsługują program .NET Framework 4.6.2 lub nowszej można zrezygnować z tego zmienić i użyć starszego normalizacji, dodając następujące polecenie, aby <code>&lt;runtime&gt;</code> sekcję pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje, których platformą docelową jest program .NET Framework 4.6.1 lub wcześniej, ale są uruchomione w środowisku .NET Framework 4.6.2 lub później włączyć zmiany ścieżki normalizacji, dodając następujący wiersz do <code>&lt;runtime&gt;</code> części pliku .configuration aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|

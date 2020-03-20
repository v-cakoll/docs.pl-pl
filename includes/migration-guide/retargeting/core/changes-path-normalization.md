---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "70259805"
---
### <a name="changes-in-path-normalization"></a>Zmiany w normalizacji ścieżki

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji, które są przeznaczone dla programu .NET Framework 4.6.2, zmienił się sposób, w jaki środowisko wykonawcze normalizuje ścieżki. Normalizacja ścieżki polega na zmodyfikowaniu ciągu identyfikującego ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym. Normalizacja zazwyczaj obejmuje:<ul><li>Kanonizacja separatorów komponentów i katalogów.</li><li>Stosowanie bieżącego katalogu do ścieżki względnej.</li><li>Ocena katalogu względnego (.) lub katalogu nadrzędnego (..) w ścieżce.</li><li>Przycinanie określonych znaków.</li></ul>Począwszy od aplikacji docelowych programu .NET Framework 4.6.2, następujące zmiany w normalizacji ścieżki są domyślnie włączone:<ul><li>Środowisko wykonawcze defers do systemu operacyjnego [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) funkcji do normalizacji ścieżek.</li><li>Normalizacja nie obejmuje już przycinania końca segmentów katalogów (na przykład spacji na końcu nazwy katalogu).</li><li>Obsługa składni ścieżki urządzenia w pełnym `\\.\` zaufaniu, w tym i dla interfejsów API we/wy pliku w pliku mscorlib.dll, `\\?\`.</li><li>Środowisko wykonawcze nie sprawdza poprawności ścieżek składni urządzenia.</li><li>Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.</li></ul>Te zmiany zwiększają wydajność, umożliwiając jednocześnie metody dostępu wcześniej niedostępne ścieżki. Aplikacje przeznaczone dla programu .NET Framework 4.6.1 i wcześniejszych wersji, ale są uruchomione w ramach .NET Framework 4.6.2 lub nowszej, nie mają wpływu na tę zmianę.|
|Sugestia|Aplikacje przeznaczone dla programu .NET Framework 4.6.2 lub nowszego mogą zrezygnować z <code>&lt;runtime&gt;</code> tej zmiany i używać normalizacji starszych, dodając następujące elementy do sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje przeznaczone dla programu .NET Framework 4.6.1 lub starsze, ale działające w programie .NET Framework 4.6.2 <code>&lt;runtime&gt;</code> lub nowszym, mogą włączyć zmiany w normalizacji ścieżki, dodając następujący wiersz do sekcji pliku konfiguracji aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Zakres|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|

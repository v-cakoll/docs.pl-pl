---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70259805"
---
### <a name="changes-in-path-normalization"></a>Zmiany normalizacji ścieżki

|   |   |
|---|---|
|Szczegóły|Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, sposób, w jaki środowisko uruchomieniowe normalizuje ścieżki, zostało zmienione. Normalizowanie ścieżki polega na zmodyfikowaniu ciągu, który identyfikuje ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym. Normalizacja zazwyczaj obejmuje:<ul><li>Separatory składników formę kanoniczną działa i katalogów.</li><li>Zastosowanie bieżącego katalogu do ścieżki względnej.</li><li>Ocenianie katalogu względnego (.) lub katalogu nadrzędnego (..) w ścieżce.</li><li>Przycinanie określonych znaków.</li></ul>Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, następujące zmiany normalizacji ścieżki są domyślnie włączone:<ul><li>Środowisko uruchomieniowe odkłada do funkcji [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) systemu operacyjnego, aby znormalizować ścieżki.</li><li>Normalizacja nie obejmuje już przecinania końców segmentów katalogów (takich jak spacja na końcu nazwy katalogu).</li><li>Obsługa składni ścieżki urządzenia w pełnym zaufaniu, w `\\.\` tym i dla interfejsów API we/wy plików w bibliotece Mscorlib. `\\?\`dll,.</li><li>Środowisko uruchomieniowe nie sprawdza poprawności ścieżek składni urządzeń.</li><li>Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.</li></ul>Te zmiany zwiększają wydajność, a jednocześnie umożliwiają uzyskanie dostępu do wcześniej niedostępnych ścieżek. Ta zmiana nie wpłynie na aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, ale działają na .NET Framework 4.6.2 lub nowszych.|
|Sugestia|Aplikacje przeznaczone dla .NET Framework 4.6.2 lub nowszych mogą zrezygnować z tej zmiany i użyć starszej normalizacji, dodając następujący element do <code>&lt;runtime&gt;</code> sekcji pliku konfiguracyjnego aplikacji:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 lub wcześniejszych, ale działają na .NET Framework 4.6.2 lub później, mogą umożliwić zmianę normalizacji ścieżki, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku Application. Configuration:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Scope|Mały|
|Wersja|4.6.2|
|Typ|Przekierowanie|

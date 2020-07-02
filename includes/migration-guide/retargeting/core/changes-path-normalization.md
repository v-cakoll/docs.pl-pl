---
ms.openlocfilehash: 04c4fb4c8e9da8c58a5e26f78a7b13aa6a0df4a0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614687"
---
### <a name="changes-in-path-normalization"></a>Zmiany normalizacji ścieżki

#### <a name="details"></a>Szczegóły

Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, sposób, w jaki środowisko uruchomieniowe normalizuje ścieżki, zostało zmienione. Normalizowanie ścieżki polega na zmodyfikowaniu ciągu, który identyfikuje ścieżkę lub plik, tak aby był zgodny z prawidłową ścieżką w docelowym systemie operacyjnym. Normalizacja zazwyczaj obejmuje:

- Separatory składników formę kanoniczną działa i katalogów.
- Zastosowanie bieżącego katalogu do ścieżki względnej.
- Ocenianie katalogu względnego (.) lub katalogu nadrzędnego (..) w ścieżce.
- Przycinanie określonych znaków.
Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, następujące zmiany normalizacji ścieżki są domyślnie włączone:
  - Środowisko uruchomieniowe odkłada do funkcji [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) systemu operacyjnego, aby znormalizować ścieżki.
- Normalizacja nie obejmuje już przecinania końców segmentów katalogów (takich jak spacja na końcu nazwy katalogu).
- Obsługa składni ścieżki urządzenia w pełnym zaufaniu, w tym `\\.\` i dla interfejsów API we/wy plików w mscorlib.dll, `\\?\` .
- Środowisko uruchomieniowe nie sprawdza poprawności ścieżek składni urządzeń.
- Obsługiwane jest użycie składni urządzenia w celu uzyskania dostępu do alternatywnych strumieni danych.
Te zmiany zwiększają wydajność, a jednocześnie umożliwiają uzyskanie dostępu do wcześniej niedostępnych ścieżek. Ta zmiana nie wpłynie na aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych wersji, ale działają na .NET Framework 4.6.2 lub nowszych.

#### <a name="suggestion"></a>Sugestia

Aplikacje przeznaczone dla .NET Framework 4.6.2 lub nowszych mogą zrezygnować z tej zmiany i użyć starszej normalizacji, dodając następujący element do `<runtime>` sekcji pliku konfiguracyjnego aplikacji:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />
</runtime>
```

Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 lub wcześniejszych, ale działają na .NET Framework 4.6.2 lub później, mogą umożliwić zmianę normalizacji ścieżki, dodając następujący wiersz do `<runtime>` sekcji pliku Application. Configuration:

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=false" />
</runtime>
```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Mały       |
| Wersja | 4.6.2       |
| Typ    | Przekierowanie |

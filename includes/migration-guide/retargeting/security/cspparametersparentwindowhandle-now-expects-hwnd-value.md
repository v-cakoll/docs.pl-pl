---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235531"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle oczekuje teraz wartości HWND

|   |   |
|---|---|
|Szczegóły|Wartość, <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> wprowadzona w programie .NET Framework 2.0, umożliwia aplikacji zarejestrowanie wartości dojścia okna nadrzędnego w taki sposób, że dowolny interfejs użytkownika wymagany do uzyskania dostępu do klucza (na przykład monit o numer PIN lub okno zgody) zostanie otwarty jako podrzędny modalny do określonego okna. Począwszy od aplikacji docelowych .NET Framework 4.7, <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> aplikacja Windows Forms można ustawić właściwość z kodem, jak poniżej:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>W poprzednich wersjach programu .NET Framework oczekiwano, że wartość będzie reprezentująca <xref:System.IntPtr?displayProperty=name> lokalizację w pamięci, w której znajdowała się wartość [HWND.](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) Ustawienie właściwości do formularza. Uchwyt w systemie Windows 7 i wcześniejszych wersjach nie miał wpływu, &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>ale w systemie Windows 8 i nowszych wersjach powoduje: Parametr jest niepoprawny.&quot;|
|Sugestia|Aplikacje przeznaczone dla platformy .NET Framework 4.7 lub nowszej, które chcą zarejestrować relację okna nadrzędnego, są zachęcane do korzystania z formularza uproszczonego:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Użytkownicy, którzy zidentyfikowali, że poprawną wartością do przekazania był <code>form.Handle</code> adres lokalizacji pamięci, która posiadała wartość, mogą zrezygnować ze zmiany zachowania, ustawiając przełącznik <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> AppContext na: <code>true</code><ol><li>Poprzez programowe ustawienie przełączników compat na AppContext, jak wyjaśniono [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Z drugiej strony użytkownicy, którzy chcą wyrazić zgodę na nowe zachowanie w czasie wykonywania programu .NET Framework 4.7, gdy aplikacja ładuje się w starszych wersjach programu .NET Framework, mogą ustawić przełącznik AppContext na <code>false</code>.|
|Zakres|Mały|
|Wersja|4.7|
|Typ|Przekierowanie|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|

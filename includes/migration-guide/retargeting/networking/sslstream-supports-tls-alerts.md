---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614759"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream obsługuje alerty protokołu TLS

#### <a name="details"></a>Szczegóły

Po niepomyślnym uzgadnianiu protokołu TLS <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> zostanie wygenerowany wyjątek wewnętrzny z wyjątkiem operacji odczytu/zapisu w pierwszej kolejności. <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>Kod dla programu <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> można zamapować na alert protokołu TLS ze strony zdalnej przy użyciu [kodów błędów Schannel dla alertów protokołu TLS i SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Aby uzyskać więcej informacji, zobacz artykuł [RFC 2246: sekcja 7.2.2 alerty błędów](https://tools.ietf.org/html/rfc2246#section-7.2.2). <br/>Zachowanie w .NET Framework 4.6.2 i wcześniejszym polega na tym, że kanał transportu (zazwyczaj połączenie TCP) będzie przekroczyć limit czasu podczas zapisu lub odczytu, jeśli druga strona nie powiodła się, a następnie natychmiast odrzuci połączenie.

#### <a name="suggestion"></a>Sugestia

Aplikacje wywołujące interfejsy API we/wy sieci, takie jak <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> powinny obsługiwać <xref:System.IO.IOException> lub <xref:System.TimeoutException?displayProperty=fullName> .<br/>Funkcja alertów protokołu TLS jest domyślnie włączona począwszy od .NET Framework 4,7. Aplikacje ukierunkowane na wersje .NET Framework od 4,0 do 4.6.2 uruchomione w systemie .NET Framework 4,7 lub nowszym będą mieć tę funkcję, aby zachować zgodność. <br/>Następujący interfejs API konfiguracji jest dostępny do włączenia lub wyłączenia funkcji dla .NET Framework 4,6 i nowszych aplikacji uruchomionych na .NET Framework 4,7 lub nowszym.

- Programowe: musi być pierwszym zadaniem aplikacji, ponieważ ServicePointManager zostanie zainicjowana tylko raz:

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- AppConfig

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- Klucz rejestru (globalna maszyna): Ustaw wartość, aby `false` włączyć funkcję w .NET Framework 4,6-4.6.2.

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4,7         |
| Typ    | Przekierowanie |

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>

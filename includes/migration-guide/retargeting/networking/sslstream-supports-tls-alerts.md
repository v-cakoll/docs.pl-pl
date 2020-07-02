---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614759"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="15b3a-101">SslStream obsługuje alerty protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="15b3a-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="15b3a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="15b3a-102">Details</span></span>

<span data-ttu-id="15b3a-103">Po niepomyślnym uzgadnianiu protokołu TLS <xref:System.IO.IOException?displayProperty=fullName> <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> zostanie wygenerowany wyjątek wewnętrzny z wyjątkiem operacji odczytu/zapisu w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="15b3a-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="15b3a-104"><xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName>Kod dla programu <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> można zamapować na alert protokołu TLS ze strony zdalnej przy użyciu [kodów błędów Schannel dla alertów protokołu TLS i SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Aby uzyskać więcej informacji, zobacz artykuł [RFC 2246: sekcja 7.2.2 alerty błędów](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span><span class="sxs-lookup"><span data-stu-id="15b3a-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="15b3a-105">Zachowanie w .NET Framework 4.6.2 i wcześniejszym polega na tym, że kanał transportu (zazwyczaj połączenie TCP) będzie przekroczyć limit czasu podczas zapisu lub odczytu, jeśli druga strona nie powiodła się, a następnie natychmiast odrzuci połączenie.</span><span class="sxs-lookup"><span data-stu-id="15b3a-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="15b3a-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="15b3a-106">Suggestion</span></span>

<span data-ttu-id="15b3a-107">Aplikacje wywołujące interfejsy API we/wy sieci, takie jak <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)> / <xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> powinny obsługiwać <xref:System.IO.IOException> lub <xref:System.TimeoutException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="15b3a-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="15b3a-108">Funkcja alertów protokołu TLS jest domyślnie włączona począwszy od .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="15b3a-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="15b3a-109">Aplikacje ukierunkowane na wersje .NET Framework od 4,0 do 4.6.2 uruchomione w systemie .NET Framework 4,7 lub nowszym będą mieć tę funkcję, aby zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="15b3a-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="15b3a-110">Następujący interfejs API konfiguracji jest dostępny do włączenia lub wyłączenia funkcji dla .NET Framework 4,6 i nowszych aplikacji uruchomionych na .NET Framework 4,7 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="15b3a-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="15b3a-111">Programowe: musi być pierwszym zadaniem aplikacji, ponieważ ServicePointManager zostanie zainicjowana tylko raz:</span><span class="sxs-lookup"><span data-stu-id="15b3a-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="15b3a-112">AppConfig</span><span class="sxs-lookup"><span data-stu-id="15b3a-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="15b3a-113">Klucz rejestru (globalna maszyna): Ustaw wartość, aby `false` włączyć funkcję w .NET Framework 4,6-4.6.2.</span><span class="sxs-lookup"><span data-stu-id="15b3a-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="15b3a-114">Nazwa</span><span class="sxs-lookup"><span data-stu-id="15b3a-114">Name</span></span>    | <span data-ttu-id="15b3a-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="15b3a-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="15b3a-116">Zakres</span><span class="sxs-lookup"><span data-stu-id="15b3a-116">Scope</span></span>   | <span data-ttu-id="15b3a-117">Brzeg</span><span class="sxs-lookup"><span data-stu-id="15b3a-117">Edge</span></span>        |
| <span data-ttu-id="15b3a-118">Wersja</span><span class="sxs-lookup"><span data-stu-id="15b3a-118">Version</span></span> | <span data-ttu-id="15b3a-119">4,7</span><span class="sxs-lookup"><span data-stu-id="15b3a-119">4.7</span></span>         |
| <span data-ttu-id="15b3a-120">Typ</span><span class="sxs-lookup"><span data-stu-id="15b3a-120">Type</span></span>    | <span data-ttu-id="15b3a-121">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="15b3a-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="15b3a-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="15b3a-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>

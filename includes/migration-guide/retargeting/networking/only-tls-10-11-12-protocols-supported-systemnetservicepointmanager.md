---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615697"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="0398c-101">Tylko protokoły TLS 1,0, 1,1 i 1,2 obsługiwane w systemie .NET. ServicePointManager i system .NET. Security. SslStream</span><span class="sxs-lookup"><span data-stu-id="0398c-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="0398c-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0398c-102">Details</span></span>

<span data-ttu-id="0398c-103">Począwszy od .NET Framework 4,6, <xref:System.Net.ServicePointManager> klasy i mogą <xref:System.Net.Security.SslStream> korzystać tylko z jednego z następujących trzech protokołów: TLS 1.0, TLS 1.1 lub TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="0398c-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="0398c-104">Protokół SSL 3.0 i szyfr RC4 nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0398c-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0398c-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0398c-105">Suggestion</span></span>

<span data-ttu-id="0398c-106">Zalecane jest, aby uaktualnić aplikację po stronie serwera do protokołu TLS 1.0, TLS 1.1 lub TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="0398c-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="0398c-107">Jeśli nie jest to możliwe, lub jeśli aplikacje klienckie są uszkodzone, <xref:System.AppContext?displayProperty=fullName> można użyć klasy, aby zrezygnować z tej funkcji na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="0398c-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="0398c-108">Przez programowe ustawianie przełączników zgodności w programie <xref:System.AppContext?displayProperty=fullName> , jak wyjaśniono [tutaj](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="0398c-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="0398c-109">Dodając następujący wiersz do `<runtime>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="0398c-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="0398c-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0398c-110">Name</span></span>    | <span data-ttu-id="0398c-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="0398c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0398c-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="0398c-112">Scope</span></span>   | <span data-ttu-id="0398c-113">Mały</span><span class="sxs-lookup"><span data-stu-id="0398c-113">Minor</span></span>       |
| <span data-ttu-id="0398c-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="0398c-114">Version</span></span> | <span data-ttu-id="0398c-115">4.6</span><span class="sxs-lookup"><span data-stu-id="0398c-115">4.6</span></span>         |
| <span data-ttu-id="0398c-116">Typ</span><span class="sxs-lookup"><span data-stu-id="0398c-116">Type</span></span>    | <span data-ttu-id="0398c-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="0398c-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0398c-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0398c-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>

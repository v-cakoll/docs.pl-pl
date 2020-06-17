---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803244"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="8525b-101">Kestrel: zmieniono domyślne wersje protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="8525b-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="8525b-102">Kestrel teraz używa domyślnych wersji protokołu TLS systemu zamiast ograniczenia połączeń z protokołami TLS 1,1 i TLS 1,2, takimi jak wcześniej.</span><span class="sxs-lookup"><span data-stu-id="8525b-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="8525b-103">Ta zmiana umożliwia:</span><span class="sxs-lookup"><span data-stu-id="8525b-103">This change allows:</span></span>

* <span data-ttu-id="8525b-104">Protokołu TLS 1,3, który ma być używany domyślnie w środowiskach, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="8525b-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="8525b-105">Protokół TLS 1,0 do użycia w niektórych środowiskach (na przykład system Windows Server 2016 domyślnie), co zazwyczaj [nie jest pożądane](/security/engineering/solving-tls1-problem).</span><span class="sxs-lookup"><span data-stu-id="8525b-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="8525b-106">Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).</span><span class="sxs-lookup"><span data-stu-id="8525b-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8525b-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8525b-107">Version introduced</span></span>

<span data-ttu-id="8525b-108">5,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="8525b-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8525b-109">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="8525b-109">Old behavior</span></span>

<span data-ttu-id="8525b-110">Kestrel wymaga, aby połączenia domyślnie używały protokołu TLS 1,1 lub TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="8525b-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8525b-111">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="8525b-111">New behavior</span></span>

<span data-ttu-id="8525b-112">Kestrel umożliwia systemowi operacyjnemu wybranie najlepszego protokołu do użycia i zablokowanie niezabezpieczonych protokołów.</span><span class="sxs-lookup"><span data-stu-id="8525b-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="8525b-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>teraz wartość domyślna to `SslProtocols.None` zamiast `SslProtocols.Tls12 | SslProtocols.Tls11` .</span><span class="sxs-lookup"><span data-stu-id="8525b-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8525b-114">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="8525b-114">Reason for change</span></span>

<span data-ttu-id="8525b-115">Wprowadzono zmiany w celu obsługi protokołu TLS 1,3 i przyszłych wersji protokołu TLS domyślnie, gdy staną się dostępne.</span><span class="sxs-lookup"><span data-stu-id="8525b-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8525b-116">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8525b-116">Recommended action</span></span>

<span data-ttu-id="8525b-117">Jeśli aplikacja nie ma określonego powodu, należy użyć nowych wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="8525b-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="8525b-118">Sprawdź, czy system jest skonfigurowany tak, aby zezwalał tylko na bezpieczne protokoły.</span><span class="sxs-lookup"><span data-stu-id="8525b-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="8525b-119">Aby wyłączyć starsze protokoły, wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="8525b-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="8525b-120">Wyłącz starsze protokoły, takie jak TLS 1,0, system-Wide z [instrukcjami systemu Windows](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span><span class="sxs-lookup"><span data-stu-id="8525b-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="8525b-121">Jest ona obecnie włączona domyślnie we wszystkich wersjach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8525b-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="8525b-122">Ręcznie wybierz protokoły, które mają być obsługiwane w kodzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8525b-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="8525b-123">Niestety, nie istnieje interfejs API do wykluczenia określonych protokołów.</span><span class="sxs-lookup"><span data-stu-id="8525b-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="8525b-124">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8525b-124">Category</span></span>

<span data-ttu-id="8525b-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8525b-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8525b-126">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8525b-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->

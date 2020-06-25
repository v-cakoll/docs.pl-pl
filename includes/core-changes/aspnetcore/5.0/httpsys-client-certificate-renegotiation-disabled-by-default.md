---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325252"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="6aa15-101">HttpSys: ponowne negocjowanie certyfikatu klienta jest wyłączone domyślnie</span><span class="sxs-lookup"><span data-stu-id="6aa15-101">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="6aa15-102">Opcja renegocjuj połączenie i Zażądaj certyfikatu klienta została domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="6aa15-102">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="6aa15-103">Aby zapoznać się z omówieniem, zobacz temat Issue [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="6aa15-103">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6aa15-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6aa15-104">Version introduced</span></span>

<span data-ttu-id="6aa15-105">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="6aa15-105">ASP.NET Core 5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6aa15-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="6aa15-106">Old behavior</span></span>

<span data-ttu-id="6aa15-107">Połączenie może zostać ponownie wynegocjowane w celu zażądania certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="6aa15-107">The connection can be renegotiated to request a client certificate.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6aa15-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="6aa15-108">New behavior</span></span>

<span data-ttu-id="6aa15-109">Certyfikaty klienta można żądać tylko podczas początkowego uzgadniania połączeń.</span><span class="sxs-lookup"><span data-stu-id="6aa15-109">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="6aa15-110">Aby uzyskać więcej informacji, zobacz żądanie ściągnięcia [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="6aa15-110">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6aa15-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="6aa15-111">Reason for change</span></span>

<span data-ttu-id="6aa15-112">Ponowna negocjacja spowodowała wiele problemów z wydajnością i zakleszczeniami.</span><span class="sxs-lookup"><span data-stu-id="6aa15-112">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="6aa15-113">Nie jest to również obsługiwane w przypadku protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="6aa15-113">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="6aa15-114">Aby uzyskać dodatkowy kontekst od momentu, gdy opcja kontrolowania tego zachowania została wprowadzona w ASP.NET Core 3,1, zobacz temat Issue [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="6aa15-114">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6aa15-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6aa15-115">Recommended action</span></span>

<span data-ttu-id="6aa15-116">Aplikacje, które wymagają certyfikatów klienta, powinny używać *netsh.exe* , aby ustawić `clientcertnegotiation` opcję na `enabled` .</span><span class="sxs-lookup"><span data-stu-id="6aa15-116">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="6aa15-117">Aby uzyskać więcej informacji, zobacz [polecenia netsh http](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="6aa15-117">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="6aa15-118">Jeśli chcesz, aby certyfikaty klienta były włączone tylko dla niektórych części aplikacji, zapoznaj się ze wskazówkami dotyczącymi [opcjonalnych certyfikatów klienta](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span><span class="sxs-lookup"><span data-stu-id="6aa15-118">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="6aa15-119">Jeśli potrzebujesz starego zachowania renegocjuj, ustaw `HttpSysOptions.ClientCertificateMethod` dla starej wartości `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="6aa15-119">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="6aa15-120">Nie jest to zalecane z powodów przedstawionych powyżej i w połączonych wskazówkach.</span><span class="sxs-lookup"><span data-stu-id="6aa15-120">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

#### <a name="category"></a><span data-ttu-id="6aa15-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6aa15-121">Category</span></span>

<span data-ttu-id="6aa15-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6aa15-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6aa15-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6aa15-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->

---
ms.openlocfilehash: a4e20e0468d861138ad801c9dbfa15340b3f388c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394282"
---
### <a name="authentication-oauthhandler-exchangecodeasync-signature-changed"></a><span data-ttu-id="7e7ae-101">Uwierzytelnianie: OAuthHandler ExchangeCodeAsync zmieniono sygnaturę</span><span class="sxs-lookup"><span data-stu-id="7e7ae-101">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>

<span data-ttu-id="7e7ae-102">W ASP.NET Core 3,0 sygnatura `OAuthHandler.ExchangeCodeAsync` została zmieniona z:</span><span class="sxs-lookup"><span data-stu-id="7e7ae-102">In ASP.NET Core 3.0, the signature of `OAuthHandler.ExchangeCodeAsync` was changed from:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(string code, string redirectUri) { throw null; }
```

<span data-ttu-id="7e7ae-103">Do:</span><span class="sxs-lookup"><span data-stu-id="7e7ae-103">To:</span></span>

```csharp
protected virtual System.Threading.Tasks.Task<Microsoft.AspNetCore.Authentication.OAuth.OAuthTokenResponse> ExchangeCodeAsync(Microsoft.AspNetCore.Authentication.OAuth.OAuthCodeExchangeContext context) { throw null; }
```

#### <a name="version-introduced"></a><span data-ttu-id="7e7ae-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7e7ae-104">Version introduced</span></span>

<span data-ttu-id="7e7ae-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7e7ae-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7e7ae-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="7e7ae-106">Old behavior</span></span>

<span data-ttu-id="7e7ae-107">Ciągi `code` i `redirectUri` zostały przekazane jako oddzielne argumenty.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-107">The `code` and `redirectUri` strings were passed as separate arguments.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7e7ae-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="7e7ae-108">New behavior</span></span>

<span data-ttu-id="7e7ae-109">`Code` i `RedirectUri` są właściwościami `OAuthCodeExchangeContext`, które można ustawić za pośrednictwem konstruktora `OAuthCodeExchangeContext`.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-109">`Code` and `RedirectUri` are properties on `OAuthCodeExchangeContext` that can be set via the `OAuthCodeExchangeContext` constructor.</span></span> <span data-ttu-id="7e7ae-110">Nowy typ `OAuthCodeExchangeContext` jest jedynym argumentem przekazaną do `OAuthHandler.ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-110">The new `OAuthCodeExchangeContext` type is the only argument passed to `OAuthHandler.ExchangeCodeAsync`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7e7ae-111">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="7e7ae-111">Reason for change</span></span>

<span data-ttu-id="7e7ae-112">Ta zmiana pozwala na dostarczenie dodatkowych parametrów w sposób rozdzielny.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-112">This change allows additional parameters to be provided in a non-breaking manner.</span></span> <span data-ttu-id="7e7ae-113">Nie ma potrzeby tworzenia nowych przeciążeń `ExchangeCodeAsync`.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-113">There's no need to create new `ExchangeCodeAsync` overloads.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7e7ae-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7e7ae-114">Recommended action</span></span>

<span data-ttu-id="7e7ae-115">Utwórz `OAuthCodeExchangeContext` z odpowiednimi wartościami `code` i `redirectUri`.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-115">Construct an `OAuthCodeExchangeContext` with the appropriate `code` and `redirectUri` values.</span></span> <span data-ttu-id="7e7ae-116">Należy podać wystąpienie <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties>.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-116">An <xref:Microsoft.AspNetCore.Authentication.AuthenticationProperties> instance must be provided.</span></span> <span data-ttu-id="7e7ae-117">To pojedyncze wystąpienie `OAuthCodeExchangeContext` może być przekazane do `OAuthHandler.ExchangeCodeAsync` zamiast wielu argumentów.</span><span class="sxs-lookup"><span data-stu-id="7e7ae-117">This single `OAuthCodeExchangeContext` instance can be passed to `OAuthHandler.ExchangeCodeAsync` instead of multiple arguments.</span></span>

#### <a name="category"></a><span data-ttu-id="7e7ae-118">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7e7ae-118">Category</span></span>

<span data-ttu-id="7e7ae-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7e7ae-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7e7ae-120">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7e7ae-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler%601.ExchangeCodeAsync(System.String,System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Authentication.OAuth.OAuthHandler`1.ExchangeCodeAsync(System.String,System.String)`

-->
---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394230"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="d31b4-101">Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości</span><span class="sxs-lookup"><span data-stu-id="d31b4-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="d31b4-102">Domyślnie program `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest. `false`</span><span class="sxs-lookup"><span data-stu-id="d31b4-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d31b4-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d31b4-103">Version introduced</span></span>

<span data-ttu-id="d31b4-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d31b4-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d31b4-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="d31b4-105">Old behavior</span></span>

<span data-ttu-id="d31b4-106">`SignInAsync`akceptuje wszelkie podmioty zabezpieczeń/tożsamości, w tym tożsamości, `IsAuthenticated` w `false`których jest.</span><span class="sxs-lookup"><span data-stu-id="d31b4-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d31b4-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="d31b4-107">New behavior</span></span>

<span data-ttu-id="d31b4-108">Domyślnie program `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest. `false`</span><span class="sxs-lookup"><span data-stu-id="d31b4-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="d31b4-109">Istnieje nowa flaga, która pozwala pominąć to zachowanie, ale zachowanie domyślne zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="d31b4-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d31b4-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="d31b4-110">Reason for change</span></span>

<span data-ttu-id="d31b4-111">Stare zachowanie było przyczyną problemów, ponieważ domyślnie te podmioty zabezpieczeń zostały odrzucone przez `[Authorize]`  /  `RequireAuthenticatedUser()`.</span><span class="sxs-lookup"><span data-stu-id="d31b4-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d31b4-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d31b4-112">Recommended action</span></span>

<span data-ttu-id="d31b4-113">W ASP.NET Core 3,0 w wersji zapoznawczej 6 `RequireAuthenticatedSignIn` znajduje się `AuthenticationOptions` flaga, `true` która jest domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d31b4-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="d31b4-114">Ustaw tę flagę `false` na, aby przywrócić stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d31b4-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="d31b4-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d31b4-115">Category</span></span>

<span data-ttu-id="d31b4-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d31b4-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d31b4-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d31b4-117">Affected APIs</span></span>

<span data-ttu-id="d31b4-118">Brak</span><span class="sxs-lookup"><span data-stu-id="d31b4-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

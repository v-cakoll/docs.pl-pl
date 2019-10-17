---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394230"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a><span data-ttu-id="21e78-101">Tożsamość: SignInAsync zgłasza wyjątek dla nieuwierzytelnionej tożsamości</span><span class="sxs-lookup"><span data-stu-id="21e78-101">Identity: SignInAsync throws exception for unauthenticated identity</span></span>

<span data-ttu-id="21e78-102">Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="21e78-102">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="21e78-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="21e78-103">Version introduced</span></span>

<span data-ttu-id="21e78-104">3.0</span><span class="sxs-lookup"><span data-stu-id="21e78-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="21e78-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="21e78-105">Old behavior</span></span>

<span data-ttu-id="21e78-106">`SignInAsync` akceptuje wszelkie podmioty zabezpieczeń/tożsamości, w tym tożsamości, w których `IsAuthenticated` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="21e78-106">`SignInAsync` accepts any principals / identities, including identities in which `IsAuthenticated` is `false`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="21e78-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="21e78-107">New behavior</span></span>

<span data-ttu-id="21e78-108">Domyślnie `SignInAsync` zgłasza wyjątek dla podmiotów zabezpieczeń/tożsamości, w których `IsAuthenticated` jest `false`.</span><span class="sxs-lookup"><span data-stu-id="21e78-108">By default, `SignInAsync` throws an exception for principals / identities in which `IsAuthenticated` is `false`.</span></span> <span data-ttu-id="21e78-109">Istnieje nowa flaga, która pozwala pominąć to zachowanie, ale zachowanie domyślne zostało zmienione.</span><span class="sxs-lookup"><span data-stu-id="21e78-109">There's a new flag to suppress this behavior, but the default behavior has changed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="21e78-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="21e78-110">Reason for change</span></span>

<span data-ttu-id="21e78-111">Stare zachowanie było przyczyną problemów, ponieważ domyślnie te podmioty zabezpieczeń zostały odrzucone przez `[Authorize]` @ no__t-1 @ no__t-2.</span><span class="sxs-lookup"><span data-stu-id="21e78-111">The old behavior was problematic because, by default, these principals were rejected by `[Authorize]` / `RequireAuthenticatedUser()`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="21e78-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="21e78-112">Recommended action</span></span>

<span data-ttu-id="21e78-113">W ASP.NET Core 3,0 w wersji zapoznawczej 6 istnieje flaga `RequireAuthenticatedSignIn` w `AuthenticationOptions`, która domyślnie jest `true`.</span><span class="sxs-lookup"><span data-stu-id="21e78-113">In ASP.NET Core 3.0 Preview 6, there's a `RequireAuthenticatedSignIn` flag on `AuthenticationOptions` that is `true` by default.</span></span> <span data-ttu-id="21e78-114">Ustaw tę flagę na `false`, aby przywrócić stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="21e78-114">Set this flag to `false` to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="21e78-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="21e78-115">Category</span></span>

<span data-ttu-id="21e78-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="21e78-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21e78-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="21e78-117">Affected APIs</span></span>

<span data-ttu-id="21e78-118">Brak</span><span class="sxs-lookup"><span data-stu-id="21e78-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

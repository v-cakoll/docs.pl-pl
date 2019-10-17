---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393922"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="7d2c2-101">Autoryzacja: Przeciążenie metody addauthorization przeniesiono do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="7d2c2-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="7d2c2-102">Nazwy podstawowych metod `AddAuthorization`, które były używane do znajdowania w `Microsoft.AspNetCore.Authorization`, zostały zmienione na `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="7d2c2-103">Nadal istnieją stare metody `AddAuthorization`, ale w pakiecie `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` package instead.</span></span> <span data-ttu-id="7d2c2-104">Aplikacje korzystające z obu tych metod powinny nie mieć wpływu.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="7d2c2-105">Aplikacje, które nie korzystały z pakietu zasad, muszą przełączać się do korzystania z `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-105">Apps that weren't using the policy package must switch to using `AddAuthorizationCore`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7d2c2-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7d2c2-106">Version introduced</span></span>

<span data-ttu-id="7d2c2-107">3.0</span><span class="sxs-lookup"><span data-stu-id="7d2c2-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7d2c2-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="7d2c2-108">Old behavior</span></span>

<span data-ttu-id="7d2c2-109">Metody `AddAuthorization` istniały w `Microsoft.AspNetCore.Authorization`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="7d2c2-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="7d2c2-110">New behavior</span></span>

<span data-ttu-id="7d2c2-111">Metody `AddAuthorization` istnieją w `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="7d2c2-112">`AddAuthorizationCore` to nowa nazwa dla starych metod.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7d2c2-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="7d2c2-113">Reason for change</span></span>

<span data-ttu-id="7d2c2-114">`AddAuthorization` to lepsza nazwa metody do dodawania wszystkich typowych usług wymaganych do autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7d2c2-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7d2c2-115">Recommended action</span></span>

<span data-ttu-id="7d2c2-116">Dodaj odwołanie do `Microsoft.AspNetCore.Authorization.Policy` lub użyj `AddAuthorizationCore`.</span><span class="sxs-lookup"><span data-stu-id="7d2c2-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="7d2c2-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7d2c2-117">Category</span></span>

<span data-ttu-id="7d2c2-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7d2c2-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7d2c2-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7d2c2-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->

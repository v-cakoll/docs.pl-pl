---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74101294"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a><span data-ttu-id="21f10-101">Autoryzacja: Przeciążenie metody addauthorization przeniesiono do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="21f10-101">Authorization: AddAuthorization overload moved to different assembly</span></span>

<span data-ttu-id="21f10-102">Nazwy podstawowych `AddAuthorization` metod, które były używane do znajdowania w `Microsoft.AspNetCore.Authorization` programie `AddAuthorizationCore`, zostały zmienione na.</span><span class="sxs-lookup"><span data-stu-id="21f10-102">The core `AddAuthorization` methods that used to reside in `Microsoft.AspNetCore.Authorization` were renamed to `AddAuthorizationCore`.</span></span> <span data-ttu-id="21f10-103">Stare `AddAuthorization` metody nadal istnieją, ale znajdują się w `Microsoft.AspNetCore.Authorization.Policy` zestawie.</span><span class="sxs-lookup"><span data-stu-id="21f10-103">The old `AddAuthorization` methods still exist, but are in the `Microsoft.AspNetCore.Authorization.Policy` assembly instead.</span></span> <span data-ttu-id="21f10-104">Aplikacje korzystające z obu tych metod powinny nie mieć wpływu.</span><span class="sxs-lookup"><span data-stu-id="21f10-104">Apps using both methods should see no impact.</span></span> <span data-ttu-id="21f10-105">Należy pamiętać `Microsoft.AspNetCore.Authorization.Policy` , że teraz jest dostarczany w ramach udostępnionej platformy, a nie jako pakiet autonomiczny, zgodnie z opisem w sekcji [Shared Framework: zestawy usunięte z Microsoft. AspNetCore. app](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span><span class="sxs-lookup"><span data-stu-id="21f10-105">Note that `Microsoft.AspNetCore.Authorization.Policy` now ships in the shared framework rather than a standalone package as discussed in [Shared framework: Assemblies removed from Microsoft.AspNetCore.App](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="21f10-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="21f10-106">Version introduced</span></span>

<span data-ttu-id="21f10-107">3.0</span><span class="sxs-lookup"><span data-stu-id="21f10-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="21f10-108">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="21f10-108">Old behavior</span></span>
<span data-ttu-id="21f10-109">`AddAuthorization`Metody istniały w `Microsoft.AspNetCore.Authorization`.</span><span class="sxs-lookup"><span data-stu-id="21f10-109">`AddAuthorization` methods existed in `Microsoft.AspNetCore.Authorization`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="21f10-110">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="21f10-110">New behavior</span></span>

<span data-ttu-id="21f10-111">`AddAuthorization`Metody istnieją w `Microsoft.AspNetCore.Authorization.Policy`.</span><span class="sxs-lookup"><span data-stu-id="21f10-111">`AddAuthorization` methods exist in `Microsoft.AspNetCore.Authorization.Policy`.</span></span> <span data-ttu-id="21f10-112">`AddAuthorizationCore`jest nową nazwą dla starych metod.</span><span class="sxs-lookup"><span data-stu-id="21f10-112">`AddAuthorizationCore` is the new name for the old methods.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="21f10-113">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="21f10-113">Reason for change</span></span>

<span data-ttu-id="21f10-114">`AddAuthorization`jest lepszą nazwą metody dodawania wszystkich typowych usług wymaganych do autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="21f10-114">`AddAuthorization` is a better method name for adding all common services needed for authorization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="21f10-115">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="21f10-115">Recommended action</span></span>

<span data-ttu-id="21f10-116">Dodaj odwołanie do `Microsoft.AspNetCore.Authorization.Policy` lub Użyj `AddAuthorizationCore` zamiast niego.</span><span class="sxs-lookup"><span data-stu-id="21f10-116">Either add a reference to `Microsoft.AspNetCore.Authorization.Policy` or use `AddAuthorizationCore` instead.</span></span>

#### <a name="category"></a><span data-ttu-id="21f10-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="21f10-117">Category</span></span>

<span data-ttu-id="21f10-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="21f10-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21f10-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="21f10-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->

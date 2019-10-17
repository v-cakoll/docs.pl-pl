---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394063"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="15911-101">Tożsamość: Konstruktor SignInManager akceptuje nowy parametr</span><span class="sxs-lookup"><span data-stu-id="15911-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="15911-102">Począwszy od ASP.NET Core 3,0, dodano nowy parametr `IUserConfirmation<TUser>` do konstruktora `SignInManager`.</span><span class="sxs-lookup"><span data-stu-id="15911-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="15911-103">Aby uzyskać więcej informacji, zobacz [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="15911-103">For more information, see [aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="15911-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="15911-104">Version introduced</span></span>

<span data-ttu-id="15911-105">3.0</span><span class="sxs-lookup"><span data-stu-id="15911-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="15911-106">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="15911-106">Reason for change</span></span>

<span data-ttu-id="15911-107">Celem zmiany było dodanie obsługi nowych przepływów poczty e-mail/potwierdzenia w tożsamości.</span><span class="sxs-lookup"><span data-stu-id="15911-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="15911-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="15911-108">Recommended action</span></span>

<span data-ttu-id="15911-109">W przypadku ręcznego konstruowania `SignInManager` wprowadź implementację `IUserConfirmation` lub Przechwyć jeden z iniekcji zależności, aby zapewnić.</span><span class="sxs-lookup"><span data-stu-id="15911-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="15911-110">Kategoria</span><span class="sxs-lookup"><span data-stu-id="15911-110">Category</span></span>

<span data-ttu-id="15911-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="15911-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="15911-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="15911-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->

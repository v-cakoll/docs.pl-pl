---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901712"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="74403-101">Tożsamość: Konstruktor SignInManager akceptuje nowy parametr</span><span class="sxs-lookup"><span data-stu-id="74403-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="74403-102">Począwszy od ASP.NET Core 3.0, `IUserConfirmation<TUser>` nowy `SignInManager` parametr został dodany do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="74403-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="74403-103">Aby uzyskać więcej informacji, zobacz [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="74403-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="74403-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="74403-104">Version introduced</span></span>

<span data-ttu-id="74403-105">3.0</span><span class="sxs-lookup"><span data-stu-id="74403-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="74403-106">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="74403-106">Reason for change</span></span>

<span data-ttu-id="74403-107">Motywacją do zmiany było dodanie obsługi nowych przepływów e-mail / potwierdzenie w tożsamości.</span><span class="sxs-lookup"><span data-stu-id="74403-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74403-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="74403-108">Recommended action</span></span>

<span data-ttu-id="74403-109">Jeśli ręcznie konstruowanie `SignInManager`, należy `IUserConfirmation` podać implementację lub pobrać jeden z iniekcji zależności, aby zapewnić.</span><span class="sxs-lookup"><span data-stu-id="74403-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="74403-110">Kategoria</span><span class="sxs-lookup"><span data-stu-id="74403-110">Category</span></span>

<span data-ttu-id="74403-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="74403-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74403-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="74403-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->

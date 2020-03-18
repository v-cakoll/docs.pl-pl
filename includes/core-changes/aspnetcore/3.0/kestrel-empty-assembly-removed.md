---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394240"
---
### <a name="kestrel-empty-https-assembly-removed"></a><span data-ttu-id="3445c-101">Pusstrel: Usunięto pusty zespół HTTPS</span><span class="sxs-lookup"><span data-stu-id="3445c-101">Kestrel: Empty HTTPS assembly removed</span></span>

<span data-ttu-id="3445c-102">Zespół <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> został usunięty.</span><span class="sxs-lookup"><span data-stu-id="3445c-102">The assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> has been removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3445c-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3445c-103">Version introduced</span></span>

<span data-ttu-id="3445c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3445c-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3445c-105">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="3445c-105">Reason for change</span></span>

<span data-ttu-id="3445c-106">W ASP.NET Core 2.1 zawartość `Microsoft.AspNetCore.Server.Kestrel.Https` została <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>przeniesiona do .</span><span class="sxs-lookup"><span data-stu-id="3445c-106">In ASP.NET Core 2.1, the contents of `Microsoft.AspNetCore.Server.Kestrel.Https` were moved to <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>.</span></span> <span data-ttu-id="3445c-107">Ta zmiana została wykonana w sposób `[TypeForwardedTo]` nieprzerywany przy użyciu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3445c-107">This change was done in a non-breaking way using `[TypeForwardedTo]` attributes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3445c-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="3445c-108">Recommended action</span></span>

- <span data-ttu-id="3445c-109">Biblioteki odwołujące `Microsoft.AspNetCore.Server.Kestrel.Https` się do wersji 2.0 powinny zaktualizować wszystkie ASP.NET zależności rdzenia do wersji 2.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="3445c-109">Libraries referencing `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 should update all ASP.NET Core dependencies to 2.1 or later.</span></span> <span data-ttu-id="3445c-110">W przeciwnym razie mogą się zepsuć po załadowaniu do ASP.NET aplikacji Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="3445c-110">Otherwise, they may break when loaded into an ASP.NET Core 3.0 app.</span></span>
- <span data-ttu-id="3445c-111">Aplikacje i biblioteki przeznaczone ASP.NET Core 2.1 i `Microsoft.AspNetCore.Server.Kestrel.Https` nowszej powinny usunąć wszelkie bezpośrednie odwołania do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="3445c-111">Apps and libraries targeting ASP.NET Core 2.1 and later should remove any direct references to the `Microsoft.AspNetCore.Server.Kestrel.Https` NuGet package.</span></span>

#### <a name="category"></a><span data-ttu-id="3445c-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3445c-112">Category</span></span>

<span data-ttu-id="3445c-113">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3445c-113">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3445c-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3445c-114">Affected APIs</span></span>

<span data-ttu-id="3445c-115">Brak</span><span class="sxs-lookup"><span data-stu-id="3445c-115">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

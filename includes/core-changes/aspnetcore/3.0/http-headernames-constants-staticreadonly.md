---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902006"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="b5e7c-101">HTTP: stałe HeaderNames zmienione do statycznego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b5e7c-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="b5e7c-102">Począwszy od ASP.NET Core 3,0 wersja zapoznawcza 5, pola w <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> zmienione z `const` na `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="b5e7c-103">Aby zapoznać się z omówieniem, zobacz [dotnet/aspnetcore # 9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="b5e7c-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b5e7c-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="b5e7c-104">Version introduced</span></span>

<span data-ttu-id="b5e7c-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b5e7c-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b5e7c-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="b5e7c-106">Old behavior</span></span>

<span data-ttu-id="b5e7c-107">Te pola używane do `const`.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b5e7c-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="b5e7c-108">New behavior</span></span>

<span data-ttu-id="b5e7c-109">Te pola są teraz `static readonly`.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b5e7c-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="b5e7c-110">Reason for change</span></span>

<span data-ttu-id="b5e7c-111">Zmiana:</span><span class="sxs-lookup"><span data-stu-id="b5e7c-111">The change:</span></span>

* <span data-ttu-id="b5e7c-112">Zapobiega osadzaniu wartości między granicami zestawów, umożliwiając korektę wartości zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="b5e7c-113">Umożliwia szybsze sprawdzanie równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b5e7c-114">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="b5e7c-114">Recommended action</span></span>

<span data-ttu-id="b5e7c-115">Kompiluj ponownie z 3,0.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-115">Recompile against 3.0.</span></span> <span data-ttu-id="b5e7c-116">Kod źródłowy korzystający z tych pól w następujących sposobach nie może już być taki:</span><span class="sxs-lookup"><span data-stu-id="b5e7c-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="b5e7c-117">Jako argument atrybutu</span><span class="sxs-lookup"><span data-stu-id="b5e7c-117">As an attribute argument</span></span>
* <span data-ttu-id="b5e7c-118">Jako `case` w instrukcji `switch`</span><span class="sxs-lookup"><span data-stu-id="b5e7c-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="b5e7c-119">Podczas definiowania innego `const`</span><span class="sxs-lookup"><span data-stu-id="b5e7c-119">When defining another `const`</span></span>

<span data-ttu-id="b5e7c-120">Aby obejść istotną zmianę, należy przełączyć się do użycia samodzielnych stałych nazw nagłówka lub literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="b5e7c-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="b5e7c-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b5e7c-121">Category</span></span>

<span data-ttu-id="b5e7c-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b5e7c-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b5e7c-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b5e7c-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->

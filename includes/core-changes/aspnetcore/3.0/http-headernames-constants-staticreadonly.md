---
ms.openlocfilehash: 31e7f84a787d255a474f4c2b1fa3068903dbed52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902006"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a><span data-ttu-id="4eef8-101">HTTP: NagłówkiNames stałych zmienionych na statyczne tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4eef8-101">HTTP: HeaderNames constants changed to static readonly</span></span>

<span data-ttu-id="4eef8-102">Począwszy od wersji ASP.NET Core 3.0 `const` Preview `static readonly`5, pola w zmienionym <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> stosunku do .</span><span class="sxs-lookup"><span data-stu-id="4eef8-102">Starting in ASP.NET Core 3.0 Preview 5, the fields in <xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> changed from `const` to `static readonly`.</span></span>

<span data-ttu-id="4eef8-103">Aby uzyskać do dyskusji, zobacz [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span><span class="sxs-lookup"><span data-stu-id="4eef8-103">For discussion, see [dotnet/aspnetcore#9514](https://github.com/dotnet/aspnetcore/issues/9514).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4eef8-104">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4eef8-104">Version introduced</span></span>

<span data-ttu-id="4eef8-105">3.0</span><span class="sxs-lookup"><span data-stu-id="4eef8-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="4eef8-106">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="4eef8-106">Old behavior</span></span>

<span data-ttu-id="4eef8-107">Pola te były `const`kiedyś .</span><span class="sxs-lookup"><span data-stu-id="4eef8-107">These fields used to be `const`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="4eef8-108">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="4eef8-108">New behavior</span></span>

<span data-ttu-id="4eef8-109">Te pola `static readonly`są teraz .</span><span class="sxs-lookup"><span data-stu-id="4eef8-109">These fields are now `static readonly`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4eef8-110">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="4eef8-110">Reason for change</span></span>

<span data-ttu-id="4eef8-111">Zmiana:</span><span class="sxs-lookup"><span data-stu-id="4eef8-111">The change:</span></span>

* <span data-ttu-id="4eef8-112">Zapobiega osadzaniu wartości przez granice złożenia, co pozwala na korekty wartości zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="4eef8-112">Prevents the values from being embedded across assembly boundaries, allowing for value corrections as needed.</span></span>
* <span data-ttu-id="4eef8-113">Umożliwia szybsze sprawdzanie równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="4eef8-113">Enables faster reference equality checks.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4eef8-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4eef8-114">Recommended action</span></span>

<span data-ttu-id="4eef8-115">Ponownie skompilować przeciwko 3.0.</span><span class="sxs-lookup"><span data-stu-id="4eef8-115">Recompile against 3.0.</span></span> <span data-ttu-id="4eef8-116">Kod źródłowy używający tych pól w następujący sposób nie może już tego zrobić:</span><span class="sxs-lookup"><span data-stu-id="4eef8-116">Source code using these fields in the following ways can no longer do so:</span></span>

* <span data-ttu-id="4eef8-117">Jako argument atrybutu</span><span class="sxs-lookup"><span data-stu-id="4eef8-117">As an attribute argument</span></span>
* <span data-ttu-id="4eef8-118">Jako `case` w `switch` oświadczeniu</span><span class="sxs-lookup"><span data-stu-id="4eef8-118">As a `case` in a `switch` statement</span></span>
* <span data-ttu-id="4eef8-119">Przy definiowaniu innego`const`</span><span class="sxs-lookup"><span data-stu-id="4eef8-119">When defining another `const`</span></span>

<span data-ttu-id="4eef8-120">Aby obejść zmianę podziału, przełącz się na używanie samodzielnie zdefiniowanych stałych nazw nagłówka lub literałów ciągów.</span><span class="sxs-lookup"><span data-stu-id="4eef8-120">To work around the breaking change, switch to using self-defined header name constants or string literals.</span></span>

#### <a name="category"></a><span data-ttu-id="4eef8-121">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4eef8-121">Category</span></span>

<span data-ttu-id="4eef8-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4eef8-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4eef8-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4eef8-123">Affected APIs</span></span>

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->

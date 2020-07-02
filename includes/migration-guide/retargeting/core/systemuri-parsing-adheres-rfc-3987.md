---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617210"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="ca903-101">Analizowanie elementu System. URI jest zgodne ze specyfikacją RFC 3987</span><span class="sxs-lookup"><span data-stu-id="ca903-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="ca903-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="ca903-102">Details</span></span>

<span data-ttu-id="ca903-103">Analiza identyfikatorów URI została zmieniona na kilka sposobów w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ca903-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="ca903-104">Należy jednak pamiętać, że te zmiany mają wpływ tylko na kod docelowy .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="ca903-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="ca903-105">W przypadku elementów binarnych .NET Framework 4,0 zostanie zaobserwowane stare zachowanie.</span><span class="sxs-lookup"><span data-stu-id="ca903-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="ca903-106">Zmiany w analizie identyfikatora URI w .NET Framework 4,5 obejmują:</span><span class="sxs-lookup"><span data-stu-id="ca903-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="ca903-107">Analiza identyfikatora URI będzie wykonywała normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="ca903-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="ca903-108">Formularz normalizacji Unicode C zostanie wykonany tylko na części hosta identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="ca903-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="ca903-109">Nieprawidłowe identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="ca903-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="ca903-110">Końcowe kropki na końcu segmentu ścieżki są teraz zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ca903-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="ca903-111">`file://`Identyfikatory URI nie mają znaku ucieczki `?` .</span><span class="sxs-lookup"><span data-stu-id="ca903-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="ca903-112">Znaki kontrolne `U+0080` Unicode `U+009F` nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ca903-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="ca903-113">Znaki przecinki `,` lub `%2c` nie są automatycznie wyprowadzane.</span><span class="sxs-lookup"><span data-stu-id="ca903-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca903-114">Sugestia</span><span class="sxs-lookup"><span data-stu-id="ca903-114">Suggestion</span></span>

<span data-ttu-id="ca903-115">Jeśli stara składnia analizowania składni identyfikatorów URI .NET Framework 4,0 jest niezbędna (często nie są), mogą one być używane przez kierowanie .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="ca903-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="ca903-116">Można to osiągnąć przy użyciu <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> na zestawie lub za pośrednictwem interfejsu użytkownika systemu projektu programu Visual Studio na stronie właściwości projektu.</span><span class="sxs-lookup"><span data-stu-id="ca903-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="ca903-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ca903-117">Name</span></span>    | <span data-ttu-id="ca903-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="ca903-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca903-119">Zakres</span><span class="sxs-lookup"><span data-stu-id="ca903-119">Scope</span></span>   | <span data-ttu-id="ca903-120">Duży</span><span class="sxs-lookup"><span data-stu-id="ca903-120">Major</span></span>       |
| <span data-ttu-id="ca903-121">Wersja</span><span class="sxs-lookup"><span data-stu-id="ca903-121">Version</span></span> | <span data-ttu-id="ca903-122">4.5</span><span class="sxs-lookup"><span data-stu-id="ca903-122">4.5</span></span>         |
| <span data-ttu-id="ca903-123">Typ</span><span class="sxs-lookup"><span data-stu-id="ca903-123">Type</span></span>    | <span data-ttu-id="ca903-124">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="ca903-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="ca903-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ca903-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>

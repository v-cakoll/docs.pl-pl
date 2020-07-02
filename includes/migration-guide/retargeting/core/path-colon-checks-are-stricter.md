---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614718"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="49091-101">Sprawdzanie dwukropek ścieżki jest bardziej rygorystyczne</span><span class="sxs-lookup"><span data-stu-id="49091-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="49091-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="49091-102">Details</span></span>

<span data-ttu-id="49091-103">W .NET Framework 4.6.2 wprowadzono wiele zmian do obsługi wcześniej nieobsługiwanych ścieżek (zarówno w formacie długości, jak i formatu).</span><span class="sxs-lookup"><span data-stu-id="49091-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="49091-104">Sprawdza, czy składnia separatora dysku (dwukropek) była bardziej poprawna, co spowodowało zablokowanie niektórych ścieżek identyfikatorów URI w kilku interfejsach API do wybierania ścieżek, gdzie są one używane do tolerowania.</span><span class="sxs-lookup"><span data-stu-id="49091-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="49091-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="49091-105">Suggestion</span></span>

<span data-ttu-id="49091-106">W przypadku przekazywania identyfikatora URI do odpowiednich interfejsów API należy najpierw zmodyfikować ciąg tak, aby był on ścieżką prawną.</span><span class="sxs-lookup"><span data-stu-id="49091-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="49091-107">Ręcznie usuń schemat z adresów URL (np. Usuń `file://` z adresów URL)</span><span class="sxs-lookup"><span data-stu-id="49091-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="49091-108">Przekaż identyfikator URI do <xref:System.Uri> klasy i Użyj<xref:System.Uri.LocalPath></span><span class="sxs-lookup"><span data-stu-id="49091-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="49091-109">Alternatywnie można zrezygnować z nowej normalizacji ścieżki, ustawiając `Switch.System.IO.UseLegacyPathHandling` przełącznik AppContext na true.</span><span class="sxs-lookup"><span data-stu-id="49091-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="49091-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="49091-110">Name</span></span>    | <span data-ttu-id="49091-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="49091-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="49091-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="49091-112">Scope</span></span>   | <span data-ttu-id="49091-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="49091-113">Edge</span></span>        |
| <span data-ttu-id="49091-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="49091-114">Version</span></span> | <span data-ttu-id="49091-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="49091-115">4.6.2</span></span>       |
| <span data-ttu-id="49091-116">Typ</span><span class="sxs-lookup"><span data-stu-id="49091-116">Type</span></span>    | <span data-ttu-id="49091-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="49091-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="49091-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="49091-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>

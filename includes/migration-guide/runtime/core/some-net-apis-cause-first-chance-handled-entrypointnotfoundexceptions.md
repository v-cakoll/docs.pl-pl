---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622139"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a><span data-ttu-id="cea29-101">Niektóre interfejsy API platformy .NET powodują wystąpienie pierwszej szansy (obsłużone) EntryPointNotFoundExceptions</span><span class="sxs-lookup"><span data-stu-id="cea29-101">Some .NET APIs cause first chance (handled) EntryPointNotFoundExceptions</span></span>

#### <a name="details"></a><span data-ttu-id="cea29-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="cea29-102">Details</span></span>

<span data-ttu-id="cea29-103">W .NET Framework 4,5 niewielka liczba metod .NET rozpoczęła generowanie pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=fullName> s.</span><span class="sxs-lookup"><span data-stu-id="cea29-103">In the .NET Framework 4.5, a small number of .NET methods began throwing first chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span> <span data-ttu-id="cea29-104">Te wyjątki zostały obsłużone w .NET Framework, ale mogą przerwać automatyzację testu, która nie oczekiwała na wyjątki pierwszej szansy.</span><span class="sxs-lookup"><span data-stu-id="cea29-104">These exceptions were handled within the .NET Framework, but could break test automation that did not expect the first chance exceptions.</span></span> <span data-ttu-id="cea29-105">Te same interfejsy API przerywają niektóre scenariusze ApiVerifier, gdy HighVersionLie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="cea29-105">These same APIs break some ApiVerifier scenarios when HighVersionLie is enabled.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cea29-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="cea29-106">Suggestion</span></span>

<span data-ttu-id="cea29-107">Tę usterkę można uniknąć przez uaktualnienie do .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="cea29-107">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="cea29-108">Alternatywnie można zaktualizować automatyzację testową, aby nie przerywać pierwszej szansy <xref:System.EntryPointNotFoundException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="cea29-108">Alternatively, test automation can be updated to not break on first-chance <xref:System.EntryPointNotFoundException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="cea29-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cea29-109">Name</span></span>    | <span data-ttu-id="cea29-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="cea29-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cea29-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="cea29-111">Scope</span></span>   |<span data-ttu-id="cea29-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="cea29-112">Edge</span></span>|
|<span data-ttu-id="cea29-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="cea29-113">Version</span></span>|<span data-ttu-id="cea29-114">4.5</span><span class="sxs-lookup"><span data-stu-id="cea29-114">4.5</span></span>|
|<span data-ttu-id="cea29-115">Typ</span><span class="sxs-lookup"><span data-stu-id="cea29-115">Type</span></span>|<span data-ttu-id="cea29-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="cea29-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cea29-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cea29-117">Affected APIs</span></span>

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|

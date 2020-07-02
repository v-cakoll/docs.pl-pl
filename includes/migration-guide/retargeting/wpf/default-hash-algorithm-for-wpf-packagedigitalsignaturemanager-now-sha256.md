---
ms.openlocfilehash: d3e0a61601f60a389b662f6f74934b6e6dc6e663
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614917"
---
### <a name="the-default-hash-algorithm-for-wpf-packagedigitalsignaturemanager-is-now-sha256"></a><span data-ttu-id="a0901-101">Domyślny algorytm wyznaczania wartości skrótu dla programu WPF PackageDigitalSignatureManager jest teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="a0901-101">The default hash algorithm for WPF PackageDigitalSignatureManager is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="a0901-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a0901-102">Details</span></span>

<span data-ttu-id="a0901-103">`System.IO.Packaging.PackageDigitalSignatureManager`Oferuje funkcje dla podpisów cyfrowych w odniesieniu do pakietów WPF.</span><span class="sxs-lookup"><span data-stu-id="a0901-103">The `System.IO.Packaging.PackageDigitalSignatureManager` provides functionality for digital signatures in relation to WPF packages.</span></span>  <span data-ttu-id="a0901-104">W .NET Framework 4,7 i starszych wersjach algorytm domyślny ( <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType> ) używany do podpisywania części pakietu był SHA1.</span><span class="sxs-lookup"><span data-stu-id="a0901-104">In the .NET Framework 4.7 and earlier versions, the default algorithm (<xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>) used for signing parts of a package was SHA1.</span></span>  <span data-ttu-id="a0901-105">Z powodu niedawnych problemów z zabezpieczeniami algorytmem SHA1 ta wartość domyślna została zmieniona na SHA256, począwszy od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="a0901-105">Due to recent security concerns with SHA1, this default has been changed to SHA256 starting with the .NET Framework 4.7.1.</span></span>  <span data-ttu-id="a0901-106">Ta zmiana ma wpływ na wszystkie podpisywanie pakietów, w tym dokumenty XPS.</span><span class="sxs-lookup"><span data-stu-id="a0901-106">This change affects all package signing, including XPS documents.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a0901-107">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a0901-107">Suggestion</span></span>

<span data-ttu-id="a0901-108">Deweloperzy, którzy chcą korzystać z tej zmiany podczas określania wersji platformy poniżej, .NET Framework 4.7.1 lub deweloper, który wymaga poprzedniej funkcjonalności podczas określania wartości docelowej .NET Framework 4.7.1 lub nowszy, może odpowiednio ustawić następującą flagę AppContext.</span><span class="sxs-lookup"><span data-stu-id="a0901-108">A developer who wants to utilize this change while targeting a framework version below .NET Framework 4.7.1 or a developer who requires the previous functionality while targeting .NET Framework 4.7.1 or greater can set the following AppContext flag appropriately.</span></span>  <span data-ttu-id="a0901-109">Wartość true spowoduje użycie SHA1 jako algorytmu domyślnego; wartość false w SHA256.</span><span class="sxs-lookup"><span data-stu-id="a0901-109">A value of true will result in SHA1 being used as the default algorithm; false results in SHA256.</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.UseSha1AsDefaultHashAlgorithmForDigitalSignatures=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a0901-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a0901-110">Name</span></span>    | <span data-ttu-id="a0901-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="a0901-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a0901-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="a0901-112">Scope</span></span>   | <span data-ttu-id="a0901-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="a0901-113">Edge</span></span>        |
| <span data-ttu-id="a0901-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="a0901-114">Version</span></span> | <span data-ttu-id="a0901-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="a0901-115">4.7.1</span></span>       |
| <span data-ttu-id="a0901-116">Typ</span><span class="sxs-lookup"><span data-stu-id="a0901-116">Type</span></span>    | <span data-ttu-id="a0901-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="a0901-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="a0901-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a0901-118">Affected APIs</span></span>

- <xref:System.IO.Packaging.PackageDigitalSignatureManager.DefaultHashAlgorithm?displayProperty=nameWithType>

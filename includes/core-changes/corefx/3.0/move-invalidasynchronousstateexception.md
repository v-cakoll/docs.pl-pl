---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147552"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="1bef4-101">InvalidAsynchronousStateException przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="1bef4-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="1bef4-102">Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="1bef4-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1bef4-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="1bef4-103">Change description</span></span>

<span data-ttu-id="1bef4-104">W .NET Core 2.2 i <xref:System.ComponentModel.InvalidAsynchronousStateException> wcześniejszych wersjach klasa znajduje się w zestawie *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="1bef4-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="1bef4-105">Począwszy od .NET Core 3.0, znajduje się w zestawie *System.ComponentModel.Primitives.*</span><span class="sxs-lookup"><span data-stu-id="1bef4-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1bef4-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1bef4-106">Version introduced</span></span>

<span data-ttu-id="1bef4-107">3.0</span><span class="sxs-lookup"><span data-stu-id="1bef4-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1bef4-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1bef4-108">Recommended action</span></span>

<span data-ttu-id="1bef4-109">Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.InvalidAsynchronousStateException> używają odbicia, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> aby załadować <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> przez wywołanie metody, takich jak lub przeciążenie, które zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1bef4-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="1bef4-110">W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.</span><span class="sxs-lookup"><span data-stu-id="1bef4-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="1bef4-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1bef4-111">Category</span></span>

<span data-ttu-id="1bef4-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="1bef4-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1bef4-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1bef4-113">Affected APIs</span></span>

<span data-ttu-id="1bef4-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="1bef4-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

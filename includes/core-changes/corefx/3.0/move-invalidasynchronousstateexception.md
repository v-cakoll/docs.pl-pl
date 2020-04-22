---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021562"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="879b8-101">InvalidAsynchronousStateException przeniesiono do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="879b8-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="879b8-102">Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="879b8-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="879b8-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="879b8-103">Change description</span></span>

<span data-ttu-id="879b8-104">W .NET Core 2.2 i <xref:System.ComponentModel.InvalidAsynchronousStateException> wcześniejszych wersjach klasa znajduje się w *zespole System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="879b8-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="879b8-105">Począwszy od .NET Core 3.0, znajduje się w *system.ComponentModel.Primitives* złożenia.</span><span class="sxs-lookup"><span data-stu-id="879b8-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="879b8-106">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="879b8-106">Version introduced</span></span>

<span data-ttu-id="879b8-107">3.0</span><span class="sxs-lookup"><span data-stu-id="879b8-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="879b8-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="879b8-108">Recommended action</span></span>

<span data-ttu-id="879b8-109">Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.InvalidAsynchronousStateException> używają odbicia, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> aby załadować <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> przez wywołanie metody, takie jak lub przeciążenie, która zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="879b8-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="879b8-110">W takim przypadku zestaw zestawu, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.</span><span class="sxs-lookup"><span data-stu-id="879b8-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="879b8-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="879b8-111">Category</span></span>

<span data-ttu-id="879b8-112">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="879b8-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="879b8-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="879b8-113">Affected APIs</span></span>

<span data-ttu-id="879b8-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="879b8-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

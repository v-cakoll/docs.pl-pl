---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568079"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="faf51-101">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="faf51-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="faf51-102">Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="faf51-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="faf51-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="faf51-103">Change description</span></span>

<span data-ttu-id="faf51-104">W programie .NET Core 2,2 i starszych wersjach Klasa <xref:System.ComponentModel.InvalidAsynchronousStateException> została znaleziona w zestawie *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="faf51-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="faf51-105">Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ComponentModel. prymityws* .</span><span class="sxs-lookup"><span data-stu-id="faf51-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="faf51-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="faf51-106">Version introduced</span></span>

<span data-ttu-id="faf51-107">3.0</span><span class="sxs-lookup"><span data-stu-id="faf51-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="faf51-108">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="faf51-108">Recommended action</span></span>

<span data-ttu-id="faf51-109">Ta zmiana dotyczy tylko aplikacji, które używają odbicia w celu załadowania <xref:System.ComponentModel.InvalidAsynchronousStateException> przez wywołanie metody, takiej jak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub Przeciążenie <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, który zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="faf51-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="faf51-110">W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="faf51-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="faf51-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="faf51-111">Category</span></span>

<span data-ttu-id="faf51-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="faf51-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="faf51-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="faf51-113">Affected APIs</span></span>

- <span data-ttu-id="faf51-114">Brak</span><span class="sxs-lookup"><span data-stu-id="faf51-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

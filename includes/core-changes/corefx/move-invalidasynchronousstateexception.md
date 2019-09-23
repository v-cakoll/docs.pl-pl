---
ms.openlocfilehash: 4b41e5fcb6da638457ca8029a635f391b6a7b8ec
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182011"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a><span data-ttu-id="11f4e-101">InvalidAsynchronousStateException — przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="11f4e-101">InvalidAsynchronousStateException moved to another assembly</span></span>

<span data-ttu-id="11f4e-102"><xref:System.ComponentModel.InvalidAsynchronousStateException> Klasa została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="11f4e-102">The <xref:System.ComponentModel.InvalidAsynchronousStateException> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="11f4e-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="11f4e-103">Change description</span></span>

<span data-ttu-id="11f4e-104">W programie .NET Core 2,2 i starszych wersjach <xref:System.ComponentModel.InvalidAsynchronousStateException> Klasa jest dostępna w zestawie *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="11f4e-104">In .NET Core 2.2 and earlier versions, the <xref:System.ComponentModel.InvalidAsynchronousStateException> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="11f4e-105">Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ComponentModel. prymityws* .</span><span class="sxs-lookup"><span data-stu-id="11f4e-105">Starting with .NET Core 3.0, it is found in the *System.ComponentModel.Primitives* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="11f4e-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="11f4e-106">Version introduced</span></span>

<span data-ttu-id="11f4e-107">3.0</span><span class="sxs-lookup"><span data-stu-id="11f4e-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="11f4e-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="11f4e-108">Recommended action</span></span>

<span data-ttu-id="11f4e-109">Ta zmiana dotyczy tylko aplikacji, które używają odbicia do <xref:System.ComponentModel.InvalidAsynchronousStateException> ładowania przez wywołanie metody, takiej <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> jak lub przeciążenia <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , która zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="11f4e-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.InvalidAsynchronousStateException> by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="11f4e-110">W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="11f4e-110">If that is the case, the assembly the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="11f4e-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="11f4e-111">Category</span></span>

<span data-ttu-id="11f4e-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="11f4e-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="11f4e-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="11f4e-113">Affected APIs</span></span>

- <span data-ttu-id="11f4e-114">Brak</span><span class="sxs-lookup"><span data-stu-id="11f4e-114">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->
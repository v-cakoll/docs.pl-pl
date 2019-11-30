---
ms.openlocfilehash: 4d479636f41095610eaf39f92ad0dad4863ab8b5
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568170"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="3a078-101">TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="3a078-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="3a078-102">Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="3a078-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3a078-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="3a078-103">Change description</span></span>

<span data-ttu-id="3a078-104">W programie .NET Core 2,2 i starszych wersjach Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została znaleziona w zestawie *System. ComponentModel. TypeConverter* .</span><span class="sxs-lookup"><span data-stu-id="3a078-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="3a078-105">Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ObjectModel* .</span><span class="sxs-lookup"><span data-stu-id="3a078-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a078-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="3a078-106">Version introduced</span></span>

<span data-ttu-id="3a078-107">3.0</span><span class="sxs-lookup"><span data-stu-id="3a078-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a078-108">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="3a078-108">Recommended action</span></span>

<span data-ttu-id="3a078-109">Ta zmiana dotyczy tylko aplikacji, które używają odbicia do ładowania typu <xref:System.ComponentModel.TypeDescriptionProviderAttribute> przez wywołanie metody, takiej jak <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> lub Przeciążenie <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, który zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="3a078-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="3a078-110">W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="3a078-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="3a078-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="3a078-111">Category</span></span>

<span data-ttu-id="3a078-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a078-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a078-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3a078-113">Affected APIs</span></span>

- <span data-ttu-id="3a078-114">Brak</span><span class="sxs-lookup"><span data-stu-id="3a078-114">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

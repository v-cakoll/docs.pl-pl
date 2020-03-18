---
ms.openlocfilehash: 57ca2ad839aab8d61da1a929660920efe1190334
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147539"
---
### <a name="typedescriptionproviderattribute-moved-to-another-assembly"></a><span data-ttu-id="0a7ac-101">Atrybut TypeDescriptionProviderAttribute przeniesiony do innego zestawu</span><span class="sxs-lookup"><span data-stu-id="0a7ac-101">TypeDescriptionProviderAttribute moved to another assembly</span></span>

<span data-ttu-id="0a7ac-102">Klasa <xref:System.ComponentModel.TypeDescriptionProviderAttribute> została przeniesiona.</span><span class="sxs-lookup"><span data-stu-id="0a7ac-102">The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class has been moved.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0a7ac-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="0a7ac-103">Change description</span></span>

<span data-ttu-id="0a7ac-104">W .NET Core 2.2 i <xref:System.ComponentModel.TypeDescriptionProviderAttribute> wcześniejszych wersjach Klasa znajduje się w assembly *System.ComponentModel.TypeConverter.*</span><span class="sxs-lookup"><span data-stu-id="0a7ac-104">In .NET Core 2.2 and earlier versions, The <xref:System.ComponentModel.TypeDescriptionProviderAttribute> class is found in the *System.ComponentModel.TypeConverter* assembly.</span></span>

<span data-ttu-id="0a7ac-105">Począwszy od .NET Core 3.0, znajduje się w zestawie *System.ObjectModel.*</span><span class="sxs-lookup"><span data-stu-id="0a7ac-105">Starting with .NET Core 3.0, it is found in the *System.ObjectModel* assembly.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0a7ac-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0a7ac-106">Version introduced</span></span>

<span data-ttu-id="0a7ac-107">3.0</span><span class="sxs-lookup"><span data-stu-id="0a7ac-107">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0a7ac-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0a7ac-108">Recommended action</span></span>

<span data-ttu-id="0a7ac-109">Ta zmiana dotyczy tylko aplikacji, które <xref:System.ComponentModel.TypeDescriptionProviderAttribute> używają odbicia do <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ładowania typu przez <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> wywołanie metody, takich jak lub przeciążenie, które zakłada, że typ znajduje się w określonym zestawie.</span><span class="sxs-lookup"><span data-stu-id="0a7ac-109">This change only affects applications that use reflection to load the <xref:System.ComponentModel.TypeDescriptionProviderAttribute> type by calling a method such as <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> or an overload of <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> that assumes the type is in a particular assembly.</span></span> <span data-ttu-id="0a7ac-110">W takim przypadku zestaw, do którego odwołuje się wywołanie metody, powinien zostać zaktualizowany w celu odzwierciedlenia nowej lokalizacji zestawu typu.</span><span class="sxs-lookup"><span data-stu-id="0a7ac-110">If that is the case, the assembly referenced in the method call should be updated to reflect the type's new assembly location.</span></span>

#### <a name="category"></a><span data-ttu-id="0a7ac-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0a7ac-111">Category</span></span>

<span data-ttu-id="0a7ac-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0a7ac-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0a7ac-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0a7ac-113">Affected APIs</span></span>

<span data-ttu-id="0a7ac-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a7ac-114">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->

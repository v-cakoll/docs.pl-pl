---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644048"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="6a9dd-101">Zmiana dostępu dla accessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="6a9dd-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="6a9dd-102">Począwszy od .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1, `protected` `internal`dostępność została zmieniona z .</span><span class="sxs-lookup"><span data-stu-id="6a9dd-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6a9dd-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6a9dd-103">Change description</span></span>

<span data-ttu-id="6a9dd-104">Począwszy od .NET Core 3.0 Preview 4, `AccessibleObject.RuntimeIDFirstItem` pole było `protected`.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="6a9dd-105">Począwszy od .NET Core 3.0 RC1, został zmieniony z `protected` na wyrównanie `internal` z dostępnością pola w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6a9dd-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6a9dd-106">Version introduced</span></span>

<span data-ttu-id="6a9dd-107">3.0 Rc1</span><span class="sxs-lookup"><span data-stu-id="6a9dd-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6a9dd-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6a9dd-108">Recommended action</span></span>

<span data-ttu-id="6a9dd-109">Zmiana może mieć wpływ, jeśli opracowano aplikację .NET Core z <xref:System.Windows.Forms.AccessibleObject> typem, `RuntimeIDFirstItem` który pochodzi od pola i uzyskuje dostęp do niego.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="6a9dd-110">W takim przypadku można zdefiniować stałą lokalną w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6a9dd-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="6a9dd-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6a9dd-111">Category</span></span>

<span data-ttu-id="6a9dd-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6a9dd-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6a9dd-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6a9dd-113">Affected APIs</span></span>

- <span data-ttu-id="6a9dd-114">Nie wykrywalne za pomocą analizy Interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="6a9dd-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

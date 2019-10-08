---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003021"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="03c5e-101">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="03c5e-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="03c5e-102">Począwszy od platformy .NET Core 3,0 RC1, dostępność `AccessibleObject.RuntimeIDFirstItem` zmieniła się z `protected` na `internal`.</span><span class="sxs-lookup"><span data-stu-id="03c5e-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="03c5e-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="03c5e-103">Change description</span></span>

<span data-ttu-id="03c5e-104">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 4, pole `AccessibleObject.RuntimeIDFirstItem` było `protected`.</span><span class="sxs-lookup"><span data-stu-id="03c5e-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="03c5e-105">Począwszy od programu .NET Core 3,0 RC1, zmienił się z `protected` na `internal`, aby wyrównać dostępność pola w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="03c5e-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="03c5e-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="03c5e-106">Version introduced</span></span>

<span data-ttu-id="03c5e-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="03c5e-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="03c5e-108">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="03c5e-108">Recommended action</span></span>

<span data-ttu-id="03c5e-109">Ta zmiana może mieć wpływ na użytkownika, jeśli opracowano aplikację .NET Core z typem pochodzącym z <xref:System.Windows.Forms.AccessibleObject> i uzyskuje dostęp do pola `RuntimeIDFirstItem`.</span><span class="sxs-lookup"><span data-stu-id="03c5e-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="03c5e-110">W takim przypadku można zdefiniować stałą lokalną w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03c5e-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="03c5e-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="03c5e-111">Category</span></span>

<span data-ttu-id="03c5e-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="03c5e-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03c5e-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="03c5e-113">Affected APIs</span></span>

- <span data-ttu-id="03c5e-114">Nie wykrywalne za pośrednictwem analizy interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="03c5e-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->

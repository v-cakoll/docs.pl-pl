---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702451"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="9e03a-101">Właściwości WinForms teraz generują wyjątku ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="9e03a-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="9e03a-102">Niektóre właściwości Windows Forms teraz zwracają <xref:System.ArgumentOutOfRangeException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.</span><span class="sxs-lookup"><span data-stu-id="9e03a-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9e03a-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9e03a-103">Change description</span></span>

<span data-ttu-id="9e03a-104">Wcześniej te właściwości spowodowały różne wyjątki, takie jak <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> , lub <xref:System.ArgumentException> , gdy przekazane są argumenty poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="9e03a-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="9e03a-105">Począwszy od platformy .NET 5,0, te właściwości generują teraz, <xref:System.ArgumentOutOfRangeException> gdy przekazane argumenty są poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="9e03a-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="9e03a-106">Zgłaszanie jest <xref:System.ArgumentOutOfRangeException> zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="9e03a-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="9e03a-107">Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="9e03a-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9e03a-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9e03a-108">Version introduced</span></span>

<span data-ttu-id="9e03a-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9e03a-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9e03a-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9e03a-110">Recommended action</span></span>

- <span data-ttu-id="9e03a-111">Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="9e03a-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="9e03a-112">Jeśli to konieczne, należy obsłużyć <xref:System.ArgumentOutOfRangeException> podczas ustawiania właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e03a-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="9e03a-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9e03a-113">Category</span></span>

<span data-ttu-id="9e03a-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e03a-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9e03a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9e03a-115">Affected APIs</span></span>

<span data-ttu-id="9e03a-116">W poniższej tabeli wymieniono odpowiednie właściwości i parametry:</span><span class="sxs-lookup"><span data-stu-id="9e03a-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="9e03a-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9e03a-117">Property</span></span> | <span data-ttu-id="9e03a-118">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9e03a-118">Parameter name</span></span> | <span data-ttu-id="9e03a-119">Dodana wersja</span><span class="sxs-lookup"><span data-stu-id="9e03a-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="9e03a-120">5,0 wersja zapoznawcza 5</span><span class="sxs-lookup"><span data-stu-id="9e03a-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="9e03a-121">5,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="9e03a-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="9e03a-122">5,0 wersja zapoznawcza 6</span><span class="sxs-lookup"><span data-stu-id="9e03a-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->

---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702450"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="989a2-101">Metody WinForms teraz generują ArgumentException</span><span class="sxs-lookup"><span data-stu-id="989a2-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="989a2-102">Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.</span><span class="sxs-lookup"><span data-stu-id="989a2-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="989a2-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="989a2-103">Change description</span></span>

<span data-ttu-id="989a2-104">Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan.</span><span class="sxs-lookup"><span data-stu-id="989a2-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="989a2-105">Począwszy od platformy .NET 5,0, metody te generują teraz, <xref:System.ArgumentException> gdy przekazane nieprawidłowe argumenty.</span><span class="sxs-lookup"><span data-stu-id="989a2-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="989a2-106">Zgłaszanie jest <xref:System.ArgumentException> zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="989a2-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="989a2-107">Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="989a2-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="989a2-108">Poniższa tabela zawiera listę odpowiednich metod i parametrów:</span><span class="sxs-lookup"><span data-stu-id="989a2-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="989a2-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="989a2-109">Method</span></span> | <span data-ttu-id="989a2-110">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="989a2-110">Parameter name</span></span> | <span data-ttu-id="989a2-111">Warunek</span><span class="sxs-lookup"><span data-stu-id="989a2-111">Condition</span></span> | <span data-ttu-id="989a2-112">Dodana wersja</span><span class="sxs-lookup"><span data-stu-id="989a2-112">Version added</span></span> |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="989a2-113">Argument nie jest typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="989a2-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="989a2-114">5,0 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="989a2-114">5.0 Preview 1</span></span> |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | <span data-ttu-id="989a2-115">Argument to `null` , <xref:System.String.Empty?displayProperty=nameWithType> lub biały znak.</span><span class="sxs-lookup"><span data-stu-id="989a2-115">Argument is `null`, <xref:System.String.Empty?displayProperty=nameWithType>, or white space.</span></span> | <span data-ttu-id="989a2-116">5,0 wersja zapoznawcza 5</span><span class="sxs-lookup"><span data-stu-id="989a2-116">5.0 Preview 5</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="989a2-117">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="989a2-117">Version introduced</span></span>

<span data-ttu-id="989a2-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="989a2-118">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="989a2-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="989a2-119">Recommended action</span></span>

- <span data-ttu-id="989a2-120">Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="989a2-120">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="989a2-121">W razie potrzeby dojście do <xref:System.ArgumentException> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="989a2-121">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="989a2-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="989a2-122">Category</span></span>

<span data-ttu-id="989a2-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="989a2-123">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="989a2-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="989a2-124">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->

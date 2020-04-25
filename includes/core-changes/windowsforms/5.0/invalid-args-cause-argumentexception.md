---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158407"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="e2dc6-101">Metody WinForms teraz generują ArgumentException</span><span class="sxs-lookup"><span data-stu-id="e2dc6-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="e2dc6-102">Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e2dc6-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="e2dc6-103">Change description</span></span>

<span data-ttu-id="e2dc6-104">Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="e2dc6-105">Począwszy od platformy .NET 5,0, metody te generują <xref:System.ArgumentException> teraz, gdy przekazane nieprawidłowe argumenty.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="e2dc6-106">Zgłaszanie <xref:System.ArgumentException> jest zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e2dc6-107">Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="e2dc6-108">Poniższa tabela zawiera listę odpowiednich metod i parametrów:</span><span class="sxs-lookup"><span data-stu-id="e2dc6-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="e2dc6-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2dc6-109">Method</span></span> | <span data-ttu-id="e2dc6-110">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="e2dc6-110">Parameter name</span></span> | <span data-ttu-id="e2dc6-111">Warunek</span><span class="sxs-lookup"><span data-stu-id="e2dc6-111">Condition</span></span> | <span data-ttu-id="e2dc6-112">Dodana wersja</span><span class="sxs-lookup"><span data-stu-id="e2dc6-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="e2dc6-113">Argument nie jest typu <xref:System.Windows.Forms.TabPage>.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="e2dc6-114">5,0 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="e2dc6-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="e2dc6-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e2dc6-115">Version introduced</span></span>

<span data-ttu-id="e2dc6-116">.NET 5,0 — wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="e2dc6-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e2dc6-117">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="e2dc6-117">Recommended action</span></span>

- <span data-ttu-id="e2dc6-118">Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="e2dc6-119">W razie potrzeby dojście <xref:System.ArgumentException> do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="e2dc6-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="e2dc6-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="e2dc6-120">Category</span></span>

<span data-ttu-id="e2dc6-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2dc6-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e2dc6-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e2dc6-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->

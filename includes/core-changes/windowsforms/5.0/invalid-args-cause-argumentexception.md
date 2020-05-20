---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702473"
---
### <a name="winforms-methods-now-throw-argumentexception"></a><span data-ttu-id="97d46-101">Metody WinForms teraz generują ArgumentException</span><span class="sxs-lookup"><span data-stu-id="97d46-101">WinForms methods now throw ArgumentException</span></span>

<span data-ttu-id="97d46-102">Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.</span><span class="sxs-lookup"><span data-stu-id="97d46-102">Some Windows Forms methods now throw an <xref:System.ArgumentException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="97d46-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="97d46-103">Change description</span></span>

<span data-ttu-id="97d46-104">Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan.</span><span class="sxs-lookup"><span data-stu-id="97d46-104">Previously, passing arguments of an unexpected or incorrect type to certain Windows Forms methods would result in an indeterminate state.</span></span> <span data-ttu-id="97d46-105">Począwszy od platformy .NET 5,0, metody te generują teraz, <xref:System.ArgumentException> gdy przekazane nieprawidłowe argumenty.</span><span class="sxs-lookup"><span data-stu-id="97d46-105">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentException> when passed invalid arguments.</span></span>

<span data-ttu-id="97d46-106">Zgłaszanie jest <xref:System.ArgumentException> zgodne z zachowaniem środowiska uruchomieniowego .NET.</span><span class="sxs-lookup"><span data-stu-id="97d46-106">Throwing an <xref:System.ArgumentException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="97d46-107">Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="97d46-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

<span data-ttu-id="97d46-108">Poniższa tabela zawiera listę odpowiednich metod i parametrów:</span><span class="sxs-lookup"><span data-stu-id="97d46-108">The following table lists the affected methods and parameters:</span></span>

| <span data-ttu-id="97d46-109">Metoda</span><span class="sxs-lookup"><span data-stu-id="97d46-109">Method</span></span> | <span data-ttu-id="97d46-110">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="97d46-110">Parameter name</span></span> | <span data-ttu-id="97d46-111">Warunek</span><span class="sxs-lookup"><span data-stu-id="97d46-111">Condition</span></span> | <span data-ttu-id="97d46-112">Dodana wersja</span><span class="sxs-lookup"><span data-stu-id="97d46-112">Version added</span></span> |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | <span data-ttu-id="97d46-113">Argument nie jest typu <xref:System.Windows.Forms.TabPage> .</span><span class="sxs-lookup"><span data-stu-id="97d46-113">Argument is not of type <xref:System.Windows.Forms.TabPage>.</span></span> | <span data-ttu-id="97d46-114">5,0 wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="97d46-114">5.0 Preview 1</span></span> |

#### <a name="version-introduced"></a><span data-ttu-id="97d46-115">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="97d46-115">Version introduced</span></span>

<span data-ttu-id="97d46-116">.NET 5,0 — wersja zapoznawcza 1</span><span class="sxs-lookup"><span data-stu-id="97d46-116">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="97d46-117">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="97d46-117">Recommended action</span></span>

- <span data-ttu-id="97d46-118">Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.</span><span class="sxs-lookup"><span data-stu-id="97d46-118">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="97d46-119">W razie potrzeby dojście do <xref:System.ArgumentException> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="97d46-119">If necessary, handle an <xref:System.ArgumentException> when calling the method.</span></span>

#### <a name="category"></a><span data-ttu-id="97d46-120">Kategoria</span><span class="sxs-lookup"><span data-stu-id="97d46-120">Category</span></span>

<span data-ttu-id="97d46-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="97d46-121">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="97d46-122">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="97d46-122">Affected APIs</span></span>

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->

---
ms.openlocfilehash: 171b7a3a962f8259e64b88f1ae893e649b5f24bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621253"
---
### <a name="chained-popups-with-staysopenfalse"></a><span data-ttu-id="edac7-101">Połączone okienka podręczne z StaysOpen = false</span><span class="sxs-lookup"><span data-stu-id="edac7-101">Chained Popups with StaysOpen=False</span></span>

#### <a name="details"></a><span data-ttu-id="edac7-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="edac7-102">Details</span></span>

<span data-ttu-id="edac7-103">Okno podręczne z StaysOpen = false ma być zamknięte po kliknięciu poza oknem podręcznym.</span><span class="sxs-lookup"><span data-stu-id="edac7-103">A Popup with StaysOpen=False is supposed to close when you click outside the Popup.</span></span> <span data-ttu-id="edac7-104">Gdy dwa lub więcej takich okien podręcznych jest łańcucha (tj. jeden zawiera inny), wystąpił wiele problemów, w tym:</span><span class="sxs-lookup"><span data-stu-id="edac7-104">When two or more such Popups are chained (i.e. one contains another), there were many problems, including:</span></span><ul><li><span data-ttu-id="edac7-105">Otwórz dwa poziomy, kliknij poza P2, ale wewnątrz P1.</span><span class="sxs-lookup"><span data-stu-id="edac7-105">Open two levels, click outside P2 but inside P1.</span></span>  <span data-ttu-id="edac7-106">Nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="edac7-106">Nothing happens.</span></span></li><li><span data-ttu-id="edac7-107">Otwórz dwa poziomy, kliknij poza P1.</span><span class="sxs-lookup"><span data-stu-id="edac7-107">Open two levels, click outside P1.</span></span>  <span data-ttu-id="edac7-108">Zamknij oba okna podręczne.</span><span class="sxs-lookup"><span data-stu-id="edac7-108">Both popups close.</span></span></li><li><span data-ttu-id="edac7-109">Otwórz i Zamknij dwa poziomy.</span><span class="sxs-lookup"><span data-stu-id="edac7-109">Open and close two levels.</span></span>  <span data-ttu-id="edac7-110">Następnie spróbuj ponownie otworzyć P2.</span><span class="sxs-lookup"><span data-stu-id="edac7-110">Then try to open P2 again.</span></span>  <span data-ttu-id="edac7-111">Nic się nie dzieje.</span><span class="sxs-lookup"><span data-stu-id="edac7-111">Nothing happens.</span></span></li><li><span data-ttu-id="edac7-112">Spróbuj otworzyć trzy poziomy.</span><span class="sxs-lookup"><span data-stu-id="edac7-112">Try to open three levels.</span></span>  <span data-ttu-id="edac7-113">Nie możesz.</span><span class="sxs-lookup"><span data-stu-id="edac7-113">You can't.</span></span>  <span data-ttu-id="edac7-114">(Nic się nie dzieje lub pierwsze dwa poziomy są zamykane, w zależności od tego, gdzie klikniesz). Te przypadki (i inne warianty) działają teraz zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="edac7-114">(Either nothing happens or the first two levels close, depending on where you click.) These cases (and other variants) now work as expected.</span></span></li></ul>

| <span data-ttu-id="edac7-115">Nazwa</span><span class="sxs-lookup"><span data-stu-id="edac7-115">Name</span></span>    | <span data-ttu-id="edac7-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="edac7-116">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="edac7-117">Zakres</span><span class="sxs-lookup"><span data-stu-id="edac7-117">Scope</span></span>   |<span data-ttu-id="edac7-118">Brzeg</span><span class="sxs-lookup"><span data-stu-id="edac7-118">Edge</span></span>|
|<span data-ttu-id="edac7-119">Wersja</span><span class="sxs-lookup"><span data-stu-id="edac7-119">Version</span></span>|<span data-ttu-id="edac7-120">4.7.1</span><span class="sxs-lookup"><span data-stu-id="edac7-120">4.7.1</span></span>|
|<span data-ttu-id="edac7-121">Typ</span><span class="sxs-lookup"><span data-stu-id="edac7-121">Type</span></span>|<span data-ttu-id="edac7-122">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="edac7-122">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="edac7-123">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="edac7-123">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

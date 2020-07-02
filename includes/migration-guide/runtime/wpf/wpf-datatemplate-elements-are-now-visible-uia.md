---
ms.openlocfilehash: 06c699281c8890ac65be1d282b72b54774acc280
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620477"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a><span data-ttu-id="25830-101">Elementy DataTemplate WPF są teraz widoczne dla UIA</span><span class="sxs-lookup"><span data-stu-id="25830-101">WPF DataTemplate elements are now visible to UIA</span></span>

#### <a name="details"></a><span data-ttu-id="25830-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="25830-102">Details</span></span>

<span data-ttu-id="25830-103">Wcześniej <xref:System.Windows.DataTemplate?displayProperty=fullName> elementy były niewidoczne dla automatyzacji interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="25830-103">Previously, <xref:System.Windows.DataTemplate?displayProperty=fullName> elements were invisible to UI Automation.</span></span> <span data-ttu-id="25830-104">Począwszy od 4,5, Automatyzacja interfejsu użytkownika będzie wykrywać te elementy.</span><span class="sxs-lookup"><span data-stu-id="25830-104">Beginning in 4.5, UI Automation will detect these elements.</span></span> <span data-ttu-id="25830-105">Jest to przydatne w wielu przypadkach, ale może przerwać testy, które są zależne od drzew UIA, które nie zawierają <xref:System.Windows.DataTemplate?displayProperty=fullName> elementów.</span><span class="sxs-lookup"><span data-stu-id="25830-105">This is useful in many cases, but can break tests that depend on UIA trees not containing <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25830-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="25830-106">Suggestion</span></span>

<span data-ttu-id="25830-107">Testy automatyzacji interfejsu użytkownika dla tej aplikacji mogą wymagać aktualizacji do konta dla drzewa UIA teraz, łącznie z wcześniej niewidocznymi <xref:System.Windows.DataTemplate?displayProperty=fullName> elementami.</span><span class="sxs-lookup"><span data-stu-id="25830-107">UI Automation tests for this app may need updated to account for the UIA tree now including previously invisible <xref:System.Windows.DataTemplate?displayProperty=fullName> elements.</span></span> <span data-ttu-id="25830-108">Na przykład testy, które oczekują, że niektóre elementy powinny znajdować się obok siebie, mogą teraz oczekiwać, że wcześniej niewidoczne elementy UIA między.</span><span class="sxs-lookup"><span data-stu-id="25830-108">For example, tests that expect some elements to be next to each other may now need to expect previously invisible UIA elements in between.</span></span> <span data-ttu-id="25830-109">Testy, które opierają się na określonych licznikach lub indeksach dla elementów UIA, mogą wymagać aktualizacji z nowymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="25830-109">Or tests that rely on certain counts or indexes for UIA elements may need updated with new values.</span></span>

| <span data-ttu-id="25830-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="25830-110">Name</span></span>    | <span data-ttu-id="25830-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="25830-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25830-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="25830-112">Scope</span></span>   |<span data-ttu-id="25830-113">Brzeg</span><span class="sxs-lookup"><span data-stu-id="25830-113">Edge</span></span>|
|<span data-ttu-id="25830-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="25830-114">Version</span></span>|<span data-ttu-id="25830-115">4.5</span><span class="sxs-lookup"><span data-stu-id="25830-115">4.5</span></span>|
|<span data-ttu-id="25830-116">Typ</span><span class="sxs-lookup"><span data-stu-id="25830-116">Type</span></span>|<span data-ttu-id="25830-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="25830-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25830-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="25830-118">Affected APIs</span></span>

-<xref:System.Windows.DataTemplate.%23ctor></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)></li></ul>|

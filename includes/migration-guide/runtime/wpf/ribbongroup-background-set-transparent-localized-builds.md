---
ms.openlocfilehash: a3ba42868577ac20ea2e082f90fc4973a1bfe108
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622376"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="326a0-101">Tło zestawu wstążki jest ustawione jako przezroczyste w zlokalizowanych kompilacjach</span><span class="sxs-lookup"><span data-stu-id="326a0-101">RibbonGroup background is set to transparent in localized builds</span></span>

#### <a name="details"></a><span data-ttu-id="326a0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="326a0-102">Details</span></span>

<span data-ttu-id="326a0-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>w tle dla zlokalizowanych kompilacji zawsze jest malowany przezroczysty Pędzel, co spowodowało słabą obsługę interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="326a0-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="326a0-104">Ten problem został rozwiązany w .NET Framework 4,7 WPF, aktualizując zlokalizowane zasoby dla <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName> , które z kolei zapewniają, że wybrany jest prawidłowy pędzel.</span><span class="sxs-lookup"><span data-stu-id="326a0-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=fullName>, which in turn ensures that the correct brush is selected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="326a0-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="326a0-105">Suggestion</span></span>

<span data-ttu-id="326a0-106">Uaktualnij do .NET Framework 4,7</span><span class="sxs-lookup"><span data-stu-id="326a0-106">Upgrade to .NET Framework 4.7</span></span>

| <span data-ttu-id="326a0-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="326a0-107">Name</span></span>    | <span data-ttu-id="326a0-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="326a0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="326a0-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="326a0-109">Scope</span></span>   |<span data-ttu-id="326a0-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="326a0-110">Edge</span></span>|
|<span data-ttu-id="326a0-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="326a0-111">Version</span></span>|<span data-ttu-id="326a0-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="326a0-112">4.6.2</span></span>|
|<span data-ttu-id="326a0-113">Typ</span><span class="sxs-lookup"><span data-stu-id="326a0-113">Type</span></span>|<span data-ttu-id="326a0-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="326a0-114">Runtime</span></span>|

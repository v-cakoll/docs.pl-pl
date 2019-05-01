---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665239"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="120be-101">Tło RibbonGroup ustawiono w wersji zlokalizowanej</span><span class="sxs-lookup"><span data-stu-id="120be-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="120be-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="120be-102">Details</span></span>|<span data-ttu-id="120be-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> podstawowe informacje dotyczące wersji zlokalizowanej był zawsze rysowane pędzlem przezroczyste, co spowoduje niską możliwości interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="120be-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="120be-104">Problem ten został rozwiązany w .NET Framework w wersji 4.7 poprawkę WPF, aktualizując zlokalizowane zasoby dla <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, co z kolei zapewnia wybrano poprawny pędzla.</span><span class="sxs-lookup"><span data-stu-id="120be-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="120be-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="120be-105">Suggestion</span></span>|<span data-ttu-id="120be-106">Uaktualnianie do programu .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="120be-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="120be-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="120be-107">Scope</span></span>|<span data-ttu-id="120be-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="120be-108">Edge</span></span>|
|<span data-ttu-id="120be-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="120be-109">Version</span></span>|<span data-ttu-id="120be-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="120be-110">4.6.2</span></span>|
|<span data-ttu-id="120be-111">Typ</span><span class="sxs-lookup"><span data-stu-id="120be-111">Type</span></span>|<span data-ttu-id="120be-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="120be-112">Runtime</span></span>|

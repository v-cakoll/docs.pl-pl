---
ms.openlocfilehash: 921baed7381fad363cc832c6b6af69068c2c8f43
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236091"
---
### <a name="ribbongroup-background-is-set-to-transparent-in-localized-builds"></a><span data-ttu-id="9a217-101">Tło RibbonGroup ustawiono w wersji zlokalizowanej</span><span class="sxs-lookup"><span data-stu-id="9a217-101">RibbonGroup background is set to transparent in localized builds</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9a217-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9a217-102">Details</span></span>|<span data-ttu-id="9a217-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> podstawowe informacje dotyczące wersji zlokalizowanej był zawsze rysowane pędzlem przezroczyste, co spowoduje niską możliwości interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a217-103"><xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name> background on localized builds was always painted with Transparent brush, resulting in poor UI experience.</span></span> <span data-ttu-id="9a217-104">Problem ten został rozwiązany w .NET Framework w wersji 4.7 poprawkę WPF, aktualizując zlokalizowane zasoby dla <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, co z kolei zapewnia wybrano poprawny pędzla.</span><span class="sxs-lookup"><span data-stu-id="9a217-104">This is fixed in .NET Framework 4.7 WPF fix by updating the localized resources for <xref:System.Windows.Controls.Ribbon.RibbonGroup?displayProperty=name>, which in turn ensures that the correct brush is selected.</span></span>|
|<span data-ttu-id="9a217-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="9a217-105">Suggestion</span></span>|<span data-ttu-id="9a217-106">Uaktualnianie do programu .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9a217-106">Upgrade to .NET Framework 4.7</span></span>|
|<span data-ttu-id="9a217-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="9a217-107">Scope</span></span>|<span data-ttu-id="9a217-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="9a217-108">Edge</span></span>|
|<span data-ttu-id="9a217-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="9a217-109">Version</span></span>|<span data-ttu-id="9a217-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="9a217-110">4.6.2</span></span>|
|<span data-ttu-id="9a217-111">Typ</span><span class="sxs-lookup"><span data-stu-id="9a217-111">Type</span></span>|<span data-ttu-id="9a217-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9a217-112">Runtime</span></span>|

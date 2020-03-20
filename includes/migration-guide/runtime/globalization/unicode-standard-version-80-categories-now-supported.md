---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857527"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="e7df8-101">Obsługiwane są teraz standardowe kategorie Unicode w wersji 8.0</span><span class="sxs-lookup"><span data-stu-id="e7df8-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e7df8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e7df8-102">Details</span></span>|<span data-ttu-id="e7df8-103">W .NET Framework 4.6.2 dane Unicode zostały uaktualnione z standardu Unicode w wersji 6.3 do wersji 8.0.</span><span class="sxs-lookup"><span data-stu-id="e7df8-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="e7df8-104">Żądając kategorii znaków Unicode w .NET Framework 4.6.2, niektóre wyniki mogą nie odpowiadać wynikom w poprzednich wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7df8-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="e7df8-105">Ta zmiana dotyczy głównie sylaby Cherokee i nowych samogłosek Tai Lue znaków i znaków tonu.</span><span class="sxs-lookup"><span data-stu-id="e7df8-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="e7df8-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e7df8-106">Suggestion</span></span>|<span data-ttu-id="e7df8-107">Przejrzyj kod i usuń/zmień logikę, która zależy od zakodowanych na stałe kategorii znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="e7df8-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="e7df8-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="e7df8-108">Scope</span></span>|<span data-ttu-id="e7df8-109">Mały</span><span class="sxs-lookup"><span data-stu-id="e7df8-109">Minor</span></span>|
|<span data-ttu-id="e7df8-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="e7df8-110">Version</span></span>|<span data-ttu-id="e7df8-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e7df8-111">4.6.2</span></span>|
|<span data-ttu-id="e7df8-112">Typ</span><span class="sxs-lookup"><span data-stu-id="e7df8-112">Type</span></span>|<span data-ttu-id="e7df8-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e7df8-113">Runtime</span></span>|
|<span data-ttu-id="e7df8-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="e7df8-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

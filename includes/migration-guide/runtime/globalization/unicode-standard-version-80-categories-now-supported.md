---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981909"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="81a1b-101">Teraz obsługiwane kategorie standardowej wersji 8.0 Unicode</span><span class="sxs-lookup"><span data-stu-id="81a1b-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="81a1b-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="81a1b-102">Details</span></span>|<span data-ttu-id="81a1b-103">W programie .NET Framework 4.6.2 danych Unicode został uaktualniony ze standardu Unicode wersji 6.3 do wersji 8.0.</span><span class="sxs-lookup"><span data-stu-id="81a1b-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="81a1b-104">Podczas żądania kategorii znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81a1b-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="81a1b-105">Ta zmiana przede wszystkim ma wpływ sylab Czirokeski i nowe Tai artość samogłosek znaki i znaki tonowe.</span><span class="sxs-lookup"><span data-stu-id="81a1b-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="81a1b-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="81a1b-106">Suggestion</span></span>|<span data-ttu-id="81a1b-107">Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalonych kategorii znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="81a1b-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="81a1b-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="81a1b-108">Scope</span></span>|<span data-ttu-id="81a1b-109">Mały</span><span class="sxs-lookup"><span data-stu-id="81a1b-109">Minor</span></span>|
|<span data-ttu-id="81a1b-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="81a1b-110">Version</span></span>|<span data-ttu-id="81a1b-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="81a1b-111">4.6.2</span></span>|
|<span data-ttu-id="81a1b-112">Typ</span><span class="sxs-lookup"><span data-stu-id="81a1b-112">Type</span></span>|<span data-ttu-id="81a1b-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="81a1b-113">Runtime</span></span>|
|<span data-ttu-id="81a1b-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="81a1b-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

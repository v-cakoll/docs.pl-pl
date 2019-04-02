---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760672"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="52846-101">Teraz obsługiwane kategorie standardowej wersji 8.0 Unicode</span><span class="sxs-lookup"><span data-stu-id="52846-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="52846-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="52846-102">Details</span></span>|<span data-ttu-id="52846-103">W programie .NET Framework 4.6.2 danych Unicode został uaktualniony ze standardu Unicode wersji 6.3 do wersji 8.0.</span><span class="sxs-lookup"><span data-stu-id="52846-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="52846-104">Podczas żądania kategorii znaków Unicode w programie .NET Framework 4.6.2, niektóre wyniki mogą być niezgodne wyniki w poprzednich wersjach systemu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52846-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="52846-105">Ta zmiana przede wszystkim ma wpływ sylab Czirokeski i nowe Tai artość samogłosek znaki i znaki tonowe.</span><span class="sxs-lookup"><span data-stu-id="52846-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="52846-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="52846-106">Suggestion</span></span>|<span data-ttu-id="52846-107">Przegląd kodu i Usuń/Zmień logikę, która jest zależna od ustalonych kategorii znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="52846-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="52846-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="52846-108">Scope</span></span>|<span data-ttu-id="52846-109">Mały</span><span class="sxs-lookup"><span data-stu-id="52846-109">Minor</span></span>|
|<span data-ttu-id="52846-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="52846-110">Version</span></span>|<span data-ttu-id="52846-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="52846-111">4.6.2</span></span>|
|<span data-ttu-id="52846-112">Typ</span><span class="sxs-lookup"><span data-stu-id="52846-112">Type</span></span>|<span data-ttu-id="52846-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="52846-113">Runtime</span></span>|
|<span data-ttu-id="52846-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="52846-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|


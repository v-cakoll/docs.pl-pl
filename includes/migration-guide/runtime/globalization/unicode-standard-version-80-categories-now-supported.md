---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621190"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="22d22-101">Kategorie Unicode w wersji Standard 8,0 są teraz obsługiwane</span><span class="sxs-lookup"><span data-stu-id="22d22-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="22d22-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="22d22-102">Details</span></span>

<span data-ttu-id="22d22-103">W .NET Framework 4.6.2 dane Unicode zostały uaktualnione z wersji standard Unicode 6,3 do wersji 8,0.</span><span class="sxs-lookup"><span data-stu-id="22d22-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="22d22-104">Podczas żądania kategorii znaków Unicode w .NET Framework 4.6.2 niektóre wyniki mogą być niezgodne z wynikami w poprzednich .NET Framework wersjach.</span><span class="sxs-lookup"><span data-stu-id="22d22-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="22d22-105">Ta zmiana głównie ma wpływ na sylaby czirokeski i nowe znaki samogłosek artość oraz znaki tonu.</span><span class="sxs-lookup"><span data-stu-id="22d22-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="22d22-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="22d22-106">Suggestion</span></span>

<span data-ttu-id="22d22-107">Przejrzyj kod i Usuń lub Zmień logikę, która zależy od zakodowanych kategorii znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="22d22-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="22d22-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="22d22-108">Name</span></span>    | <span data-ttu-id="22d22-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="22d22-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="22d22-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="22d22-110">Scope</span></span>   |<span data-ttu-id="22d22-111">Mały</span><span class="sxs-lookup"><span data-stu-id="22d22-111">Minor</span></span>|
|<span data-ttu-id="22d22-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="22d22-112">Version</span></span>|<span data-ttu-id="22d22-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="22d22-113">4.6.2</span></span>|
|<span data-ttu-id="22d22-114">Typ</span><span class="sxs-lookup"><span data-stu-id="22d22-114">Type</span></span>|<span data-ttu-id="22d22-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="22d22-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22d22-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="22d22-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

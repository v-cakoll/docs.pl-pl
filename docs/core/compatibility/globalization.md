---
title: Zmiany dotyczące podziału globalizacji
description: Wyświetla listę istotnych zmian w globalizacji w programie .NET Core.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702310"
---
# <a name="globalization-breaking-changes"></a><span data-ttu-id="c44ea-103">Zmiany dotyczące podziału globalizacji</span><span class="sxs-lookup"><span data-stu-id="c44ea-103">Globalization breaking changes</span></span>

<span data-ttu-id="c44ea-104">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="c44ea-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="c44ea-105">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="c44ea-105">Breaking change</span></span> | <span data-ttu-id="c44ea-106">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="c44ea-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="c44ea-107">Interfejsy API globalizacji korzystają z bibliotek ICU w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="c44ea-107">Globalization APIs use ICU libraries on Windows</span></span>](#globalization-apis-use-icu-libraries-on-windows) | <span data-ttu-id="c44ea-108">5.0</span><span class="sxs-lookup"><span data-stu-id="c44ea-108">5.0</span></span> |
| [<span data-ttu-id="c44ea-109">StringInfo i TextElementEnumerator są teraz zgodne UAX29</span><span class="sxs-lookup"><span data-stu-id="c44ea-109">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | <span data-ttu-id="c44ea-110">5.0</span><span class="sxs-lookup"><span data-stu-id="c44ea-110">5.0</span></span> |
| [<span data-ttu-id="c44ea-111">Ustawienia regionalne "C" są mapowane na niezmienne ustawienia regionalne</span><span class="sxs-lookup"><span data-stu-id="c44ea-111">"C" locale maps to the invariant locale</span></span>](#c-locale-maps-to-the-invariant-locale) | <span data-ttu-id="c44ea-112">3.0</span><span class="sxs-lookup"><span data-stu-id="c44ea-112">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="c44ea-113">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c44ea-113">.NET 5.0</span></span>

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="c44ea-114">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="c44ea-114">.NET Core 3.0</span></span>

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***

---
title: Konwertowanie typów programu .NET Framework na ciągi znaków
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59e288a756a022763bae2235964a8b25a9d72bd1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48579478"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="d1121-102">Konwertowanie typów programu .NET Framework na ciągi znaków</span><span class="sxs-lookup"><span data-stu-id="d1121-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="d1121-103">Jeśli chcesz przekonwertować typ .NET Framework na ciąg, użyj **ToString** metody.</span><span class="sxs-lookup"><span data-stu-id="d1121-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="d1121-104">**ToString** metoda zwraca reprezentację ciągu przekazany typ to.</span><span class="sxs-lookup"><span data-stu-id="d1121-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="d1121-105">Poniższa tabela zawiera listę typów programu .NET Framework, które zwracają ciąg w formacie, który jest mapowany do specyfikacji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="d1121-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="d1121-106">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1121-106">.NET Framework type</span></span>|<span data-ttu-id="d1121-107">Ciąg typ zwracany</span><span class="sxs-lookup"><span data-stu-id="d1121-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="d1121-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="d1121-108">Boolean</span></span>|<span data-ttu-id="d1121-109">"true", "fałsz"</span><span class="sxs-lookup"><span data-stu-id="d1121-109">"true", "false"</span></span>|  
|<span data-ttu-id="d1121-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="d1121-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="d1121-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="d1121-111">"INF"</span></span>|  
|<span data-ttu-id="d1121-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="d1121-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="d1121-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="d1121-113">"-INF"</span></span>|  
|<span data-ttu-id="d1121-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="d1121-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="d1121-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="d1121-115">"INF"</span></span>|  
|<span data-ttu-id="d1121-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="d1121-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="d1121-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="d1121-117">"-INF"</span></span>|  
|<span data-ttu-id="d1121-118">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="d1121-118">DateTime</span></span>|<span data-ttu-id="d1121-119">Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzbiory.</span><span class="sxs-lookup"><span data-stu-id="d1121-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="d1121-120">Przedział czasu</span><span class="sxs-lookup"><span data-stu-id="d1121-120">Timespan</span></span>|<span data-ttu-id="d1121-121">Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest wartość typu duration 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="d1121-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1121-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1121-122">See also</span></span>

- [<span data-ttu-id="d1121-123">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="d1121-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
- [<span data-ttu-id="d1121-124">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d1121-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

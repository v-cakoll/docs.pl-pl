---
title: Konwertowanie typów programu .NET Framework na ciągi znaków
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98ebc9248b0585295adf12e04dece0fef654c2e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583132"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="86180-102">Konwertowanie typów programu .NET Framework na ciągi znaków</span><span class="sxs-lookup"><span data-stu-id="86180-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="86180-103">Jeśli chcesz przekonwertować typ .NET Framework na ciąg, użyj **ToString** metody.</span><span class="sxs-lookup"><span data-stu-id="86180-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="86180-104">**ToString** metoda zwraca reprezentację ciągu przekazany typ to.</span><span class="sxs-lookup"><span data-stu-id="86180-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="86180-105">Poniższa tabela zawiera listę typów programu .NET Framework, które zwracają ciąg w formacie, który jest mapowany do specyfikacji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="86180-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="86180-106">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="86180-106">.NET Framework type</span></span>|<span data-ttu-id="86180-107">Ciąg typ zwracany</span><span class="sxs-lookup"><span data-stu-id="86180-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="86180-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="86180-108">Boolean</span></span>|<span data-ttu-id="86180-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="86180-109">"true", "false"</span></span>|  
|<span data-ttu-id="86180-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="86180-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="86180-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="86180-111">"INF"</span></span>|  
|<span data-ttu-id="86180-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="86180-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="86180-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="86180-113">"-INF"</span></span>|  
|<span data-ttu-id="86180-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="86180-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="86180-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="86180-115">"INF"</span></span>|  
|<span data-ttu-id="86180-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="86180-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="86180-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="86180-117">"-INF"</span></span>|  
|<span data-ttu-id="86180-118">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="86180-118">DateTime</span></span>|<span data-ttu-id="86180-119">Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzbiory.</span><span class="sxs-lookup"><span data-stu-id="86180-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="86180-120">Przedział czasu</span><span class="sxs-lookup"><span data-stu-id="86180-120">Timespan</span></span>|<span data-ttu-id="86180-121">Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest wartość typu duration 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="86180-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86180-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86180-122">See also</span></span>

- [<span data-ttu-id="86180-123">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="86180-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="86180-124">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="86180-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

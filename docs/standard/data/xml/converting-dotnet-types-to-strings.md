---
title: Konwertowanie typów programu .NET Framework na ciągi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98ebc9248b0585295adf12e04dece0fef654c2e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953988"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="dfab2-102">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="dfab2-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="dfab2-103">Jeśli chcesz przekonwertować typ .NET Framework na ciąg, użyj **ToString** metody.</span><span class="sxs-lookup"><span data-stu-id="dfab2-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="dfab2-104">**ToString** metoda zwraca reprezentację ciągu przekazany typ to.</span><span class="sxs-lookup"><span data-stu-id="dfab2-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="dfab2-105">Poniższa tabela zawiera listę typów programu .NET Framework, które zwracają ciąg w formacie, który jest mapowany do specyfikacji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="dfab2-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="dfab2-106">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dfab2-106">.NET Framework type</span></span>|<span data-ttu-id="dfab2-107">Ciąg typ zwracany</span><span class="sxs-lookup"><span data-stu-id="dfab2-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="dfab2-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="dfab2-108">Boolean</span></span>|<span data-ttu-id="dfab2-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="dfab2-109">"true", "false"</span></span>|  
|<span data-ttu-id="dfab2-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dfab2-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="dfab2-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="dfab2-111">"INF"</span></span>|  
|<span data-ttu-id="dfab2-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dfab2-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="dfab2-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dfab2-113">"-INF"</span></span>|  
|<span data-ttu-id="dfab2-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="dfab2-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="dfab2-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="dfab2-115">"INF"</span></span>|  
|<span data-ttu-id="dfab2-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="dfab2-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="dfab2-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="dfab2-117">"-INF"</span></span>|  
|<span data-ttu-id="dfab2-118">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="dfab2-118">DateTime</span></span>|<span data-ttu-id="dfab2-119">Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzbiory.</span><span class="sxs-lookup"><span data-stu-id="dfab2-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="dfab2-120">Przedział czasu</span><span class="sxs-lookup"><span data-stu-id="dfab2-120">Timespan</span></span>|<span data-ttu-id="dfab2-121">Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest wartość typu duration 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="dfab2-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfab2-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfab2-122">See also</span></span>

- [<span data-ttu-id="dfab2-123">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="dfab2-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="dfab2-124">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="dfab2-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

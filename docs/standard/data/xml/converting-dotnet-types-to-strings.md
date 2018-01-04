---
title: "Konwertowanie typów programu .NET Framework na ciągi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6ca134e13593fdacd759b0000e0e159f76ea067f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="a981d-102">Konwertowanie typów programu .NET Framework na ciągi</span><span class="sxs-lookup"><span data-stu-id="a981d-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="a981d-103">Aby przekonwertować na ciąg typu .NET Framework, należy użyć **ToString** metody.</span><span class="sxs-lookup"><span data-stu-id="a981d-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="a981d-104">**ToString** metoda zwraca reprezentację ciągu przekazany typ.</span><span class="sxs-lookup"><span data-stu-id="a981d-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="a981d-105">Poniższa tabela zawiera listę typów .NET Framework, które zwracają ciąg w formacie, który jest mapowany na specyfikacje schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="a981d-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="a981d-106">Typ programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a981d-106">.NET Framework type</span></span>|<span data-ttu-id="a981d-107">String — typ zwracany</span><span class="sxs-lookup"><span data-stu-id="a981d-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="a981d-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="a981d-108">Boolean</span></span>|<span data-ttu-id="a981d-109">"true", "fałsz"</span><span class="sxs-lookup"><span data-stu-id="a981d-109">"true", "false"</span></span>|  
|<span data-ttu-id="a981d-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a981d-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="a981d-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="a981d-111">"INF"</span></span>|  
|<span data-ttu-id="a981d-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a981d-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="a981d-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a981d-113">"-INF"</span></span>|  
|<span data-ttu-id="a981d-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="a981d-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="a981d-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="a981d-115">"INF"</span></span>|  
|<span data-ttu-id="a981d-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="a981d-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="a981d-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="a981d-117">"-INF"</span></span>|  
|<span data-ttu-id="a981d-118">DataGodzina</span><span class="sxs-lookup"><span data-stu-id="a981d-118">DateTime</span></span>|<span data-ttu-id="a981d-119">Format to RRRR-MM-ddTHH:mm:sszzzzzz i jego podzestawy.</span><span class="sxs-lookup"><span data-stu-id="a981d-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="a981d-120">Zakres czasu</span><span class="sxs-lookup"><span data-stu-id="a981d-120">Timespan</span></span>|<span data-ttu-id="a981d-121">Format jest PnYnMnTnHnMnS, na przykład `P2Y10M15DT10H30M20S` jest czas trwania 10hours 2 lata, 10 miesięcy, 15 dni, 30 minut i 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="a981d-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a981d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a981d-122">See Also</span></span>  
 [<span data-ttu-id="a981d-123">Konwersja typów danych XML</span><span class="sxs-lookup"><span data-stu-id="a981d-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="a981d-124">Konwertowanie ciągów na typy danych programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a981d-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

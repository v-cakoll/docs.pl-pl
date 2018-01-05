---
title: "Obsługa dziedziczenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c898d8448b39fc5da63e5eda2046d0747837509b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="inheritance-support"></a><span data-ttu-id="57933-102">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="57933-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="57933-103">obsługuje *pojedynczej tabeli mapowania*.</span><span class="sxs-lookup"><span data-stu-id="57933-103"> supports *single-table mapping*.</span></span> <span data-ttu-id="57933-104">Innymi słowy hierarchii dziedziczenia pełną są przechowywane w tabeli pojedynczej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="57933-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="57933-105">Tabela zawiera spłaszczoną Unii wszystkich kolumn danych w całej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="57933-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="57933-106">(Unii jest wynikiem połączenia dwóch tabel w jednej tabeli, która ma wiersze, które były obecne w oryginalnej tabel). Każdy wiersz ma wartości null w kolumnach, który nie ma zastosowania do typu wystąpienia reprezentowany przez wiersz.</span><span class="sxs-lookup"><span data-stu-id="57933-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="57933-107">Strategię mapowania pojedynczej tabeli jest najprostsza reprezentacja dziedziczenia i dostarcza charakterystyk dobrą wydajność dla wielu różnych kategorii zapytania.</span><span class="sxs-lookup"><span data-stu-id="57933-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="57933-108">Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy określić atrybuty i właściwości atrybutu dla klasy głównym hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="57933-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="57933-109">Aby uzyskać więcej informacji, zobacz [porady: hierarchii dziedziczenia mapy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="57933-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="57933-110">Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] także [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="57933-110">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57933-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57933-111">See Also</span></span>  
 [<span data-ttu-id="57933-112">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="57933-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

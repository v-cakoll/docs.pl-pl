---
title: Obsługa dziedziczenia
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 3d396632902b178eee34801a9716d8aa222a08d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359565"
---
# <a name="inheritance-support"></a><span data-ttu-id="938a6-102">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="938a6-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="938a6-103"> obsługuje *pojedynczej tabeli mapowania*.</span><span class="sxs-lookup"><span data-stu-id="938a6-103"> supports *single-table mapping*.</span></span> <span data-ttu-id="938a6-104">Innymi słowy hierarchii dziedziczenia pełną są przechowywane w tabeli pojedynczej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="938a6-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="938a6-105">Tabela zawiera spłaszczoną Unii wszystkich kolumn danych w całej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="938a6-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="938a6-106">(Unii jest wynikiem połączenia dwóch tabel w jednej tabeli, która ma wiersze, które były obecne w oryginalnej tabel). Każdy wiersz ma wartości null w kolumnach, który nie ma zastosowania do typu wystąpienia reprezentowany przez wiersz.</span><span class="sxs-lookup"><span data-stu-id="938a6-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="938a6-107">Strategię mapowania pojedynczej tabeli jest najprostsza reprezentacja dziedziczenia i dostarcza charakterystyk dobrą wydajność dla wielu różnych kategorii zapytania.</span><span class="sxs-lookup"><span data-stu-id="938a6-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="938a6-108">Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy określić atrybuty i właściwości atrybutu dla klasy głównym hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="938a6-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="938a6-109">Aby uzyskać więcej informacji, zobacz [porady: hierarchii dziedziczenia mapy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="938a6-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="938a6-110">Za pomocą programu Visual Studio programiści mogą również wykorzystać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="938a6-110">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a6-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="938a6-111">See Also</span></span>  
 [<span data-ttu-id="938a6-112">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="938a6-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

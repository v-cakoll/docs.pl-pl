---
title: Obsługa dziedziczenia
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 576fa896364d603f2cdbb7b6532e3efc3cd6f674
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743073"
---
# <a name="inheritance-support"></a><span data-ttu-id="73ea4-102">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="73ea4-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="73ea4-103">obsługuje *pojedynczej tabeli mapowania*.</span><span class="sxs-lookup"><span data-stu-id="73ea4-103">supports *single-table mapping*.</span></span> <span data-ttu-id="73ea4-104">Innymi słowy hierarchii dziedziczenia pełną są przechowywane w jednej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="73ea4-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="73ea4-105">Tabela zawiera spłaszczonych sumę wszystkich kolumn danych w całej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="73ea4-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="73ea4-106">(Unii jest wynikiem łączenie dwóch tabel w jedną tabelę wierszy, które znajdowały się w jednej z tabel, oryginalnym). Każdy wiersz zawiera wartości null w kolumnach, który nie ma zastosowania do typu wystąpienia, reprezentowane przez wiersz.</span><span class="sxs-lookup"><span data-stu-id="73ea4-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="73ea4-107">Strategia pojedynczej tabeli mapowania to najprostsza reprezentacja dziedziczenia i dostarcza charakterystyk wydajności dla wielu różnych kategorii zapytania.</span><span class="sxs-lookup"><span data-stu-id="73ea4-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="73ea4-108">Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy określić atrybuty i właściwości atrybutów, które znajdują się w klasie głównego hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="73ea4-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="73ea4-109">Aby uzyskać więcej informacji, zobacz [jak: Mapowanie hierarchii dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span><span class="sxs-lookup"><span data-stu-id="73ea4-109">For more information, see [How to: Map Inheritance Hierarchies](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="73ea4-110">Deweloperzy korzystający z programu Visual Studio umożliwia również Object Relational Designer mapowanie hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="73ea4-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73ea4-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73ea4-111">See also</span></span>

- [<span data-ttu-id="73ea4-112">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="73ea4-112">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

---
title: Obsługa dziedziczenia
ms.date: 03/30/2017
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
ms.openlocfilehash: 034aa6e75ca304d98aa4d3e1f3023c1a6940b73c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781568"
---
# <a name="inheritance-support"></a><span data-ttu-id="54add-102">Obsługa dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="54add-102">Inheritance Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="54add-103">obsługuje *Mapowanie pojedynczej tabeli*.</span><span class="sxs-lookup"><span data-stu-id="54add-103">supports *single-table mapping*.</span></span> <span data-ttu-id="54add-104">Innymi słowy, pełna Hierarchia dziedziczenia jest przechowywana w pojedynczej tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="54add-104">In other words, a complete inheritance hierarchy is stored in a single database table.</span></span> <span data-ttu-id="54add-105">Tabela zawiera spłaszczoną Unię wszystkich możliwych kolumn danych dla całej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="54add-105">The table contains the flattened union of all possible data columns for the whole hierarchy.</span></span> <span data-ttu-id="54add-106">(Unia jest wynikiem łączenia dwóch tabel w jedną tabelę, w której znajdują się wiersze, które znajdowały się w jednej z oryginalnych tabel). Każdy wiersz ma wartości null w kolumnach, które nie mają zastosowania do typu wystąpienia reprezentowanego przez wiersz.</span><span class="sxs-lookup"><span data-stu-id="54add-106">(A union is the result of combining two tables into one table that has the rows that were present in either of the original tables.) Each row has nulls in the columns that do not apply to the type of the instance represented by the row.</span></span>  
  
 <span data-ttu-id="54add-107">Strategia mapowania jednej tabeli jest najprostszą reprezentacją dziedziczenia i zapewnia dobrą charakterystykę wydajności dla wielu różnych kategorii zapytań.</span><span class="sxs-lookup"><span data-stu-id="54add-107">The single-table mapping strategy is the simplest representation of inheritance and provides good performance characteristics for many different categories of queries.</span></span>  
  
 <span data-ttu-id="54add-108">Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="54add-108">To implement this mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy.</span></span> <span data-ttu-id="54add-109">Aby uzyskać więcej informacji, zobacz [jak: Hierarchie](how-to-map-inheritance-hierarchies.md)dziedziczenia mapowania.</span><span class="sxs-lookup"><span data-stu-id="54add-109">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>  
  
 <span data-ttu-id="54add-110">Deweloperzy korzystający z programu Visual Studio mogą również używać Object Relational Designer do mapowania hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="54add-110">Developers using Visual Studio can also use the Object Relational Designer to map inheritance hierarchies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54add-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54add-111">See also</span></span>

- [<span data-ttu-id="54add-112">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="54add-112">Background Information</span></span>](background-information.md)

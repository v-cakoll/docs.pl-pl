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
# <a name="inheritance-support"></a>Obsługa dziedziczenia
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje *pojedynczej tabeli mapowania*. Innymi słowy hierarchii dziedziczenia pełną są przechowywane w jednej bazie danych. Tabela zawiera spłaszczonych sumę wszystkich kolumn danych w całej hierarchii. (Unii jest wynikiem łączenie dwóch tabel w jedną tabelę wierszy, które znajdowały się w jednej z tabel, oryginalnym). Każdy wiersz zawiera wartości null w kolumnach, który nie ma zastosowania do typu wystąpienia, reprezentowane przez wiersz.  
  
 Strategia pojedynczej tabeli mapowania to najprostsza reprezentacja dziedziczenia i dostarcza charakterystyk wydajności dla wielu różnych kategorii zapytania.  
  
 Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy określić atrybuty i właściwości atrybutów, które znajdują się w klasie głównego hierarchii dziedziczenia. Aby uzyskać więcej informacji, zobacz [jak: Mapowanie hierarchii dziedziczenia](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Deweloperzy korzystający z programu Visual Studio umożliwia również Object Relational Designer mapowanie hierarchii dziedziczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

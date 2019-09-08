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
# <a name="inheritance-support"></a>Obsługa dziedziczenia
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje *Mapowanie pojedynczej tabeli*. Innymi słowy, pełna Hierarchia dziedziczenia jest przechowywana w pojedynczej tabeli bazy danych. Tabela zawiera spłaszczoną Unię wszystkich możliwych kolumn danych dla całej hierarchii. (Unia jest wynikiem łączenia dwóch tabel w jedną tabelę, w której znajdują się wiersze, które znajdowały się w jednej z oryginalnych tabel). Każdy wiersz ma wartości null w kolumnach, które nie mają zastosowania do typu wystąpienia reprezentowanego przez wiersz.  
  
 Strategia mapowania jednej tabeli jest najprostszą reprezentacją dziedziczenia i zapewnia dobrą charakterystykę wydajności dla wielu różnych kategorii zapytań.  
  
 Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie, należy określić atrybuty i właściwości atrybutów w klasie głównej hierarchii dziedziczenia. Aby uzyskać więcej informacji, zobacz [jak: Hierarchie](how-to-map-inheritance-hierarchies.md)dziedziczenia mapowania.  
  
 Deweloperzy korzystający z programu Visual Studio mogą również używać Object Relational Designer do mapowania hierarchii dziedziczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)

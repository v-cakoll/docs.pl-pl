---
title: Obsługa dziedziczenia
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19bb2794-b4e7-402e-8307-1d1517381a08
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 7633ba80d2657f2f0135ee702a6cc89a260fec68
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="inheritance-support"></a>Obsługa dziedziczenia
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje *pojedynczej tabeli mapowania*. Innymi słowy hierarchii dziedziczenia pełną są przechowywane w tabeli pojedynczej bazy danych. Tabela zawiera spłaszczoną Unii wszystkich kolumn danych w całej hierarchii. (Unii jest wynikiem połączenia dwóch tabel w jednej tabeli, która ma wiersze, które były obecne w oryginalnej tabel). Każdy wiersz ma wartości null w kolumnach, który nie ma zastosowania do typu wystąpienia reprezentowany przez wiersz.  
  
 Strategię mapowania pojedynczej tabeli jest najprostsza reprezentacja dziedziczenia i dostarcza charakterystyk dobrą wydajność dla wielu różnych kategorii zapytania.  
  
 Aby zaimplementować to mapowanie w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], należy określić atrybuty i właściwości atrybutu dla klasy głównym hierarchii dziedziczenia. Aby uzyskać więcej informacji, zobacz [porady: hierarchii dziedziczenia mapy](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md).  
  
 Za pomocą programu Visual Studio programiści mogą również wykorzystać [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania hierarchii dziedziczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

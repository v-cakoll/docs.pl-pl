---
title: Wyrażenia stałe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: b31cd881f1307ec734c026d3c873d7a650e19a20
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251132"
---
# <a name="constant-expressions"></a>Wyrażenia stałe
Wyrażenie stałe składa się z stałej wartości. Stałe wartości są bezpośrednio konwertowane na stałe wyrażenia drzewa poleceń, bez żadnego tłumaczenia na klienta. Obejmuje to wyrażenia, które powodują powstanie wartości stałej. W związku z tym należy oczekiwać zachowania źródła danych dla wszystkich wyrażeń obejmujących stałe. Może to spowodować zachowanie, które różni się od zachowania środowiska CLR.  
  
 Poniższy przykład przedstawia wyrażenie stałe, które jest oceniane na serwerze.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities nie obsługuje używania klasy użytkownika jako stałej. Jednak odwołanie do właściwości w klasie użytkownika jest uznawane za stałe i zostanie przekonwertowane na wyrażenie stałe drzewa poleceń i wykonane w źródle danych.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](expressions-in-linq-to-entities-queries.md)

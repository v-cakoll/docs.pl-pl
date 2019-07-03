---
title: Wyrażenia stałe
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: cc3a214a2faa06c79ee0794b0158381bff0c4b0b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539883"
---
# <a name="constant-expressions"></a>Wyrażenia stałe
Wyrażenie stałe składa się z wartością stałą. Wartości stałe bezpośrednio są konwertowane na stałe polecenia drzewa wyrażeń, bez tłumaczenia na komputerze klienckim. Obejmuje to stała wartość wyrażenia. W związku z tym, zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń obejmujących stałe. Może to spowodować, że zachowanie, które różni się od zachowania CLR.  
  
 Poniższy przykład pokazuje wyrażenie stałe, które jest oceniane na serwerze.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 Składnik LINQ to Entities nie obsługuje używania klasy użytkownika jako stała. Jednak odwołaniem do właściwości w klasie użytkownika jest uznawany za stałą, zostanie przekonwertowane na wyrażeniu stałym drzewa poleceń i wykonywane w źródle danych.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

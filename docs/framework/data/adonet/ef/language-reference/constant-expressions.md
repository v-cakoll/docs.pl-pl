---
title: "Wyrażenia stałe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ccc54df7a69db8186c653afb415a5679b65ab50d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="constant-expressions"></a>Wyrażenia stałe
Wyrażenie stałe składa się z wartością stałą. Wartości stałe bezpośrednio są konwertowane na wyrażenia drzewa polecenia stałe, bez tłumaczenia na kliencie. W tym wyrażeń, które powodują powstanie wartość stałą. W związku z tym zachowanie źródła danych można się spodziewać dla wszystkich wyrażeń zawierających stałe. Może to spowodować zachowanie różni się od zachowania CLR.  
  
 W poniższym przykładzie przedstawiono stałe wyrażenie, które jest obliczane na serwerze.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]nie obsługuje używania klasy użytkownika jako stała. Jednak odwołania do właściwości klasy użytkownika jest uznawany za stałą i będzie można przekonwertować na stałe wyrażenie drzewa polecenia ani wykonywać w źródle danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

---
title: "Wyrażenia inicjowania"
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
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dd5706c2eb09b0161d7eb1a4412471e9e75fcf75
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="initialization-expressions"></a>Wyrażenia inicjowania
Wyrażenia inicjowania inicjuje nowy obiekt. Większość wyrażenia inicjowania są obsługiwane, tym większości nowych 3.0 C# i Visual Basic 9.0 inicjowania wyrażeń. Następujące typy mogą zainicjowany i zwrócony przez LINQ do jednostek kwerendy:  
  
-   Kolekcja zero lub więcej obiektów typów jednostek lub dla projekcji typów złożonych, które są zdefiniowane w modelu koncepcyjnym.  
  
-   Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
-   Kolekcje wbudowane.  
  
-   Typy anonimowe.  
  
 Inicjowanie typu anonimowego pokazano w poniższym przykładzie w składni wyrażeń zapytania:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono inicjowania typu anonimowego:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Obsługiwane jest również inicjowania klasy zdefiniowanej przez użytkownika. Wzorzec inicjowania 3.0 C# i Visual Basic 9.0 jest obsługiwana i przyjęto założenie, że właściwość pobierającej i ustawiającej są symetryczne. W poniższym przykładzie w składni wyrażeń zapytania przedstawiono niestandardowej klasy inicjowany w zapytaniu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 W poniższym przykładzie w składni zapytania oparte na metodzie przedstawiono niestandardowej klasy inicjowany w zapytaniu:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia w składniku LINQ to Entities zapytań](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

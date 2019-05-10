---
title: Wyrażenia inicjowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 78bafcad0a0f34c74ea58f107621ad145c1b405b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631530"
---
# <a name="initialization-expressions"></a>Wyrażenia inicjowania
Wyrażenia inicjowania inicjuje nowy obiekt. Większość wyrażenia inicjowania są obsługiwane, w tym najbardziej nowe C# 3.0 i wyrażenia inicjowania 9.0 Visual Basic. Następujące typy można zainicjowany i zwrócony przez LINQ zapytanie jednostki:  
  
- Kolekcja zero lub więcej obiektów typów jednostek lub projekcji złożonych typów, które są zdefiniowane w modelu koncepcyjnym.  
  
- Typy CLR obsługiwane przez [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  
  
- Kolekcje wbudowane.  
  
- Typy anonimowe.  
  
 Inicjalizacja typu anonimowego pokazano w poniższym przykładzie w składni wyrażenia zapytania:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 Poniższy przykład przy użyciu składni zapytania oparte na metodzie pokazuje inicjowania typu anonimowego:  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 Obsługiwane jest również inicjowanie klasy zdefiniowanej przez użytkownika. C# 3.0 i Visual Basic 9.0 wzorzec inicjowania jest obsługiwana i przyjęto założenie, że pobierającej i ustawiającej są symetryczne. W składni wyrażenia zapytania poniższy kod przedstawia klasę niestandardową, która jest inicjowany w zapytaniu:  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 Poniższy przykład przy użyciu składni zapytania oparte na metodzie pokazuje klasę niestandardową, która jest inicjowany w zapytaniu:  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)

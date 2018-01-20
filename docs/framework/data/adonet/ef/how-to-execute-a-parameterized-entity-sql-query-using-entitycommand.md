---
title: "Porady: wykonywanie zapytań SQL sparametryzowane jednostki przy użyciu EntityCommand"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d43be857e4f920a1ce36625d9be207b9025ff423
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a>Porady: wykonywanie zapytań SQL sparametryzowane jednostki przy użyciu EntityCommand
W tym temacie przedstawiono sposób wykonania [!INCLUDE[esql](../../../../../includes/esql-md.md)] kwerendę, która ma parametry, używając <xref:System.Data.EntityClient.EntityCommand> obiektu.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1.  Dodaj [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu i konfigurowanie projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stronie kodu aplikacji, Dodaj następujący `using` instrukcje (`Imports` w języku Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia ciągu zapytania z dwoma parametrami. Następnie tworzy <xref:System.Data.EntityClient.EntityCommand>, dodaje dwa parametry <xref:System.Data.EntityClient.EntityParameter> kolekcji tego <xref:System.Data.EntityClient.EntityCommand>i iteruje po kolekcji `Contact` elementów.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wykonanie zapytania parametrycznego](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 [Jednostki języka SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)

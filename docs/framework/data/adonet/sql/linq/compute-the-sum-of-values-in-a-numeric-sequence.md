---
title: "Oblicza sumę wartości liczbowych sekwencji"
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
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 547d9f245d41fac2e2d65877ddbb2a8660d73c42
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Oblicza sumę wartości liczbowych sekwencji
Użyj <xref:System.Linq.Enumerable.Sum%2A> operatora, aby obliczyć sumę wartości liczbowe w sekwencji.  
  
 Należy zwrócić uwagę na następujące cechy `Sum` operatora w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Operator zagregowany standardowe — Operator zapytań `Sum` ocenia równą zero dla pustej sekwencji lub sekwencję, która zawiera tylko wartości null. W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], semantykę SQL pozostaną niezmienione. Z tego powodu `Sum` daje w wyniku wartość null zamiast od zera dla pustej sekwencji lub sekwencję, która zawiera tylko wartości null.  
  
-   Ograniczenia SQL pośrednich wyników dotyczą wartości zagregowanych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Sumę ilości 32-bitową liczbę całkowitą nie jest obliczana przy użyciu 64-bitowych wyników i mogą być przepełnienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczenie `Sum`. Istnieje taka możliwość, nawet jeśli implementacja standardowe — Operator zapytań nie spowoduje przepełnienie w odpowiedniej sekwencji w pamięci.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie całkowita transport wszystkich zamówień w `Order` tabeli.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe są: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie łączna liczba jednostek w kolejności dla wszystkich produktów.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe są: `780`.  
  
 Należy pamiętać, że należy rzutować `short` typów (na przykład `UnitsOnOrder`) ponieważ `Sum` ma żadna metoda przeciążenia krótkich typów.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)

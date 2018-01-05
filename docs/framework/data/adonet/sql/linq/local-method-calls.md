---
title: "Wywołania metody lokalnego"
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
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 105814dd45bc8cd07bf25c4972d4d1b3aa93b1f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="local-method-calls"></a>Wywołania metody lokalnego
Wywołanie metody lokalnych to taki, który jest wykonywana w ramach modelu obiektów. Wywołanie metody zdalnej jest jednym który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy do bazy danych SQL i przesyła do aparatu bazy danych w celu wykonania. Wywołania metody lokalnym są wymagane podczas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może dokonywać translacji wywołania SQL. W przeciwnym razie <xref:System.InvalidOperationException> jest generowany.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie `Order` klasy jest mapowany do tabeli zamówienia w bazie danych Northwind. Metoda lokalne wystąpienie dodano do klasy.  
  
 W 1 kwerendy. Konstruktor `Order` klasy jest wykonywane lokalnie. W kwerendzie 2, jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbował tłumaczenie `LocalInstanceMethod()`SQL, próba nie powiedzie się i <xref:System.InvalidOperationException> może zostać zgłoszony wyjątek. Jednak ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia obsługę dla wywołań metod lokalnego kwerenda2 nie spowoduje zgłoszenie wyjątku.  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)

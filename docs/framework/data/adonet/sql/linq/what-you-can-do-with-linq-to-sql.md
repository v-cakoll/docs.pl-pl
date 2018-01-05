---
title: "Co można zrobić za pomocą LINQ do SQL"
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
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 70e783c0ad6b13097aaa1912f1338714a1f43f73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Co można zrobić za pomocą LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje wszystkie funkcje klucza, który można oczekiwać Deweloper SQL. Można wyszukiwać informacje i wstawiania, aktualizacji i usuwania informacji z tabel.  
  
## <a name="selecting"></a>Wybieranie  
 Wybieranie (*projekcji*) jest to osiągane przez właśnie zapisywania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] kwerendy w języku programowania, a następnie wykonywanie tej kwerendy można pobrać wyników. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przekłada się wszelkie niezbędne działania na potrzeby operacji SQL, które znasz. Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 W poniższym przykładzie nazwy firm klientów z Londynu są pobierane i wyświetlane w oknie konsoli.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Wstawianie  
 Aby wykonać SQL `Insert`, wystarczy dodać obiekty do modelu obiektów, które zostały utworzone i wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 W poniższym przykładzie nowego klienta i informacje na temat klienta jest dodawany do `Customers` tabeli za pomocą <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizowanie  
 Aby `Update` zapisu bazy danych, najpierw pobrać element i edytować bezpośrednio w modelu obiektu. Po zmodyfikowaniu obiektu wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> aktualizacji bazy danych.  
  
 W poniższym przykładzie są pobierane wszystkich klientów, którzy są w Londynie. Następnie nazwę miasta jest zmieniony z "Londynie" na "Metro — Londynie". Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, aby wysłać zmiany do bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Usuwanie  
 Aby `Delete` elementu, Usuń element z kolekcji, do której należy, a następnie wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> można zatwierdzić zmiany.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie rozpoznaje operacjami usuwania kaskadowego. Jeśli chcesz usunąć wiersz w tabeli, która ma ograniczenia na nim, zobacz [porady: usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 W poniższym przykładzie klienta, który ma `CustomerID` z `98128` są pobierane z bazy danych. Po potwierdzeniu, że pobrano wiersza klienta, a następnie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jest wywoływana, aby usunąć ten obiekt z kolekcji. Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana w celu przekazywania do usunięcia bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)

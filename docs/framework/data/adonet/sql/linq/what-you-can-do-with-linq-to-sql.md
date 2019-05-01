---
title: Co można zrobić za pomocą funkcji LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: efb7b86c3add99e596e6798c8267c09689899d56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923932"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Co można zrobić za pomocą funkcji LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje wszystkie kluczowe możliwości, których można oczekiwać dla deweloperów programu SQL. Można wyszukiwać informacje i wstawiania, aktualizacji i usuwania informacji z tabel.  
  
## <a name="selecting"></a>Zaznaczenie  
 Wybieranie (*projekcji*) odbywa się po prostu pisząc [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w języku programowania, a następnie wykonywania tego zapytania do pobierania wyników. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sam tłumaczy niezbędne operacje do niezbędnych operacji SQL, które znasz. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 W poniższym przykładzie nazwy firm klientów z Londynu są pobierane i wyświetlane w oknie konsoli.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Wstawianie  
 Aby wykonać SQL `Insert`, wystarczy dodać obiekty z modelu obiektów, które zostały utworzone w celu wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 W poniższym przykładzie nowego klienta i informacje o kliencie są dodawane do `Customers` tabelę za pomocą <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizowanie  
 Aby `Update` wpis w bazie danych, najpierw pobrać elementu i edytować bezpośrednio w modelu obiektów. Po zmodyfikowaniu obiektu, wywołaj <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> aktualizacji bazy danych.  
  
 W poniższym przykładzie pobierane są wszyscy klienci z Londynu. Następnie nazwę miasta jest zmieniony z "Londyn" na "Metro — London". Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, aby wysłać zmiany z bazą danych.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Usuwanie  
 Aby `Delete` element, Usuń element z kolekcji, do której należy, a następnie wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext> aby zatwierdzić zmiany.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie rozpoznaje usuwanie kaskadowe operacji. Jeśli chcesz usunąć wiersz w tabeli, który ma ograniczenia względem go, zobacz [jak: Usuwanie wierszy z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 W poniższym przykładzie klienta, który ma `CustomerID` z `98128` są pobierane z bazy danych. Po potwierdzeniu, że wiersz klienta został pobrany, a następnie <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jest wywoływana, aby usunąć ten obiekt z kolekcji. Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, aby przekazywać do usunięcia bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)

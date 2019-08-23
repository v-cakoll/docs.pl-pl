---
title: Co można zrobić za pomocą funkcji LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: 21ed620ab5b7a78fc4f396cc474e7c62b70f1ddd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946621"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Co można zrobić za pomocą funkcji LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program obsługuje wszystkie kluczowe możliwości, które należy oczekiwać jako deweloper SQL. Możesz wysyłać zapytania o informacje oraz wstawiać, aktualizować i usuwać informacje z tabel.  
  
## <a name="selecting"></a>Zaznaczenie  
 Wybór (*projekcja*) jest realizowany przez zapisanie [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania w własnym języku programowania, a następnie wykonanie zapytania w celu pobrania wyników. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]samo tłumaczy wszystkie niezbędne operacje na niezbędne operacje SQL, które znasz. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
 W poniższym przykładzie nazwy firmowe klientów z Londynie są pobierane i wyświetlane w oknie konsoli.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Wstawieniu  
 Aby wykonać instrukcję SQL `Insert`, wystarczy dodać obiekty do modelu obiektów, który został utworzony, i wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext>polecenie.  
  
 W poniższym przykładzie nowy klient i informacje o kliencie są dodawane do `Customers` tabeli przy użyciu. <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizowanie  
 Aby `Update` wejść do bazy danych, najpierw Pobierz element i edytuj go bezpośrednio w modelu obiektów. Po zmodyfikowaniu obiektu Wywołaj <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> polecenie, aby zaktualizować bazę danych.  
  
 W poniższym przykładzie są pobierane wszyscy klienci z usługi Londyn. Nazwa miasta zostanie zmieniona z "Londyn" na "Londyn-metro". Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana w celu wysłania zmian do bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Usunąć  
 Do `Delete` elementu, Usuń element z kolekcji, do której należy, a następnie Wywołaj metodę <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> , aby zatwierdzić zmianę.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz z tabeli zawierającej ograniczenia, zobacz [How to: Usuń wiersze z bazy danych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 W poniższym przykładzie klient, który ma `CustomerID` zostać pobrany z bazy danych programu. `98128` Następnie po potwierdzeniu, że wiersz klienta został pobrany, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jest wywoływana, aby usunąć ten obiekt z kolekcji. Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, aby przesłać dalej operację usuwania do bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)

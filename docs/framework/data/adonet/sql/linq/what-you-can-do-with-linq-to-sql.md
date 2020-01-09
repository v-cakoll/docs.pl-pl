---
title: Co można zrobić za pomocą funkcji LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: e84047843aff4044c75ba1b971a9e2f061e2e8d6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634004"
---
# <a name="what-you-can-do-with-linq-to-sql"></a>Co można zrobić za pomocą funkcji LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje wszystkie kluczowe możliwości, które należy oczekiwać jako deweloper SQL. Możesz wysyłać zapytania o informacje oraz wstawiać, aktualizować i usuwać informacje z tabel.  
  
## <a name="selecting"></a>Zaznaczenie  
 Wybór (*projekcja*) jest realizowany przez zapisanie zapytania LINQ we własnym języku programowania, a następnie wykonanie zapytania w celu pobrania wyników. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] samo tłumaczy wszystkie niezbędne operacje na niezbędne operacje SQL, które znasz. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](index.md).  
  
 W poniższym przykładzie nazwy firmowe klientów z Londynie są pobierane i wyświetlane w oknie konsoli.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a>Wstawieniu  
 Aby wykonać `Insert`SQL, wystarczy dodać obiekty do modelu obiektów, który został utworzony, i wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w <xref:System.Data.Linq.DataContext>.  
  
 W poniższym przykładzie nowy klient i informacje o kliencie są dodawane do tabeli `Customers` przy użyciu <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a>Aktualizowanie  
 Aby `Update` wpis bazy danych, najpierw Pobierz element i edytuj go bezpośrednio w modelu obiektów. Po zmodyfikowaniu obiektu Wywołaj <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>, aby zaktualizować bazę danych.  
  
 W poniższym przykładzie są pobierane wszyscy klienci z usługi Londyn. Nazwa miasta zostanie zmieniona z "Londyn" na "Londyn-metro". Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana w celu wysłania zmian do bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a>Usuwanie  
 Aby `Delete` element, Usuń element z kolekcji, do którego należy, a następnie Wywołaj <xref:System.Data.Linq.DataContext.SubmitChanges%2A> w <xref:System.Data.Linq.DataContext>, aby zatwierdzić zmianę.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie rozpoznaje operacji kaskadowego usuwania. Jeśli chcesz usunąć wiersz z tabeli zawierającej ograniczenia, zobacz [How to: delete Rows from a Database](how-to-delete-rows-from-the-database.md).  
  
 W poniższym przykładzie klient, który ma `CustomerID` `98128` jest pobierany z bazy danych. Następnie po potwierdzeniu, że wiersz klienta został pobrany, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> jest wywoływana, aby usunąć ten obiekt z kolekcji. Na koniec <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana w celu przekierowania usuwania do bazy danych.  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania](programming-guide.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
- [Wprowadzenie](getting-started.md)

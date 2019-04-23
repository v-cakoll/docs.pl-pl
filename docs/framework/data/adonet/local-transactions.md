---
title: Transakcje lokalne
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
ms.openlocfilehash: e139cafa168b0a6851e5d8474e6bb4db94f36e9a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339154"
---
# <a name="local-transactions"></a>Transakcje lokalne
Transakcje w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] są używane, gdy chcesz powiązać ze sobą wiele zadań, tak, aby są wykonywane jako pojedyncza jednostka pracy. Na przykład załóżmy, że aplikacja wykonuje dwa zadania. Najpierw aktualizuje tabelę z informacjami o kolejności. Po drugie aktualizuje tabelę, która zawiera informacje dotyczące spisu, obciążenie elementy uporządkowane. Zadanie nie powiedzie się, zarówno aktualizacje zostaną wycofane.  
  
## <a name="determining-the-transaction-type"></a>Określanie typu transakcji  
 Transakcja jest uważana za lokalnej transakcji, jednofazowy transakcji i obsługiwane przez bazę danych bezpośrednio. Transakcja jest uważana za transakcję rozproszoną, kiedy są koordynowany przez monitor transakcji i używa mechanizmów odporne na uszkodzenia (na przykład dwufazowego) do rozpoznawania transakcji.  
  
 Każdy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawców danych ma swój własny `Transaction` obiektu do wykonywania transakcji lokalnych. Jeśli potrzebujesz transakcji wykonywanych w bazie danych programu SQL Server, wybierz <xref:System.Data.SqlClient> transakcji. W przypadku transakcji bazy danych Oracle, użyj <xref:System.Data.OracleClient> dostawcy. Ponadto, istnieje <xref:System.Data.Common.DbTransaction> klasę, która jest dostępna dla zapisywania kod niezależny od dostawcy, który wymaga transakcji.  
  
> [!NOTE]
> Transakcje są najbardziej efektywne, gdy są one wykonywane na serwerze. Jeśli pracujesz z bazą danych programu SQL Server, który sprawia, że zwiększone użycie jawnego transakcji, należy rozważyć, zapisując je jako procedur przechowywanych, za pomocą instrukcji języka Transact-SQL BEGIN TRANSACTION.
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Wykonywanie transakcji za pomocą pojedynczego połączenia  
 W [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], możesz kontrolować transakcji za pomocą `Connection` obiektu. Możesz zainicjować lokalnej transakcji przy użyciu `BeginTransaction` metody. Po rozpoczęciu transakcji można zarejestrować polecenia w ramach transakcji przy użyciu `Transaction` właściwość `Command` obiektu. Można następnie Zatwierdź lub wycofać zmiany dokonane w źródle danych, w oparciu o powodzeniu lub niepowodzeniu składniki transakcji.  
  
> [!NOTE]
>  `EnlistDistributedTransaction` Nie należy używać metody dla lokalnych transakcji.  
  
 Zakres transakcji jest ograniczony do połączenia. Poniższy przykład wykonuje transakcji jawnej, który składa się z dwóch oddzielnych poleceń w `try` bloku. Polecenie zostanie wykonane instrukcji INSERT w tabeli Production.ScrapReason w przykładowej bazie AdventureWorks programu SQL Server, które są zatwierdzone, jeśli żadne wyjątki są zgłaszane. Kod w `catch` bloku powoduje wycofanie transakcji, jeśli zostanie zgłoszony wyjątek. Jeśli transakcja została przerwana lub połączenie jest zamknięte przed ukończeniem transakcji, jego zostanie automatycznie wycofana.  
  
## <a name="example"></a>Przykład  
 Wykonaj następujące kroki do wykonania transakcji.  
  
1. Wywołaj <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu do oznaczania początku transakcji. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda zwraca odwołanie do transakcji. Ta dokumentacja jest przypisany do <xref:System.Data.SqlClient.SqlCommand> obiektów, które są zarejestrowane w transakcji.  
  
2. Przypisz `Transaction` obiekt <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> właściwość <xref:System.Data.SqlClient.SqlCommand> do wykonania. Jeśli polecenie jest wykonywane przy połączeniu z aktywnej transakcji, a `Transaction` obiekt nie został przypisany do `Transaction` właściwość `Command` obiektu, jest zgłaszany wyjątek.  
  
3. Wykonaj wymagane polecenia.  
  
4. Wywołaj <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> metody <xref:System.Data.SqlClient.SqlTransaction> obiektu do zrealizowania transakcji, lub zadzwoń <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metodę, aby zakończyć transakcji. Jeśli połączenie jest zamknięte lub usunięty przed albo <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> lub <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metody zostały wykonane, transakcja zostanie wycofana.  
  
 Poniższy przykład kodu demonstruje, przy użyciu logiki transakcyjnej [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] z programem Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [Transakcje rozproszone](../../../../docs/framework/data/adonet/distributed-transactions.md)
- [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

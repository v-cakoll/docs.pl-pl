---
title: Lokalne transakcje
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
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f9b1280f3a05a42a2f713adf993bb439245c95a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="local-transactions"></a>Lokalne transakcje
Transakcje w [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] są używane, kiedy chcesz powiązać wielu zadań jednocześnie, dzięki czemu są one wykonywane jako pojedynczą jednostkę pracy. Na przykład załóżmy, że aplikacja wykonuje dwa zadania. Najpierw aktualizuje tabelę z informacjami o kolejności. Po drugie aktualizuje tabeli, która zawiera informacje o spisie, obciążenie elementy uporządkowane. Zadanie nie powiedzie się, zarówno aktualizacje są przywracane.  
  
## <a name="determining-the-transaction-type"></a>Określanie typu transakcji  
 Transakcja jest uważana za transakcji lokalnej, gdy transakcja jednofazowy i są bezpośrednio obsługiwane przez bazę danych. Transakcja jest uważana za transakcji rozproszonej, kiedy jest koordynowane przez monitor transakcji i używa awaryjnego mechanizmów (na przykład dwufazowego) do rozpoznawania transakcji.  
  
 Każdy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] danych dostawców ma własną `Transaction` obiektu do wykonania transakcji lokalnej. Jeśli potrzebujesz transakcji wykonywanych w bazie danych programu SQL Server, wybierz <xref:System.Data.SqlClient> transakcji. Dla transakcji Oracle, użyj <xref:System.Data.OracleClient> dostawcy. Ponadto jest dostępna nowa <xref:System.Data.Common.DbTransaction> klasy, która jest dostępna dla zapisywania kod niezależny od dostawcy, który wymaga transakcji.  
  
> [!NOTE]
>  Transakcje są najbardziej efektywne, gdy jest wykonywane na serwerze. Jeśli pracujesz z bazy danych programu SQL Server, która sprawia, że zwiększone użycie jawnych transakcji, należy wziąć pod uwagę zostaną zapisane jako procedury składowane za pomocą instrukcji języka Transact-SQL BEGIN TRANSACTION. Aby uzyskać więcej informacji o wydajności transakcji po stronie serwera zobacz dokumentację SQL Server — książki Online.  
  
## <a name="performing-a-transaction-using-a-single-connection"></a>Wykonywanie transakcji za pomocą pojedynczego połączenia  
 W [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], możesz kontrolować transakcje z `Connection` obiektu. Możesz zainicjować transakcji lokalnej z `BeginTransaction` metody. Po rozpoczęciu transakcji można zarejestrować polecenia w tej transakcji z `Transaction` właściwość `Command` obiektu. Można następnie Zatwierdź lub wycofać zmian wprowadzonych w źródle danych oparte na powodzenie lub niepowodzenie składników transakcji.  
  
> [!NOTE]
>  `EnlistDistributedTransaction` — Metoda nie powinna być używana dla transakcji lokalnej.  
  
 Zakres transakcji jest ograniczony do połączenia. Poniższy przykład wykonuje składający się z dwóch oddzielnych poleceń w transakcji jawnej `try` bloku. Polecenie zostanie wykonane instrukcji INSERT w tabeli Production.ScrapReason w AdventureWorks [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] przykładowej bazy danych, które są zatwierdzone, jeśli żadne wyjątki są zgłaszane. Kod w `catch` bloku wycofuje transakcji jest zgłaszany wyjątek. Jeśli transakcja jest przerywana lub połączenie jest zamknięte przed transakcja została ukończona, jego została automatycznie wycofana.  
  
## <a name="example"></a>Przykład  
 Wykonaj poniższe kroki do wykonania transakcji.  
  
1.  Wywołanie <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> metody <xref:System.Data.SqlClient.SqlConnection> obiektu, aby oznaczyć rozpoczęcia transakcji. <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> Metoda zwraca odwołanie do transakcji. To odwołanie jest przypisany do <xref:System.Data.SqlClient.SqlCommand> obiektów, które są zarejestrowane w ramach transakcji.  
  
2.  Przypisz `Transaction` do obiektu <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> właściwość <xref:System.Data.SqlClient.SqlCommand> do wykonania. Jeśli polecenie jest wykonywane w połączeniu z aktywnej transakcji i `Transaction` obiektu nie został przypisany do `Transaction` właściwość `Command` obiektu, jest zgłaszany wyjątek.  
  
3.  Wykonaj wymagane polecenia.  
  
4.  Wywołanie <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> metody <xref:System.Data.SqlClient.SqlTransaction> obiektu do zrealizowania transakcji, lub zadzwoń <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metodę, aby zakończyć transakcji. Jeśli połączenie jest zamknięty lub usunięty przed albo <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> lub <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> metody zostały wykonane, transakcja zostanie wycofana.  
  
 Poniższy przykład kodu pokazuje, przy użyciu logiki transakcyjnej [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] z programem Microsoft SQL Server.  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Transakcje i współbieżność](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [Transakcje rozproszone](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [System.Transactions integracji z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

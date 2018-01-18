---
title: ADO.NET i LINQ do SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c95a84bafcb32861e299135feb0b89b931d11165
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET i LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wchodzi w skład [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodziny technologii. Jest on oparty na usług świadczonych przez [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] dostawcy modelu. W związku z tym można łączyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu z istniejącym [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikacji i przeprowadzić migrację bieżącego [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rozwiązania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Poniższa ilustracja przedstawia ogólny widok relacji.  
  
 ![LINQ do SQL i ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Połączenia  
 Możesz podać istniejące [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] połączenia podczas tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Wszystkie operacje przed <xref:System.Data.Linq.DataContext> (w tym zapytań) Użyj tej podane połączenie. Jeśli połączenie jest już otwarty, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozostawia go jako jest po zakończeniu pracy z nim.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Zawsze możesz uzyskiwać dostęp do połączenia i zamknij je samodzielnie przy użyciu <xref:System.Data.Linq.DataContext.Connection%2A> właściwości, zgodnie z poniższym kodem:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakcje  
 Możesz podać Twoje <xref:System.Data.Linq.DataContext> przy użyciu własnego transakcji bazy danych w przypadku aplikacji zainicjował już transakcji użytkownika <xref:System.Data.Linq.DataContext> zaangażować.  
  
 Preferowaną metodą prowadzenia transakcji z [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] jest użycie <xref:System.Transactions.TransactionScope> obiektu. Przy użyciu tej metody, możesz wprowadzić transakcji rozproszonych, obsługiwanych przez baz danych i menedżerów innych rezydentny zasobów. Zakresy transakcji wymaga niewielkiej ilości zasobów, aby rozpocząć. One przełącza się do transakcji rozproszonych tylko wtedy, gdy wiele połączeń w zakresie transakcji.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Nie można użyć tej metody dla wszystkich baz danych. Na przykład połączenie SqlClient nie można podwyższyć poziomu transakcji systemu podczas działania przed [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serwera. Zamiast tego automatycznie współdziała on do pełnego transakcji rozproszonej przy każdym stwierdzeniu zakresu transakcji używany.  
  
## <a name="direct-sql-commands"></a>Poleceń SQL bezpośredniego  
 Czasami może wystąpić sytuacje gdzie zdolność <xref:System.Data.Linq.DataContext> do wykonywania kwerend lub przesyłania zmian jest niewystarczający dla specjalne zadanie, które chcesz wykonać. W takiej sytuacji można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metody w celu wydawania polecenia SQL z bazą danych i przekonwertować na obiekty wyniki zapytania.  
  
 Załóżmy na przykład, że dane dla `Customer` klasy jest rozkładu ponad dwie tabele (customer1 i customer2). Następujące zapytanie zwraca sekwencji `Customer` obiektów:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tak długo, jak nazwy kolumn w wynikach tabelarycznym odpowiada właściwości kolumny klasy jednostki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty poza każde zapytanie SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda przyjmuje parametry. Poniższy kod wykonuje zapytania parametrycznego:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametry są wyrażane w tekst zapytania przy użyciu tego samego notacji klamrowych używanych przez `Console.WriteLine()` i `String.Format()`. `String.Format()`pobiera ciąg zapytania, podaj i zastępuje takich jak parametry nawiasach klamrowych z nazwy parametru wygenerowanego `@p0`, `@p1` ..., `@p(n)`.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)

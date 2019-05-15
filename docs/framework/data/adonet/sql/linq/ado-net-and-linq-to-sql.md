---
title: ADO.NET i LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 49f28acc5001d63e7a1f6a5bfe8cb3415311e379
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582749"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET i LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest częścią [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rodziny technologii. Jest on oparty na usługi świadczone przez [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] dostawcy modelu. W związku z tym możesz mieszać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kodu przy użyciu istniejących [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplikacji i przeprowadzić migrację bieżącego [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] rozwiązania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Następująca ilustracja przedstawia ogólny widok relacji.  
  
 ![LINQ to SQL i ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Połączenia  
 Możesz podać istniejące [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] połączenia podczas tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>. Wszystkie operacje na <xref:System.Data.Linq.DataContext> (w tym zapytań), użyj tego podano połączenia. Jeśli połączenie jest już otwarty, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozostawi je się po zakończeniu pracy z nim.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Zawsze możesz uzyskiwać dostęp do połączenia i zamknij go samodzielnie za pomocą <xref:System.Data.Linq.DataContext.Connection%2A> właściwości, tak jak w poniższym kodzie:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakcje  
 Możesz podać swoje <xref:System.Data.Linq.DataContext> przy użyciu własnych transakcji bazy danych w przypadku aplikacji już zainicjował transakcji Twojej <xref:System.Data.Linq.DataContext> zaangażować.  
  
 Preferowaną metodą działania transakcji za pomocą programu .NET Framework jest użycie <xref:System.Transactions.TransactionScope> obiektu. Za pomocą tego podejścia, możesz wprowadzać transakcji rozproszonych, który działa wobec obsługiwanych baz danych i innych menedżerów zasobów rezydentnego. Zakresy transakcji wymaga niewielkiej ilości zasobów, aby rozpocząć. One przełącza się do transakcje rozproszone tylko wtedy, gdy wiele połączeń w zakresie transakcji.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Nie można użyć tej metody dla wszystkich baz danych. Na przykład połączeń klient SQL nie można podwyższyć poziomu transakcji systemu podczas działania względem [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] serwera. Zamiast tego automatycznie współdziała on do transakcji rozproszonych, pełna zawsze wtedy, gdy widzi, używany zakres transakcji.  
  
## <a name="direct-sql-commands"></a>Polecenia SQL bezpośrednie  
 Czasami mogą wystąpić sytuacje gdzie zdolność <xref:System.Data.Linq.DataContext> mają być odczytane lub Prześlij zmiany jest niewystarczająca dla specjalne zadanie, które chcesz wykonać. W takiej sytuacji można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metody do wysyłania poleceń SQL w bazie danych i konwertowania wyników zapytania do obiektów.  
  
 Na przykład, załóżmy, że dane dla `Customer` klasy jest rozłożona się powyżej dwóch tabel (serwer customer1 i customer2). Następujące zapytanie zwraca sekwencję `Customer` obiektów:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tak długo, jak nazwy kolumn w wyniki tabelaryczne dopasować kolumny właściwości swojej klasy jednostki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty z dowolnego zapytania SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda przyjmuje parametrów. Poniższy kod wykonuje zapytanie parametryczne:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  Parametry są wyrażone w tekst zapytania przy użyciu takiej samej notacji nawiasów posługują się `Console.WriteLine()` i `String.Format()`. `String.Format()` pobiera ciąg zapytania, podaj i zastępuje takich jak parametry nawiasów klamrowych, przy użyciu nazwy parametrów wygenerowanego `@p0`, `@p1` ..., `@p(n)`.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)

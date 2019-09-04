---
title: ADO.NET i LINQ to SQL
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 0bebc8d890325ec4ab090470952e11b90d0e37ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248117"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET i LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest częścią ADO.NETej technologii. Jest on oparty na usługach oferowanych przez model dostawcy ADO.NET. W związku z tym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] możesz mieszać kod z istniejącymi aplikacjami ADO.NET i migrować bieżące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]rozwiązania ADO.NET do programu. Poniższa ilustracja przedstawia ogólny widok relacji.  
  
 ![LINQ to SQL i ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Połączenia  
 Podczas tworzenia programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>można podać istniejące połączenie usługi ADO.NET. Wszystkie operacje związane z <xref:System.Data.Linq.DataContext> (łącznie z zapytaniami) używają tego podanego połączenia. Jeśli połączenie jest już otwarte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozostawia je po zakończeniu pracy.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Zawsze możesz uzyskać dostęp do połączenia i zamknąć go samodzielnie przy użyciu <xref:System.Data.Linq.DataContext.Connection%2A> właściwości, jak w poniższym kodzie:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakcje  
 Możesz podać swoją <xref:System.Data.Linq.DataContext> własną transakcję bazy danych, gdy aplikacja już zainicjowała transakcję i <xref:System.Data.Linq.DataContext> chcesz, aby była ona używana.  
  
 Preferowaną metodą wykonywania transakcji z .NET Framework jest użycie <xref:System.Transactions.TransactionScope> obiektu. Korzystając z tej metody, można tworzyć transakcje rozproszone, które działają między bazami danych i innymi menedżerami zasobów zamieszkałymi w pamięci. Zakresy transakcji wymagają kilku zasobów do uruchomienia. Promują się one tylko do transakcji rozproszonych, tylko gdy istnieje wiele połączeń w ramach transakcji.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Nie można użyć tej metody dla wszystkich baz danych. Na przykład połączenie SqlClient nie może podwyższyć poziomu transakcji systemowych, gdy działa na serwerze SQL Server 2000. Zamiast tego automatycznie rejestrowana jest pełna, rozproszona transakcja, gdy widzi ona zakres transakcji, który jest używany.  
  
## <a name="direct-sql-commands"></a>Bezpośrednie polecenia SQL  
 Czasami można napotkać sytuacje, w których możliwość <xref:System.Data.Linq.DataContext> wykonywania zapytań lub przesyłania zmian jest niewystarczająca dla wyspecjalizowanego zadania, które chcesz wykonać. W takich przypadkach można użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metody do wydawania poleceń SQL do bazy danych i przekonwertowania wyników zapytania na obiekty.  
  
 Załóżmy na przykład, że dane dla `Customer` klasy są rozłożone na dwie tabele (customer1 i Customer2). Następujące zapytanie zwraca sekwencję `Customer` obiektów:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tak długo, jak nazwy kolumn w wynikach tabelarycznych są zgodne z właściwościami kolumny klasy Entity [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , program tworzy obiekty z dowolnego zapytania SQL.  
  
### <a name="parameters"></a>Parametry  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metoda przyjmuje parametry. Poniższy kod wykonuje zapytanie parametryczne:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametry są wyrażane w tekście zapytania przy użyciu tej samej notacji klamrowej `Console.WriteLine()` używanej przez i `String.Format()`. `String.Format()`Pobiera ciąg zapytania, który jest udostępniany i zastępuje parametry klamrowe z wygenerowanymi nazwami parametrów, `@p0`takimi jak, `@p1` . `@p(n)`..,.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a elementem DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)

---
title: ADO.NET i LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980005"
---
# <a name="adonet-and-linq-to-sql"></a>ADO.NET i LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest częścią ADO.NET technologii. Jest on oparty na usługach oferowanych przez model dostawcy ADO.NET. W związku z tym możesz mieszać kod [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] z istniejącymi aplikacjami ADO.NET i migrować bieżące rozwiązania ADO.NET do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Poniższa ilustracja przedstawia ogólny widok relacji.  
  
 ![LINQ to SQL i ADO.NET](./media/dlinq-3.png "DLinq_3")  
  
## <a name="connections"></a>Połączenia  
 Podczas tworzenia <xref:System.Data.Linq.DataContext>[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można podać istniejące połączenie usługi ADO.NET. Wszystkie operacje dotyczące <xref:System.Data.Linq.DataContext> (w tym zapytania) używają tego podanego połączenia. Jeśli połączenie jest już otwarte, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pozostawia je po zakończeniu pracy.  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 Zawsze możesz uzyskać dostęp do połączenia i zamknąć go samodzielnie przy użyciu właściwości <xref:System.Data.Linq.DataContext.Connection%2A>, jak w poniższym kodzie:  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a>Transakcje  
 Możesz podać <xref:System.Data.Linq.DataContext> z własną transakcją bazy danych, gdy aplikacja już zainicjowała transakcję i chcesz, aby <xref:System.Data.Linq.DataContext>.  
  
 Preferowaną metodą wykonywania transakcji z .NET Framework jest użycie obiektu <xref:System.Transactions.TransactionScope>. Korzystając z tej metody, można tworzyć transakcje rozproszone, które działają między bazami danych i innymi menedżerami zasobów zamieszkałymi w pamięci. Zakresy transakcji wymagają kilku zasobów do uruchomienia. Promują się one tylko do transakcji rozproszonych, tylko gdy istnieje wiele połączeń w ramach transakcji.  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 Nie można użyć tej metody dla wszystkich baz danych. Na przykład połączenie SqlClient nie może podwyższyć poziomu transakcji systemowych, gdy działa na serwerze SQL Server 2000. Zamiast tego automatycznie rejestrowana jest pełna, rozproszona transakcja, gdy widzi ona zakres transakcji, który jest używany.  
  
## <a name="direct-sql-commands"></a>Bezpośrednie polecenia SQL  
 Czasami można napotkać sytuacje, w których zdolność <xref:System.Data.Linq.DataContext> do zapytania lub przesłania zmiany są niewystarczające dla wyspecjalizowanego zadania, które chcesz wykonać. W takich okolicznościach można użyć metody <xref:System.Data.Linq.DataContext.ExecuteQuery%2A>, aby wydać polecenia SQL do bazy danych i przekonwertować wyniki zapytania na obiekty.  
  
 Załóżmy na przykład, że dane dla klasy `Customer` są rozłożone na dwie tabele (customer1 i Customer2). Następujące zapytanie zwraca sekwencję `Customer` obiektów:  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 Tak długo, jak nazwy kolumn w wynikach tabelarycznych pasują do właściwości kolumny klasy Entity, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty z dowolnego zapytania SQL.  
  
### <a name="parameters"></a>Parametry  
 Metoda <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> akceptuje parametry. Poniższy kod wykonuje zapytanie parametryczne:  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> Parametry są wyrażane w tekście zapytania przy użyciu tej samej notacji klamrowej używanej przez `Console.WriteLine()` i `String.Format()`. `String.Format()` Pobiera ciąg zapytania, który jest udostępniany i zastępuje parametry klamrowe z wygenerowanymi nazwami parametrów, takimi jak `@p0`, `@p1`..., `@p(n)`.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [Instrukcje: Ponowne użycie połączenia między poleceniem ADO.NET a DataContext](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)

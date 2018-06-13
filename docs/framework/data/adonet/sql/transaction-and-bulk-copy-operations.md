---
title: Transakcja i operacje kopiowania masowego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: 9b485ac3f12587256a56fdfa44cf8b9c8b41a6bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365345"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transakcja i operacje kopiowania masowego
Jako operacje izolowanej lub w ramach wielu transakcji krok można wykonać operacji kopiowania zbiorczego. Ta opcja ostatnie umożliwia wykonać więcej niż jedną operację kopiowania zbiorczego w ramach jednej transakcji, a także wykonywać innych operacji bazy danych (na przykład wstawienia, aktualizacje i usunięcia), przy zachowaniu możliwości przekazać ani wycofać cała transakcja.  
  
 Domyślnie jest wykonywane kopiowania masowego izolowanego operacji. Występuje kopiowania masowego w sposób obsługi nietransakcyjnego z ma wtedy możliwości wycofanie go. Jeśli trzeba przywrócić całość lub część kopiowania zbiorczego po wystąpieniu błędu, możesz użyć <xref:System.Data.SqlClient.SqlBulkCopy>-zarządzane transakcji, wykonać kopiowania masowego w istniejącej transakcji lub być zarejestrowany w **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Wykonywanie operacji kopiowania zbiorczego nietransakcyjnej  
 Następującej aplikacji konsoli Pokazuje, co się dzieje podczas operacji kopiowania zbiorczego nietransakcyjnej napotka błąd tym za pomocą operacji.  
  
 W tym przykładzie tabeli źródłowej, jak i tabela docelowa obejmują `Identity` kolumny o nazwie **ProductID**. Kod najpierw przygotowuje tabeli docelowej, usuwając wszystkie wiersze, a następnie wstawianie pojedynczy wiersz którego **ProductID** istnieje w tabeli źródłowej. Domyślnie nową wartość dla `Identity` wygenerowaniu kolumny w tabeli docelowej dla każdego wiersza dodane. W tym przykładzie ustawiono opcję po otwarciu połączenia wymusza proces ładowania zbiorczego do użycia `Identity` zamiast wartości z tabeli źródłowej.  
  
 Operacja kopiowania zbiorczego jest wykonywane z <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> właściwości ustawiony na 10. Podczas operacji napotkał nieprawidłowy wiersz, jest zgłaszany wyjątek. W tym przykładzie pierwsze kopiowania masowego jest nietransakcyjnej. Wszystkie instancje skopiowany do punktu błędu są zatwierdzone; wsadowe zawierające zduplikowany klucz zostanie wycofana i kopiowania masowego jest zatrzymany przed przetworzeniem innych partie.  
  
> [!NOTE]
>  W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` instrukcji, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Wykonywanie operacji kopiowania zbiorczego dedykowanych w transakcji  
 Domyślnie kopiowania masowego jest jego własnej transakcji. Do wykonania operacji kopiowania zbiorczego dedykowanych, należy utworzyć nowe wystąpienie klasy <xref:System.Data.SqlClient.SqlBulkCopy> z parametrów połączenia, lub użyj istniejącego <xref:System.Data.SqlClient.SqlConnection> obiektu bez aktywnej transakcji. W każdym scenariuszu operacja kopiowania zbiorczego tworzy i następnie zatwierdza lub wycofuje transakcję.  
  
 Można jawnie określić <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> opcji <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora klasy jawnie powoduje kopiowania masowego do wykonania w jego własnej transakcji powoduje poszczególnych partii kopiowania masowego do wykonania w osobnej transakcji.  
  
> [!NOTE]
>  Ponieważ różnych instancji są wykonywane w innej transakcji, jeśli wystąpi błąd podczas operacji kopiowania zbiorczego, wszystkie wiersze w bieżącej partii zostanie wycofana, ale wiersze z poprzedniej partii pozostaną w bazie danych.  
  
 Następującej aplikacji konsoli przypomina poprzedni przykład, z jednym wyjątkiem: W tym przykładzie kopiowania masowego zarządza własną transakcji. Wszystkie instancje skopiowany do punktu błędu są zatwierdzone; wsadowe zawierające zduplikowany klucz zostanie wycofana i kopiowania masowego jest zatrzymany przed przetworzeniem innych partie.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` instrukcji, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Przy użyciu istniejącej transakcji  
 Można określić istniejącą <xref:System.Data.SqlClient.SqlTransaction> obiektu jako parametru w <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora. W takim przypadku kopiowania masowego jest wykonywane w istniejącej transakcji i nie wprowadzania zmian w stan transakcji (to znaczy go nie jest zatwierdzone ani przerwane). Umożliwia to aplikacji do uwzględnienia operacji kopiowania zbiorczego w transakcji z innymi operacjami bazy danych. Jednak jeśli nie określisz <xref:System.Data.SqlClient.SqlTransaction> obiektu i przekazać pustej referencji i połączenie ma aktywnych transakcji, jest zgłaszany wyjątek.  
  
 Jeśli trzeba przywrócić cały zbiorczego operacji kopiowania ponieważ wystąpi błąd lub jeśli kopiowania zbiorczego powinien zostać wykonany jako część większego procesu, który można wycofać, możesz podać <xref:System.Data.SqlClient.SqlTransaction> do obiektu <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora.  
  
 Następującej aplikacji konsoli jest podobny jak w pierwszym przykładzie (nietransakcyjnej) z jednym wyjątkiem: w tym przykładzie kopiowania masowego znajduje się w większych transakcji zewnętrznej. Gdy wystąpi błąd naruszenia dotyczącego klucza podstawowego, cała transakcja zostanie wycofana i żadne wiersze są dodawane do tabeli docelowej.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze użyj [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] `INSERT … SELECT` instrukcji, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Transakcja i operacje kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f6f0cbc9-f7bf-4d6e-875f-ad1ba0b4aa62
ms.openlocfilehash: f30974e020545a69ad20c03bc05ac6a28f289b01
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074628"
---
# <a name="transaction-and-bulk-copy-operations"></a>Transakcja i operacje kopiowania zbiorczego
Jako operacje izolowanej lub w ramach wielu transakcji krok można wykonać operacji kopiowania zbiorczego. Tę opcję, ostatnie pozwala wykonać kilka operacji kopiowania zbiorczego w ramach tej samej transakcji, a także wykonywać inne operacje bazy danych (na przykład wstawiania, aktualizacji i usuwania) przy zachowaniu możliwości Zatwierdź lub Wycofaj całą transakcję.  
  
 Domyślnie operacji kopiowania zbiorczego odbywa się jako operacja izolowanym. Operacji kopiowania zbiorczego występuje w sposób nietransakcyjnej z nie możliwości jego wycofania. Jeśli musisz wycofać całość lub część kopiowania masowego po wystąpieniu błędu, możesz użyć <xref:System.Data.SqlClient.SqlBulkCopy>-managed transakcji, wykonywać operacji kopiowania zbiorczego w ramach istniejącej transakcji lub być zarejestrowany w **System.Transactions** <xref:System.Transactions.Transaction>.  
  
## <a name="performing-a-non-transacted-bulk-copy-operation"></a>Wykonywanie operacji kopiowania zbiorczego nietransakcyjnej  
 Następująca aplikacja konsoli Pokazuje, co się stanie, gdy operacja kopiowania zbiorczego nietransakcyjnej napotka błąd zatrzymuje za pośrednictwem operacji.  
  
 W tym przykładzie tabeli źródłowej, jak i tabela docelowa zawiera `Identity` kolumnę o nazwie **ProductID**. Kod najpierw przygotowuje tabelę docelową, usuwając wszystkie wiersze, a następnie wstawianie pojedynczego wiersza, którego **ProductID** istnieje w tabeli źródłowej. Domyślnie nową wartość dla `Identity` kolumny jest generowany w tabeli docelowej dla każdego wiersza dodane. W tym przykładzie opcja jest ustawiona, gdy połączenie jest otwarte, która wymusza proces ładowania zbiorczego, używać `Identity` zamiast wartości z tabeli źródłowej.  
  
 Operacji kopiowania zbiorczego jest wykonywane przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy.BatchSize%2A> właściwość jest ustawiona na 10. Gdy operacja napotka nieprawidłowy wiersz, jest zgłaszany wyjątek. W tym przykładzie pierwsze operacji kopiowania zbiorczego jest nietransakcyjnej. Wszystkie instancje skopiowane aż do momentu wystąpienia błędu są zatwierdzone; zadanie wsadowe zawierające zduplikowany klucz zostanie wycofana i operacji kopiowania zbiorczego zostało zatrzymane przed przetworzeniem pozostałe partie.  
  
> [!NOTE]
>  W tym przykładzie nie będzie działać, chyba że utworzonego tabelami pracy zgodnie z opisem w [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zademonstrowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do użycia [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrukcję, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.DefaultTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.DefaultTransaction/VB/source.vb#1)]  
  
## <a name="performing-a-dedicated-bulk-copy-operation-in-a-transaction"></a>Wykonywanie operacji kopiowania zbiorczego dedykowanych w ramach transakcji  
 Domyślnie operacji kopiowania zbiorczego jest swój własny transakcji. Do wykonania operacji kopiowania zbiorczego dedykowane, należy utworzyć nowe wystąpienie klasy <xref:System.Data.SqlClient.SqlBulkCopy> przy użyciu parametrów połączenia lub użyj istniejącego <xref:System.Data.SqlClient.SqlConnection> obiektu braku aktywnej transakcji. W każdym scenariuszu operacji kopiowania zbiorczego tworzy i następnie zatwierdza lub powoduje wycofanie transakcji.  
  
 Możesz jawnie określić <xref:System.Data.SqlClient.SqlBulkCopyOptions.UseInternalTransaction> opcji <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora klasy, aby jawnie wywołać operacji kopiowania zbiorczego, można wykonać w jego własnej transakcji, powodując każdej partii operacji kopiowania zbiorczego można wykonać w osobnej transakcji.  
  
> [!NOTE]
>  Ponieważ różnych partii są wykonywane w innej transakcji, jeśli wystąpi błąd podczas operacji kopiowania zbiorczego, wszystkie wiersze w bieżącej partii zostanie wycofana, ale wiersze z poprzednich partii pozostaną w bazie danych.  
  
 Następująca aplikacja konsoli jest podobny do poprzedniego przykładu, z jednym wyjątkiem: W tym przykładzie operacji kopiowania zbiorczego zarządza własną transakcji. Wszystkie instancje skopiowane aż do momentu wystąpienia błędu są zatwierdzone; zadanie wsadowe zawierające zduplikowany klucz zostanie wycofana i operacji kopiowania zbiorczego zostało zatrzymane przed przetworzeniem pozostałe partie.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, chyba że utworzonego tabelami pracy zgodnie z opisem w [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zademonstrowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do użycia [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrukcję, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.InternalTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.InternalTransaction/VB/source.vb#1)]  
  
## <a name="using-existing-transactions"></a>Przy użyciu istniejących transakcji  
 Można określić istniejący <xref:System.Data.SqlClient.SqlTransaction> obiekt jako parametr w <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora. W takiej sytuacji operacji kopiowania zbiorczego odbywa się w istniejącej transakcji i wprowadzania nie zmian w stan transakcji (oznacza to, go nie jest zatwierdzone ani przerwane). Umożliwia to aplikacji, które mają zostać objęte operacji kopiowania zbiorczego transakcji z innymi operacjami bazy danych. Jednakże jeśli nie określisz <xref:System.Data.SqlClient.SqlTransaction> obiektu i przekazać odwołanie o wartości null, a połączenie ma aktywnej transakcji, zgłaszany jest wyjątek.  
  
 Jeśli musisz wycofać cała zbiorcza skopiować operacji, ponieważ wystąpi błąd lub jeśli kopiowania masowego powinien zostać wykonany jako część większego procesu, który można wycofać, można podać <xref:System.Data.SqlClient.SqlTransaction> obiekt <xref:System.Data.SqlClient.SqlBulkCopy> konstruktora.  
  
 Następująca aplikacja konsoli jest podobne do pierwszego (nietransakcyjnej), z jednym wyjątkiem: w tym przykładzie operacji kopiowania zbiorczego znajduje się w ramach transakcji większych i zewnętrznych. Gdy wystąpi błąd naruszenia klucza podstawowego, cała transakcja zostanie wycofana, a żadne wiersze są dodawane do tabeli docelowej.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, chyba że utworzonego tabelami pracy zgodnie z opisem w [Konfiguracja przykładu kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zademonstrowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do użycia [!INCLUDE[tsql](../../../../../includes/tsql-md.md)]`INSERT … SELECT` instrukcję, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.SqlTransaction#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.SqlTransaction/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

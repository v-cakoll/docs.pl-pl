---
title: Modyfikowanie danych w procedurach składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: d9dcda6b93fbc036818ad2ad43da4bfac95f6833
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-data-with-stored-procedures"></a>Modyfikowanie danych w procedurach składowanych
Procedury składowane można akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawów wyników lub wartości zwracanych. Poniższy przykład przedstawia sposób ADO.NET wysyła i odbiera dane wejściowe parametrów wyjściowych parametrów i wartości zwracane. Przykład wstawia nowego rekordu do tabeli, w których kolumna klucza podstawowego jest kolumną tożsamości w bazie danych programu SQL Server.  
  
> [!NOTE]
>  Jeśli używasz procedur składowanych serwera SQL, aby edytować lub usunąć danych przy użyciu <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej. Powoduje to, że liczba zmodyfikowanych wierszy zwrócił zero, który `DataAdapter` jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie wygenerowany.  
  
## <a name="example"></a>Przykład  
 Próbki używa następującą procedurę składowaną, aby wstawić nową kategorię do **Northwind** **kategorii** tabeli. Procedura składowana przyjmuje wartość **CategoryName** kolumny jako parametr wejściowy i używa SCOPE_IDENTITY() funkcji do pobrania nowa wartość pola tożsamości **CategoryID**i przywróć jego Parametr wyjściowy. Używa instrukcji RETURN @@ROWCOUNT funkcja zwraca liczbę wstawionych wierszy.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Poniższy przykład kodu wykorzystuje `InsertCategory` pokazanym powyżej jako źródło dla procedury składowanej <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Parametru wyjściowego zostaną odzwierciedlone w <xref:System.Data.DataSet> po rekord został wstawiony do bazy danych podczas `Update` metoda <xref:System.Data.SqlClient.SqlDataAdapter> jest wywoływana. Ten kod pobiera również wartość zwracaną.  
  
> [!NOTE]
>  Korzystając z <xref:System.Data.OleDb.OleDbDataAdapter>, należy określić parametry z <xref:System.Data.ParameterDirection> z **ReturnValue** przed innych parametrów.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

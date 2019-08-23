---
title: Modyfikowanie danych za pomocą procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: ebf5c61010a6f658d846ed435ea3a7d18d0d3832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934438"
---
# <a name="modifying-data-with-stored-procedures"></a>Modyfikowanie danych za pomocą procedur składowanych
Procedury składowane mogą akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawy wyników lub wartości zwracane. W poniższym przykładzie pokazano, jak ADO.NET wysyła i odbiera parametry wejściowe, parametry wyjściowe oraz wartości zwracane. Przykład wstawia nowy rekord do tabeli, w której kolumna klucza podstawowego jest kolumną tożsamości w bazie danych SQL Server.  
  
> [!NOTE]
> Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu programu <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że w definicji procedury składowanej nie używasz opcji SET NOCOUNT on. Powoduje to, że liczba zwracanych wierszy jest równa zero, `DataAdapter` która interpretuje jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszone zdarzenie.  
  
## <a name="example"></a>Przykład  
 Przykład używa następującej procedury składowanej, aby wstawić nową kategorię do tabeli kategorii **Northwind** . Procedura składowana przyjmuje wartość w kolumnie **CategoryName** jako parametr wejściowy i używa funkcji SCOPE_IDENTITY (), aby pobrać nową wartość pola tożsamości, **IDkategorii**i zwrócić go w parametrze wyjściowym. Instrukcja return używa funkcji @@ROWCOUNT , aby zwrócić liczbę wstawionych wierszy.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Poniższy przykład kodu używa `InsertCategory` procedury składowanej pokazanej powyżej jako źródła <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> dla elementu <xref:System.Data.SqlClient.SqlDataAdapter>. Parametr wyjściowy zostanie odzwierciedlony <xref:System.Data.DataSet> w po wstawieniu rekordu `Update` do bazy danych, <xref:System.Data.SqlClient.SqlDataAdapter> gdy wywoływana jest metoda obiektu. `@Identity` Kod pobiera również wartość zwracaną.  
  
> [!NOTE]
> Podczas używania <xref:System.Data.OleDb.OleDbDataAdapter>, należy określić parametry <xref:System.Data.ParameterDirection> z **ReturnValue** przed innymi parametrami.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

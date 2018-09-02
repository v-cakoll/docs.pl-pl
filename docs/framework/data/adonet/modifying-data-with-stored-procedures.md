---
title: Modyfikowanie danych za pomocą procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: c975913ab5df9c2e7f792ed73f8c5d20bdca1c5a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474041"
---
# <a name="modifying-data-with-stored-procedures"></a>Modyfikowanie danych za pomocą procedur składowanych
Procedury składowane może akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawów danych lub zwracanych wartości. Poniższy przykład ilustruje sposób ADO.NET wysyła i odbiera dane wejściowe parametrów wyjściowych parametry i zwracane wartości. Przykład Wstawia nowy rekord w tabeli, w których kolumna klucza podstawowego jest kolumną tożsamości w bazie danych programu SQL Server.  
  
> [!NOTE]
>  Jeśli używasz procedur składowanych serwera SQL Server, aby edytować lub usunąć dane za pomocą <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej. Powoduje to, że liczba zmodyfikowanych wierszy zwracane jako zera, które `DataAdapter` interpretuje jako konflikt współbieżności. W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszony.  
  
## <a name="example"></a>Przykład  
 W przykładzie użyto następującą procedurę składowaną, aby wstawić nową kategorię do **Northwind** **kategorie** tabeli. Procedura składowana przyjmuje wartość **CategoryName** kolumny jako parametr wejściowy oraz zastosowania SCOPE_IDENTITY() funkcji do pobrania nowej wartości pola tożsamości **CategoryID**i zwróć Parametr wyjściowy. Używa instrukcji RETURN @@ROWCOUNT funkcja zwraca liczby wierszy wstawionych.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Poniższy przykład kodu wykorzystuje `InsertCategory` powyżej jako źródła dla procedury składowanej <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Parametru wyjściowego zostaną odzwierciedlone w <xref:System.Data.DataSet> po rekord został wstawiony do bazy danych podczas `Update` metoda <xref:System.Data.SqlClient.SqlDataAdapter> jest wywoływana. Ten kod pobiera również wartość zwracaną.  
  
> [!NOTE]
>  Korzystając z <xref:System.Data.OleDb.OleDbDataAdapter>, należy tak określić parametry, z <xref:System.Data.ParameterDirection> z **ReturnValue** przed innych parametrów.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Wykonywanie polecenia](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

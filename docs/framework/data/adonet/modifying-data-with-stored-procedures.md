---
title: Modyfikowanie danych za pomocą procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: c868528edbccfeb32e6aca02c92b87d51bb0b829
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144770"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="53295-102">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="53295-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="53295-103">Procedury składowane może akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawów danych lub zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="53295-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="53295-104">Poniższy przykład ilustruje sposób ADO.NET wysyła i odbiera dane wejściowe parametrów wyjściowych parametry i zwracane wartości.</span><span class="sxs-lookup"><span data-stu-id="53295-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="53295-105">Przykład Wstawia nowy rekord w tabeli, w których kolumna klucza podstawowego jest kolumną tożsamości w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="53295-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53295-106">Jeśli używasz procedur składowanych serwera SQL Server, aby edytować lub usunąć dane za pomocą <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="53295-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="53295-107">Powoduje to, że liczba zmodyfikowanych wierszy zwracane jako zera, które `DataAdapter` interpretuje jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="53295-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="53295-108">W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="53295-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53295-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="53295-109">Example</span></span>  
 <span data-ttu-id="53295-110">W przykładzie użyto następującą procedurę składowaną, aby wstawić nową kategorię do **Northwind** **kategorie** tabeli.</span><span class="sxs-lookup"><span data-stu-id="53295-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="53295-111">Procedura składowana przyjmuje wartość **CategoryName** kolumny jako parametr wejściowy oraz zastosowania SCOPE_IDENTITY() funkcji do pobrania nowej wartości pola tożsamości **CategoryID**i zwróć Parametr wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="53295-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="53295-112">Używa instrukcji RETURN @@ROWCOUNT funkcja zwraca liczby wierszy wstawionych.</span><span class="sxs-lookup"><span data-stu-id="53295-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="53295-113">Poniższy przykład kodu wykorzystuje `InsertCategory` powyżej jako źródła dla procedury składowanej <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="53295-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="53295-114">`@Identity` Parametru wyjściowego zostaną odzwierciedlone w <xref:System.Data.DataSet> po rekord został wstawiony do bazy danych podczas `Update` metoda <xref:System.Data.SqlClient.SqlDataAdapter> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="53295-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="53295-115">Ten kod pobiera również wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="53295-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53295-116">Korzystając z <xref:System.Data.OleDb.OleDbDataAdapter>, należy tak określić parametry, z <xref:System.Data.ParameterDirection> z **ReturnValue** przed innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="53295-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="53295-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53295-117">See Also</span></span>  
 [<span data-ttu-id="53295-118">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="53295-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="53295-119">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="53295-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="53295-120">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="53295-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="53295-121">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="53295-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

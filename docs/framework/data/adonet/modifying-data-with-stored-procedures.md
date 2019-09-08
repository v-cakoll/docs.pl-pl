---
title: Modyfikowanie danych za pomocą procedur składowanych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 46c92301b717e285c4c18241f84d0069069c7bdc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783529"
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="96e2a-102">Modyfikowanie danych za pomocą procedur składowanych</span><span class="sxs-lookup"><span data-stu-id="96e2a-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="96e2a-103">Procedury składowane mogą akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawy wyników lub wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="96e2a-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="96e2a-104">W poniższym przykładzie pokazano, jak ADO.NET wysyła i odbiera parametry wejściowe, parametry wyjściowe oraz wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="96e2a-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="96e2a-105">Przykład wstawia nowy rekord do tabeli, w której kolumna klucza podstawowego jest kolumną tożsamości w bazie danych SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96e2a-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96e2a-106">Jeśli używasz SQL Server procedur składowanych do edytowania lub usuwania danych przy użyciu programu <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że w definicji procedury składowanej nie używasz opcji SET NOCOUNT on.</span><span class="sxs-lookup"><span data-stu-id="96e2a-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="96e2a-107">Powoduje to, że liczba zwracanych wierszy jest równa zero, `DataAdapter` która interpretuje jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="96e2a-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="96e2a-108">W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie zgłoszone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="96e2a-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96e2a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="96e2a-109">Example</span></span>  
 <span data-ttu-id="96e2a-110">Przykład używa następującej procedury składowanej, aby wstawić nową kategorię do tabeli kategorii **Northwind** .</span><span class="sxs-lookup"><span data-stu-id="96e2a-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="96e2a-111">Procedura składowana przyjmuje wartość w kolumnie **CategoryName** jako parametr wejściowy i używa funkcji SCOPE_IDENTITY (), aby pobrać nową wartość pola tożsamości, **IDkategorii**i zwrócić go w parametrze wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="96e2a-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="96e2a-112">Instrukcja return używa funkcji @@ROWCOUNT , aby zwrócić liczbę wstawionych wierszy.</span><span class="sxs-lookup"><span data-stu-id="96e2a-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="96e2a-113">Poniższy przykład kodu używa `InsertCategory` procedury składowanej pokazanej powyżej jako źródła <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> dla elementu <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="96e2a-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="96e2a-114">Parametr wyjściowy zostanie odzwierciedlony <xref:System.Data.DataSet> w po wstawieniu rekordu `Update` do bazy danych, <xref:System.Data.SqlClient.SqlDataAdapter> gdy wywoływana jest metoda obiektu. `@Identity`</span><span class="sxs-lookup"><span data-stu-id="96e2a-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="96e2a-115">Kod pobiera również wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="96e2a-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96e2a-116">Podczas używania <xref:System.Data.OleDb.OleDbDataAdapter>, należy określić parametry <xref:System.Data.ParameterDirection> z **ReturnValue** przed innymi parametrami.</span><span class="sxs-lookup"><span data-stu-id="96e2a-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="96e2a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96e2a-117">See also</span></span>

- [<span data-ttu-id="96e2a-118">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96e2a-118">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="96e2a-119">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="96e2a-119">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="96e2a-120">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="96e2a-120">Executing a Command</span></span>](executing-a-command.md)
- [<span data-ttu-id="96e2a-121">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="96e2a-121">ADO.NET Overview</span></span>](ado-net-overview.md)

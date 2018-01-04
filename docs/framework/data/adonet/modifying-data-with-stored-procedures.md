---
title: "Modyfikowanie danych w procedurach składowanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5df938d6d55786c12e6d73171d2a5cb33f80ea84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-data-with-stored-procedures"></a><span data-ttu-id="5c7df-102">Modyfikowanie danych w procedurach składowanych</span><span class="sxs-lookup"><span data-stu-id="5c7df-102">Modifying Data with Stored Procedures</span></span>
<span data-ttu-id="5c7df-103">Procedury składowane można akceptować dane jako parametry wejściowe i mogą zwracać dane jako parametry wyjściowe, zestawów wyników lub wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="5c7df-103">Stored procedures can accept data as input parameters and can return data as output parameters, result sets, or return values.</span></span> <span data-ttu-id="5c7df-104">Poniższy przykład przedstawia sposób ADO.NET wysyła i odbiera dane wejściowe parametrów wyjściowych parametrów i wartości zwracane.</span><span class="sxs-lookup"><span data-stu-id="5c7df-104">The sample below illustrates how ADO.NET sends and receives input parameters, output parameters, and return values.</span></span> <span data-ttu-id="5c7df-105">Przykład wstawia nowego rekordu do tabeli, w których kolumna klucza podstawowego jest kolumną tożsamości w bazie danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c7df-105">The example inserts a new record into a table where the primary key column is an identity column in a SQL Server database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c7df-106">Jeśli używasz procedur składowanych serwera SQL, aby edytować lub usunąć danych przy użyciu <xref:System.Data.SqlClient.SqlDataAdapter>, upewnij się, że nie używasz SET NOCOUNT ON w definicji procedury składowanej.</span><span class="sxs-lookup"><span data-stu-id="5c7df-106">If you are using SQL Server stored procedures to edit or delete data using a <xref:System.Data.SqlClient.SqlDataAdapter>, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="5c7df-107">Powoduje to, że liczba zmodyfikowanych wierszy zwrócił zero, który `DataAdapter` jako konflikt współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5c7df-107">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="5c7df-108">W takim przypadku <xref:System.Data.DBConcurrencyException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="5c7df-108">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c7df-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c7df-109">Example</span></span>  
 <span data-ttu-id="5c7df-110">Próbki używa następującą procedurę składowaną, aby wstawić nową kategorię do **Northwind** **kategorii** tabeli.</span><span class="sxs-lookup"><span data-stu-id="5c7df-110">The sample uses the following stored procedure to insert a new category into the **Northwind** **Categories** table.</span></span> <span data-ttu-id="5c7df-111">Procedura składowana przyjmuje wartość **CategoryName** kolumny jako parametr wejściowy i używa SCOPE_IDENTITY() funkcji do pobrania nowa wartość pola tożsamości **CategoryID**i przywróć jego Parametr wyjściowy.</span><span class="sxs-lookup"><span data-stu-id="5c7df-111">The stored procedure takes the value in the **CategoryName** column as an input parameter and uses the SCOPE_IDENTITY() function to retrieve the new value of the identity field, **CategoryID**, and return it in an output parameter.</span></span> <span data-ttu-id="5c7df-112">Używa instrukcji RETURN @@ROWCOUNT funkcja zwraca liczbę wstawionych wierszy.</span><span class="sxs-lookup"><span data-stu-id="5c7df-112">The RETURN statement uses the @@ROWCOUNT function to return the number of rows inserted.</span></span>  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 <span data-ttu-id="5c7df-113">Poniższy przykład kodu wykorzystuje `InsertCategory` pokazanym powyżej jako źródło dla procedury składowanej <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> z <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="5c7df-113">The following code example uses the `InsertCategory` stored procedure shown above as the source for the <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span> <span data-ttu-id="5c7df-114">`@Identity` Parametru wyjściowego zostaną odzwierciedlone w <xref:System.Data.DataSet> po rekord został wstawiony do bazy danych podczas `Update` metoda <xref:System.Data.SqlClient.SqlDataAdapter> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5c7df-114">The `@Identity` output parameter will be reflected in the <xref:System.Data.DataSet> after the record has been inserted into the database when the `Update` method of the <xref:System.Data.SqlClient.SqlDataAdapter> is called.</span></span> <span data-ttu-id="5c7df-115">Ten kod pobiera również wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="5c7df-115">The code also retrieves the return value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c7df-116">Korzystając z <xref:System.Data.OleDb.OleDbDataAdapter>, należy określić parametry z <xref:System.Data.ParameterDirection> z **ReturnValue** przed innych parametrów.</span><span class="sxs-lookup"><span data-stu-id="5c7df-116">When using the <xref:System.Data.OleDb.OleDbDataAdapter>, you must specify parameters with a <xref:System.Data.ParameterDirection> of **ReturnValue** before the other parameters.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5c7df-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c7df-117">See Also</span></span>  
 [<span data-ttu-id="5c7df-118">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5c7df-118">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="5c7df-119">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="5c7df-119">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="5c7df-120">Wykonywanie polecenia</span><span class="sxs-lookup"><span data-stu-id="5c7df-120">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [<span data-ttu-id="5c7df-121">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="5c7df-121">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

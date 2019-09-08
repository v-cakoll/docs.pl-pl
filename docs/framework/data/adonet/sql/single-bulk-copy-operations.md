---
title: Pojedyncze operacje kopiowania zbiorczego
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
ms.openlocfilehash: 05e3cf25352e731d320061001f08a835cd520b15
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780931"
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="b1791-102">Pojedyncze operacje kopiowania zbiorczego</span><span class="sxs-lookup"><span data-stu-id="b1791-102">Single Bulk Copy Operations</span></span>

<span data-ttu-id="b1791-103">Najprostszym podejściem do wykonywania SQL Server operacji kopiowania zbiorczego jest wykonanie pojedynczej operacji w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b1791-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="b1791-104">Domyślnie operacja kopiowania zbiorczego jest wykonywana jako operacja izolowana: operacja kopiowania odbywa się w sposób nietransakcyjny, bez możliwości przywrócenia jej z powrotem.</span><span class="sxs-lookup"><span data-stu-id="b1791-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>

> [!NOTE]
> <span data-ttu-id="b1791-105">Jeśli chcesz wycofać całość lub część kopiowania zbiorczego, gdy wystąpi błąd, możesz użyć <xref:System.Data.SqlClient.SqlBulkCopy>transakcji zarządzanej lub wykonać operację kopiowania zbiorczego w ramach istniejącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="b1791-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="b1791-106">**SqlBulkCopy** również będzie współdziałać z usługą <xref:System.Transactions> , jeśli połączenie zostanie zarejestrowane (niejawnie lub jawnie) w transakcji **System. Transactions** .</span><span class="sxs-lookup"><span data-stu-id="b1791-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>
>
> <span data-ttu-id="b1791-107">Aby uzyskać więcej informacji, zobacz [operacje transakcji i kopiowania zbiorczego](transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b1791-107">For more information, see [Transaction and Bulk Copy Operations](transaction-and-bulk-copy-operations.md).</span></span>

<span data-ttu-id="b1791-108">Ogólne kroki wykonywania operacji kopiowania zbiorczego są następujące:</span><span class="sxs-lookup"><span data-stu-id="b1791-108">The general steps for performing a bulk copy operation are as follows:</span></span>

1. <span data-ttu-id="b1791-109">Nawiąż połączenie z serwerem źródłowym i uzyskaj dane, które mają zostać skopiowane.</span><span class="sxs-lookup"><span data-stu-id="b1791-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="b1791-110">Dane mogą również pochodzić z innych źródeł, jeśli można je pobrać z <xref:System.Data.IDataReader> obiektu lub. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="b1791-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>

2. <span data-ttu-id="b1791-111">Nawiąż połączenie z serwerem docelowym (chyba że chcesz, aby **SqlBulkCopy** się nawiązać połączenie).</span><span class="sxs-lookup"><span data-stu-id="b1791-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>

3. <span data-ttu-id="b1791-112"><xref:System.Data.SqlClient.SqlBulkCopy> Utwórz obiekt, ustawiając wszelkie niezbędne właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1791-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>

4. <span data-ttu-id="b1791-113">Ustaw właściwość **DestinationTableName** , aby wskazać tabelę docelową dla operacji wstawiania zbiorczego.</span><span class="sxs-lookup"><span data-stu-id="b1791-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>

5. <span data-ttu-id="b1791-114">Wywołaj jedną z metod **WriteToServer** .</span><span class="sxs-lookup"><span data-stu-id="b1791-114">Call one of the **WriteToServer** methods.</span></span>

6. <span data-ttu-id="b1791-115">Opcjonalnie należy zaktualizować właściwości i ponownie wywołać **WriteToServer** w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b1791-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>

7. <span data-ttu-id="b1791-116">Wywołaj <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>lub zawiń operacje kopiowania zbiorczego `Using` w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b1791-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>

> [!CAUTION]
> <span data-ttu-id="b1791-117">Zalecamy, aby typy danych kolumny źródłowej i docelowej były zgodne.</span><span class="sxs-lookup"><span data-stu-id="b1791-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="b1791-118">Jeśli typy danych nie są zgodne, **SqlBulkCopy** próbuje skonwertować każdą wartość źródłową na docelowy typ danych przy użyciu reguł używanych przez <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="b1791-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="b1791-119">Konwersje mogą mieć wpływ na wydajność, a także powodować nieoczekiwane błędy.</span><span class="sxs-lookup"><span data-stu-id="b1791-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="b1791-120">Na przykład `Double` typ danych można przekonwertować `Decimal` na typ danych w większości czasu, ale nie zawsze.</span><span class="sxs-lookup"><span data-stu-id="b1791-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>

## <a name="example"></a><span data-ttu-id="b1791-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1791-121">Example</span></span>

<span data-ttu-id="b1791-122">W poniższej aplikacji konsolowej pokazano, <xref:System.Data.SqlClient.SqlBulkCopy> jak załadować dane przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="b1791-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="b1791-123">W tym przykładzie <xref:System.Data.SqlClient.SqlDataReader> jest używany do kopiowania danych z tabeli **Production. Product** w bazie danych SQL Server **AdventureWorks** do podobnej tabeli w tej samej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b1791-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the SQL Server **AdventureWorks** database to a similar table in the same database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1791-124">Ten przykład nie zostanie uruchomiony, jeśli nie utworzono tabel roboczych, zgodnie z opisem w [przykładowej konfiguracji kopiowania zbiorczego](bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="b1791-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="b1791-125">Ten kod jest dostarczany w celu przedstawienia składni tylko za pomocą **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="b1791-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="b1791-126">Jeśli tabele źródłowe i docelowe znajdują się w tym samym wystąpieniu SQL Server, łatwiej i szybciej można używać instrukcji języka Transact-SQL `INSERT … SELECT` do kopiowania danych.</span><span class="sxs-lookup"><span data-stu-id="b1791-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>

[!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
[!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]

## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="b1791-127">Wykonywanie operacji kopiowania zbiorczego za pomocą języka Transact-SQL i klasy poleceń</span><span class="sxs-lookup"><span data-stu-id="b1791-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>

<span data-ttu-id="b1791-128">Poniższy przykład ilustruje sposób używania <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metody do wykonywania instrukcji BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="b1791-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>

> [!NOTE]
> <span data-ttu-id="b1791-129">Ścieżka pliku dla źródła danych jest określana względem serwera.</span><span class="sxs-lookup"><span data-stu-id="b1791-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="b1791-130">Proces serwera musi mieć dostęp do tej ścieżki w celu pomyślnego wykonania operacji kopiowania zbiorczego.</span><span class="sxs-lookup"><span data-stu-id="b1791-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>

```vb
Using connection As SqlConnection = New SqlConnection(connectionString)
Dim queryString As String = _
    "BULK INSERT Northwind.dbo.[Order Details] FROM " & _
    "'f:\mydata\data.tbl' WITH (FORMATFILE='f:\mydata\data.fmt' )"
connection.Open()
SqlCommand command = New SqlCommand(queryString, connection);

command.ExecuteNonQuery()
End Using
```

```csharp
using (SqlConnection connection = New SqlConnection(connectionString))
{
string queryString =  "BULK INSERT Northwind.dbo.[Order Details] " +
    "FROM 'f:\mydata\data.tbl' " +
    "WITH ( FORMATFILE='f:\mydata\data.fmt' )";
connection.Open();
SqlCommand command = new SqlCommand(queryString, connection);

command.ExecuteNonQuery();
}
```

## <a name="see-also"></a><span data-ttu-id="b1791-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1791-131">See also</span></span>

- [<span data-ttu-id="b1791-132">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="b1791-132">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="b1791-133">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b1791-133">ADO.NET Overview</span></span>](../ado-net-overview.md)

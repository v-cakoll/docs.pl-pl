---
title: Operacje kopiowania masowego pojedynczego
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
ms.assetid: 5e7ff0be-3f23-4996-a92c-bd54d65c3836
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 001bd24d46d0106887ad693534c51d152eedfb1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="single-bulk-copy-operations"></a><span data-ttu-id="e20d1-102">Operacje kopiowania masowego pojedynczego</span><span class="sxs-lookup"><span data-stu-id="e20d1-102">Single Bulk Copy Operations</span></span>
<span data-ttu-id="e20d1-103">Najprostsza metoda wykonywanie operacji kopiowania zbiorczego SQL Server jest na wykonanie jednej operacji na bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e20d1-103">The simplest approach to performing a SQL Server bulk copy operation is to perform a single operation against a database.</span></span> <span data-ttu-id="e20d1-104">Domyślnie kopiowania masowego odbywa się jako operacja izolowanego: operacja kopiowania odbywa się w sposób obsługi nietransakcyjnego z udostępnieniem jej nie możliwości tworzenia kopii.</span><span class="sxs-lookup"><span data-stu-id="e20d1-104">By default, a bulk copy operation is performed as an isolated operation: the copy operation occurs in a non-transacted way, with no opportunity for rolling it back.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20d1-105">Jeśli chcesz wycofać całość lub część kopiowania zbiorczego po wystąpieniu błędu, można użyć <xref:System.Data.SqlClient.SqlBulkCopy>-zarządzane transakcji lub wykonania operacji kopiowania zbiorczego w istniejącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="e20d1-105">If you need to roll back all or part of the bulk copy when an error occurs, you can either use a <xref:System.Data.SqlClient.SqlBulkCopy>-managed transaction, or perform the bulk copy operation within an existing transaction.</span></span> <span data-ttu-id="e20d1-106">**SqlBulkCopy** będzie również współpracować z <xref:System.Transactions> Jeśli połączenie jest zarejestrowane (jawnie ani niejawnie) do **System.Transactions** transakcji.</span><span class="sxs-lookup"><span data-stu-id="e20d1-106">**SqlBulkCopy** will also work with <xref:System.Transactions> if the connection is enlisted (implicitly or explicitly) into a **System.Transactions** transaction.</span></span>  
>   
>  <span data-ttu-id="e20d1-107">Aby uzyskać więcej informacji, zobacz [transakcji i operacje kopiowania masowego](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e20d1-107">For more information, see [Transaction and Bulk Copy Operations](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md).</span></span>  
  
 <span data-ttu-id="e20d1-108">Ogólne kroki do wykonania operacji kopiowania zbiorczego są następujące:</span><span class="sxs-lookup"><span data-stu-id="e20d1-108">The general steps for performing a bulk copy operation are as follows:</span></span>  
  
1.  <span data-ttu-id="e20d1-109">Nawiąż połączenie z serwerem źródłowym i uzyskać dane do skopiowania.</span><span class="sxs-lookup"><span data-stu-id="e20d1-109">Connect to the source server and obtain the data to be copied.</span></span> <span data-ttu-id="e20d1-110">Dane mogą również pochodzić z innych źródeł, jeśli będzie można pobrać z <xref:System.Data.IDataReader> lub <xref:System.Data.DataTable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e20d1-110">Data can also come from other sources, if it can be retrieved from an <xref:System.Data.IDataReader> or <xref:System.Data.DataTable> object.</span></span>  
  
2.  <span data-ttu-id="e20d1-111">Nawiąż połączenie z serwerem docelowym (chyba że chcesz **SqlBulkCopy** ustanowić połączenie dla Ciebie).</span><span class="sxs-lookup"><span data-stu-id="e20d1-111">Connect to the destination server (unless you want **SqlBulkCopy** to establish a connection for you).</span></span>  
  
3.  <span data-ttu-id="e20d1-112">Utwórz <xref:System.Data.SqlClient.SqlBulkCopy> obiektu wszelkie wymagane właściwości.</span><span class="sxs-lookup"><span data-stu-id="e20d1-112">Create a <xref:System.Data.SqlClient.SqlBulkCopy> object, setting any necessary properties.</span></span>  
  
4.  <span data-ttu-id="e20d1-113">Ustaw **DestinationTableName** Właściwość wskazująca tabeli docelowej do zbiorczego operacji wstawiania.</span><span class="sxs-lookup"><span data-stu-id="e20d1-113">Set the **DestinationTableName** property to indicate the target table for the bulk insert operation.</span></span>  
  
5.  <span data-ttu-id="e20d1-114">Wywoływanie jednego z **WriteToServer** metody.</span><span class="sxs-lookup"><span data-stu-id="e20d1-114">Call one of the **WriteToServer** methods.</span></span>  
  
6.  <span data-ttu-id="e20d1-115">Opcjonalnie, zaktualizuj właściwości i wywołanie **WriteToServer** ponownie w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e20d1-115">Optionally, update properties and call **WriteToServer** again as necessary.</span></span>  
  
7.  <span data-ttu-id="e20d1-116">Wywołanie <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, lub zawijać operacji kopiowania zbiorczego w obrębie `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e20d1-116">Call <xref:System.Data.SqlClient.SqlBulkCopy.Close%2A>, or wrap the bulk copy operations within a `Using` statement.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e20d1-117">Zaleca się, że typy danych kolumn źródłowa i docelowa są zgodne.</span><span class="sxs-lookup"><span data-stu-id="e20d1-117">We recommend that the source and target column data types match.</span></span> <span data-ttu-id="e20d1-118">Jeśli typy danych są niezgodne, **SqlBulkCopy** próbuje przekonwertować wartości każdego źródłowego na docelowy typ danych, przy użyciu reguł stosowanych przez <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="e20d1-118">If the data types do not match, **SqlBulkCopy** attempts to convert each source value to the target data type, using the rules employed by <xref:System.Data.SqlClient.SqlParameter.Value%2A>.</span></span> <span data-ttu-id="e20d1-119">Konwersje może wpłynąć na wydajność, a także może spowodować nieoczekiwane błędy.</span><span class="sxs-lookup"><span data-stu-id="e20d1-119">Conversions can affect performance, and also can result in unexpected errors.</span></span> <span data-ttu-id="e20d1-120">Na przykład `Double` można przekonwertować na typ danych `Decimal` większość typów danych o czasie, ale nie zawsze.</span><span class="sxs-lookup"><span data-stu-id="e20d1-120">For example, a `Double` data type can be converted to a `Decimal` data type most of the time, but not always.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e20d1-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20d1-121">Example</span></span>  
 <span data-ttu-id="e20d1-122">Następującej aplikacji konsoli Pokazuje, jak załadować dane przy użyciu <xref:System.Data.SqlClient.SqlBulkCopy> klasy.</span><span class="sxs-lookup"><span data-stu-id="e20d1-122">The following console application demonstrates how to load data using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="e20d1-123">W tym przykładzie <xref:System.Data.SqlClient.SqlDataReader> służy do kopiowania danych z **Production.Product** tabeli w [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] **AdventureWorks** bazy danych do tabeli podobne w tej samej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e20d1-123">In this example, a <xref:System.Data.SqlClient.SqlDataReader> is used to copy data from the **Production.Product** table in the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]**AdventureWorks** database to a similar table in the same database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e20d1-124">W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="e20d1-124">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="e20d1-125">Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko.</span><span class="sxs-lookup"><span data-stu-id="e20d1-125">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="e20d1-126">Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do używania języka Transact-SQL `INSERT … SELECT` instrukcji, aby skopiować dane.</span><span class="sxs-lookup"><span data-stu-id="e20d1-126">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/CS/source.cs#1)]
 [!code-vb[DataWorks BulkCopy.Single#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks BulkCopy.Single/VB/source.vb#1)]  
  
## <a name="performing-a-bulk-copy-operation-using-transact-sql-and-the-command-class"></a><span data-ttu-id="e20d1-127">Wykonywanie operacji kopiowania zbiorczego przy użyciu języka Transact-SQL i klasy poleceń</span><span class="sxs-lookup"><span data-stu-id="e20d1-127">Performing a Bulk Copy Operation Using Transact-SQL and the Command Class</span></span>  
 <span data-ttu-id="e20d1-128">Poniższy przykład przedstawia sposób użycia <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> metodę można wykonać instrukcji BULK INSERT.</span><span class="sxs-lookup"><span data-stu-id="e20d1-128">The following example illustrates how to use the <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A> method to execute the BULK INSERT statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e20d1-129">Ścieżka pliku źródła danych jest określana względem serwera.</span><span class="sxs-lookup"><span data-stu-id="e20d1-129">The file path for the data source is relative to the server.</span></span> <span data-ttu-id="e20d1-130">Proces serwera musi mieć dostęp do tej ścieżki w kolejności dla operacji kopiowania zbiorczego powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e20d1-130">The server process must have access to that path in order for the bulk copy operation to succeed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e20d1-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e20d1-131">See Also</span></span>  
 [<span data-ttu-id="e20d1-132">Operacje kopiowania masowego w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="e20d1-132">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="e20d1-133">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="e20d1-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Podczas pobierania danych przy użyciu elementu DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="38509-102">Podczas pobierania danych przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="38509-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="38509-103">Podczas pobierania danych przy użyciu **DataReader** obejmuje utworzenie wystąpienia **polecenia** obiektu, a następnie utworzenie **DataReader** przez wywołanie metody  **Command.ExecuteReader** pobieranie wierszy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="38509-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="38509-104">Poniższy przykład przedstawia przy użyciu **DataReader** gdzie `reader` reprezentuje prawidłową DataReader i `command` reprezentuje prawidłowy obiekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="38509-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="38509-105">Możesz użyć **odczytu** metody **DataReader** obiektu można uzyskać wiersza z wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="38509-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="38509-106">Dostęp do każdej kolumny wiersza zwrócone przez przekazanie nazwa lub numer porządkowy odwołania do kolumny, która ma **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="38509-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="38509-107">Jednak w celu uzyskania najlepszej wydajności **DataReader** udostępnia szereg metod, które umożliwiają dostęp do wartości w kolumnie w ich typach danych natywnych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="38509-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="38509-108">Aby uzyskać listę metod dostępu typu danych specyficznych dla dostawcy **DataReaders**, zobacz <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="38509-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="38509-109">Przy użyciu metody typu dostępu, przy założeniu podstawowy typ danych jest znany, zmniejsza ilość konwersji typu wymagane podczas pobierania wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="38509-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38509-110">Wersja systemu Windows Server 2003 programu .NET Framework zawiera dodatkowe właściwości dla **DataReader**, **HasRows**, co pozwala określić, czy **DataReader**zwróciło żadnych wyników przed dokonaniem odczytu z niego.</span><span class="sxs-lookup"><span data-stu-id="38509-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="38509-111">Poniższy przykład kodu iteruje **DataReader** obiektu i zwraca dwie kolumny z każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="38509-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="38509-112">**DataReader** zapewnia Niebuforowane strumień danych, które umożliwia procedurach logiki wydajnie sekwencyjnie przetworzyć wyniki ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="38509-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="38509-113">**DataReader** jest dobrym rozwiązaniem, gdy trwa pobieranie dużych ilości danych, ponieważ dane nie są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="38509-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="38509-114">Zamykanie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="38509-114">Closing the DataReader</span></span>  
 <span data-ttu-id="38509-115">Zawsze należy wywołać **Zamknij** metody po zakończeniu przy użyciu **DataReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="38509-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="38509-116">Jeśli Twoje **polecenia** dane wyjściowe zawierają parametrów lub zwracanych wartości nie będą one dostępne do **DataReader** jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="38509-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="38509-117">Należy pamiętać, że podczas **DataReader** jest otwarty, **połączenia** jest używany wyłącznie przez to **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="38509-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="38509-118">Nie można wykonać żadnych poleceń **połączenia**, łącznie z utworzyć inny **DataReader**, aż do oryginalnej **DataReader** jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="38509-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38509-119">Nie wywołuj **Zamknij** lub **Dispose** na **połączenia**, **DataReader**, lub innego obiektu zarządzanego w **Finalize**  metody klasy.</span><span class="sxs-lookup"><span data-stu-id="38509-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="38509-120">W finalizator zwolnić tylko niezarządzane zasoby, które bezpośrednio należą do klasy.</span><span class="sxs-lookup"><span data-stu-id="38509-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="38509-121">Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj **Finalize** metody w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="38509-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="38509-122">Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="38509-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="38509-123">Pobieranie wielu zestawów wyników przy użyciu NextResult</span><span class="sxs-lookup"><span data-stu-id="38509-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="38509-124">Jeśli wiele zestawów wyników są zwracane, **DataReader** zapewnia **NextResult** Ustawia metodę do iteracji wynik w kolejności.</span><span class="sxs-lookup"><span data-stu-id="38509-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="38509-125">W poniższym przykładzie przedstawiono <xref:System.Data.SqlClient.SqlDataReader> przetwarzania wyników dwóch instrukcji "SELECT" przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="38509-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="38509-126">Uzyskiwanie informacji schematu z elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="38509-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="38509-127">Gdy **DataReader** jest otwarty, możesz pobierać schematu informacje o bieżącym wyniku ustawić za pomocą **GetSchemaTable** metody.</span><span class="sxs-lookup"><span data-stu-id="38509-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="38509-128">**GetSchemaTable** zwraca <xref:System.Data.DataTable> obiektu wypełnione wiersze i kolumny, które zawierają informacje o schemacie dla bieżącego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="38509-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="38509-129">**DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="38509-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="38509-130">Każda kolumna wiersza tabeli schematu mapowany na właściwość kolumny zwracane w zestaw wyników, których **ColumnName** jest nazwą właściwości i wartość w kolumnie jest wartością właściwości.</span><span class="sxs-lookup"><span data-stu-id="38509-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="38509-131">Poniższy przykład kodu zapisuje informacji schematu dla **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="38509-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="38509-132">Praca z OLE DB rozdziałach</span><span class="sxs-lookup"><span data-stu-id="38509-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="38509-133">Hierarchiczna zestawów wierszy lub działami (typ OLE DB **DBTYPE_HCHAPTER**, typu ADO **adChapter**) można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="38509-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="38509-134">Gdy kwerendę, która obejmuje rozdział są zwracane jako **DataReader**, rozdziału jest zwracana jako kolumny w tym **DataReader** i jest udostępniany jako **DataReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="38509-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="38509-135">ADO.NET **DataSet** mogą służyć do reprezentowania hierarchiczne zestawy wierszy przy użyciu relacji nadrzędny podrzędny między tabelami.</span><span class="sxs-lookup"><span data-stu-id="38509-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="38509-136">Aby uzyskać więcej informacji, zobacz [zestawów danych, DataTables i DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="38509-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="38509-137">Poniższy przykład kodu wykorzystuje dostawcy MSDataShape do generowania kolumną rozdziału zamówień dla każdego klienta w listę klientów.</span><span class="sxs-lookup"><span data-stu-id="38509-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="38509-138">Zwracania wyników z kursorami REF Oracle</span><span class="sxs-lookup"><span data-stu-id="38509-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="38509-139">.NET Framework Data Provider for Oracle obsługuje Oracle REF kursory zwracanie wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="38509-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="38509-140">Oracle REF CURSOR jest zwracana jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="38509-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="38509-141">Możesz pobrać **OracleDataReader** obiektu, które reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody, a także określić <xref:System.Data.OracleClient.OracleCommand> zwracającą co najmniej jeden kursory REF Oracle jako  **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używaną do wypełniania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="38509-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="38509-142">Aby uzyskać dostęp do REF CURSOR zwracane ze źródła danych Oracle, należy utworzyć **OracleCommand** zapytania i Dodaj parametr wyjściowy, który odwołuje się do REF CURSOR do **parametry** kolekcji Twojego **OracleCommand**.</span><span class="sxs-lookup"><span data-stu-id="38509-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="38509-143">Nazwa parametru musi odpowiadać nazwie parametru REF CURSOR w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="38509-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="38509-144">Ustaw typ parametru **OracleType.Cursor**.</span><span class="sxs-lookup"><span data-stu-id="38509-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="38509-145">**ExecuteReader** metody z **OracleCommand** zwróci **OracleDataReader** dla REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="38509-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="38509-146">Jeśli Twoje **OracleCommand** zwraca wiele KURSORY REF, Dodaj wiele parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="38509-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="38509-147">Dostęp do różnych kursorów REF wywołując **OracleCommand.ExecuteReader** metody.</span><span class="sxs-lookup"><span data-stu-id="38509-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="38509-148">Wywołanie **ExecuteReader** zwraca **OracleDataReader** odwołuje się do pierwszej REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="38509-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="38509-149">Następnie można wywołać **OracleDataReader.NextResult** metodę dostępu kolejnych kursory REF.</span><span class="sxs-lookup"><span data-stu-id="38509-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="38509-150">Mimo że parametrów w Twojej **OracleCommand.Parameters** dopasowania kolekcji REF CURSOR output parametry nazwę **OracleDataReader** uzyskuje dostęp do nich w kolejności, że zostały one dodane do  **Parametry** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38509-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="38509-151">Rozważmy na przykład następujący pakiet Oracle i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="38509-151">For example, consider the following Oracle package and package body.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="38509-152">Poniższy kod tworzy **OracleCommand** zwracającą kursory REF z poprzednim pakiecie Oracle, dodając dwa parametry typu **OracleType.Cursor** do **parametry** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="38509-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="38509-153">Poniższy kod zwraca wyniki poprzedniego przy użyciu polecenia **odczytu** i **NextResult** metody **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="38509-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="38509-154">Parametry REF CURSOR są zwracane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="38509-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="38509-155">W poniższym przykładzie użyto poprzednie polecenie, aby wypełnić **DataSet** z wynikami pakietu programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="38509-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38509-156">Aby uniknąć **overflowexception —**, zalecamy również obsługiwać żadnych konwersja z typu numer Oracle do prawidłowego typu .NET Framework przed zapisaniem wartości w **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="38509-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="38509-157">Można użyć **FillError** zdarzeń, aby ustalić, czy **overflowexception —** wystąpił.</span><span class="sxs-lookup"><span data-stu-id="38509-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="38509-158">Aby uzyskać więcej informacji na temat **FillError** zdarzeń, zobacz [obsługi zdarzeń element DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="38509-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a><span data-ttu-id="38509-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38509-159">See Also</span></span>  
 [<span data-ttu-id="38509-160">Praca z DataReaders</span><span class="sxs-lookup"><span data-stu-id="38509-160">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="38509-161">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="38509-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="38509-162">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="38509-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="38509-163">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="38509-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="38509-164">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="38509-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

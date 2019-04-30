---
title: Pobieranie danych przy użyciu elementu DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 8063f239123ec1a2f2650adf9d76f7ceaaa50673
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664263"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="dce32-102">Pobierają dane przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dce32-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="dce32-103">Do pobierania danych przy użyciu **DataReader**, Utwórz wystąpienie obiektu **polecenia** obiektu, a następnie utwórz **DataReader** przez wywołanie metody **Command.ExecuteReader**  pobieranie wierszy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dce32-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="dce32-104">**DataReader** zapewnia Niebuforowane strumienia danych, które umożliwia procedurach logikę w celu wydajnego przetwarzania wyników ze źródła danych, po kolei.</span><span class="sxs-lookup"><span data-stu-id="dce32-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="dce32-105">**DataReader** to dobry wybór w przypadku, gdy w przypadku pobierania dużych ilości danych, ponieważ dane nie są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="dce32-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="dce32-106">Poniższy przykład ilustruje użycie **DataReader**, gdzie `reader` reprezentuje prawidłowy element DataReader i `command` reprezentuje prawidłowy obiekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="dce32-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="dce32-107">Użyj **DataReader.Read** metodę, aby uzyskać wiersz z wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="dce32-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="dce32-108">Dostęp do poszczególnych kolumn zwracany wiersz, przekazując nazwę lub liczbę porządkową kolumny do **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dce32-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="dce32-109">Jednak w celu uzyskania najlepszej wydajności **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości w kolumnie w ich typach danych natywnych (**GetDateTime**, **GetDouble**, **Getguid —**, **GetInt32**i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="dce32-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="dce32-110">Lista metod typizowane metody dostępu do danych specyficznych dla dostawcy **DataReaders**, zobacz <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dce32-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="dce32-111">Za pomocą metody dostępu wpisane, gdy wiesz, podstawowych danych typu zmniejsza konwersji typu wymagane podczas pobierania wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="dce32-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="dce32-112">Poniższy przykład wykonuje iterację przez **DataReader** obiektu i zwraca dwie kolumny z każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="dce32-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="dce32-113">Zamykanie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dce32-113">Closing the DataReader</span></span>  
 <span data-ttu-id="dce32-114">Zawsze wywołuj **Zamknij** metody po zakończeniu korzystania z **DataReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="dce32-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="dce32-115">Jeśli Twoje **polecenia** dane wyjściowe zawierają parametrów lub zwracanych wartości tych wartości nie są dostępne do momentu **DataReader** jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="dce32-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="dce32-116">Gdy **DataReader** jest otwarty, **połączenia** jest używana wyłącznie przez to **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dce32-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="dce32-117">Nie można wykonać żadnych poleceń **połączenia**, takich jak tworzenie drugiego **DataReader**, aż do oryginalnego **DataReader** jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="dce32-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dce32-118">Nie wywołuj **Zamknij** lub **Dispose** na **połączenia**, **DataReader**, lub inne obiekt zarządzany w **Finalize**  metody klasy.</span><span class="sxs-lookup"><span data-stu-id="dce32-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="dce32-119">W finalizatora zwolnić tylko niezarządzane zasoby, które należą bezpośrednio do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="dce32-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="dce32-120">Jeśli klasa nie ma żadnych niezarządzanych zasobów, nie dołączaj **Finalize** metody w swojej definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="dce32-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="dce32-121">Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="dce32-121">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="dce32-122">Trwa pobieranie wielu wyników ustawia przy użyciu NextResult</span><span class="sxs-lookup"><span data-stu-id="dce32-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="dce32-123">Jeśli **DataReader** zwraca wiele zestawów wyników, wywołanie **NextResult** metodę, aby wykonać iterację wynik ustawia sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="dce32-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="dce32-124">W poniższym przykładzie przedstawiono <xref:System.Data.SqlClient.SqlDataReader> przetwarzania wyników dwóch instrukcji "SELECT" przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dce32-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="dce32-125">Pobieranie informacji o schemacie z elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dce32-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="dce32-126">Gdy **DataReader** jest otwarty, możesz pobrać informacji o schemacie o wyniku bieżącego zestawu przy użyciu **GetSchemaTable** metody.</span><span class="sxs-lookup"><span data-stu-id="dce32-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="dce32-127">**GetSchemaTable** zwraca <xref:System.Data.DataTable> obiektu wypełnione z wierszami i kolumnami, które zawierają informacje o schemacie dla bieżącego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="dce32-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="dce32-128">**DataTable** zawiera ona jeden wiersz dla każdej kolumny zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="dce32-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="dce32-129">Każda kolumna tabeli schematów mapuje właściwość kolumny zwracane w wiersze wynik ustawione, gdzie **ColumnName** jest nazwę właściwości, a wartość kolumny jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="dce32-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="dce32-130">Poniższy przykład zapisuje się informacji o schemacie dla **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dce32-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="dce32-131">Praca z działami OLE DB</span><span class="sxs-lookup"><span data-stu-id="dce32-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="dce32-132">Hierarchiczna zestawów wierszy lub rozdziałów (typ OLE DB **DBTYPE_HCHAPTER**, typ ADO **adChapter**), można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dce32-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="dce32-133">Gdy zapytanie, które zawiera rozdział jest zwracana jako **DataReader**, rozdziału jest zwracana jako kolumny w tym **DataReader** i jest udostępniany jako **DataReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="dce32-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="dce32-134">ADO.NET **DataSet** może również służyć do reprezentowania hierarchiczne zestawy wierszy przy użyciu relacji nadrzędny podrzędny między tabelami.</span><span class="sxs-lookup"><span data-stu-id="dce32-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="dce32-135">Aby uzyskać więcej informacji, zobacz [DataSet, DataTable i DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="dce32-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="dce32-136">Poniższy przykład kodu używa dostawcy MSDataShape do generowania kolumny rozdziałów zamówień dla każdego klienta na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="dce32-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="dce32-137">Zwracanie wyników z Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="dce32-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="dce32-138">.NET Framework Data Provider for Oracle obsługuje Oracle REF CURSOR do zwrócenia wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="dce32-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="dce32-139">Oracle REF CURSOR jest zwracana jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dce32-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="dce32-140">Możesz pobrać <xref:System.Data.OracleClient.OracleDataReader> obiekt, który reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dce32-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="dce32-141">Można również określić <xref:System.Data.OracleClient.OracleCommand> zwracającego co najmniej jeden Oracle REF CURSOR jako **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używany do wypełniania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="dce32-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="dce32-142">Dostępu REF CURSOR zwrócone ze źródła danych Oracle, należy utworzyć <xref:System.Data.OracleClient.OracleCommand> dla zapytania i Dodaj parametr wyjściowy, odwołujący się do kursora REF <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcję usługi <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="dce32-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="dce32-143">Nazwa parametru musi odpowiadać Nazwa parametru REF CURSOR w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="dce32-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="dce32-144">Ustaw typ parametru, aby <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dce32-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dce32-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Metody usługi <xref:System.Data.OracleClient.OracleCommand> zwraca <xref:System.Data.OracleClient.OracleDataReader> kursora REF.</span><span class="sxs-lookup"><span data-stu-id="dce32-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="dce32-146">Jeśli Twoje <xref:System.Data.OracleClient.OracleCommand> zwraca wielu kursorów REF CURSOR, dodać wiele parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dce32-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="dce32-147">Dostęp do różnych kursora REF CURSOR, wywołując <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dce32-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dce32-148">Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwraca <xref:System.Data.OracleClient.OracleDataReader> odwołuje się do pierwszego REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="dce32-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="dce32-149">Następnie możesz wywołać <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> metodę, aby dostęp do kolejnych kursora REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="dce32-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="dce32-150">Mimo że parametrów w swojej <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> dopasowanie kolekcji REF CURSOR output parametrów przy użyciu nazwy, <xref:System.Data.OracleClient.OracleDataReader> uzyskuje do nich dostęp w kolejności, w jakiej zostały dodane do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dce32-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="dce32-151">Na przykład rozważmy następujący pakiet oprogramowania Oracle i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="dce32-151">For example, consider the following Oracle package and package body.</span></span>  
  
```sql
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
  
 <span data-ttu-id="dce32-152">Poniższy kod tworzy <xref:System.Data.OracleClient.OracleCommand> zwracającego z poprzedniego pakietu programu Oracle REF CURSOR, dodając dwa parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dce32-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="dce32-153">Poniższy kod zwraca wyniki do poprzedniego polecenia przy użyciu <xref:System.Data.OracleClient.OracleDataReader.Read> i <xref:System.Data.OracleClient.OracleDataReader.NextResult> metody <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="dce32-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="dce32-154">Parametry kursora REF są zwracane w porządku.</span><span class="sxs-lookup"><span data-stu-id="dce32-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="dce32-155">W poniższym przykładzie użyto poprzednie polecenie, aby wypełnić <xref:System.Data.DataSet> z wynikami pakietu programu Oracle.</span><span class="sxs-lookup"><span data-stu-id="dce32-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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

> [!NOTE]
>  <span data-ttu-id="dce32-156">Aby uniknąć **overflowexception —**, firma Microsoft zaleca również obsługiwać każda konwersja z typu Liczba Oracle na prawidłowy typ .NET Framework przed zapisaniem wartości w <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="dce32-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="dce32-157">Możesz użyć <xref:System.Data.Common.DataAdapter.FillError> zdarzenia w celu określenia, czy **overflowexception —** wystąpił.</span><span class="sxs-lookup"><span data-stu-id="dce32-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="dce32-158">Aby uzyskać więcej informacji na temat <xref:System.Data.Common.DataAdapter.FillError> zdarzeń, zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="dce32-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce32-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dce32-159">See also</span></span>

- [<span data-ttu-id="dce32-160">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="dce32-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="dce32-161">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="dce32-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="dce32-162">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="dce32-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="dce32-163">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="dce32-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

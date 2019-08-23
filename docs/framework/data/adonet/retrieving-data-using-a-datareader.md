---
title: Pobieranie danych przy użyciu elementu DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 561ebd7ac6948fa42f73ebb4f1eb97c574e6d7e7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963186"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="3e0b3-102">Pobieranie danych przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="3e0b3-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="3e0b3-103">Aby pobrać dane przy użyciu elementu **DataReader**, Utwórz wystąpienie obiektu **Command** , a następnie Utwórz element **DataReader** , wywołując **polecenie Command. ExecuteReader** , aby pobrać wiersze ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="3e0b3-104">Element **DataReader** zawiera niebuforowany strumień danych, który umożliwia logiki proceduralnej efektywnie przetwarzać wyniki ze źródła danych sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="3e0b3-105">Element **DataReader** jest dobrym rozwiązaniem w przypadku pobierania dużej ilości danych, ponieważ dane nie są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="3e0b3-106">Poniższy przykład ilustruje użycie elementu **DataReader**, gdzie `reader` reprezentuje prawidłowy element DataReader i `command` reprezentuje prawidłowy obiekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="3e0b3-107">Użyj metody **DataReader. Read** , aby uzyskać wiersz z wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="3e0b3-108">Możesz uzyskać dostęp do każdej kolumny zwracanego wiersza, przekazując nazwę lub numer porządkowy kolumny do elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="3e0b3-109">Jednak w celu uzyskania najlepszej wydajności element **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości kolumn w ich natywnych typach danych (**GetDateTime**, GetDouble, GetGuid, GetInt32 itd.).</span><span class="sxs-lookup"><span data-stu-id="3e0b3-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="3e0b3-110">Aby zapoznać się z listą metod akcesora typu dla specyficznych dla dostawcy danych, <xref:System.Data.OleDb.OleDbDataReader> zobacz <xref:System.Data.SqlClient.SqlDataReader>i.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="3e0b3-111">Przy użyciu metod metody dostępu typu, Jeśli wiesz, że typ danych jest mniejszy niż wymagana podczas pobierania wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="3e0b3-112">Poniższy przykład wykonuje iterację przez obiekt **DataReader** i zwraca dwie kolumny z każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="3e0b3-113">Zamykanie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="3e0b3-113">Closing the DataReader</span></span>  
 <span data-ttu-id="3e0b3-114">Zawsze wywołuj metodę **Close** po zakończeniu korzystania z obiektu **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="3e0b3-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="3e0b3-115">Jeśli **polecenie** zawiera parametry wyjściowe lub wartości zwracane, te wartości są niedostępne, dopóki element **DataReader** nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="3e0b3-116">Gdy element **DataReader** jest otwarty, **połączenie** jest używane wyłącznie przez ten element **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="3e0b3-117">Nie można wykonać żadnych poleceń dla **połączenia**, w tym tworzenia innego elementu **DataReader**do momentu zamknięcia oryginalnego elementu **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="3e0b3-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e0b3-118">Nie wywołuj metody **Close** ani **Dispose** dla **połączenia**, elementu **DataReader**lub innego obiektu zarządzanego w metodzie **Finalize** klasy.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="3e0b3-119">W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="3e0b3-120">Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie dołączaj metody **Finalize** w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="3e0b3-121">Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e0b3-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="3e0b3-122">Pobieranie wielu zestawów wyników przy użyciu NextResult</span><span class="sxs-lookup"><span data-stu-id="3e0b3-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="3e0b3-123">Jeśli element **DataReader** zwraca wiele zestawów wyników, wywołaj metodę **NextResult** , aby wykonać iterację w zestawach wyników sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="3e0b3-124">Poniższy przykład pokazuje <xref:System.Data.SqlClient.SqlDataReader> przetwarzanie wyników dwóch instrukcji SELECT <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="3e0b3-125">Pobieranie informacji o schemacie z elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="3e0b3-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="3e0b3-126">Gdy element **DataReader** jest otwarty, można pobrać informacje o schemacie bieżącego zestawu wyników przy użyciu metody **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="3e0b3-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="3e0b3-127">Getschemaing zwraca <xref:System.Data.DataTable> obiekt wypełniony wierszami i kolumnami zawierającymi informacje o schemacie dla bieżącego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="3e0b3-128">Element **DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="3e0b3-129">Każda kolumna tabeli schematu jest mapowana na właściwość kolumn zwracanych w wierszach zestawu wyników, gdzie ColumnName jest nazwą właściwości, a wartością kolumny jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="3e0b3-130">Poniższy przykład zapisuje informacje o schemacie dla elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="3e0b3-131">Praca z rozdziałami OLE DB</span><span class="sxs-lookup"><span data-stu-id="3e0b3-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="3e0b3-132">Hierarchiczne zestawy wierszy lub rozdziały (OLE DB typu **DBTYPE_HCHAPTER**, ADO Type **adChapter**) można <xref:System.Data.OleDb.OleDbDataReader>pobrać przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="3e0b3-133">Gdy zapytanie zawierające rozdział jest zwracane jako element **DataReader**, rozdział jest zwracany jako kolumna w tym elemencie **DataReader** i jest udostępniany jako obiekt **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="3e0b3-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="3e0b3-134">**Zestaw danych** ADO.NET może być również używany do reprezentowania hierarchicznych zestawów wierszy przy użyciu relacji nadrzędny-podrzędny między tabelami.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="3e0b3-135">Aby uzyskać więcej informacji, zobacz [zestawy danych, DataTables i](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)DataViews.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="3e0b3-136">Poniższy przykład kodu używa dostawcy MSDataShape w celu wygenerowania kolumny rozdział zamówień dla każdego klienta na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="3e0b3-137">Zwracanie wyników przy użyciu kursorów REF Oracle</span><span class="sxs-lookup"><span data-stu-id="3e0b3-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="3e0b3-138">.NET Framework Dostawca danych dla programu Oracle obsługuje używanie kursorów REF Oracle do zwracania wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="3e0b3-139">WSKAŹNIK REF Oracle jest zwracany jako <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="3e0b3-140">Można pobrać <xref:System.Data.OracleClient.OracleDataReader> obiekt, który reprezentuje kursor ref Oracle przy <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="3e0b3-141">Można również określić, że <xref:System.Data.OracleClient.OracleCommand> zwraca co najmniej jeden wskaźnik ref Oracle jako <xref:System.Data.OracleClient.OracleDataAdapter> **Właściwość SelectCommand** dla użyta do wypełnienia <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="3e0b3-142">Aby uzyskać dostęp do kursora ref zwróconego ze źródła danych Oracle, Utwórz <xref:System.Data.OracleClient.OracleCommand> dla zapytania i Dodaj parametr wyjściowy, który odwołuje się <xref:System.Data.OracleClient.OracleCommand.Parameters> do kursora ref do kolekcji <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="3e0b3-143">Nazwa parametru musi być zgodna z nazwą parametru REF CURSOR w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="3e0b3-144">Ustaw typ parametru na <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3e0b3-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Metoda zwracadla<xref:System.Data.OracleClient.OracleDataReader>kursoraref. <xref:System.Data.OracleClient.OracleCommand></span><span class="sxs-lookup"><span data-stu-id="3e0b3-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="3e0b3-146"><xref:System.Data.OracleClient.OracleCommand> Jeśli zwracasz wiele kursorów ref, Dodaj wiele parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="3e0b3-147">Możesz uzyskać dostęp do różnych kursorów ref przez wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3e0b3-148"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader> Wywołanie<xref:System.Data.OracleClient.OracleDataReader> zwracające odwołanie do pierwszego kursora ref.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="3e0b3-149">Następnie można wywołać metodę, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> Aby uzyskać dostęp do kolejnych kursorów ref.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="3e0b3-150">Chociaż parametry w <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji są zgodne z parametrami wyjściowymi kursora ref według nazwy <xref:System.Data.OracleClient.OracleDataReader> , uzyskują dostęp do nich w kolejności, w której zostały dodane do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="3e0b3-151">Rozważmy na przykład poniższy pakiet Oracle i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="3e0b3-152">Poniższy kod tworzy <xref:System.Data.OracleClient.OracleCommand> , który zwraca kursory ref z poprzedniego pakietu Oracle, dodając dwa parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="3e0b3-153">Poniższy kod zwraca wyniki poprzedniego polecenia przy użyciu <xref:System.Data.OracleClient.OracleDataReader.Read> metod <xref:System.Data.OracleClient.OracleDataReader>i <xref:System.Data.OracleClient.OracleDataReader.NextResult> .</span><span class="sxs-lookup"><span data-stu-id="3e0b3-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="3e0b3-154">Parametry kursora REF są zwracane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="3e0b3-155">W poniższym przykładzie użyte zostało poprzednie polecenie do wypełnienia <xref:System.Data.DataSet> wynikami pakietu Oracle.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="3e0b3-156">Aby uniknąć przepełnienia, zalecamy również obsługę konwersji z typu numeru Oracle na prawidłowy typ .NET Framework przed zapisaniem wartości w. <xref:System.Data.DataRow></span><span class="sxs-lookup"><span data-stu-id="3e0b3-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="3e0b3-157">Możesz użyć <xref:System.Data.Common.DataAdapter.FillError> zdarzenia, aby określić, czy wystąpił wyjątek przepełnienia.</span><span class="sxs-lookup"><span data-stu-id="3e0b3-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="3e0b3-158">Aby uzyskać więcej informacji <xref:System.Data.Common.DataAdapter.FillError> o zdarzeniu, zobacz [Obsługa zdarzeń DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="3e0b3-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e0b3-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e0b3-159">See also</span></span>

- [<span data-ttu-id="3e0b3-160">Elementy DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="3e0b3-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="3e0b3-161">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="3e0b3-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="3e0b3-162">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="3e0b3-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="3e0b3-163">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="3e0b3-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

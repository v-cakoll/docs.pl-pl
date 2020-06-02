---
title: Pobieranie danych przy użyciu elementu DataReader
description: Dowiedz się, jak pobierać dane przy użyciu elementu DataReader w ADO.NET przy użyciu tego przykładowego kodu. Element DataReader udostępnia niebuforowany strumień danych.
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286601"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="dd204-104">Pobieranie danych przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dd204-104">Retrieve data using a DataReader</span></span>
<span data-ttu-id="dd204-105">Aby pobrać dane przy użyciu elementu **DataReader**, Utwórz wystąpienie obiektu **Command** , a następnie Utwórz element **DataReader** , wywołując **polecenie Command. ExecuteReader** , aby pobrać wiersze ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="dd204-105">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="dd204-106">Element **DataReader** zawiera niebuforowany strumień danych, który umożliwia logiki proceduralnej efektywnie przetwarzać wyniki ze źródła danych sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="dd204-106">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="dd204-107">Element **DataReader** jest dobrym rozwiązaniem w przypadku pobierania dużej ilości danych, ponieważ dane nie są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="dd204-107">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="dd204-108">Poniższy przykład ilustruje użycie elementu **DataReader**, gdzie `reader` reprezentuje prawidłowy element DataReader i `command` reprezentuje prawidłowy obiekt polecenia.</span><span class="sxs-lookup"><span data-stu-id="dd204-108">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="dd204-109">Użyj metody **DataReader. Read** , aby uzyskać wiersz z wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="dd204-109">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="dd204-110">Możesz uzyskać dostęp do każdej kolumny zwracanego wiersza, przekazując nazwę lub numer porządkowy kolumny do elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dd204-110">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="dd204-111">Jednak w celu uzyskania najlepszej wydajności element **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości kolumn w ich natywnych typach danych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**itd.).</span><span class="sxs-lookup"><span data-stu-id="dd204-111">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="dd204-112">Aby zapoznać się z listą metod akcesora typu dla specyficznych dla dostawcy **danych, zobacz** <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="dd204-112">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="dd204-113">Przy użyciu metod metody dostępu typu, Jeśli wiesz, że typ danych jest mniejszy niż wymagana podczas pobierania wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="dd204-113">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="dd204-114">Poniższy przykład wykonuje iterację przez obiekt **DataReader** i zwraca dwie kolumny z każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="dd204-114">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="dd204-115">Zamykanie elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dd204-115">Closing the DataReader</span></span>  
 <span data-ttu-id="dd204-116">Zawsze wywołuj metodę **Close** po zakończeniu korzystania z obiektu **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="dd204-116">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="dd204-117">Jeśli **polecenie** zawiera parametry wyjściowe lub wartości zwracane, te wartości są niedostępne, dopóki element **DataReader** nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="dd204-117">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="dd204-118">Gdy element **DataReader** jest otwarty, **połączenie** jest używane wyłącznie przez ten element **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dd204-118">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="dd204-119">Nie można wykonać żadnych poleceń dla **połączenia**, w tym tworzenia innego elementu **DataReader**do momentu zamknięcia oryginalnego elementu **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="dd204-119">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd204-120">Nie wywołuj metody **Close** ani **Dispose** dla **połączenia**, elementu **DataReader**lub innego obiektu zarządzanego w metodzie **Finalize** klasy.</span><span class="sxs-lookup"><span data-stu-id="dd204-120">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="dd204-121">W finalizatorze zwalniane są tylko niezarządzane zasoby, które są własnością klasy bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="dd204-121">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="dd204-122">Jeśli Klasa nie jest własnością żadnych niezarządzanych zasobów, nie dołączaj metody **Finalize** w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="dd204-122">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="dd204-123">Aby uzyskać więcej informacji, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd204-123">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="dd204-124">Pobieranie wielu zestawów wyników przy użyciu NextResult</span><span class="sxs-lookup"><span data-stu-id="dd204-124">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="dd204-125">Jeśli element **DataReader** zwraca wiele zestawów wyników, wywołaj metodę **NextResult** , aby wykonać iterację w zestawach wyników sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="dd204-125">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="dd204-126">Poniższy przykład pokazuje <xref:System.Data.SqlClient.SqlDataReader> Przetwarzanie wyników dwóch instrukcji SELECT przy użyciu <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dd204-126">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="dd204-127">Pobieranie informacji o schemacie z elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="dd204-127">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="dd204-128">Gdy element **DataReader** jest otwarty, można pobrać informacje o schemacie bieżącego zestawu wyników przy użyciu metody **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="dd204-128">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="dd204-129">**Getschemaing** zwraca <xref:System.Data.DataTable> obiekt wypełniony wierszami i kolumnami zawierającymi informacje o schemacie dla bieżącego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="dd204-129">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="dd204-130">Element **DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="dd204-130">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="dd204-131">Każda kolumna tabeli schematu jest mapowana na właściwość kolumn zwracanych w wierszach zestawu wyników, gdzie **ColumnName** jest nazwą właściwości, a wartością kolumny jest wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd204-131">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="dd204-132">Poniższy przykład zapisuje informacje o schemacie dla elementu **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="dd204-132">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="dd204-133">Praca z rozdziałami OLE DB</span><span class="sxs-lookup"><span data-stu-id="dd204-133">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="dd204-134">Hierarchiczne zestawy wierszy lub rozdziały (OLE DB typu **DBTYPE_HCHAPTER**, ADO Type **adChapter**) można pobrać przy użyciu <xref:System.Data.OleDb.OleDbDataReader> .</span><span class="sxs-lookup"><span data-stu-id="dd204-134">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="dd204-135">Gdy zapytanie zawierające rozdział jest zwracane jako element **DataReader**, rozdział jest zwracany jako kolumna w tym elemencie **DataReader** i jest udostępniany jako obiekt **DataReader** .</span><span class="sxs-lookup"><span data-stu-id="dd204-135">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="dd204-136">**Zestaw danych** ADO.NET może być również używany do reprezentowania hierarchicznych zestawów wierszy przy użyciu relacji nadrzędny-podrzędny między tabelami.</span><span class="sxs-lookup"><span data-stu-id="dd204-136">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="dd204-137">Aby uzyskać więcej informacji, zobacz [zestawy danych, DataTables i DataViews](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd204-137">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="dd204-138">Poniższy przykład kodu używa dostawcy MSDataShape w celu wygenerowania kolumny rozdział zamówień dla każdego klienta na liście klientów.</span><span class="sxs-lookup"><span data-stu-id="dd204-138">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="dd204-139">Zwracanie wyników przy użyciu kursorów REF Oracle</span><span class="sxs-lookup"><span data-stu-id="dd204-139">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="dd204-140">.NET Framework Dostawca danych dla programu Oracle obsługuje używanie kursorów REF Oracle do zwracania wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="dd204-140">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="dd204-141">WSKAŹNIK REF Oracle jest zwracany jako <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="dd204-141">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="dd204-142">Można pobrać <xref:System.Data.OracleClient.OracleDataReader> obiekt, który reprezentuje kursor ref Oracle przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dd204-142">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="dd204-143">Można również określić <xref:System.Data.OracleClient.OracleCommand> , że zwraca co najmniej jeden wskaźnik ref Oracle jako **Właściwość SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> użyta do wypełnienia <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="dd204-143">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="dd204-144">Aby uzyskać dostęp do kursora REF zwróconego ze źródła danych Oracle, Utwórz <xref:System.Data.OracleClient.OracleCommand> dla zapytania i Dodaj parametr wyjściowy, który odwołuje się do kursora ref do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji <xref:System.Data.OracleClient.OracleCommand> .</span><span class="sxs-lookup"><span data-stu-id="dd204-144">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="dd204-145">Nazwa parametru musi być zgodna z nazwą parametru REF CURSOR w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="dd204-145">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="dd204-146">Ustaw typ parametru na <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="dd204-146">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dd204-147"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>Metoda <xref:System.Data.OracleClient.OracleCommand> zwraca <xref:System.Data.OracleClient.OracleDataReader> dla kursora ref.</span><span class="sxs-lookup"><span data-stu-id="dd204-147">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="dd204-148">Jeśli <xref:System.Data.OracleClient.OracleCommand> zwracasz wiele kursorów ref, Dodaj wiele parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="dd204-148">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="dd204-149">Możesz uzyskać dostęp do różnych kursorów REF przez wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="dd204-149">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="dd204-150">Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwracające odwołanie do <xref:System.Data.OracleClient.OracleDataReader> pierwszego kursora ref.</span><span class="sxs-lookup"><span data-stu-id="dd204-150">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="dd204-151">Następnie można wywołać metodę, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> Aby uzyskać dostęp do kolejnych kursorów ref.</span><span class="sxs-lookup"><span data-stu-id="dd204-151">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="dd204-152">Chociaż parametry w <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji są zgodne z parametrami wyjściowymi kursora ref według nazwy, <xref:System.Data.OracleClient.OracleDataReader> uzyskują dostęp do nich w kolejności, w której zostały dodane do <xref:System.Data.OracleClient.OracleCommand.Parameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dd204-152">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="dd204-153">Rozważmy na przykład poniższy pakiet Oracle i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="dd204-153">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="dd204-154">Poniższy kod tworzy <xref:System.Data.OracleClient.OracleCommand> , który zwraca kursory ref z poprzedniego pakietu Oracle, dodając dwa parametry typu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> do <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dd204-154">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="dd204-155">Poniższy kod zwraca wyniki poprzedniego polecenia przy użyciu <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> metod i <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="dd204-155">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="dd204-156">Parametry kursora REF są zwracane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="dd204-156">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="dd204-157">W poniższym przykładzie użyte zostało poprzednie polecenie do wypełnienia <xref:System.Data.DataSet> wynikami pakietu Oracle.</span><span class="sxs-lookup"><span data-stu-id="dd204-157">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="dd204-158">Aby uniknąć **przepełnienia**, zalecamy również obsługę konwersji z typu numeru Oracle na prawidłowy typ .NET Framework przed zapisaniem wartości w <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="dd204-158">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="dd204-159">Możesz użyć zdarzenia, <xref:System.Data.Common.DataAdapter.FillError> Aby określić, czy wystąpił wyjątek **przepełnienia** .</span><span class="sxs-lookup"><span data-stu-id="dd204-159">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="dd204-160">Aby uzyskać więcej informacji o <xref:System.Data.Common.DataAdapter.FillError> zdarzeniu, zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="dd204-160">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd204-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd204-161">See also</span></span>

- [<span data-ttu-id="dd204-162">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="dd204-162">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="dd204-163">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="dd204-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="dd204-164">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="dd204-164">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="dd204-165">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="dd204-165">ADO.NET Overview</span></span>](ado-net-overview.md)

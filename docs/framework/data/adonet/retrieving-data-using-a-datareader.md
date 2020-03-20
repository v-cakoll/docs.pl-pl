---
title: Pobieranie danych przy użyciu elementu DataReader
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149027"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="0cce1-102">Pobieranie danych przy użyciu czytnika danych</span><span class="sxs-lookup"><span data-stu-id="0cce1-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="0cce1-103">Aby pobrać dane przy użyciu **programu DataReader,** należy utworzyć wystąpienie obiektu **Command,** a następnie utworzyć **program DataReader,** wywołując **program Command.ExecuteReader** w celu pobrania wierszy ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0cce1-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="0cce1-104">**DataReader** zapewnia niebuforowany strumień danych, który umożliwia logiki proceduralnej skutecznie przetwarzać wyniki ze źródła danych sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="0cce1-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="0cce1-105">**DataReader** jest dobrym wyborem podczas pobierania dużych ilości danych, ponieważ dane nie są buforowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0cce1-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="0cce1-106">Poniższy przykład ilustruje przy użyciu **DataReader**, gdzie `reader` reprezentuje prawidłowy DataReader i `command` reprezentuje prawidłowy Obiekt Polecenia.</span><span class="sxs-lookup"><span data-stu-id="0cce1-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="0cce1-107">Użyj **DataReader.Read** metody, aby uzyskać wiersz z wyników kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0cce1-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="0cce1-108">Dostęp do każdej kolumny zwróconego wiersza można uzyskać, przekazując nazwę lub numer porządkowy kolumny do **programu DataReader**.</span><span class="sxs-lookup"><span data-stu-id="0cce1-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="0cce1-109">Jednak dla najlepszej wydajności **DataReader** zawiera szereg metod, które umożliwiają dostęp do wartości kolumn w ich natywnych typów danych (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="0cce1-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="0cce1-110">Aby uzyskać listę metod akcesora wpisanego dla <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.SqlClient.SqlDataReader> **czytników danych**specyficznych dla dostawcy danych, zobacz i .</span><span class="sxs-lookup"><span data-stu-id="0cce1-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="0cce1-111">Za pomocą metody akcesora wpisane, gdy wiesz, że typ danych bazowych zmniejsza ilość konwersji typu wymagane podczas pobierania wartości kolumny.</span><span class="sxs-lookup"><span data-stu-id="0cce1-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="0cce1-112">Poniższy przykład iteruje za pośrednictwem **obiektu DataReader** i zwraca dwie kolumny z każdego wiersza.</span><span class="sxs-lookup"><span data-stu-id="0cce1-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="0cce1-113">Zamykanie czytnika danych</span><span class="sxs-lookup"><span data-stu-id="0cce1-113">Closing the DataReader</span></span>  
 <span data-ttu-id="0cce1-114">Zawsze wywołać **Close** metody po zakończeniu przy użyciu **DataReader** obiektu.</span><span class="sxs-lookup"><span data-stu-id="0cce1-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="0cce1-115">Jeśli **polecenie** zawiera parametry wyjściowe lub zwracane wartości, wartości te nie są dostępne, dopóki **datareader** nie zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="0cce1-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="0cce1-116">Gdy **datareader** jest otwarty, **połączenie** jest używane wyłącznie przez tego **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="0cce1-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="0cce1-117">Nie można wykonać żadnych poleceń dla **połączenia**, w tym tworzenia innego **DataReader**, dopóki oryginalny **DataReader** zostanie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="0cce1-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cce1-118">Nie należy wywoływać **Zamknij** lub **Dispose** na **połączenie**, **DataReader**lub inny obiekt zarządzany w **Finalize** metody klasy.</span><span class="sxs-lookup"><span data-stu-id="0cce1-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="0cce1-119">W finalizatorze tylko zwolnić niezarządzanych zasobów, które posiada bezpośrednio klasy.</span><span class="sxs-lookup"><span data-stu-id="0cce1-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="0cce1-120">Jeśli klasa nie jest właścicielem żadnych zasobów niezarządzanych, nie należy **uwzględniać Finalize** metody w definicji klasy.</span><span class="sxs-lookup"><span data-stu-id="0cce1-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="0cce1-121">Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cce1-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="0cce1-122">Pobieranie wielu zestawów wyników przy użyciu funkcji NextResult</span><span class="sxs-lookup"><span data-stu-id="0cce1-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="0cce1-123">Jeśli **DataReader** zwraca wiele zestawów wyników, wywołać **NextResult** metoda iteracji za pośrednictwem zestawów wyników sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="0cce1-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="0cce1-124">W poniższym <xref:System.Data.SqlClient.SqlDataReader> przykładzie przedstawiono przetwarzanie wyników <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> dwóch instrukcji SELECT przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="0cce1-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="0cce1-125">Uzyskiwanie informacji o schemacie z czytnika danych</span><span class="sxs-lookup"><span data-stu-id="0cce1-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="0cce1-126">Gdy **DataReader** jest otwarty, można pobrać informacje o schemacie o bieżącym zestawie wyników przy użyciu **GetSchemaTable** metody.</span><span class="sxs-lookup"><span data-stu-id="0cce1-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="0cce1-127">**GetSchemaTable** zwraca <xref:System.Data.DataTable> obiekt wypełniony wierszami i kolumnami, które zawierają informacje o schemacie dla bieżącego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="0cce1-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="0cce1-128">**DataTable** zawiera jeden wiersz dla każdej kolumny zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="0cce1-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="0cce1-129">Każda kolumna tabeli schematu jest mapowana do właściwości kolumn zwracanych w wierszach zestawu wyników, gdzie **ColumnName** jest nazwą właściwości, a wartość kolumny jest wartością właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cce1-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="0cce1-130">W poniższym przykładzie zapisuje informacje o schemacie dla **programu DataReader**.</span><span class="sxs-lookup"><span data-stu-id="0cce1-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="0cce1-131">Praca z rozdziałami OLE DB</span><span class="sxs-lookup"><span data-stu-id="0cce1-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="0cce1-132">Hierarchiczne zestawy wierszy lub rozdziały (typ OLE DB **DBTYPE_HCHAPTER**, ADO type **adChapter**) można pobrać za pomocą <xref:System.Data.OleDb.OleDbDataReader>pliku .</span><span class="sxs-lookup"><span data-stu-id="0cce1-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="0cce1-133">Gdy kwerenda zawierająca rozdział jest zwracana jako **DataReader**, rozdział jest zwracany jako kolumna w tym **DataReader** i jest narażony jako obiekt **DataReader.**</span><span class="sxs-lookup"><span data-stu-id="0cce1-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="0cce1-134">ADO.NET **DataSet** może również służyć do reprezentowania hierarchicznych zestawów wierszy przy użyciu relacji nadrzędny-podrzędny między tabelami.</span><span class="sxs-lookup"><span data-stu-id="0cce1-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="0cce1-135">Aby uzyskać więcej informacji, zobacz [Zestawy danych, Tablice informacyjne i DataViews](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cce1-135">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="0cce1-136">Poniższy przykład kodu używa dostawcy MSDataShape do generowania kolumny rozdział zamówień dla każdego klienta na liście odbiorców.</span><span class="sxs-lookup"><span data-stu-id="0cce1-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="0cce1-137">Zwracanie wyników dzięki oracle ref cursor</span><span class="sxs-lookup"><span data-stu-id="0cce1-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="0cce1-138">Dostawca danych .NET Framework dla Oracle obsługuje korzystanie z oracle ref cursors do zwracania wyników kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0cce1-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="0cce1-139">Kursor ref Oracle jest zwracany jako . <xref:System.Data.OracleClient.OracleDataReader></span><span class="sxs-lookup"><span data-stu-id="0cce1-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="0cce1-140">Można pobrać obiekt, <xref:System.Data.OracleClient.OracleDataReader> który reprezentuje Oracle REF CURSOR przy użyciu <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0cce1-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="0cce1-141">Można również <xref:System.Data.OracleClient.OracleCommand> określić, który zwraca jeden lub więcej oracle ref cursors jako **SelectCommand** dla <xref:System.Data.OracleClient.OracleDataAdapter> używane do wypełnienia . <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="0cce1-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="0cce1-142">Aby uzyskać dostęp do ref cursor zwrócony <xref:System.Data.OracleClient.OracleCommand> ze źródła danych Oracle, należy utworzyć dla kwerendy <xref:System.Data.OracleClient.OracleCommand.Parameters> i <xref:System.Data.OracleClient.OracleCommand>dodać parametr wyjściowy, który odwołuje się do REF CURSOR do kolekcji . .</span><span class="sxs-lookup"><span data-stu-id="0cce1-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="0cce1-143">Nazwa parametru musi być zgodna z nazwą parametru REF CURSOR w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="0cce1-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="0cce1-144">Ustaw typ parametru <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>na .</span><span class="sxs-lookup"><span data-stu-id="0cce1-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0cce1-145">Metoda <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> zwraca <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> dla REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="0cce1-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="0cce1-146">Jeśli <xref:System.Data.OracleClient.OracleCommand> zwraca wiele kursorów REF, dodaj wiele parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="0cce1-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="0cce1-147">Można uzyskać dostęp do różnych ref cursors wywołując <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="0cce1-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0cce1-148">Wywołanie <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> zwraca <xref:System.Data.OracleClient.OracleDataReader> odwołanie się do pierwszego KURSORA REF.</span><span class="sxs-lookup"><span data-stu-id="0cce1-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="0cce1-149">Następnie można wywołać metodę, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> aby uzyskać dostęp do kolejnych ref cursorów.</span><span class="sxs-lookup"><span data-stu-id="0cce1-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="0cce1-150">Mimo że parametry <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> w kolekcji odpowiadają parametrom wyjściowym <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR według nazwy, uzyskuje <xref:System.Data.OracleClient.OracleCommand.Parameters> do nich dostęp w kolejności, w jakiej zostały dodane do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0cce1-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="0cce1-151">Rozważmy na przykład następujący pakiet Oracle i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="0cce1-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="0cce1-152">Poniższy kod <xref:System.Data.OracleClient.OracleCommand> tworzy, który zwraca ref cursors z poprzedniego pakietu <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> Oracle <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> przez dodanie dwóch parametrów typu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0cce1-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="0cce1-153">Poniższy kod zwraca wyniki poprzedniego polecenia <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> przy użyciu <xref:System.Data.OracleClient.OracleDataReader>i metod .</span><span class="sxs-lookup"><span data-stu-id="0cce1-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="0cce1-154">Parametry RE CURSOR są zwracane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="0cce1-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="0cce1-155">W poniższym przykładzie użyto poprzedniego <xref:System.Data.DataSet> polecenia do wypełniania a z wynikami pakietu Oracle.</span><span class="sxs-lookup"><span data-stu-id="0cce1-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="0cce1-156">Aby uniknąć **nadmiernego przepełnienia,** zaleca się również obsługę dowolnej konwersji z typu Oracle NUMBER do prawidłowego typu .NET Framework przed zapisaniem wartości w pliku <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="0cce1-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="0cce1-157">Można użyć <xref:System.Data.Common.DataAdapter.FillError> zdarzenia, aby ustalić, czy wystąpił **przepełnieniePrzezstaw.**</span><span class="sxs-lookup"><span data-stu-id="0cce1-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="0cce1-158">Aby uzyskać więcej <xref:System.Data.Common.DataAdapter.FillError> informacji na temat zdarzenia, zobacz [Obsługa zdarzeń dataadapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="0cce1-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cce1-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cce1-159">See also</span></span>

- [<span data-ttu-id="0cce1-160">Elementy DataAdapter i DataReader</span><span class="sxs-lookup"><span data-stu-id="0cce1-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="0cce1-161">Polecenia i parametry</span><span class="sxs-lookup"><span data-stu-id="0cce1-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="0cce1-162">Pobieranie informacji o schemacie bazy danych</span><span class="sxs-lookup"><span data-stu-id="0cce1-162">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="0cce1-163">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0cce1-163">ADO.NET Overview</span></span>](ado-net-overview.md)

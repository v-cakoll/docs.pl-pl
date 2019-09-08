---
title: Tworzenie elementu DataTable przy użyciu elementu DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d45cf41-d8ae-4409-af3e-a96a7e476d85
ms.openlocfilehash: 6e066bcbe02fa9cf498e11af431b9f6dcd4432ab
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785513"
---
# <a name="creating-a-datatable-from-a-dataview"></a><span data-ttu-id="1e29b-102">Tworzenie elementu DataTable przy użyciu elementu DataView</span><span class="sxs-lookup"><span data-stu-id="1e29b-102">Creating a DataTable from a DataView</span></span>
<span data-ttu-id="1e29b-103">Po pobraniu danych ze źródła danych, które zostały wypełnione <xref:System.Data.DataTable> danymi, możesz chcieć posortować, filtrować lub w inny sposób ograniczyć zwrócone dane bez konieczności pobierania ich.</span><span class="sxs-lookup"><span data-stu-id="1e29b-103">Once you have retrieved data from a data source, and have filled a <xref:System.Data.DataTable> with the data, you may want to sort, filter, or otherwise limit the returned data without retrieving it again.</span></span> <span data-ttu-id="1e29b-104">Jest <xref:System.Data.DataView> to możliwe.</span><span class="sxs-lookup"><span data-stu-id="1e29b-104">The <xref:System.Data.DataView> class makes this possible.</span></span> <span data-ttu-id="1e29b-105">Ponadto, jeśli konieczne <xref:System.Data.DataTable> jest utworzenie nowego z programu <xref:System.Data.DataView> <xref:System.Data.DataView.ToTable%2A> , można użyć metody do skopiowania wszystkich wierszy i kolumn lub podzbioru danych do nowej <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1e29b-105">In addition, if you need to create a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView>, you can use the <xref:System.Data.DataView.ToTable%2A> method to copy all the rows and columns, or a subset of the data into a new <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1e29b-106"><xref:System.Data.DataView.ToTable%2A> Metoda zapewnia przeciążenia:</span><span class="sxs-lookup"><span data-stu-id="1e29b-106">The <xref:System.Data.DataView.ToTable%2A> method provides overloads to:</span></span>  
  
- <span data-ttu-id="1e29b-107">Utwórz zawierające kolumny, które są podzbiorem kolumn <xref:System.Data.DataView>w. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="1e29b-107">Create a <xref:System.Data.DataTable> containing columns that are a subset of the columns in the <xref:System.Data.DataView>.</span></span>  
  
- <span data-ttu-id="1e29b-108">Utwórz, <xref:System.Data.DataView>który zawiera tylko unikatowe wiersze od, analogicznie do DISTINCT słowo kluczowe w języku Transact-SQL. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="1e29b-108">Create a <xref:System.Data.DataTable> that includes only distinct rows from the <xref:System.Data.DataView>, analogously to the DISTINCT keyword in Transact-SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e29b-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e29b-109">Example</span></span>  
 <span data-ttu-id="1e29b-110">Poniższy przykład aplikacji konsolowej tworzy <xref:System.Data.DataTable> , który zawiera dane z tabeli **Person. Contact** w przykładowej bazie danych **AdventureWorks** .</span><span class="sxs-lookup"><span data-stu-id="1e29b-110">The following console application example creates a <xref:System.Data.DataTable> that contains data from the **Person.Contact** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="1e29b-111">Następnie przykład tworzy sortowanie i filtrowanie <xref:System.Data.DataView> na podstawie. <xref:System.Data.DataTable></span><span class="sxs-lookup"><span data-stu-id="1e29b-111">Next, the example creates a sorted and filtered <xref:System.Data.DataView> based on the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="1e29b-112">Po <xref:System.Data.DataTable> wyświetleniu zawartości <xref:System.Data.DataTable> <xref:System.Data.DataView>i, przykład <xref:System.Data.DataView> tworzy nowy z, wywołując <xref:System.Data.DataView.ToTable%2A> metodę, wybierając tylko podzestaw dostępnych kolumn.</span><span class="sxs-lookup"><span data-stu-id="1e29b-112">After displaying the contents of the <xref:System.Data.DataTable> and the <xref:System.Data.DataView>, the example creates a new <xref:System.Data.DataTable> from the <xref:System.Data.DataView> by calling the <xref:System.Data.DataView.ToTable%2A> method, selecting only a subset of the available columns.</span></span> <span data-ttu-id="1e29b-113">Na koniec przykład wyświetla zawartość nowego <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="1e29b-113">Finally, the example displays the contents of the new <xref:System.Data.DataTable>.</span></span>  
  
```vb  
Private Sub DemonstrateDataView()  
    ' Retrieve a DataTable from the AdventureWorks sample database.  
    ' connectionString is assumed to be a valid connection string.  
    Dim adapter As New SqlDataAdapter( _  
       "SELECT FirstName, LastName, EmailAddress FROM Person.Contact WHERE FirstName LIKE 'Mich%'", connectionString)  
    Dim table As New DataTable  
  
    adapter.Fill(table)  
    Console.WriteLine("Original table name: " & table.TableName)  
    ' Print current table values.  
    PrintTableOrView(table, "Current Values in Table")  
  
    ' Now create a DataView based on the DataTable.  
    ' Sort and filter the data.  
    Dim view As DataView = table.DefaultView  
    view.Sort = "LastName, FirstName"  
    view.RowFilter = "LastName > 'M'"  
    PrintTableOrView(view, "Current Values in View")  
  
    ' Create a new DataTable based on the DataView,  
    ' requesting only two columns with distinct values  
    ' in the columns.  
    Dim newTable As DataTable = view.ToTable("UniqueLastNames", True, "FirstName", "LastName")  
    PrintTableOrView(newTable, "Table created from DataView")  
    Console.WriteLine("New table name: " & newTable.TableName)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
    End Sub  
  
Private Sub PrintTableOrView(ByVal dv As DataView, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
    Dim table As DataTable = dv.Table  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the view.  
    For Each rowView As DataRowView In dv  
        sw = New System.IO.StringWriter  
  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(rowView(col.ColumnName).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
End Sub  
  
Private Sub PrintTableOrView(ByVal table As DataTable, ByVal label As String)  
    Dim sw As System.IO.StringWriter  
    Dim output As String  
  
    Console.WriteLine(label)  
  
    ' Loop through each row in the table.  
    For Each row As DataRow In table.Rows  
        sw = New System.IO.StringWriter  
        ' Loop through each column.  
        For Each col As DataColumn In table.Columns  
            ' Output the value of each column's data.  
            sw.Write(row(col).ToString() & ", ")  
        Next  
        output = sw.ToString  
        ' Trim off the trailing ", ", so the output looks correct.  
        If output.Length > 2 Then  
            output = output.Substring(0, output.Length - 2)  
        End If  
        ' Display the row in the console window.  
        Console.WriteLine(output)  
    Next  
    Console.WriteLine()  
    End Sub  
End Module  
```  
  
```csharp  
private static void DemonstrateDataView()  
{  
// Retrieve a DataTable from the AdventureWorks sample database.  
// connectionString is assumed to be a valid connection string.  
SqlDataAdapter adapter = new SqlDataAdapter(  
    "SELECT FirstName, LastName, EmailAddress " +  
    "FROM Person.Contact WHERE FirstName LIKE 'Mich%'",   
       GetConnectionString());  
DataTable table = new DataTable();  
  
adapter.Fill(table);  
Console.WriteLine("Original table name: " + table.TableName);  
// Print current table values.  
PrintTableOrView(table, "Current Values in Table");  
  
// Now create a DataView based on the DataTable.  
// Sort and filter the data.  
DataView view = table.DefaultView;  
view.Sort = "LastName, FirstName";  
view.RowFilter = "LastName > 'M'";  
PrintTableOrView(view, "Current Values in View");  
  
// Create a new DataTable based on the DataView,  
// requesting only two columns with distinct values  
// in the columns.  
DataTable newTable = view.ToTable("UniqueLastNames",  
     true, "FirstName", "LastName");  
PrintTableOrView(newTable, "Table created from DataView");  
Console.WriteLine("New table name: " + newTable.TableName);  
  
Console.WriteLine("Press any key to continue.");  
Console.ReadKey();  
}  
  
private static void PrintTableOrView(DataView dv, string label)  
{  
System.IO.StringWriter sw;  
string output;  
DataTable table = dv.Table;  
  
Console.WriteLine(label);  
  
// Loop through each row in the view.  
foreach (DataRowView rowView in dv)  
{  
    sw = new System.IO.StringWriter();  
  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(rowView[col.ColumnName].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
}  
Console.WriteLine();  
}  
  
private static void PrintTableOrView(DataTable table, string label)  
{  
System.IO.StringWriter sw;  
string output;  
  
Console.WriteLine(label);  
  
// Loop through each row in the table.  
foreach (DataRow row in table.Rows)  
{  
    sw = new System.IO.StringWriter();  
    // Loop through each column.  
    foreach (DataColumn col in table.Columns)  
    {  
        // Output the value of each column's data.  
        sw.Write(row[col].ToString() + ", ");  
    }  
    output = sw.ToString();  
    // Trim off the trailing ", ", so the output looks correct.  
    if (output.Length > 2)  
    {  
        output = output.Substring(0, output.Length - 2);  
    }  
    // Display the row in the console window.  
    Console.WriteLine(output);  
} //  
Console.WriteLine();  
}  
```  
  
 <span data-ttu-id="1e29b-114">}</span><span class="sxs-lookup"><span data-stu-id="1e29b-114">}</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e29b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e29b-115">See also</span></span>

- <xref:System.Data.DataView.ToTable%2A>
- [<span data-ttu-id="1e29b-116">Elementy DataView</span><span class="sxs-lookup"><span data-stu-id="1e29b-116">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="1e29b-117">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1e29b-117">ADO.NET Overview</span></span>](../ado-net-overview.md)

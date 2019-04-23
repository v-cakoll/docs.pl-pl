---
title: Manipulowanie danymi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51096a2e-8b38-4c4d-a523-799bfdb7ec69
ms.openlocfilehash: fb71fe7abb5f70022e39808369779274eda2a7f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213952"
---
# <a name="manipulating-data"></a><span data-ttu-id="ef0bd-102">Manipulowanie danymi</span><span class="sxs-lookup"><span data-stu-id="ef0bd-102">Manipulating Data</span></span>
<span data-ttu-id="ef0bd-103">Przed wprowadzeniem z wielu aktywnych zestawów wyników (MARS) deweloperów było użyć wielu połączeń lub kursory po stronie serwera do rozwiązywania niektórych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-103">Before the introduction of Multiple Active Result Sets (MARS), developers had to use either multiple connections or server-side cursors to solve certain scenarios.</span></span> <span data-ttu-id="ef0bd-104">W przypadku wielu połączeń były używane w sytuacji, transakcyjnego, powiązane połączenia (przy użyciu **sp_getbindtoken** i **procedury sp_bindsession**) były wymagane.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-104">In addition, when multiple connections were used in a transactional situation, bound connections (with **sp_getbindtoken** and **sp_bindsession**) were required.</span></span> <span data-ttu-id="ef0bd-105">W poniższych scenariuszach pokazano sposób używania połączenia z obsługą usług MARS zamiast wielu połączeń.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-105">The following scenarios show how to use a MARS-enabled connection instead of multiple connections.</span></span>  
  
## <a name="using-multiple-commands-with-mars"></a><span data-ttu-id="ef0bd-106">Korzystanie z wielu poleceń za pomocą usług MARS</span><span class="sxs-lookup"><span data-stu-id="ef0bd-106">Using Multiple Commands with MARS</span></span>  
 <span data-ttu-id="ef0bd-107">Następująca aplikacja konsoli Pokazuje, jak za pomocą dwóch <xref:System.Data.SqlClient.SqlDataReader> obiektów przy użyciu dwóch <xref:System.Data.SqlClient.SqlCommand> obiektów i jeden <xref:System.Data.SqlClient.SqlConnection> obiektu z włączoną MARS.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-107">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with two <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef0bd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef0bd-108">Example</span></span>  
 <span data-ttu-id="ef0bd-109">Przykład otwiera jedno połączenie **AdventureWorks** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-109">The example opens a single connection to the **AdventureWorks** database.</span></span> <span data-ttu-id="ef0bd-110">Za pomocą <xref:System.Data.SqlClient.SqlCommand> obiektu <xref:System.Data.SqlClient.SqlDataReader> zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-110">Using a <xref:System.Data.SqlClient.SqlCommand> object, a <xref:System.Data.SqlClient.SqlDataReader> is created.</span></span> <span data-ttu-id="ef0bd-111">W przypadku użycia czytelnika na sekundę <xref:System.Data.SqlClient.SqlDataReader> zostanie otwarty przy użyciu danych z pierwszym <xref:System.Data.SqlClient.SqlDataReader> jako dane wejściowe do klauzuli WHERE, drugi czytnika.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-111">As the reader is used, a second <xref:System.Data.SqlClient.SqlDataReader> is opened, using data from the first <xref:System.Data.SqlClient.SqlDataReader> as input to the WHERE clause for the second reader.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef0bd-112">W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-112">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="ef0bd-113">W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-113">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="ef0bd-114">Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-114">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Module Module1  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim vendorID As Integer  
  
    Dim vendorCmd As SqlCommand  
    Dim productCmd As SqlCommand  
    Dim productReader As SqlDataReader  
  
    Dim vendorSQL As String = & _   
      "SELECT VendorId, Name FROM Purchasing.Vendor"  
    Dim productSQL As String = _  
        "SELECT Production.Product.Name FROM Production.Product " & _  
        "INNER JOIN Purchasing.ProductVendor " & _  
        "ON Production.Product.ProductID = " & _  
        "Purchasing.ProductVendor.ProductID " & _  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId"  
  
    Using awConnection As New SqlConnection(connectionString)  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      productCmd = New SqlCommand(productSQL, awConnection)  
      productCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      awConnection.Open()  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorId"))  
  
          productCmd.Parameters("@VendorId").Value = vendorID  
  
          ' The following line of code requires  
          ' a MARS-enabled connection.  
          productReader = productCmd.ExecuteReader()  
          Using productReader  
            While productReader.Read()  
              Console.WriteLine("  " & CStr(productReader("Name")))  
            End While  
          End Using  
        End While  
      End Using  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks; MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Class1  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  int vendorID;  
  SqlDataReader productReader = null;  
  string vendorSQL =   
    "SELECT VendorId, Name FROM Purchasing.Vendor";  
  string productSQL =   
    "SELECT Production.Product.Name FROM Production.Product " +  
    "INNER JOIN Purchasing.ProductVendor " +  
    "ON Production.Product.ProductID = " +   
    "Purchasing.ProductVendor.ProductID " +  
    "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    SqlCommand productCmd =   
      new SqlCommand(productSQL, awConnection);  
  
    productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    awConnection.Open();  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int)vendorReader["VendorId"];  
  
        productCmd.Parameters["@VendorId"].Value = vendorID;  
        // The following line of code requires  
        // a MARS-enabled connection.  
        productReader = productCmd.ExecuteReader();  
        using (productReader)  
        {  
          while (productReader.Read())  
          {  
            Console.WriteLine("  " +  
              productReader["Name"].ToString());  
          }  
        }  
      }  
  }  
      Console.WriteLine("Press any key to continue");  
      Console.ReadLine();  
    }  
  }  
  private static string GetConnectionString()  
  {  
    // To avoid storing the connection string in your code,  
    // you can retrive it from a configuration file.  
    return "Data Source=(local);Integrated Security=SSPI;" +   
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="reading-and-updating-data-with-mars"></a><span data-ttu-id="ef0bd-115">Odczytywanie i aktualizowanie danych za pomocą usług MARS</span><span class="sxs-lookup"><span data-stu-id="ef0bd-115">Reading and Updating Data with MARS</span></span>  
 <span data-ttu-id="ef0bd-116">MARS umożliwia połączenie ma być używany dla oba rodzaje operacji i danych manipulacji języka (DML) operacji odczytu z więcej niż jednym oczekującą operację.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-116">MARS allows a connection to be used for both read operations and data manipulation language (DML) operations with more than one pending operation.</span></span> <span data-ttu-id="ef0bd-117">Ta funkcja eliminuje potrzebę stosowania aplikacji do czynienia z błędami zajęty połączenia.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-117">This feature eliminates the need for an application to deal with connection-busy errors.</span></span> <span data-ttu-id="ef0bd-118">Ponadto MARS można zastąpić użytkownika kursorów po stronie serwera, które zazwyczaj zużywać więcej zasobów.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-118">In addition, MARS can replace the user of server-side cursors, which generally consume more resources.</span></span> <span data-ttu-id="ef0bd-119">Na koniec, ponieważ wiele operacji może działać na pojedynczego połączenia, mogą współużytkować ten sam kontekst transakcji, eliminując konieczność stosowania **sp_getbindtoken** i **procedury sp_bindsession** składowanych w systemie procedury.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-119">Finally, because multiple operations can operate on a single connection, they can share the same transaction context, eliminating the need to use **sp_getbindtoken** and **sp_bindsession** system stored procedures.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef0bd-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef0bd-120">Example</span></span>  
 <span data-ttu-id="ef0bd-121">Następująca aplikacja konsoli Pokazuje, jak za pomocą dwóch <xref:System.Data.SqlClient.SqlDataReader> obiektów, z których trzy są <xref:System.Data.SqlClient.SqlCommand> obiektów i jeden <xref:System.Data.SqlClient.SqlConnection> obiektu z włączoną MARS.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-121">The following Console application demonstrates how to use two <xref:System.Data.SqlClient.SqlDataReader> objects with three <xref:System.Data.SqlClient.SqlCommand> objects and a single <xref:System.Data.SqlClient.SqlConnection> object with MARS enabled.</span></span> <span data-ttu-id="ef0bd-122">Pierwszy obiekt polecenie pobiera listę dostawców, którego poziom kredytu wynosi 5.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-122">The first command object retrieves a list of vendors whose credit rating is 5.</span></span> <span data-ttu-id="ef0bd-123">Drugi obiekt polecenia używa dostawcy podany identyfikator z <xref:System.Data.SqlClient.SqlDataReader> do załadowania drugiego <xref:System.Data.SqlClient.SqlDataReader> wszystkie produkty określonego dostawcy.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-123">The second command object uses the vendor ID provided from a <xref:System.Data.SqlClient.SqlDataReader> to load the second <xref:System.Data.SqlClient.SqlDataReader> with all of the products for the particular vendor.</span></span> <span data-ttu-id="ef0bd-124">Każdy rekord produktu jest kontrolowane przez drugi <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-124">Each product record is visited by the second <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="ef0bd-125">Obliczenie jest przeprowadzana w celu ustalenia, jakie nowe **OnOrderQty** powinien być.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-125">A calculation is performed to determine what the new **OnOrderQty** should be.</span></span> <span data-ttu-id="ef0bd-126">Trzeci obiekt polecenia jest następnie używany do aktualizacji **ProductVendor** tabeli z nową wartością.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-126">The third command object is then used to update the **ProductVendor** table with the new value.</span></span> <span data-ttu-id="ef0bd-127">Całego procesu odbywa się w ramach jednej transakcji jest przywracana na końcu.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-127">This entire process takes place within a single transaction, which is rolled back at the end.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef0bd-128">W poniższym przykładzie użyto przykładu **AdventureWorks** bazy danych z programem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-128">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="ef0bd-129">W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-129">The connection string provided in the sample code assumes that the database is installed and available on the local computer.</span></span> <span data-ttu-id="ef0bd-130">Modyfikowanie parametrów połączenia, zgodnie z potrzebami w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="ef0bd-130">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
Option Explicit On  
  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    ' By default, MARS is disabled when connecting  
    ' to a MARS-enabled host.  
    ' It must be enabled in the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Dim updateTx As SqlTransaction  
    Dim vendorCmd As SqlCommand  
    Dim prodVendCmd As SqlCommand  
    Dim updateCmd As SqlCommand  
  
    Dim prodVendReader As SqlDataReader  
  
    Dim vendorID As Integer  
    Dim productID As Integer  
    Dim minOrderQty As Integer  
    Dim maxOrderQty As Integer  
    Dim onOrderQty As Integer  
    Dim recordsUpdated As Integer  
    Dim totalRecordsUpdated As Integer  
  
    Dim vendorSQL As String = _  
        "SELECT VendorID, Name FROM Purchasing.Vendor " & _  
        "WHERE CreditRating = 5"  
    Dim prodVendSQL As String = _  
        "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " & _  
        "FROM Purchasing.ProductVendor " & _  
        "WHERE VendorID = @VendorID"  
    Dim updateSQL As String = _  
        "UPDATE Purchasing.ProductVendor " & _   
        "SET OnOrderQty = @OrderQty " & _  
        "WHERE ProductID = @ProductID AND VendorID = @VendorID"  
  
    Using awConnection As New SqlConnection(connectionString)  
      awConnection.Open()  
      updateTx = awConnection.BeginTransaction()  
  
      vendorCmd = New SqlCommand(vendorSQL, awConnection)  
      vendorCmd.Transaction = updateTx  
  
      prodVendCmd = New SqlCommand(prodVendSQL, awConnection)  
      prodVendCmd.Transaction = updateTx  
      prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int)  
  
      updateCmd = New SqlCommand(updateSQL, awConnection)  
      updateCmd.Transaction = updateTx  
      updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int)  
      updateCmd.Parameters.Add("@ProductID", SqlDbType.Int)  
      updateCmd.Parameters.Add("@VendorID", SqlDbType.Int)  
  
      Using vendorReader As SqlDataReader = vendorCmd.ExecuteReader()  
        While vendorReader.Read()  
          Console.WriteLine(vendorReader("Name"))  
  
          vendorID = CInt(vendorReader("VendorID"))  
          prodVendCmd.Parameters("@VendorID").Value = vendorID  
          prodVendReader = prodVendCmd.ExecuteReader()  
  
          Using prodVendReader  
            While (prodVendReader.Read)  
              productID = CInt(prodVendReader("ProductID"))  
  
              If IsDBNull(prodVendReader("OnOrderQty")) Then  
                minOrderQty = CInt(prodVendReader("MinOrderQty"))  
                onOrderQty = minOrderQty  
              Else  
                maxOrderQty = CInt(prodVendReader("MaxOrderQty"))  
                onOrderQty = CInt(maxOrderQty / 2)  
              End If  
  
              updateCmd.Parameters("@OrderQty").Value = onOrderQty  
              updateCmd.Parameters("@ProductID").Value = productID  
              updateCmd.Parameters("@VendorID").Value = vendorID  
  
              recordsUpdated = updateCmd.ExecuteNonQuery()  
              totalRecordsUpdated += recordsUpdated  
            End While  
          End Using  
        End While  
      End Using  
  
      Console.WriteLine("Total Records Updated: " & _   
        CStr(totalRecordsUpdated))  
      updateTx.Rollback()  
      Console.WriteLine("Transaction Rolled Back")  
    End Using  
  
    Console.WriteLine("Press any key to continue")  
    Console.ReadLine()  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=(local);Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks;MultipleActiveResultSets=True"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
static void Main()  
{  
  // By default, MARS is disabled when connecting  
  // to a MARS-enabled host.  
  // It must be enabled in the connection string.  
  string connectionString = GetConnectionString();  
  
  SqlTransaction updateTx = null;  
  SqlCommand vendorCmd = null;  
  SqlCommand prodVendCmd = null;  
  SqlCommand updateCmd = null;  
  
  SqlDataReader prodVendReader = null;  
  
  int vendorID = 0;  
  int productID = 0;  
  int minOrderQty = 0;  
  int maxOrderQty = 0;  
  int onOrderQty = 0;  
  int recordsUpdated = 0;  
  int totalRecordsUpdated = 0;  
  
  string vendorSQL =  
      "SELECT VendorID, Name FROM Purchasing.Vendor " +   
      "WHERE CreditRating = 5";  
  string prodVendSQL =  
      "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
      "FROM Purchasing.ProductVendor " +   
      "WHERE VendorID = @VendorID";  
  string updateSQL =  
      "UPDATE Purchasing.ProductVendor " +   
      "SET OnOrderQty = @OrderQty " +  
      "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
  using (SqlConnection awConnection =   
    new SqlConnection(connectionString))  
  {  
    awConnection.Open();  
    updateTx = awConnection.BeginTransaction();  
  
    vendorCmd = new SqlCommand(vendorSQL, awConnection);  
    vendorCmd.Transaction = updateTx;  
  
    prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
    prodVendCmd.Transaction = updateTx;  
    prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
    updateCmd = new SqlCommand(updateSQL, awConnection);  
    updateCmd.Transaction = updateTx;  
    updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
    updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
    updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
    using (SqlDataReader vendorReader = vendorCmd.ExecuteReader())  
    {  
      while (vendorReader.Read())  
      {  
        Console.WriteLine(vendorReader["Name"]);  
  
        vendorID = (int) vendorReader["VendorID"];  
        prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
        prodVendReader = prodVendCmd.ExecuteReader();  
  
        using (prodVendReader)  
        {  
          while (prodVendReader.Read())  
          {  
            productID = (int) prodVendReader["ProductID"];  
  
            if (prodVendReader["OnOrderQty"] == DBNull.Value)  
            {  
              minOrderQty = (int) prodVendReader["MinOrderQty"];  
              onOrderQty = minOrderQty;  
            }  
            else  
            {  
              maxOrderQty = (int) prodVendReader["MaxOrderQty"];  
              onOrderQty = (int)(maxOrderQty / 2);  
            }  
  
            updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
            updateCmd.Parameters["@ProductID"].Value = productID;  
            updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
            recordsUpdated = updateCmd.ExecuteNonQuery();  
            totalRecordsUpdated += recordsUpdated;  
          }  
        }  
      }  
    }  
    Console.WriteLine("Total Records Updated: " +   
      totalRecordsUpdated.ToString());  
    updateTx.Rollback();  
    Console.WriteLine("Transaction Rolled Back");  
  }  
  
  Console.WriteLine("Press any key to continue");  
  Console.ReadLine();  
}  
private static string GetConnectionString()  
{  
  // To avoid storing the connection string in your code,  
  // you can retrive it from a configuration file.  
  return "Data Source=(local);Integrated Security=SSPI;" +   
    "Initial Catalog=AdventureWorks;" +   
    "MultipleActiveResultSets=True";  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef0bd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef0bd-131">See also</span></span>

- [<span data-ttu-id="ef0bd-132">Wiele aktywnych zestawów wyników (MARS)</span><span class="sxs-lookup"><span data-stu-id="ef0bd-132">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="ef0bd-133">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="ef0bd-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

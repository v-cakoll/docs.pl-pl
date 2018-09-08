---
title: Określanie wartości XML jako parametrów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2c4d08b8-fc29-4614-97fa-29c8ff7ca5b3
ms.openlocfilehash: 0003e6c5e9499c066f47202a6dd03fc86268d679
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180675"
---
# <a name="specifying-xml-values-as-parameters"></a><span data-ttu-id="a13ae-102">Określanie wartości XML jako parametrów</span><span class="sxs-lookup"><span data-stu-id="a13ae-102">Specifying XML Values as Parameters</span></span>
<span data-ttu-id="a13ae-103">Jeśli zapytanie wymaga parametru, którego wartość jest ciągiem XML, deweloperzy można podać tę wartość przy użyciu wystąpienia **SqlXml** typu danych.</span><span class="sxs-lookup"><span data-stu-id="a13ae-103">If a query requires a parameter whose value is an XML string, developers can supply that value using an instance of the **SqlXml** data type.</span></span> <span data-ttu-id="a13ae-104">Istnieją tak naprawdę nie wskazówki; Kolumn XML w programie SQL Server, zaakceptuj wartości parametrów w dokładnie taki sam sposób jak inne typy danych.</span><span class="sxs-lookup"><span data-stu-id="a13ae-104">There really are no tricks; XML columns in SQL Server accept parameter values in exactly the same way as other data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a13ae-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="a13ae-105">Example</span></span>  
 <span data-ttu-id="a13ae-106">Następująca aplikacja konsoli tworzy nową tabelę w **AdventureWorks** bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a13ae-106">The following console application creates a new table in the **AdventureWorks** database.</span></span> <span data-ttu-id="a13ae-107">Nowa tabela zawiera kolumnę o nazwie **brakuje identyfikatora SalesID** i kolumny XML o nazwie **SalesInfo**.</span><span class="sxs-lookup"><span data-stu-id="a13ae-107">The new table includes a column named **SalesID** and an XML column named **SalesInfo**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a13ae-108">**AdventureWorks** przykładowej bazy danych nie jest instalowany domyślnie podczas instalowania programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a13ae-108">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="a13ae-109">Można go zainstalować, uruchamiając Instalatora programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a13ae-109">You can install it by running SQL Server Setup.</span></span>  
  
 <span data-ttu-id="a13ae-110">Przykład przygotowuje <xref:System.Data.SqlClient.SqlCommand> obiekt do wstawienia wiersza w nowej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a13ae-110">The example prepares a <xref:System.Data.SqlClient.SqlCommand> object to insert a row in the new table.</span></span> <span data-ttu-id="a13ae-111">Zapisany plik zawiera dane XML służące do **SalesInfo** kolumny.</span><span class="sxs-lookup"><span data-stu-id="a13ae-111">A saved file provides the XML data needed for the **SalesInfo** column.</span></span>  
  
 <span data-ttu-id="a13ae-112">Aby utworzyć plik konieczne na przykład aby uruchomić, należy utworzyć nowy plik tekstowy w folderze projektu.</span><span class="sxs-lookup"><span data-stu-id="a13ae-112">To create the file needed for the example to run, create a new text file in the same folder as your project.</span></span> <span data-ttu-id="a13ae-113">Nadaj plikowi nazwę MyTestStoreData.xml.</span><span class="sxs-lookup"><span data-stu-id="a13ae-113">Name the file MyTestStoreData.xml.</span></span> <span data-ttu-id="a13ae-114">Otwórz plik w programie Notatnik i skopiuj i wklej następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="a13ae-114">Open the file in Notepad and copy and paste the following text:</span></span>  
  
```xml  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>International Bank</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1970</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>7000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>T1</Internet>  
  <NumberEmployees>2</NumberEmployees>  
</StoreSurvey>  
```  
  
```vb  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports System.Xml  
  
Module Module1  
    Sub Main()  
  
        Using connection As SqlConnection = New SqlConnection(GetConnectionString())  
        connection.Open()  
  
        ' Create a sample table (dropping first if it already  
        ' exists.)  
        Dim commandNewTable As String = _  
         "IF EXISTS (SELECT * FROM dbo.sysobjects " & _  
         "WHERE id = object_id(N'[dbo].[XmlDataTypeSample]') " & _  
         "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " & _  
         "DROP TABLE [dbo].[XmlDataTypeSample];" & _  
         "CREATE TABLE [dbo].[XmlDataTypeSample](" & _  
         "[SalesID] [int] IDENTITY(1,1) NOT NULL, " & _  
         "[SalesInfo] [xml])"  
  
        Dim commandAdd As New _  
         SqlCommand(commandNewTable, connection)  
        commandAdd.ExecuteNonQuery()  
  
        Dim commandText As String = _  
         "INSERT INTO [dbo].[XmlDataTypeSample] " & _  
           "([SalesInfo] ) " & _  
           "VALUES(@xmlParameter )"  
  
        Dim command As New SqlCommand(commandText, connection)  
  
        ' Read the saved XML document as a   
        ' SqlXml-data typed variable.  
        Dim newXml As SqlXml = _  
         New SqlXml(New XmlTextReader("MyTestStoreData.xml"))  
  
        ' Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml)  
  
        Dim result As Integer = command.ExecuteNonQuery()  
        Console.WriteLine(result & " row was added.")  
        Console.WriteLine("Press Enter to continue.")  
        Console.ReadLine()  
    End Using  
End Sub  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,              
        ' you can retrieve it from a configuration file.   
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks"  
    End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Xml;  
using System.Data.SqlTypes;  
  
class Class1  
{  
    static void Main()  
    {  
        using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
       {  
        connection.Open();  
        //  Create a sample table (dropping first if it already  
        //  exists.)  
  
        string commandNewTable =   
            "IF EXISTS (SELECT * FROM dbo.sysobjects " +   
            "WHERE id = " +  
                  "object_id(N'[dbo].[XmlDataTypeSample]') " +   
            "AND OBJECTPROPERTY(id, N'IsUserTable') = 1) " +   
            "DROP TABLE [dbo].[XmlDataTypeSample];" +   
            "CREATE TABLE [dbo].[XmlDataTypeSample](" +   
            "[SalesID] [int] IDENTITY(1,1) NOT NULL, " +   
            "[SalesInfo] [xml])";  
        SqlCommand commandAdd =   
                   new SqlCommand(commandNewTable, connection);  
        commandAdd.ExecuteNonQuery();  
        string commandText =   
            "INSERT INTO [dbo].[XmlDataTypeSample] " +   
            "([SalesInfo] ) " +   
            "VALUES(@xmlParameter )";  
        SqlCommand command =   
                  new SqlCommand(commandText, connection);  
  
        //  Read the saved XML document as a   
        //  SqlXml-data typed variable.  
        SqlXml newXml =   
            new SqlXml(new XmlTextReader("MyTestStoreData.xml"));  
  
        //  Supply the SqlXml value for the value of the parameter.  
        command.Parameters.AddWithValue("@xmlParameter", newXml);  
  
        int result = command.ExecuteNonQuery();  
        Console.WriteLine(result + " row was added.");  
        Console.WriteLine("Press Enter to continue.");  
        Console.ReadLine();  
    }  
  }  
  
    private static string GetConnectionString()  
    {  
        // To avoid storing the connection string in your code,              
        // you can retrieve it from a configuration file.   
        return "Data Source=(local);Integrated Security=true;" +  
        "Initial Catalog=AdventureWorks; ";  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a13ae-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a13ae-115">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="a13ae-116">Dane XML w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="a13ae-116">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="a13ae-117">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a13ae-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

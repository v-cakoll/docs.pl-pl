---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963179"
---
# <a name="schema-restrictions"></a><span data-ttu-id="65ef0-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="65ef0-102">Schema Restrictions</span></span>
<span data-ttu-id="65ef0-103">Drugim parametrem opcjonalnym metody **GetSchema** jest ograniczenia, które są używane do ograniczenia ilości zwracanych informacji o schemacie i są przesyłane do metody **GetSchema** jako tablica ciągów.</span><span class="sxs-lookup"><span data-stu-id="65ef0-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="65ef0-104">Pozycja w tablicy określa wartości, które można przekazać, i jest równoważne z numerem ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="65ef0-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="65ef0-105">Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcję schematów "tabele" przy użyciu Dostawca danych .NET Framework dla SQL Server.</span><span class="sxs-lookup"><span data-stu-id="65ef0-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="65ef0-106">Dodatkowe ograniczenia dotyczące kolekcji schematów SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="65ef0-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="65ef0-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-107">Restriction Name</span></span>|<span data-ttu-id="65ef0-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-108">Parameter Name</span></span>|<span data-ttu-id="65ef0-109">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-109">Restriction Default</span></span>|<span data-ttu-id="65ef0-110">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-111">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-111">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-112">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-113">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-113">1</span></span>|  
|<span data-ttu-id="65ef0-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-114">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-116">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-116">2</span></span>|  
|<span data-ttu-id="65ef0-117">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-117">Table</span></span>|@Name|<span data-ttu-id="65ef0-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-118">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-119">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-119">3</span></span>|  
|<span data-ttu-id="65ef0-120">Tabletype</span><span class="sxs-lookup"><span data-stu-id="65ef0-120">TableType</span></span>|@TableType|<span data-ttu-id="65ef0-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65ef0-121">TABLE_TYPE</span></span>|<span data-ttu-id="65ef0-122">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="65ef0-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="65ef0-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="65ef0-124">Aby użyć jednego z ograniczeń kolekcji schematów "tabele", po prostu Utwórz tablicę ciągów z czterema elementami, a następnie umieść wartość w elemencie, który jest zgodny z numerem ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="65ef0-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="65ef0-125">Na przykład aby ograniczyć tabele zwracane przez metodę **GetSchema** do tylko tych tabel w schemacie "Sales", należy ustawić drugi element tablicy na "Sales" przed przekazaniem go do metody **GetSchema** .</span><span class="sxs-lookup"><span data-stu-id="65ef0-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65ef0-126">Kolekcje ograniczeń dla `SqlClient` i `OracleClient` mają dodatkową `ParameterName` kolumnę.</span><span class="sxs-lookup"><span data-stu-id="65ef0-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="65ef0-127">Domyślna kolumna ograniczenia nadal ma zgodność z poprzednimi wersjami, ale jest obecnie ignorowana.</span><span class="sxs-lookup"><span data-stu-id="65ef0-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="65ef0-128">Zapytania sparametryzowane zamiast zamiany ciągu powinny służyć do zminimalizowania ryzyka związanego z iniekcją kodu SQL podczas określania wartości ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="65ef0-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65ef0-129">Liczba elementów w tablicy musi być mniejsza lub równa liczbie ograniczeń, które są obsługiwane dla określonej kolekcji schematów, w przeciwnym razie <xref:System.ArgumentException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="65ef0-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="65ef0-130">Może być mniejsza niż maksymalna liczba ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="65ef0-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="65ef0-131">W przypadku brakujących ograniczeń przyjmuje się, że wartość jest równa null (bez ograniczeń).</span><span class="sxs-lookup"><span data-stu-id="65ef0-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="65ef0-132">Można wysłać zapytanie do dostawcy zarządzanego .NET Framework, aby określić listę obsługiwanych ograniczeń, wywołując metodę **GetSchema** z nazwą kolekcji schematów ograniczeń, która jest "ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="65ef0-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="65ef0-133">Spowoduje to zwrócenie <xref:System.Data.DataTable> listy nazw kolekcji, nazw ograniczeń, domyślnych wartości ograniczeń oraz numerów ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="65ef0-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="65ef0-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="65ef0-134">Example</span></span>  
 <span data-ttu-id="65ef0-135">W poniższych przykładach pokazano, jak za <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> pomocą metody dostawca danych .NET Framework dla klasy SQL Server <xref:System.Data.SqlClient.SqlConnection> pobrać informacje o schemacie dotyczące wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks** , i w celu ograniczenia informacji zwracanych do tylko tych tabel w schemacie "Sales":</span><span class="sxs-lookup"><span data-stu-id="65ef0-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="65ef0-136">SQL Server ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="65ef0-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="65ef0-137">W poniższej tabeli wymieniono ograniczenia dotyczące SQL Serverych kolekcji schematów.</span><span class="sxs-lookup"><span data-stu-id="65ef0-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="65ef0-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="65ef0-138">Users</span></span>  
  
|<span data-ttu-id="65ef0-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-139">Restriction Name</span></span>|<span data-ttu-id="65ef0-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-140">Parameter Name</span></span>|<span data-ttu-id="65ef0-141">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-141">Restriction Default</span></span>|<span data-ttu-id="65ef0-142">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-143">Nazwa_użytkownika</span><span class="sxs-lookup"><span data-stu-id="65ef0-143">User_Name</span></span>|@Name|<span data-ttu-id="65ef0-144">nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-144">name</span></span>|<span data-ttu-id="65ef0-145">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="65ef0-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="65ef0-146">Databases</span></span>  
  
|<span data-ttu-id="65ef0-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-147">Restriction Name</span></span>|<span data-ttu-id="65ef0-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-148">Parameter Name</span></span>|<span data-ttu-id="65ef0-149">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-149">Restriction Default</span></span>|<span data-ttu-id="65ef0-150">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-151">Name</span></span>|@Name|<span data-ttu-id="65ef0-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-152">Name</span></span>|<span data-ttu-id="65ef0-153">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="65ef0-154">Tabelę</span><span class="sxs-lookup"><span data-stu-id="65ef0-154">Tables</span></span>  
  
|<span data-ttu-id="65ef0-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-155">Restriction Name</span></span>|<span data-ttu-id="65ef0-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-156">Parameter Name</span></span>|<span data-ttu-id="65ef0-157">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-157">Restriction Default</span></span>|<span data-ttu-id="65ef0-158">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-159">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-159">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-160">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-161">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-161">1</span></span>|  
|<span data-ttu-id="65ef0-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-162">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-164">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-164">2</span></span>|  
|<span data-ttu-id="65ef0-165">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-165">Table</span></span>|@Name|<span data-ttu-id="65ef0-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-166">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-167">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-167">3</span></span>|  
|<span data-ttu-id="65ef0-168">Tabletype</span><span class="sxs-lookup"><span data-stu-id="65ef0-168">TableType</span></span>|@TableType|<span data-ttu-id="65ef0-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65ef0-169">TABLE_TYPE</span></span>|<span data-ttu-id="65ef0-170">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="65ef0-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="65ef0-171">Columns</span></span>  
  
|<span data-ttu-id="65ef0-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-172">Restriction Name</span></span>|<span data-ttu-id="65ef0-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-173">Parameter Name</span></span>|<span data-ttu-id="65ef0-174">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-174">Restriction Default</span></span>|<span data-ttu-id="65ef0-175">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-176">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-176">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-177">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-178">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-178">1</span></span>|  
|<span data-ttu-id="65ef0-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-179">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-181">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-181">2</span></span>|  
|<span data-ttu-id="65ef0-182">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-182">Table</span></span>|@Table|<span data-ttu-id="65ef0-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-183">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-184">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-184">3</span></span>|  
|<span data-ttu-id="65ef0-185">Kolumna</span><span class="sxs-lookup"><span data-stu-id="65ef0-185">Column</span></span>|@Column|<span data-ttu-id="65ef0-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-186">COLUMN_NAME</span></span>|<span data-ttu-id="65ef0-187">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="65ef0-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="65ef0-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="65ef0-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-189">Restriction Name</span></span>|<span data-ttu-id="65ef0-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-190">Parameter Name</span></span>|<span data-ttu-id="65ef0-191">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-191">Restriction Default</span></span>|<span data-ttu-id="65ef0-192">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-193">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-193">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-194">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-195">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-195">1</span></span>|  
|<span data-ttu-id="65ef0-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-196">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-198">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-198">2</span></span>|  
|<span data-ttu-id="65ef0-199">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-199">Table</span></span>|@Table|<span data-ttu-id="65ef0-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-200">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-201">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-201">3</span></span>|  
|<span data-ttu-id="65ef0-202">Kolumna</span><span class="sxs-lookup"><span data-stu-id="65ef0-202">Column</span></span>|@Column|<span data-ttu-id="65ef0-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-203">COLUMN_NAME</span></span>|<span data-ttu-id="65ef0-204">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="65ef0-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="65ef0-205">Views</span></span>  
  
|<span data-ttu-id="65ef0-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-206">Restriction Name</span></span>|<span data-ttu-id="65ef0-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-207">Parameter Name</span></span>|<span data-ttu-id="65ef0-208">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-208">Restriction Default</span></span>|<span data-ttu-id="65ef0-209">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-210">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-210">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-211">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-212">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-212">1</span></span>|  
|<span data-ttu-id="65ef0-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-213">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-215">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-215">2</span></span>|  
|<span data-ttu-id="65ef0-216">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-216">Table</span></span>|@Table|<span data-ttu-id="65ef0-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-217">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-218">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="65ef0-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="65ef0-219">ViewColumns</span></span>  
  
|<span data-ttu-id="65ef0-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-220">Restriction Name</span></span>|<span data-ttu-id="65ef0-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-221">Parameter Name</span></span>|<span data-ttu-id="65ef0-222">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-222">Restriction Default</span></span>|<span data-ttu-id="65ef0-223">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-224">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-224">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-225">VIEW_CATALOG</span></span>|<span data-ttu-id="65ef0-226">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-226">1</span></span>|  
|<span data-ttu-id="65ef0-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-227">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="65ef0-229">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-229">2</span></span>|  
|<span data-ttu-id="65ef0-230">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-230">Table</span></span>|@Table|<span data-ttu-id="65ef0-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-231">VIEW_NAME</span></span>|<span data-ttu-id="65ef0-232">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-232">3</span></span>|  
|<span data-ttu-id="65ef0-233">Kolumna</span><span class="sxs-lookup"><span data-stu-id="65ef0-233">Column</span></span>|@Column|<span data-ttu-id="65ef0-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-234">COLUMN_NAME</span></span>|<span data-ttu-id="65ef0-235">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="65ef0-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="65ef0-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="65ef0-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-237">Restriction Name</span></span>|<span data-ttu-id="65ef0-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-238">Parameter Name</span></span>|<span data-ttu-id="65ef0-239">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-239">Restriction Default</span></span>|<span data-ttu-id="65ef0-240">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-241">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-241">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="65ef0-243">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-243">1</span></span>|  
|<span data-ttu-id="65ef0-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-244">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="65ef0-246">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-246">2</span></span>|  
|<span data-ttu-id="65ef0-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-247">Name</span></span>|@Name|<span data-ttu-id="65ef0-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="65ef0-249">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-249">3</span></span>|  
|<span data-ttu-id="65ef0-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="65ef0-250">Parameter</span></span>|@Parameter|<span data-ttu-id="65ef0-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-251">PARAMETER_NAME</span></span>|<span data-ttu-id="65ef0-252">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="65ef0-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="65ef0-253">Procedures</span></span>  
  
|<span data-ttu-id="65ef0-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-254">Restriction Name</span></span>|<span data-ttu-id="65ef0-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-255">Parameter Name</span></span>|<span data-ttu-id="65ef0-256">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-256">Restriction Default</span></span>|<span data-ttu-id="65ef0-257">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-258">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="65ef0-260">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-260">1</span></span>|  
|<span data-ttu-id="65ef0-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-261">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="65ef0-263">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-263">2</span></span>|  
|<span data-ttu-id="65ef0-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-264">Name</span></span>|@Name|<span data-ttu-id="65ef0-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="65ef0-266">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-266">3</span></span>|  
|<span data-ttu-id="65ef0-267">Typ</span><span class="sxs-lookup"><span data-stu-id="65ef0-267">Type</span></span>|@Type|<span data-ttu-id="65ef0-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65ef0-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="65ef0-269">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="65ef0-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="65ef0-270">IndexColumns</span></span>  
  
|<span data-ttu-id="65ef0-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-271">Restriction Name</span></span>|<span data-ttu-id="65ef0-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-272">Parameter Name</span></span>|<span data-ttu-id="65ef0-273">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-273">Restriction Default</span></span>|<span data-ttu-id="65ef0-274">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-275">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-275">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="65ef0-276">db_name()</span></span>|<span data-ttu-id="65ef0-277">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-277">1</span></span>|  
|<span data-ttu-id="65ef0-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-278">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="65ef0-279">user_name()</span></span>|<span data-ttu-id="65ef0-280">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-280">2</span></span>|  
|<span data-ttu-id="65ef0-281">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-281">Table</span></span>|@Table|<span data-ttu-id="65ef0-282">o.name</span><span class="sxs-lookup"><span data-stu-id="65ef0-282">o.name</span></span>|<span data-ttu-id="65ef0-283">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-283">3</span></span>|  
|<span data-ttu-id="65ef0-284">Element ConstraintName</span><span class="sxs-lookup"><span data-stu-id="65ef0-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="65ef0-285">x.name</span><span class="sxs-lookup"><span data-stu-id="65ef0-285">x.name</span></span>|<span data-ttu-id="65ef0-286">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-286">4</span></span>|  
|<span data-ttu-id="65ef0-287">Kolumna</span><span class="sxs-lookup"><span data-stu-id="65ef0-287">Column</span></span>|@Column|<span data-ttu-id="65ef0-288">c.name</span><span class="sxs-lookup"><span data-stu-id="65ef0-288">c.name</span></span>|<span data-ttu-id="65ef0-289">5</span><span class="sxs-lookup"><span data-stu-id="65ef0-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="65ef0-290">Zwiększa</span><span class="sxs-lookup"><span data-stu-id="65ef0-290">Indexes</span></span>  
  
|<span data-ttu-id="65ef0-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-291">Restriction Name</span></span>|<span data-ttu-id="65ef0-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-292">Parameter Name</span></span>|<span data-ttu-id="65ef0-293">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-293">Restriction Default</span></span>|<span data-ttu-id="65ef0-294">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-295">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-295">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="65ef0-296">db_name()</span></span>|<span data-ttu-id="65ef0-297">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-297">1</span></span>|  
|<span data-ttu-id="65ef0-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-298">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="65ef0-299">user_name()</span></span>|<span data-ttu-id="65ef0-300">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-300">2</span></span>|  
|<span data-ttu-id="65ef0-301">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-301">Table</span></span>|@Table|<span data-ttu-id="65ef0-302">o.name</span><span class="sxs-lookup"><span data-stu-id="65ef0-302">o.name</span></span>|<span data-ttu-id="65ef0-303">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="65ef0-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="65ef0-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="65ef0-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-305">Restriction Name</span></span>|<span data-ttu-id="65ef0-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-306">Parameter Name</span></span>|<span data-ttu-id="65ef0-307">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-307">Restriction Default</span></span>|<span data-ttu-id="65ef0-308">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="65ef0-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="65ef0-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="65ef0-310">assemblies.name</span></span>|<span data-ttu-id="65ef0-311">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-311">1</span></span>|  
|<span data-ttu-id="65ef0-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="65ef0-312">udt_name</span></span>|@UDTName|<span data-ttu-id="65ef0-313">typy. assembly_class</span><span class="sxs-lookup"><span data-stu-id="65ef0-313">types.assembly_class</span></span>|<span data-ttu-id="65ef0-314">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="65ef0-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="65ef0-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="65ef0-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-316">Restriction Name</span></span>|<span data-ttu-id="65ef0-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-317">Parameter Name</span></span>|<span data-ttu-id="65ef0-318">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-318">Restriction Default</span></span>|<span data-ttu-id="65ef0-319">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-320">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-320">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="65ef0-322">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-322">1</span></span>|  
|<span data-ttu-id="65ef0-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-323">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="65ef0-325">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-325">2</span></span>|  
|<span data-ttu-id="65ef0-326">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-326">Table</span></span>|@Table|<span data-ttu-id="65ef0-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-327">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-328">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-328">3</span></span>|  
|<span data-ttu-id="65ef0-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65ef0-329">Name</span></span>|@Name|<span data-ttu-id="65ef0-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="65ef0-331">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="65ef0-332">Ograniczenia schematu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="65ef0-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="65ef0-333">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematów SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="65ef0-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="65ef0-334">Te ograniczenia są prawidłowe od wersji 3,5 SP1 .NET Framework i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="65ef0-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="65ef0-335">Nie są one obsługiwane we wcześniejszych wersjach .NET Framework i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="65ef0-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="65ef0-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="65ef0-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="65ef0-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-337">Restriction Name</span></span>|<span data-ttu-id="65ef0-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-338">Parameter Name</span></span>|<span data-ttu-id="65ef0-339">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-339">Restriction Default</span></span>|<span data-ttu-id="65ef0-340">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-341">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-341">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-342">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-343">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-343">1</span></span>|  
|<span data-ttu-id="65ef0-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-344">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-346">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-346">2</span></span>|  
|<span data-ttu-id="65ef0-347">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-347">Table</span></span>|@Table|<span data-ttu-id="65ef0-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-348">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-349">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="65ef0-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="65ef0-350">AllColumns</span></span>  
  
|<span data-ttu-id="65ef0-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-351">Restriction Name</span></span>|<span data-ttu-id="65ef0-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="65ef0-352">Parameter Name</span></span>|<span data-ttu-id="65ef0-353">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="65ef0-353">Restriction Default</span></span>|<span data-ttu-id="65ef0-354">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="65ef0-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="65ef0-355">Wykaz</span><span class="sxs-lookup"><span data-stu-id="65ef0-355">Catalog</span></span>|@Catalog|<span data-ttu-id="65ef0-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65ef0-356">TABLE_CATALOG</span></span>|<span data-ttu-id="65ef0-357">1</span><span class="sxs-lookup"><span data-stu-id="65ef0-357">1</span></span>|  
|<span data-ttu-id="65ef0-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="65ef0-358">Owner</span></span>|@Owner|<span data-ttu-id="65ef0-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65ef0-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="65ef0-360">2</span><span class="sxs-lookup"><span data-stu-id="65ef0-360">2</span></span>|  
|<span data-ttu-id="65ef0-361">tabela</span><span class="sxs-lookup"><span data-stu-id="65ef0-361">Table</span></span>|@Table|<span data-ttu-id="65ef0-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-362">TABLE_NAME</span></span>|<span data-ttu-id="65ef0-363">3</span><span class="sxs-lookup"><span data-stu-id="65ef0-363">3</span></span>|  
|<span data-ttu-id="65ef0-364">Kolumna</span><span class="sxs-lookup"><span data-stu-id="65ef0-364">Column</span></span>|@Column|<span data-ttu-id="65ef0-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65ef0-365">COLUMN_NAME</span></span>|<span data-ttu-id="65ef0-366">4</span><span class="sxs-lookup"><span data-stu-id="65ef0-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65ef0-367">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65ef0-367">See also</span></span>

- [<span data-ttu-id="65ef0-368">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="65ef0-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

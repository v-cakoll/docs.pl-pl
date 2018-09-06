---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 040ecd8a2ce223f89601de735b77ccc81638c7af
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801534"
---
# <a name="schema-restrictions"></a><span data-ttu-id="06a70-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="06a70-102">Schema Restrictions</span></span>
<span data-ttu-id="06a70-103">Drugi parametr opcjonalny **GetSchema** metodą jest zwracane ograniczenia, które są używane do ograniczenia ilości informacji o schemacie, a zostanie on przekazany do **GetSchema** metodę jako tablica ciągów .</span><span class="sxs-lookup"><span data-stu-id="06a70-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="06a70-104">Pozycja w tablicy określa wartości, które można przekazać, a jest równa liczbie ograniczania.</span><span class="sxs-lookup"><span data-stu-id="06a70-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="06a70-105">Na przykład w poniższej tabeli opisano ograniczenia dotyczące obsługiwanych przez kolekcji schematów "Tabele" przy użyciu .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="06a70-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="06a70-106">Dodatkowe ograniczenia dotyczące kolekcje schematów programu SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="06a70-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="06a70-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-107">Restriction Name</span></span>|<span data-ttu-id="06a70-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-108">Parameter Name</span></span>|<span data-ttu-id="06a70-109">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-109">Restriction Default</span></span>|<span data-ttu-id="06a70-110">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-111">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-111">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-112">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-113">1</span><span class="sxs-lookup"><span data-stu-id="06a70-113">1</span></span>|  
|<span data-ttu-id="06a70-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-114">Owner</span></span>|@Owner|<span data-ttu-id="06a70-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-116">2</span><span class="sxs-lookup"><span data-stu-id="06a70-116">2</span></span>|  
|<span data-ttu-id="06a70-117">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-117">Table</span></span>|@Name|<span data-ttu-id="06a70-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-118">TABLE_NAME</span></span>|<span data-ttu-id="06a70-119">3</span><span class="sxs-lookup"><span data-stu-id="06a70-119">3</span></span>|  
|<span data-ttu-id="06a70-120">Typem</span><span class="sxs-lookup"><span data-stu-id="06a70-120">TableType</span></span>|@TableType|<span data-ttu-id="06a70-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="06a70-121">TABLE_TYPE</span></span>|<span data-ttu-id="06a70-122">4</span><span class="sxs-lookup"><span data-stu-id="06a70-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="06a70-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="06a70-124">Aby użyć jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicę ciągów z czterema elementami, a następnie umieść wartość w elemencie który odpowiada liczbie ograniczania.</span><span class="sxs-lookup"><span data-stu-id="06a70-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="06a70-125">Na przykład, aby ograniczyć tabele zwracane przez **GetSchema** metody tylko do tabel schematu "Sprzedaż", ustaw drugiego elementu tablicy, aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="06a70-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06a70-126">Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkową `ParameterName` kolumny.</span><span class="sxs-lookup"><span data-stu-id="06a70-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="06a70-127">Ograniczenie domyślną kolumnę jest nadal dostępna dla wstecznej zgodności, ale obecnie jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="06a70-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="06a70-128">Aby zminimalizować ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczenia należy używać zamiast zastępowania ciągów zapytań sparametryzowanych.</span><span class="sxs-lookup"><span data-stu-id="06a70-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06a70-129">Liczba elementów w tablicy musi być mniejsza niż liczba ograniczeń obsługiwane w przypadku kolekcji określony schemat else <xref:System.ArgumentException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="06a70-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="06a70-130">Może być mniejsza niż maksymalna liczba ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="06a70-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="06a70-131">Brak ograniczeń są uznawane za wartość null (nieograniczony).</span><span class="sxs-lookup"><span data-stu-id="06a70-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="06a70-132">Można tworzyć zapytania zarządzanego dostawcy .NET Framework, aby określić listę ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji schematów ograniczeniom, czyli "Ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="06a70-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="06a70-133">Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazw kolekcji, nazwy ograniczeń, wartości domyślne ograniczenia i ograniczenie liczby.</span><span class="sxs-lookup"><span data-stu-id="06a70-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="06a70-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="06a70-134">Example</span></span>  
 <span data-ttu-id="06a70-135">W poniższych przykładach pokazano sposób użycia <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody .NET Framework Data Provider for SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy do pobrania informacji o schemacie o wszystkich tabelach zawartych w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwrócone do tylko tych tabel w schemacie "terminy sprzedaż":</span><span class="sxs-lookup"><span data-stu-id="06a70-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="06a70-136">Ograniczenia schematu programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="06a70-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="06a70-137">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcje schematów programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="06a70-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="06a70-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="06a70-138">Users</span></span>  
  
|<span data-ttu-id="06a70-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-139">Restriction Name</span></span>|<span data-ttu-id="06a70-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-140">Parameter Name</span></span>|<span data-ttu-id="06a70-141">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-141">Restriction Default</span></span>|<span data-ttu-id="06a70-142">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-143">Nazwa_użytkownika</span><span class="sxs-lookup"><span data-stu-id="06a70-143">User_Name</span></span>|@Name|<span data-ttu-id="06a70-144">nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-144">name</span></span>|<span data-ttu-id="06a70-145">1</span><span class="sxs-lookup"><span data-stu-id="06a70-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="06a70-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="06a70-146">Databases</span></span>  
  
|<span data-ttu-id="06a70-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-147">Restriction Name</span></span>|<span data-ttu-id="06a70-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-148">Parameter Name</span></span>|<span data-ttu-id="06a70-149">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-149">Restriction Default</span></span>|<span data-ttu-id="06a70-150">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-151">Name</span></span>|@Name|<span data-ttu-id="06a70-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-152">Name</span></span>|<span data-ttu-id="06a70-153">1</span><span class="sxs-lookup"><span data-stu-id="06a70-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="06a70-154">Tabele</span><span class="sxs-lookup"><span data-stu-id="06a70-154">Tables</span></span>  
  
|<span data-ttu-id="06a70-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-155">Restriction Name</span></span>|<span data-ttu-id="06a70-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-156">Parameter Name</span></span>|<span data-ttu-id="06a70-157">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-157">Restriction Default</span></span>|<span data-ttu-id="06a70-158">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-159">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-159">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-160">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-161">1</span><span class="sxs-lookup"><span data-stu-id="06a70-161">1</span></span>|  
|<span data-ttu-id="06a70-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-162">Owner</span></span>|@Owner|<span data-ttu-id="06a70-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-164">2</span><span class="sxs-lookup"><span data-stu-id="06a70-164">2</span></span>|  
|<span data-ttu-id="06a70-165">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-165">Table</span></span>|@Name|<span data-ttu-id="06a70-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-166">TABLE_NAME</span></span>|<span data-ttu-id="06a70-167">3</span><span class="sxs-lookup"><span data-stu-id="06a70-167">3</span></span>|  
|<span data-ttu-id="06a70-168">Typem</span><span class="sxs-lookup"><span data-stu-id="06a70-168">TableType</span></span>|@TableType|<span data-ttu-id="06a70-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="06a70-169">TABLE_TYPE</span></span>|<span data-ttu-id="06a70-170">4</span><span class="sxs-lookup"><span data-stu-id="06a70-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="06a70-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-171">Columns</span></span>  
  
|<span data-ttu-id="06a70-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-172">Restriction Name</span></span>|<span data-ttu-id="06a70-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-173">Parameter Name</span></span>|<span data-ttu-id="06a70-174">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-174">Restriction Default</span></span>|<span data-ttu-id="06a70-175">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-176">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-176">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-177">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-178">1</span><span class="sxs-lookup"><span data-stu-id="06a70-178">1</span></span>|  
|<span data-ttu-id="06a70-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-179">Owner</span></span>|@Owner|<span data-ttu-id="06a70-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-181">2</span><span class="sxs-lookup"><span data-stu-id="06a70-181">2</span></span>|  
|<span data-ttu-id="06a70-182">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-182">Table</span></span>|@Table|<span data-ttu-id="06a70-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-183">TABLE_NAME</span></span>|<span data-ttu-id="06a70-184">3</span><span class="sxs-lookup"><span data-stu-id="06a70-184">3</span></span>|  
|<span data-ttu-id="06a70-185">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-185">Column</span></span>|@Column|<span data-ttu-id="06a70-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-186">COLUMN_NAME</span></span>|<span data-ttu-id="06a70-187">4</span><span class="sxs-lookup"><span data-stu-id="06a70-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="06a70-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="06a70-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="06a70-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-189">Restriction Name</span></span>|<span data-ttu-id="06a70-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-190">Parameter Name</span></span>|<span data-ttu-id="06a70-191">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-191">Restriction Default</span></span>|<span data-ttu-id="06a70-192">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-193">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-193">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-194">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-195">1</span><span class="sxs-lookup"><span data-stu-id="06a70-195">1</span></span>|  
|<span data-ttu-id="06a70-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-196">Owner</span></span>|@Owner|<span data-ttu-id="06a70-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-198">2</span><span class="sxs-lookup"><span data-stu-id="06a70-198">2</span></span>|  
|<span data-ttu-id="06a70-199">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-199">Table</span></span>|@Table|<span data-ttu-id="06a70-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-200">TABLE_NAME</span></span>|<span data-ttu-id="06a70-201">3</span><span class="sxs-lookup"><span data-stu-id="06a70-201">3</span></span>|  
|<span data-ttu-id="06a70-202">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-202">Column</span></span>|@Column|<span data-ttu-id="06a70-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-203">COLUMN_NAME</span></span>|<span data-ttu-id="06a70-204">4</span><span class="sxs-lookup"><span data-stu-id="06a70-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="06a70-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="06a70-205">Views</span></span>  
  
|<span data-ttu-id="06a70-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-206">Restriction Name</span></span>|<span data-ttu-id="06a70-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-207">Parameter Name</span></span>|<span data-ttu-id="06a70-208">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-208">Restriction Default</span></span>|<span data-ttu-id="06a70-209">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-210">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-210">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-211">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-212">1</span><span class="sxs-lookup"><span data-stu-id="06a70-212">1</span></span>|  
|<span data-ttu-id="06a70-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-213">Owner</span></span>|@Owner|<span data-ttu-id="06a70-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-215">2</span><span class="sxs-lookup"><span data-stu-id="06a70-215">2</span></span>|  
|<span data-ttu-id="06a70-216">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-216">Table</span></span>|@Table|<span data-ttu-id="06a70-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-217">TABLE_NAME</span></span>|<span data-ttu-id="06a70-218">3</span><span class="sxs-lookup"><span data-stu-id="06a70-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="06a70-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="06a70-219">ViewColumns</span></span>  
  
|<span data-ttu-id="06a70-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-220">Restriction Name</span></span>|<span data-ttu-id="06a70-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-221">Parameter Name</span></span>|<span data-ttu-id="06a70-222">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-222">Restriction Default</span></span>|<span data-ttu-id="06a70-223">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-224">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-224">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-225">VIEW_CATALOG</span></span>|<span data-ttu-id="06a70-226">1</span><span class="sxs-lookup"><span data-stu-id="06a70-226">1</span></span>|  
|<span data-ttu-id="06a70-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-227">Owner</span></span>|@Owner|<span data-ttu-id="06a70-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="06a70-229">2</span><span class="sxs-lookup"><span data-stu-id="06a70-229">2</span></span>|  
|<span data-ttu-id="06a70-230">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-230">Table</span></span>|@Table|<span data-ttu-id="06a70-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-231">VIEW_NAME</span></span>|<span data-ttu-id="06a70-232">3</span><span class="sxs-lookup"><span data-stu-id="06a70-232">3</span></span>|  
|<span data-ttu-id="06a70-233">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-233">Column</span></span>|@Column|<span data-ttu-id="06a70-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-234">COLUMN_NAME</span></span>|<span data-ttu-id="06a70-235">4</span><span class="sxs-lookup"><span data-stu-id="06a70-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="06a70-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="06a70-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="06a70-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-237">Restriction Name</span></span>|<span data-ttu-id="06a70-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-238">Parameter Name</span></span>|<span data-ttu-id="06a70-239">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-239">Restriction Default</span></span>|<span data-ttu-id="06a70-240">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-241">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-241">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="06a70-243">1</span><span class="sxs-lookup"><span data-stu-id="06a70-243">1</span></span>|  
|<span data-ttu-id="06a70-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-244">Owner</span></span>|@Owner|<span data-ttu-id="06a70-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="06a70-246">2</span><span class="sxs-lookup"><span data-stu-id="06a70-246">2</span></span>|  
|<span data-ttu-id="06a70-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-247">Name</span></span>|@Name|<span data-ttu-id="06a70-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="06a70-249">3</span><span class="sxs-lookup"><span data-stu-id="06a70-249">3</span></span>|  
|<span data-ttu-id="06a70-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="06a70-250">Parameter</span></span>|@Parameter|<span data-ttu-id="06a70-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-251">PARAMETER_NAME</span></span>|<span data-ttu-id="06a70-252">4</span><span class="sxs-lookup"><span data-stu-id="06a70-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="06a70-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="06a70-253">Procedures</span></span>  
  
|<span data-ttu-id="06a70-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-254">Restriction Name</span></span>|<span data-ttu-id="06a70-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-255">Parameter Name</span></span>|<span data-ttu-id="06a70-256">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-256">Restriction Default</span></span>|<span data-ttu-id="06a70-257">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-258">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="06a70-260">1</span><span class="sxs-lookup"><span data-stu-id="06a70-260">1</span></span>|  
|<span data-ttu-id="06a70-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-261">Owner</span></span>|@Owner|<span data-ttu-id="06a70-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="06a70-263">2</span><span class="sxs-lookup"><span data-stu-id="06a70-263">2</span></span>|  
|<span data-ttu-id="06a70-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-264">Name</span></span>|@Name|<span data-ttu-id="06a70-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="06a70-266">3</span><span class="sxs-lookup"><span data-stu-id="06a70-266">3</span></span>|  
|<span data-ttu-id="06a70-267">Typ</span><span class="sxs-lookup"><span data-stu-id="06a70-267">Type</span></span>|@Type|<span data-ttu-id="06a70-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="06a70-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="06a70-269">4</span><span class="sxs-lookup"><span data-stu-id="06a70-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="06a70-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="06a70-270">IndexColumns</span></span>  
  
|<span data-ttu-id="06a70-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-271">Restriction Name</span></span>|<span data-ttu-id="06a70-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-272">Parameter Name</span></span>|<span data-ttu-id="06a70-273">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-273">Restriction Default</span></span>|<span data-ttu-id="06a70-274">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-275">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-275">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="06a70-276">db_name()</span></span>|<span data-ttu-id="06a70-277">1</span><span class="sxs-lookup"><span data-stu-id="06a70-277">1</span></span>|  
|<span data-ttu-id="06a70-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-278">Owner</span></span>|@Owner|<span data-ttu-id="06a70-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="06a70-279">user_name()</span></span>|<span data-ttu-id="06a70-280">2</span><span class="sxs-lookup"><span data-stu-id="06a70-280">2</span></span>|  
|<span data-ttu-id="06a70-281">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-281">Table</span></span>|@Table|<span data-ttu-id="06a70-282">o.name</span><span class="sxs-lookup"><span data-stu-id="06a70-282">o.name</span></span>|<span data-ttu-id="06a70-283">3</span><span class="sxs-lookup"><span data-stu-id="06a70-283">3</span></span>|  
|<span data-ttu-id="06a70-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="06a70-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="06a70-285">x.name</span><span class="sxs-lookup"><span data-stu-id="06a70-285">x.name</span></span>|<span data-ttu-id="06a70-286">4</span><span class="sxs-lookup"><span data-stu-id="06a70-286">4</span></span>|  
|<span data-ttu-id="06a70-287">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-287">Column</span></span>|@Column|<span data-ttu-id="06a70-288">c.name</span><span class="sxs-lookup"><span data-stu-id="06a70-288">c.name</span></span>|<span data-ttu-id="06a70-289">5</span><span class="sxs-lookup"><span data-stu-id="06a70-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="06a70-290">Indeksy</span><span class="sxs-lookup"><span data-stu-id="06a70-290">Indexes</span></span>  
  
|<span data-ttu-id="06a70-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-291">Restriction Name</span></span>|<span data-ttu-id="06a70-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-292">Parameter Name</span></span>|<span data-ttu-id="06a70-293">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-293">Restriction Default</span></span>|<span data-ttu-id="06a70-294">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-295">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-295">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="06a70-296">db_name()</span></span>|<span data-ttu-id="06a70-297">1</span><span class="sxs-lookup"><span data-stu-id="06a70-297">1</span></span>|  
|<span data-ttu-id="06a70-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-298">Owner</span></span>|@Owner|<span data-ttu-id="06a70-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="06a70-299">user_name()</span></span>|<span data-ttu-id="06a70-300">2</span><span class="sxs-lookup"><span data-stu-id="06a70-300">2</span></span>|  
|<span data-ttu-id="06a70-301">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-301">Table</span></span>|@Table|<span data-ttu-id="06a70-302">o.name</span><span class="sxs-lookup"><span data-stu-id="06a70-302">o.name</span></span>|<span data-ttu-id="06a70-303">3</span><span class="sxs-lookup"><span data-stu-id="06a70-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="06a70-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="06a70-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="06a70-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-305">Restriction Name</span></span>|<span data-ttu-id="06a70-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-306">Parameter Name</span></span>|<span data-ttu-id="06a70-307">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-307">Restriction Default</span></span>|<span data-ttu-id="06a70-308">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="06a70-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="06a70-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="06a70-310">assemblies.name</span></span>|<span data-ttu-id="06a70-311">1</span><span class="sxs-lookup"><span data-stu-id="06a70-311">1</span></span>|  
|<span data-ttu-id="06a70-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="06a70-312">udt_name</span></span>|@UDTName|<span data-ttu-id="06a70-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="06a70-313">types.assembly_class</span></span>|<span data-ttu-id="06a70-314">2</span><span class="sxs-lookup"><span data-stu-id="06a70-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="06a70-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="06a70-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="06a70-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-316">Restriction Name</span></span>|<span data-ttu-id="06a70-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-317">Parameter Name</span></span>|<span data-ttu-id="06a70-318">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-318">Restriction Default</span></span>|<span data-ttu-id="06a70-319">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-320">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-320">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="06a70-322">1</span><span class="sxs-lookup"><span data-stu-id="06a70-322">1</span></span>|  
|<span data-ttu-id="06a70-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-323">Owner</span></span>|@Owner|<span data-ttu-id="06a70-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="06a70-325">2</span><span class="sxs-lookup"><span data-stu-id="06a70-325">2</span></span>|  
|<span data-ttu-id="06a70-326">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-326">Table</span></span>|@Table|<span data-ttu-id="06a70-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-327">TABLE_NAME</span></span>|<span data-ttu-id="06a70-328">3</span><span class="sxs-lookup"><span data-stu-id="06a70-328">3</span></span>|  
|<span data-ttu-id="06a70-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06a70-329">Name</span></span>|@Name|<span data-ttu-id="06a70-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="06a70-331">4</span><span class="sxs-lookup"><span data-stu-id="06a70-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="06a70-332">Ograniczenia schematu programu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="06a70-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="06a70-333">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcje schematów programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="06a70-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="06a70-334">Te ograniczenia są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="06a70-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="06a70-335">Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="06a70-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="06a70-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="06a70-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="06a70-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-337">Restriction Name</span></span>|<span data-ttu-id="06a70-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-338">Parameter Name</span></span>|<span data-ttu-id="06a70-339">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-339">Restriction Default</span></span>|<span data-ttu-id="06a70-340">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-341">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-341">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-342">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-343">1</span><span class="sxs-lookup"><span data-stu-id="06a70-343">1</span></span>|  
|<span data-ttu-id="06a70-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-344">Owner</span></span>|@Owner|<span data-ttu-id="06a70-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-346">2</span><span class="sxs-lookup"><span data-stu-id="06a70-346">2</span></span>|  
|<span data-ttu-id="06a70-347">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-347">Table</span></span>|@Table|<span data-ttu-id="06a70-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-348">TABLE_NAME</span></span>|<span data-ttu-id="06a70-349">3</span><span class="sxs-lookup"><span data-stu-id="06a70-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="06a70-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="06a70-350">AllColumns</span></span>  
  
|<span data-ttu-id="06a70-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="06a70-351">Restriction Name</span></span>|<span data-ttu-id="06a70-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="06a70-352">Parameter Name</span></span>|<span data-ttu-id="06a70-353">Ograniczenia domyślne</span><span class="sxs-lookup"><span data-stu-id="06a70-353">Restriction Default</span></span>|<span data-ttu-id="06a70-354">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="06a70-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="06a70-355">Wykaz</span><span class="sxs-lookup"><span data-stu-id="06a70-355">Catalog</span></span>|@Catalog|<span data-ttu-id="06a70-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="06a70-356">TABLE_CATALOG</span></span>|<span data-ttu-id="06a70-357">1</span><span class="sxs-lookup"><span data-stu-id="06a70-357">1</span></span>|  
|<span data-ttu-id="06a70-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="06a70-358">Owner</span></span>|@Owner|<span data-ttu-id="06a70-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="06a70-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="06a70-360">2</span><span class="sxs-lookup"><span data-stu-id="06a70-360">2</span></span>|  
|<span data-ttu-id="06a70-361">tabela</span><span class="sxs-lookup"><span data-stu-id="06a70-361">Table</span></span>|@Table|<span data-ttu-id="06a70-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-362">TABLE_NAME</span></span>|<span data-ttu-id="06a70-363">3</span><span class="sxs-lookup"><span data-stu-id="06a70-363">3</span></span>|  
|<span data-ttu-id="06a70-364">Kolumny</span><span class="sxs-lookup"><span data-stu-id="06a70-364">Column</span></span>|@Column|<span data-ttu-id="06a70-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="06a70-365">COLUMN_NAME</span></span>|<span data-ttu-id="06a70-366">4</span><span class="sxs-lookup"><span data-stu-id="06a70-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06a70-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06a70-367">See Also</span></span>  
 [<span data-ttu-id="06a70-368">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="06a70-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

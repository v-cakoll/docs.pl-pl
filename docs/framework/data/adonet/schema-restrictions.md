---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 17c42c5131252993d1f16e4a2f7a6450f0984d11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149014"
---
# <a name="schema-restrictions"></a><span data-ttu-id="07962-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="07962-102">Schema Restrictions</span></span>
<span data-ttu-id="07962-103">Drugi parametr opcjonalny **Metody GetSchema** jest ograniczenia, które są używane do ograniczenia ilości informacji o schemacie zwracane i jest przekazywana do **Metody GetSchema** jako tablicy ciągów.</span><span class="sxs-lookup"><span data-stu-id="07962-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="07962-104">Położenie w tablicy określa wartości, które można przekazać, a to jest równoważne z numerem ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="07962-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="07962-105">Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcję schematów "Tabele" przy użyciu dostawcy danych programu .NET Framework dla programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07962-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="07962-106">Dodatkowe ograniczenia dla kolekcji schematów programu SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="07962-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="07962-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-107">Restriction Name</span></span>|<span data-ttu-id="07962-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-108">Parameter Name</span></span>|<span data-ttu-id="07962-109">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-109">Restriction Default</span></span>|<span data-ttu-id="07962-110">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-111">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-111">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-112">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-113">1</span><span class="sxs-lookup"><span data-stu-id="07962-113">1</span></span>|  
|<span data-ttu-id="07962-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-114">Owner</span></span>|@Owner|<span data-ttu-id="07962-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-116">2</span><span class="sxs-lookup"><span data-stu-id="07962-116">2</span></span>|  
|<span data-ttu-id="07962-117">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-117">Table</span></span>|@Name|<span data-ttu-id="07962-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-118">TABLE_NAME</span></span>|<span data-ttu-id="07962-119">3</span><span class="sxs-lookup"><span data-stu-id="07962-119">3</span></span>|  
|<span data-ttu-id="07962-120">Typ tabeli</span><span class="sxs-lookup"><span data-stu-id="07962-120">TableType</span></span>|@TableType|<span data-ttu-id="07962-121">Table_type</span><span class="sxs-lookup"><span data-stu-id="07962-121">TABLE_TYPE</span></span>|<span data-ttu-id="07962-122">4</span><span class="sxs-lookup"><span data-stu-id="07962-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="07962-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="07962-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="07962-124">Aby użyć jednego z ograniczeń kolekcji schematu "Tabele", wystarczy utworzyć tablicę ciągów z czterema elementami, a następnie umieścić wartość w elemencie, który pasuje do numeru ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="07962-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="07962-125">Na przykład, aby ograniczyć tabele zwrócone przez **Metodę GetSchema** tylko do tych tabel w schemacie "Sprzedaż", należy ustawić drugi element tablicy na "Sprzedaż" przed przekazaniem go do **Metody GetSchema.**</span><span class="sxs-lookup"><span data-stu-id="07962-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07962-126">Kolekcje ograniczeń i `SqlClient` `OracleClient` mają dodatkową `ParameterName` kolumnę.</span><span class="sxs-lookup"><span data-stu-id="07962-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="07962-127">Domyślna kolumna ograniczenia jest nadal tam dla zgodności z powrotem, ale jest obecnie ignorowana.</span><span class="sxs-lookup"><span data-stu-id="07962-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="07962-128">Sparametryzowane kwerendy, a nie zastępowanie ciągów powinny być używane w celu zminimalizowania ryzyka ataku iniekcji SQL podczas określania wartości ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="07962-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07962-129">Liczba elementów w tablicy musi być mniejsza lub równa liczbie ograniczeń obsługiwanych dla <xref:System.ArgumentException> określonej kolekcji schematu inaczej zostanie rzucona.</span><span class="sxs-lookup"><span data-stu-id="07962-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="07962-130">Może być mniejsza niż maksymalna liczba ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="07962-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="07962-131">Zakłada się, że brakujące ograniczenia mają wartość null (bez ograniczeń).</span><span class="sxs-lookup"><span data-stu-id="07962-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="07962-132">Można zbadać .NET Framework zarządzanego dostawcy, aby określić listę obsługiwanych ograniczeń, wywołując **GetSchema** metody o nazwie kolekcji schematu ograniczeń, który jest "Ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="07962-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="07962-133">Spowoduje to <xref:System.Data.DataTable> zwrócenie a z listy nazw kolekcji, nazwy ograniczeń, domyślne wartości ograniczeń i numery ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="07962-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="07962-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="07962-134">Example</span></span>  
 <span data-ttu-id="07962-135">Poniższe przykłady pokazują, <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> jak używać metody dostawcy danych programu <xref:System.Data.SqlClient.SqlConnection> .NET Framework dla klasy PROGRAMU SQL Server do pobierania informacji o schemacie wszystkich tabel zawartych w przykładowej bazie danych **AdventureWorks** i ograniczania informacji zwracanych tylko do tych tabel w schemacie "Sprzedaż":</span><span class="sxs-lookup"><span data-stu-id="07962-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="07962-136">Ograniczenia schematu programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="07962-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="07962-137">W poniższych tabelach przedstawiono ograniczenia dotyczące kolekcji schematów programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07962-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="07962-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="07962-138">Users</span></span>  
  
|<span data-ttu-id="07962-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-139">Restriction Name</span></span>|<span data-ttu-id="07962-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-140">Parameter Name</span></span>|<span data-ttu-id="07962-141">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-141">Restriction Default</span></span>|<span data-ttu-id="07962-142">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-143">Nazwa_użytkownika</span><span class="sxs-lookup"><span data-stu-id="07962-143">User_Name</span></span>|@Name|<span data-ttu-id="07962-144">name</span><span class="sxs-lookup"><span data-stu-id="07962-144">name</span></span>|<span data-ttu-id="07962-145">1</span><span class="sxs-lookup"><span data-stu-id="07962-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="07962-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="07962-146">Databases</span></span>  
  
|<span data-ttu-id="07962-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-147">Restriction Name</span></span>|<span data-ttu-id="07962-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-148">Parameter Name</span></span>|<span data-ttu-id="07962-149">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-149">Restriction Default</span></span>|<span data-ttu-id="07962-150">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07962-151">Name</span></span>|@Name|<span data-ttu-id="07962-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07962-152">Name</span></span>|<span data-ttu-id="07962-153">1</span><span class="sxs-lookup"><span data-stu-id="07962-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="07962-154">Tabele</span><span class="sxs-lookup"><span data-stu-id="07962-154">Tables</span></span>  
  
|<span data-ttu-id="07962-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-155">Restriction Name</span></span>|<span data-ttu-id="07962-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-156">Parameter Name</span></span>|<span data-ttu-id="07962-157">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-157">Restriction Default</span></span>|<span data-ttu-id="07962-158">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-159">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-159">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-160">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-161">1</span><span class="sxs-lookup"><span data-stu-id="07962-161">1</span></span>|  
|<span data-ttu-id="07962-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-162">Owner</span></span>|@Owner|<span data-ttu-id="07962-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-164">2</span><span class="sxs-lookup"><span data-stu-id="07962-164">2</span></span>|  
|<span data-ttu-id="07962-165">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-165">Table</span></span>|@Name|<span data-ttu-id="07962-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-166">TABLE_NAME</span></span>|<span data-ttu-id="07962-167">3</span><span class="sxs-lookup"><span data-stu-id="07962-167">3</span></span>|  
|<span data-ttu-id="07962-168">Typ tabeli</span><span class="sxs-lookup"><span data-stu-id="07962-168">TableType</span></span>|@TableType|<span data-ttu-id="07962-169">Table_type</span><span class="sxs-lookup"><span data-stu-id="07962-169">TABLE_TYPE</span></span>|<span data-ttu-id="07962-170">4</span><span class="sxs-lookup"><span data-stu-id="07962-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="07962-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="07962-171">Columns</span></span>  
  
|<span data-ttu-id="07962-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-172">Restriction Name</span></span>|<span data-ttu-id="07962-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-173">Parameter Name</span></span>|<span data-ttu-id="07962-174">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-174">Restriction Default</span></span>|<span data-ttu-id="07962-175">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-176">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-176">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-177">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-178">1</span><span class="sxs-lookup"><span data-stu-id="07962-178">1</span></span>|  
|<span data-ttu-id="07962-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-179">Owner</span></span>|@Owner|<span data-ttu-id="07962-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-181">2</span><span class="sxs-lookup"><span data-stu-id="07962-181">2</span></span>|  
|<span data-ttu-id="07962-182">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-182">Table</span></span>|@Table|<span data-ttu-id="07962-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-183">TABLE_NAME</span></span>|<span data-ttu-id="07962-184">3</span><span class="sxs-lookup"><span data-stu-id="07962-184">3</span></span>|  
|<span data-ttu-id="07962-185">Kolumna</span><span class="sxs-lookup"><span data-stu-id="07962-185">Column</span></span>|@Column|<span data-ttu-id="07962-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-186">COLUMN_NAME</span></span>|<span data-ttu-id="07962-187">4</span><span class="sxs-lookup"><span data-stu-id="07962-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="07962-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="07962-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="07962-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-189">Restriction Name</span></span>|<span data-ttu-id="07962-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-190">Parameter Name</span></span>|<span data-ttu-id="07962-191">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-191">Restriction Default</span></span>|<span data-ttu-id="07962-192">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-193">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-193">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-194">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-195">1</span><span class="sxs-lookup"><span data-stu-id="07962-195">1</span></span>|  
|<span data-ttu-id="07962-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-196">Owner</span></span>|@Owner|<span data-ttu-id="07962-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-198">2</span><span class="sxs-lookup"><span data-stu-id="07962-198">2</span></span>|  
|<span data-ttu-id="07962-199">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-199">Table</span></span>|@Table|<span data-ttu-id="07962-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-200">TABLE_NAME</span></span>|<span data-ttu-id="07962-201">3</span><span class="sxs-lookup"><span data-stu-id="07962-201">3</span></span>|  
|<span data-ttu-id="07962-202">Kolumna</span><span class="sxs-lookup"><span data-stu-id="07962-202">Column</span></span>|@Column|<span data-ttu-id="07962-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-203">COLUMN_NAME</span></span>|<span data-ttu-id="07962-204">4</span><span class="sxs-lookup"><span data-stu-id="07962-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="07962-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="07962-205">Views</span></span>  
  
|<span data-ttu-id="07962-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-206">Restriction Name</span></span>|<span data-ttu-id="07962-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-207">Parameter Name</span></span>|<span data-ttu-id="07962-208">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-208">Restriction Default</span></span>|<span data-ttu-id="07962-209">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-210">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-210">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-211">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-212">1</span><span class="sxs-lookup"><span data-stu-id="07962-212">1</span></span>|  
|<span data-ttu-id="07962-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-213">Owner</span></span>|@Owner|<span data-ttu-id="07962-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-215">2</span><span class="sxs-lookup"><span data-stu-id="07962-215">2</span></span>|  
|<span data-ttu-id="07962-216">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-216">Table</span></span>|@Table|<span data-ttu-id="07962-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-217">TABLE_NAME</span></span>|<span data-ttu-id="07962-218">3</span><span class="sxs-lookup"><span data-stu-id="07962-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="07962-219">ViewColumns (Wychwki)</span><span class="sxs-lookup"><span data-stu-id="07962-219">ViewColumns</span></span>  
  
|<span data-ttu-id="07962-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-220">Restriction Name</span></span>|<span data-ttu-id="07962-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-221">Parameter Name</span></span>|<span data-ttu-id="07962-222">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-222">Restriction Default</span></span>|<span data-ttu-id="07962-223">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-224">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-224">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-225">VIEW_CATALOG</span></span>|<span data-ttu-id="07962-226">1</span><span class="sxs-lookup"><span data-stu-id="07962-226">1</span></span>|  
|<span data-ttu-id="07962-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-227">Owner</span></span>|@Owner|<span data-ttu-id="07962-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="07962-229">2</span><span class="sxs-lookup"><span data-stu-id="07962-229">2</span></span>|  
|<span data-ttu-id="07962-230">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-230">Table</span></span>|@Table|<span data-ttu-id="07962-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-231">VIEW_NAME</span></span>|<span data-ttu-id="07962-232">3</span><span class="sxs-lookup"><span data-stu-id="07962-232">3</span></span>|  
|<span data-ttu-id="07962-233">Kolumna</span><span class="sxs-lookup"><span data-stu-id="07962-233">Column</span></span>|@Column|<span data-ttu-id="07962-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-234">COLUMN_NAME</span></span>|<span data-ttu-id="07962-235">4</span><span class="sxs-lookup"><span data-stu-id="07962-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="07962-236">ProceduryParametry</span><span class="sxs-lookup"><span data-stu-id="07962-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="07962-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-237">Restriction Name</span></span>|<span data-ttu-id="07962-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-238">Parameter Name</span></span>|<span data-ttu-id="07962-239">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-239">Restriction Default</span></span>|<span data-ttu-id="07962-240">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-241">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-241">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="07962-243">1</span><span class="sxs-lookup"><span data-stu-id="07962-243">1</span></span>|  
|<span data-ttu-id="07962-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-244">Owner</span></span>|@Owner|<span data-ttu-id="07962-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="07962-246">2</span><span class="sxs-lookup"><span data-stu-id="07962-246">2</span></span>|  
|<span data-ttu-id="07962-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07962-247">Name</span></span>|@Name|<span data-ttu-id="07962-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="07962-249">3</span><span class="sxs-lookup"><span data-stu-id="07962-249">3</span></span>|  
|<span data-ttu-id="07962-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="07962-250">Parameter</span></span>|@Parameter|<span data-ttu-id="07962-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-251">PARAMETER_NAME</span></span>|<span data-ttu-id="07962-252">4</span><span class="sxs-lookup"><span data-stu-id="07962-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="07962-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="07962-253">Procedures</span></span>  
  
|<span data-ttu-id="07962-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-254">Restriction Name</span></span>|<span data-ttu-id="07962-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-255">Parameter Name</span></span>|<span data-ttu-id="07962-256">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-256">Restriction Default</span></span>|<span data-ttu-id="07962-257">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-258">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-258">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="07962-260">1</span><span class="sxs-lookup"><span data-stu-id="07962-260">1</span></span>|  
|<span data-ttu-id="07962-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-261">Owner</span></span>|@Owner|<span data-ttu-id="07962-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="07962-263">2</span><span class="sxs-lookup"><span data-stu-id="07962-263">2</span></span>|  
|<span data-ttu-id="07962-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07962-264">Name</span></span>|@Name|<span data-ttu-id="07962-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="07962-266">3</span><span class="sxs-lookup"><span data-stu-id="07962-266">3</span></span>|  
|<span data-ttu-id="07962-267">Typ</span><span class="sxs-lookup"><span data-stu-id="07962-267">Type</span></span>|@Type|<span data-ttu-id="07962-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="07962-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="07962-269">4</span><span class="sxs-lookup"><span data-stu-id="07962-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="07962-270">IndexColumns (Kody indeksu)</span><span class="sxs-lookup"><span data-stu-id="07962-270">IndexColumns</span></span>  
  
|<span data-ttu-id="07962-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-271">Restriction Name</span></span>|<span data-ttu-id="07962-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-272">Parameter Name</span></span>|<span data-ttu-id="07962-273">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-273">Restriction Default</span></span>|<span data-ttu-id="07962-274">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-275">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-275">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="07962-276">db_name()</span></span>|<span data-ttu-id="07962-277">1</span><span class="sxs-lookup"><span data-stu-id="07962-277">1</span></span>|  
|<span data-ttu-id="07962-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-278">Owner</span></span>|@Owner|<span data-ttu-id="07962-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="07962-279">user_name()</span></span>|<span data-ttu-id="07962-280">2</span><span class="sxs-lookup"><span data-stu-id="07962-280">2</span></span>|  
|<span data-ttu-id="07962-281">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-281">Table</span></span>|@Table|<span data-ttu-id="07962-282">o.name</span><span class="sxs-lookup"><span data-stu-id="07962-282">o.name</span></span>|<span data-ttu-id="07962-283">3</span><span class="sxs-lookup"><span data-stu-id="07962-283">3</span></span>|  
|<span data-ttu-id="07962-284">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="07962-285">x.name</span><span class="sxs-lookup"><span data-stu-id="07962-285">x.name</span></span>|<span data-ttu-id="07962-286">4</span><span class="sxs-lookup"><span data-stu-id="07962-286">4</span></span>|  
|<span data-ttu-id="07962-287">Kolumna</span><span class="sxs-lookup"><span data-stu-id="07962-287">Column</span></span>|@Column|<span data-ttu-id="07962-288">c.name</span><span class="sxs-lookup"><span data-stu-id="07962-288">c.name</span></span>|<span data-ttu-id="07962-289">5</span><span class="sxs-lookup"><span data-stu-id="07962-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="07962-290">Indeksy</span><span class="sxs-lookup"><span data-stu-id="07962-290">Indexes</span></span>  
  
|<span data-ttu-id="07962-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-291">Restriction Name</span></span>|<span data-ttu-id="07962-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-292">Parameter Name</span></span>|<span data-ttu-id="07962-293">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-293">Restriction Default</span></span>|<span data-ttu-id="07962-294">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-295">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-295">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="07962-296">db_name()</span></span>|<span data-ttu-id="07962-297">1</span><span class="sxs-lookup"><span data-stu-id="07962-297">1</span></span>|  
|<span data-ttu-id="07962-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-298">Owner</span></span>|@Owner|<span data-ttu-id="07962-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="07962-299">user_name()</span></span>|<span data-ttu-id="07962-300">2</span><span class="sxs-lookup"><span data-stu-id="07962-300">2</span></span>|  
|<span data-ttu-id="07962-301">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-301">Table</span></span>|@Table|<span data-ttu-id="07962-302">o.name</span><span class="sxs-lookup"><span data-stu-id="07962-302">o.name</span></span>|<span data-ttu-id="07962-303">3</span><span class="sxs-lookup"><span data-stu-id="07962-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="07962-304">Zdefiniowane typy użytkownika</span><span class="sxs-lookup"><span data-stu-id="07962-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="07962-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-305">Restriction Name</span></span>|<span data-ttu-id="07962-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-306">Parameter Name</span></span>|<span data-ttu-id="07962-307">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-307">Restriction Default</span></span>|<span data-ttu-id="07962-308">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="07962-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="07962-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="07962-310">assemblies.name</span></span>|<span data-ttu-id="07962-311">1</span><span class="sxs-lookup"><span data-stu-id="07962-311">1</span></span>|  
|<span data-ttu-id="07962-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="07962-312">udt_name</span></span>|@UDTName|<span data-ttu-id="07962-313">typy.assembly_class</span><span class="sxs-lookup"><span data-stu-id="07962-313">types.assembly_class</span></span>|<span data-ttu-id="07962-314">2</span><span class="sxs-lookup"><span data-stu-id="07962-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="07962-315">Klawisze obce</span><span class="sxs-lookup"><span data-stu-id="07962-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="07962-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-316">Restriction Name</span></span>|<span data-ttu-id="07962-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-317">Parameter Name</span></span>|<span data-ttu-id="07962-318">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-318">Restriction Default</span></span>|<span data-ttu-id="07962-319">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-320">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-320">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="07962-322">1</span><span class="sxs-lookup"><span data-stu-id="07962-322">1</span></span>|  
|<span data-ttu-id="07962-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-323">Owner</span></span>|@Owner|<span data-ttu-id="07962-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="07962-325">2</span><span class="sxs-lookup"><span data-stu-id="07962-325">2</span></span>|  
|<span data-ttu-id="07962-326">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-326">Table</span></span>|@Table|<span data-ttu-id="07962-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-327">TABLE_NAME</span></span>|<span data-ttu-id="07962-328">3</span><span class="sxs-lookup"><span data-stu-id="07962-328">3</span></span>|  
|<span data-ttu-id="07962-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="07962-329">Name</span></span>|@Name|<span data-ttu-id="07962-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="07962-331">4</span><span class="sxs-lookup"><span data-stu-id="07962-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="07962-332">Ograniczenia schematu programu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="07962-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="07962-333">W poniższych tabelach przedstawiono ograniczenia dotyczące kolekcji schematów programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="07962-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="07962-334">Te ograniczenia są prawidłowe począwszy od wersji 3.5 SP1 programu .NET Framework i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="07962-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="07962-335">Nie są one obsługiwane we wcześniejszych wersjach programu .NET Framework i SQL Server.</span><span class="sxs-lookup"><span data-stu-id="07962-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="07962-336">ColumnSetColumns (Typy kolumn)</span><span class="sxs-lookup"><span data-stu-id="07962-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="07962-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-337">Restriction Name</span></span>|<span data-ttu-id="07962-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-338">Parameter Name</span></span>|<span data-ttu-id="07962-339">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-339">Restriction Default</span></span>|<span data-ttu-id="07962-340">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-341">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-341">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-342">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-343">1</span><span class="sxs-lookup"><span data-stu-id="07962-343">1</span></span>|  
|<span data-ttu-id="07962-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-344">Owner</span></span>|@Owner|<span data-ttu-id="07962-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-346">2</span><span class="sxs-lookup"><span data-stu-id="07962-346">2</span></span>|  
|<span data-ttu-id="07962-347">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-347">Table</span></span>|@Table|<span data-ttu-id="07962-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-348">TABLE_NAME</span></span>|<span data-ttu-id="07962-349">3</span><span class="sxs-lookup"><span data-stu-id="07962-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="07962-350">AllKolumny</span><span class="sxs-lookup"><span data-stu-id="07962-350">AllColumns</span></span>  
  
|<span data-ttu-id="07962-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-351">Restriction Name</span></span>|<span data-ttu-id="07962-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="07962-352">Parameter Name</span></span>|<span data-ttu-id="07962-353">Domyślne ograniczenie</span><span class="sxs-lookup"><span data-stu-id="07962-353">Restriction Default</span></span>|<span data-ttu-id="07962-354">Numer ograniczenia</span><span class="sxs-lookup"><span data-stu-id="07962-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="07962-355">Wykaz</span><span class="sxs-lookup"><span data-stu-id="07962-355">Catalog</span></span>|@Catalog|<span data-ttu-id="07962-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="07962-356">TABLE_CATALOG</span></span>|<span data-ttu-id="07962-357">1</span><span class="sxs-lookup"><span data-stu-id="07962-357">1</span></span>|  
|<span data-ttu-id="07962-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="07962-358">Owner</span></span>|@Owner|<span data-ttu-id="07962-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="07962-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="07962-360">2</span><span class="sxs-lookup"><span data-stu-id="07962-360">2</span></span>|  
|<span data-ttu-id="07962-361">Tabela</span><span class="sxs-lookup"><span data-stu-id="07962-361">Table</span></span>|@Table|<span data-ttu-id="07962-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-362">TABLE_NAME</span></span>|<span data-ttu-id="07962-363">3</span><span class="sxs-lookup"><span data-stu-id="07962-363">3</span></span>|  
|<span data-ttu-id="07962-364">Kolumna</span><span class="sxs-lookup"><span data-stu-id="07962-364">Column</span></span>|@Column|<span data-ttu-id="07962-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="07962-365">COLUMN_NAME</span></span>|<span data-ttu-id="07962-366">4</span><span class="sxs-lookup"><span data-stu-id="07962-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07962-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07962-367">See also</span></span>

- [<span data-ttu-id="07962-368">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="07962-368">ADO.NET Overview</span></span>](ado-net-overview.md)

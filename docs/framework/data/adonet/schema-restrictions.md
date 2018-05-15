---
title: Ograniczenia schematu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: c62f934561fa4a6c352ff84b8c1201461c42de39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="9ca10-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="9ca10-102">Schema Restrictions</span></span>
<span data-ttu-id="9ca10-103">Drugi parametr opcjonalny **GetSchema** metoda jest zwracane ograniczenia, które są używane w celu ograniczenia ilości informacji o schemacie, a jest przekazywana do **GetSchema** metodę jako tablica ciągów .</span><span class="sxs-lookup"><span data-stu-id="9ca10-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="9ca10-104">Pozycja w tablicy określa wartości, które mogą upłynąć, a jest to równoważne numer ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="9ca10-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="9ca10-105">Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcji schematów "Tabele" za pomocą dostawcy .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ca10-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="9ca10-106">Dodatkowe ograniczenia dotyczące kolekcji schematu programu SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9ca10-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="9ca10-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-107">Restriction Name</span></span>|<span data-ttu-id="9ca10-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-108">Parameter Name</span></span>|<span data-ttu-id="9ca10-109">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-109">Restriction Default</span></span>|<span data-ttu-id="9ca10-110">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-111">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-111">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-112">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-113">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-113">1</span></span>|  
|<span data-ttu-id="9ca10-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-114">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-116">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-116">2</span></span>|  
|<span data-ttu-id="9ca10-117">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-117">Table</span></span>|@Name|<span data-ttu-id="9ca10-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-118">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-119">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-119">3</span></span>|  
|<span data-ttu-id="9ca10-120">Typem</span><span class="sxs-lookup"><span data-stu-id="9ca10-120">TableType</span></span>|@TableType|<span data-ttu-id="9ca10-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ca10-121">TABLE_TYPE</span></span>|<span data-ttu-id="9ca10-122">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="9ca10-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="9ca10-124">Do korzystania z jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicy ciągów z czterech elementów, a następnie umieść wartość w elemencie, który jest zgodna z liczbą ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="9ca10-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="9ca10-125">Na przykład, aby ograniczyć tabele zwrócony przez **GetSchema** metody tylko tych tabel w schemacie "Sprzedaż" ustawienie drugiego elementu tablicy, tak aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="9ca10-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ca10-126">Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkowych `ParameterName` kolumny.</span><span class="sxs-lookup"><span data-stu-id="9ca10-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="9ca10-127">Ograniczenie domyślna kolumna jest nadal istnieje dla zapewnienia zgodności, ale obecnie jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="9ca10-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="9ca10-128">Zapytania sparametryzowane zamiast zastępowania ciągów należy ograniczyć ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="9ca10-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ca10-129">Liczba elementów w tablicy musi być mniejsza niż liczba obsługiwana w przypadku kolekcji określony schemat else ograniczeń <xref:System.ArgumentException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="9ca10-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="9ca10-130">Może być krótsza niż maksymalna liczba ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="9ca10-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="9ca10-131">Brak ograniczeń są rozpatrywane null (bez ograniczeń).</span><span class="sxs-lookup"><span data-stu-id="9ca10-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="9ca10-132">Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji ograniczeń schematu, czyli "Ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="9ca10-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="9ca10-133">Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazwy kolekcji, nazwy ograniczenia wartości domyślne ograniczenia i ograniczenie liczby.</span><span class="sxs-lookup"><span data-stu-id="9ca10-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ca10-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ca10-134">Example</span></span>  
 <span data-ttu-id="9ca10-135">W poniższych przykładach pokazano, jak używać <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody dostawcy danych programu .NET Framework dla programu SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy można pobrać informacji schematu o wszystkie tabele zawarte w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwracane tylko tych tabel w schemacie "Sprzedaż":</span><span class="sxs-lookup"><span data-stu-id="9ca10-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="9ca10-136">Ograniczenia schematu serwera SQL</span><span class="sxs-lookup"><span data-stu-id="9ca10-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="9ca10-137">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ca10-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="9ca10-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="9ca10-138">Users</span></span>  
  
|<span data-ttu-id="9ca10-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-139">Restriction Name</span></span>|<span data-ttu-id="9ca10-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-140">Parameter Name</span></span>|<span data-ttu-id="9ca10-141">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-141">Restriction Default</span></span>|<span data-ttu-id="9ca10-142">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-143">Nazwa_użytkownika</span><span class="sxs-lookup"><span data-stu-id="9ca10-143">User_Name</span></span>|@Name|<span data-ttu-id="9ca10-144">nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-144">name</span></span>|<span data-ttu-id="9ca10-145">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="9ca10-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="9ca10-146">Databases</span></span>  
  
|<span data-ttu-id="9ca10-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-147">Restriction Name</span></span>|<span data-ttu-id="9ca10-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-148">Parameter Name</span></span>|<span data-ttu-id="9ca10-149">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-149">Restriction Default</span></span>|<span data-ttu-id="9ca10-150">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-151">Name</span></span>|@Name|<span data-ttu-id="9ca10-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-152">Name</span></span>|<span data-ttu-id="9ca10-153">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="9ca10-154">Tabele</span><span class="sxs-lookup"><span data-stu-id="9ca10-154">Tables</span></span>  
  
|<span data-ttu-id="9ca10-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-155">Restriction Name</span></span>|<span data-ttu-id="9ca10-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-156">Parameter Name</span></span>|<span data-ttu-id="9ca10-157">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-157">Restriction Default</span></span>|<span data-ttu-id="9ca10-158">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-159">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-159">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-160">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-161">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-161">1</span></span>|  
|<span data-ttu-id="9ca10-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-162">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-164">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-164">2</span></span>|  
|<span data-ttu-id="9ca10-165">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-165">Table</span></span>|@Name|<span data-ttu-id="9ca10-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-166">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-167">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-167">3</span></span>|  
|<span data-ttu-id="9ca10-168">Typem</span><span class="sxs-lookup"><span data-stu-id="9ca10-168">TableType</span></span>|@TableType|<span data-ttu-id="9ca10-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ca10-169">TABLE_TYPE</span></span>|<span data-ttu-id="9ca10-170">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="9ca10-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-171">Columns</span></span>  
  
|<span data-ttu-id="9ca10-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-172">Restriction Name</span></span>|<span data-ttu-id="9ca10-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-173">Parameter Name</span></span>|<span data-ttu-id="9ca10-174">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-174">Restriction Default</span></span>|<span data-ttu-id="9ca10-175">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-176">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-176">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-177">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-178">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-178">1</span></span>|  
|<span data-ttu-id="9ca10-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-179">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-181">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-181">2</span></span>|  
|<span data-ttu-id="9ca10-182">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-182">Table</span></span>|@Table|<span data-ttu-id="9ca10-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-183">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-184">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-184">3</span></span>|  
|<span data-ttu-id="9ca10-185">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-185">Column</span></span>|@Column|<span data-ttu-id="9ca10-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-186">COLUMN_NAME</span></span>|<span data-ttu-id="9ca10-187">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="9ca10-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="9ca10-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="9ca10-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-189">Restriction Name</span></span>|<span data-ttu-id="9ca10-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-190">Parameter Name</span></span>|<span data-ttu-id="9ca10-191">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-191">Restriction Default</span></span>|<span data-ttu-id="9ca10-192">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-193">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-193">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-194">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-195">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-195">1</span></span>|  
|<span data-ttu-id="9ca10-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-196">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-198">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-198">2</span></span>|  
|<span data-ttu-id="9ca10-199">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-199">Table</span></span>|@Table|<span data-ttu-id="9ca10-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-200">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-201">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-201">3</span></span>|  
|<span data-ttu-id="9ca10-202">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-202">Column</span></span>|@Column|<span data-ttu-id="9ca10-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-203">COLUMN_NAME</span></span>|<span data-ttu-id="9ca10-204">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="9ca10-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="9ca10-205">Views</span></span>  
  
|<span data-ttu-id="9ca10-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-206">Restriction Name</span></span>|<span data-ttu-id="9ca10-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-207">Parameter Name</span></span>|<span data-ttu-id="9ca10-208">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-208">Restriction Default</span></span>|<span data-ttu-id="9ca10-209">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-210">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-210">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-211">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-212">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-212">1</span></span>|  
|<span data-ttu-id="9ca10-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-213">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-215">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-215">2</span></span>|  
|<span data-ttu-id="9ca10-216">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-216">Table</span></span>|@Table|<span data-ttu-id="9ca10-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-217">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-218">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="9ca10-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="9ca10-219">ViewColumns</span></span>  
  
|<span data-ttu-id="9ca10-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-220">Restriction Name</span></span>|<span data-ttu-id="9ca10-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-221">Parameter Name</span></span>|<span data-ttu-id="9ca10-222">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-222">Restriction Default</span></span>|<span data-ttu-id="9ca10-223">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-224">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-224">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-225">VIEW_CATALOG</span></span>|<span data-ttu-id="9ca10-226">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-226">1</span></span>|  
|<span data-ttu-id="9ca10-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-227">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="9ca10-229">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-229">2</span></span>|  
|<span data-ttu-id="9ca10-230">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-230">Table</span></span>|@Table|<span data-ttu-id="9ca10-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-231">VIEW_NAME</span></span>|<span data-ttu-id="9ca10-232">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-232">3</span></span>|  
|<span data-ttu-id="9ca10-233">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-233">Column</span></span>|@Column|<span data-ttu-id="9ca10-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-234">COLUMN_NAME</span></span>|<span data-ttu-id="9ca10-235">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="9ca10-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="9ca10-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="9ca10-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-237">Restriction Name</span></span>|<span data-ttu-id="9ca10-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-238">Parameter Name</span></span>|<span data-ttu-id="9ca10-239">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-239">Restriction Default</span></span>|<span data-ttu-id="9ca10-240">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-241">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-241">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="9ca10-243">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-243">1</span></span>|  
|<span data-ttu-id="9ca10-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-244">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="9ca10-246">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-246">2</span></span>|  
|<span data-ttu-id="9ca10-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-247">Name</span></span>|@Name|<span data-ttu-id="9ca10-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="9ca10-249">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-249">3</span></span>|  
|<span data-ttu-id="9ca10-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="9ca10-250">Parameter</span></span>|@Parameter|<span data-ttu-id="9ca10-251">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="9ca10-251">PARAMETER_NAME</span></span>|<span data-ttu-id="9ca10-252">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="9ca10-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="9ca10-253">Procedures</span></span>  
  
|<span data-ttu-id="9ca10-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-254">Restriction Name</span></span>|<span data-ttu-id="9ca10-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-255">Parameter Name</span></span>|<span data-ttu-id="9ca10-256">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-256">Restriction Default</span></span>|<span data-ttu-id="9ca10-257">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-258">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="9ca10-260">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-260">1</span></span>|  
|<span data-ttu-id="9ca10-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-261">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="9ca10-263">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-263">2</span></span>|  
|<span data-ttu-id="9ca10-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-264">Name</span></span>|@Name|<span data-ttu-id="9ca10-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="9ca10-266">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-266">3</span></span>|  
|<span data-ttu-id="9ca10-267">Typ</span><span class="sxs-lookup"><span data-stu-id="9ca10-267">Type</span></span>|@Type|<span data-ttu-id="9ca10-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="9ca10-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="9ca10-269">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="9ca10-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="9ca10-270">IndexColumns</span></span>  
  
|<span data-ttu-id="9ca10-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-271">Restriction Name</span></span>|<span data-ttu-id="9ca10-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-272">Parameter Name</span></span>|<span data-ttu-id="9ca10-273">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-273">Restriction Default</span></span>|<span data-ttu-id="9ca10-274">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-275">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-275">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="9ca10-276">db_name()</span></span>|<span data-ttu-id="9ca10-277">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-277">1</span></span>|  
|<span data-ttu-id="9ca10-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-278">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="9ca10-279">user_name()</span></span>|<span data-ttu-id="9ca10-280">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-280">2</span></span>|  
|<span data-ttu-id="9ca10-281">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-281">Table</span></span>|@Table|<span data-ttu-id="9ca10-282">o.name</span><span class="sxs-lookup"><span data-stu-id="9ca10-282">o.name</span></span>|<span data-ttu-id="9ca10-283">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-283">3</span></span>|  
|<span data-ttu-id="9ca10-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="9ca10-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="9ca10-285">x.name</span><span class="sxs-lookup"><span data-stu-id="9ca10-285">x.name</span></span>|<span data-ttu-id="9ca10-286">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-286">4</span></span>|  
|<span data-ttu-id="9ca10-287">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-287">Column</span></span>|@Column|<span data-ttu-id="9ca10-288">c.name</span><span class="sxs-lookup"><span data-stu-id="9ca10-288">c.name</span></span>|<span data-ttu-id="9ca10-289">5</span><span class="sxs-lookup"><span data-stu-id="9ca10-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="9ca10-290">Indeksy</span><span class="sxs-lookup"><span data-stu-id="9ca10-290">Indexes</span></span>  
  
|<span data-ttu-id="9ca10-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-291">Restriction Name</span></span>|<span data-ttu-id="9ca10-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-292">Parameter Name</span></span>|<span data-ttu-id="9ca10-293">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-293">Restriction Default</span></span>|<span data-ttu-id="9ca10-294">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-295">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-295">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="9ca10-296">db_name()</span></span>|<span data-ttu-id="9ca10-297">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-297">1</span></span>|  
|<span data-ttu-id="9ca10-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-298">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="9ca10-299">user_name()</span></span>|<span data-ttu-id="9ca10-300">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-300">2</span></span>|  
|<span data-ttu-id="9ca10-301">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-301">Table</span></span>|@Table|<span data-ttu-id="9ca10-302">o.name</span><span class="sxs-lookup"><span data-stu-id="9ca10-302">o.name</span></span>|<span data-ttu-id="9ca10-303">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="9ca10-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="9ca10-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="9ca10-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-305">Restriction Name</span></span>|<span data-ttu-id="9ca10-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-306">Parameter Name</span></span>|<span data-ttu-id="9ca10-307">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-307">Restriction Default</span></span>|<span data-ttu-id="9ca10-308">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-309">nazwa_zestawu</span><span class="sxs-lookup"><span data-stu-id="9ca10-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="9ca10-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="9ca10-310">assemblies.name</span></span>|<span data-ttu-id="9ca10-311">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-311">1</span></span>|  
|<span data-ttu-id="9ca10-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="9ca10-312">udt_name</span></span>|@UDTName|<span data-ttu-id="9ca10-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="9ca10-313">types.assembly_class</span></span>|<span data-ttu-id="9ca10-314">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="9ca10-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="9ca10-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="9ca10-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-316">Restriction Name</span></span>|<span data-ttu-id="9ca10-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-317">Parameter Name</span></span>|<span data-ttu-id="9ca10-318">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-318">Restriction Default</span></span>|<span data-ttu-id="9ca10-319">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-320">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-320">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="9ca10-322">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-322">1</span></span>|  
|<span data-ttu-id="9ca10-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-323">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="9ca10-325">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-325">2</span></span>|  
|<span data-ttu-id="9ca10-326">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-326">Table</span></span>|@Table|<span data-ttu-id="9ca10-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-327">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-328">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-328">3</span></span>|  
|<span data-ttu-id="9ca10-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9ca10-329">Name</span></span>|@Name|<span data-ttu-id="9ca10-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="9ca10-331">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="9ca10-332">Ograniczenia schematu programu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="9ca10-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="9ca10-333">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9ca10-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="9ca10-334">Ograniczenia te są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="9ca10-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="9ca10-335">Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9ca10-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="9ca10-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="9ca10-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="9ca10-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-337">Restriction Name</span></span>|<span data-ttu-id="9ca10-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-338">Parameter Name</span></span>|<span data-ttu-id="9ca10-339">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-339">Restriction Default</span></span>|<span data-ttu-id="9ca10-340">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-341">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-341">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-342">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-343">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-343">1</span></span>|  
|<span data-ttu-id="9ca10-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-344">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-346">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-346">2</span></span>|  
|<span data-ttu-id="9ca10-347">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-347">Table</span></span>|@Table|<span data-ttu-id="9ca10-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-348">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-349">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="9ca10-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="9ca10-350">AllColumns</span></span>  
  
|<span data-ttu-id="9ca10-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="9ca10-351">Restriction Name</span></span>|<span data-ttu-id="9ca10-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="9ca10-352">Parameter Name</span></span>|<span data-ttu-id="9ca10-353">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="9ca10-353">Restriction Default</span></span>|<span data-ttu-id="9ca10-354">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="9ca10-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="9ca10-355">Katalogu</span><span class="sxs-lookup"><span data-stu-id="9ca10-355">Catalog</span></span>|@Catalog|<span data-ttu-id="9ca10-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="9ca10-356">TABLE_CATALOG</span></span>|<span data-ttu-id="9ca10-357">1</span><span class="sxs-lookup"><span data-stu-id="9ca10-357">1</span></span>|  
|<span data-ttu-id="9ca10-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="9ca10-358">Owner</span></span>|@Owner|<span data-ttu-id="9ca10-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="9ca10-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="9ca10-360">2</span><span class="sxs-lookup"><span data-stu-id="9ca10-360">2</span></span>|  
|<span data-ttu-id="9ca10-361">tabela</span><span class="sxs-lookup"><span data-stu-id="9ca10-361">Table</span></span>|@Table|<span data-ttu-id="9ca10-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-362">TABLE_NAME</span></span>|<span data-ttu-id="9ca10-363">3</span><span class="sxs-lookup"><span data-stu-id="9ca10-363">3</span></span>|  
|<span data-ttu-id="9ca10-364">Kolumny</span><span class="sxs-lookup"><span data-stu-id="9ca10-364">Column</span></span>|@Column|<span data-ttu-id="9ca10-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="9ca10-365">COLUMN_NAME</span></span>|<span data-ttu-id="9ca10-366">4</span><span class="sxs-lookup"><span data-stu-id="9ca10-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ca10-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ca10-367">See Also</span></span>  
 [<span data-ttu-id="9ca10-368">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="9ca10-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

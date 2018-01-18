---
title: Ograniczenia schematu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f5b004b70716c61af8ac37fef76f660c488e5a74
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="schema-restrictions"></a><span data-ttu-id="471b5-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="471b5-102">Schema Restrictions</span></span>
<span data-ttu-id="471b5-103">Drugi parametr opcjonalny **GetSchema** metoda jest zwracane ograniczenia, które są używane w celu ograniczenia ilości informacji o schemacie, a jest przekazywana do **GetSchema** metodę jako tablica ciągów .</span><span class="sxs-lookup"><span data-stu-id="471b5-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="471b5-104">Pozycja w tablicy określa wartości, które mogą upłynąć, a jest to równoważne numer ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="471b5-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="471b5-105">Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcji schematów "Tabele" za pomocą dostawcy .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="471b5-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="471b5-106">Dodatkowe ograniczenia dotyczące kolekcji schematu programu SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="471b5-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="471b5-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-107">Restriction Name</span></span>|<span data-ttu-id="471b5-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-108">Parameter Name</span></span>|<span data-ttu-id="471b5-109">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-109">Restriction Default</span></span>|<span data-ttu-id="471b5-110">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-111">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-111">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-112">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-113">1</span><span class="sxs-lookup"><span data-stu-id="471b5-113">1</span></span>|  
|<span data-ttu-id="471b5-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-114">Owner</span></span>|@Owner|<span data-ttu-id="471b5-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-116">2</span><span class="sxs-lookup"><span data-stu-id="471b5-116">2</span></span>|  
|<span data-ttu-id="471b5-117">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-117">Table</span></span>|@Name|<span data-ttu-id="471b5-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-118">TABLE_NAME</span></span>|<span data-ttu-id="471b5-119">3</span><span class="sxs-lookup"><span data-stu-id="471b5-119">3</span></span>|  
|<span data-ttu-id="471b5-120">Typem</span><span class="sxs-lookup"><span data-stu-id="471b5-120">TableType</span></span>|@TableType|<span data-ttu-id="471b5-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="471b5-121">TABLE_TYPE</span></span>|<span data-ttu-id="471b5-122">4</span><span class="sxs-lookup"><span data-stu-id="471b5-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="471b5-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="471b5-124">Do korzystania z jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicy ciągów z czterech elementów, a następnie umieść wartość w elemencie, który jest zgodna z liczbą ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="471b5-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="471b5-125">Na przykład, aby ograniczyć tabele zwrócony przez **GetSchema** metody tylko tych tabel w schemacie "Sprzedaż" ustawienie drugiego elementu tablicy, tak aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="471b5-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="471b5-126">Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkowych `ParameterName` kolumny.</span><span class="sxs-lookup"><span data-stu-id="471b5-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="471b5-127">Ograniczenie domyślna kolumna jest nadal istnieje dla zapewnienia zgodności, ale obecnie jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="471b5-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="471b5-128">Zapytania sparametryzowane zamiast zastępowania ciągów należy ograniczyć ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="471b5-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="471b5-129">Liczba elementów w tablicy musi być mniejsza niż liczba obsługiwana w przypadku kolekcji określony schemat else ograniczeń <xref:System.ArgumentException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="471b5-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="471b5-130">Może być krótsza niż maksymalna liczba ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="471b5-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="471b5-131">Brak ograniczeń są rozpatrywane null (bez ograniczeń).</span><span class="sxs-lookup"><span data-stu-id="471b5-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="471b5-132">Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji ograniczeń schematu, czyli "Ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="471b5-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="471b5-133">Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazwy kolekcji, nazwy ograniczenia wartości domyślne ograniczenia i ograniczenie liczby.</span><span class="sxs-lookup"><span data-stu-id="471b5-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="471b5-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="471b5-134">Example</span></span>  
 <span data-ttu-id="471b5-135">W poniższych przykładach pokazano, jak używać <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody dostawcy danych programu .NET Framework dla programu SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy można pobrać informacji schematu o wszystkie tabele zawarte w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwracane tylko tych tabel w schemacie "Sprzedaż":</span><span class="sxs-lookup"><span data-stu-id="471b5-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="471b5-136">Ograniczenia schematu serwera SQL</span><span class="sxs-lookup"><span data-stu-id="471b5-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="471b5-137">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="471b5-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="471b5-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="471b5-138">Users</span></span>  
  
|<span data-ttu-id="471b5-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-139">Restriction Name</span></span>|<span data-ttu-id="471b5-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-140">Parameter Name</span></span>|<span data-ttu-id="471b5-141">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-141">Restriction Default</span></span>|<span data-ttu-id="471b5-142">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="471b5-143">User_Name</span></span>|@Name|<span data-ttu-id="471b5-144">nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-144">name</span></span>|<span data-ttu-id="471b5-145">1</span><span class="sxs-lookup"><span data-stu-id="471b5-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="471b5-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="471b5-146">Databases</span></span>  
  
|<span data-ttu-id="471b5-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-147">Restriction Name</span></span>|<span data-ttu-id="471b5-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-148">Parameter Name</span></span>|<span data-ttu-id="471b5-149">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-149">Restriction Default</span></span>|<span data-ttu-id="471b5-150">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-151">Name</span></span>|@Name|<span data-ttu-id="471b5-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-152">Name</span></span>|<span data-ttu-id="471b5-153">1</span><span class="sxs-lookup"><span data-stu-id="471b5-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="471b5-154">Tabele</span><span class="sxs-lookup"><span data-stu-id="471b5-154">Tables</span></span>  
  
|<span data-ttu-id="471b5-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-155">Restriction Name</span></span>|<span data-ttu-id="471b5-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-156">Parameter Name</span></span>|<span data-ttu-id="471b5-157">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-157">Restriction Default</span></span>|<span data-ttu-id="471b5-158">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-159">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-159">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-160">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-161">1</span><span class="sxs-lookup"><span data-stu-id="471b5-161">1</span></span>|  
|<span data-ttu-id="471b5-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-162">Owner</span></span>|@Owner|<span data-ttu-id="471b5-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-164">2</span><span class="sxs-lookup"><span data-stu-id="471b5-164">2</span></span>|  
|<span data-ttu-id="471b5-165">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-165">Table</span></span>|@Name|<span data-ttu-id="471b5-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-166">TABLE_NAME</span></span>|<span data-ttu-id="471b5-167">3</span><span class="sxs-lookup"><span data-stu-id="471b5-167">3</span></span>|  
|<span data-ttu-id="471b5-168">Typem</span><span class="sxs-lookup"><span data-stu-id="471b5-168">TableType</span></span>|@TableType|<span data-ttu-id="471b5-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="471b5-169">TABLE_TYPE</span></span>|<span data-ttu-id="471b5-170">4</span><span class="sxs-lookup"><span data-stu-id="471b5-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="471b5-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-171">Columns</span></span>  
  
|<span data-ttu-id="471b5-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-172">Restriction Name</span></span>|<span data-ttu-id="471b5-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-173">Parameter Name</span></span>|<span data-ttu-id="471b5-174">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-174">Restriction Default</span></span>|<span data-ttu-id="471b5-175">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-176">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-176">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-177">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-178">1</span><span class="sxs-lookup"><span data-stu-id="471b5-178">1</span></span>|  
|<span data-ttu-id="471b5-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-179">Owner</span></span>|@Owner|<span data-ttu-id="471b5-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-181">2</span><span class="sxs-lookup"><span data-stu-id="471b5-181">2</span></span>|  
|<span data-ttu-id="471b5-182">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-182">Table</span></span>|@Table|<span data-ttu-id="471b5-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-183">TABLE_NAME</span></span>|<span data-ttu-id="471b5-184">3</span><span class="sxs-lookup"><span data-stu-id="471b5-184">3</span></span>|  
|<span data-ttu-id="471b5-185">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-185">Column</span></span>|@Column|<span data-ttu-id="471b5-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-186">COLUMN_NAME</span></span>|<span data-ttu-id="471b5-187">4</span><span class="sxs-lookup"><span data-stu-id="471b5-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="471b5-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="471b5-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="471b5-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-189">Restriction Name</span></span>|<span data-ttu-id="471b5-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-190">Parameter Name</span></span>|<span data-ttu-id="471b5-191">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-191">Restriction Default</span></span>|<span data-ttu-id="471b5-192">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-193">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-193">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-194">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-195">1</span><span class="sxs-lookup"><span data-stu-id="471b5-195">1</span></span>|  
|<span data-ttu-id="471b5-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-196">Owner</span></span>|@Owner|<span data-ttu-id="471b5-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-198">2</span><span class="sxs-lookup"><span data-stu-id="471b5-198">2</span></span>|  
|<span data-ttu-id="471b5-199">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-199">Table</span></span>|@Table|<span data-ttu-id="471b5-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-200">TABLE_NAME</span></span>|<span data-ttu-id="471b5-201">3</span><span class="sxs-lookup"><span data-stu-id="471b5-201">3</span></span>|  
|<span data-ttu-id="471b5-202">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-202">Column</span></span>|@Column|<span data-ttu-id="471b5-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-203">COLUMN_NAME</span></span>|<span data-ttu-id="471b5-204">4</span><span class="sxs-lookup"><span data-stu-id="471b5-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="471b5-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="471b5-205">Views</span></span>  
  
|<span data-ttu-id="471b5-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-206">Restriction Name</span></span>|<span data-ttu-id="471b5-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-207">Parameter Name</span></span>|<span data-ttu-id="471b5-208">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-208">Restriction Default</span></span>|<span data-ttu-id="471b5-209">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-210">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-210">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-211">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-212">1</span><span class="sxs-lookup"><span data-stu-id="471b5-212">1</span></span>|  
|<span data-ttu-id="471b5-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-213">Owner</span></span>|@Owner|<span data-ttu-id="471b5-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-215">2</span><span class="sxs-lookup"><span data-stu-id="471b5-215">2</span></span>|  
|<span data-ttu-id="471b5-216">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-216">Table</span></span>|@Table|<span data-ttu-id="471b5-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-217">TABLE_NAME</span></span>|<span data-ttu-id="471b5-218">3</span><span class="sxs-lookup"><span data-stu-id="471b5-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="471b5-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="471b5-219">ViewColumns</span></span>  
  
|<span data-ttu-id="471b5-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-220">Restriction Name</span></span>|<span data-ttu-id="471b5-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-221">Parameter Name</span></span>|<span data-ttu-id="471b5-222">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-222">Restriction Default</span></span>|<span data-ttu-id="471b5-223">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-224">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-224">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-225">VIEW_CATALOG</span></span>|<span data-ttu-id="471b5-226">1</span><span class="sxs-lookup"><span data-stu-id="471b5-226">1</span></span>|  
|<span data-ttu-id="471b5-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-227">Owner</span></span>|@Owner|<span data-ttu-id="471b5-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="471b5-229">2</span><span class="sxs-lookup"><span data-stu-id="471b5-229">2</span></span>|  
|<span data-ttu-id="471b5-230">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-230">Table</span></span>|@Table|<span data-ttu-id="471b5-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-231">VIEW_NAME</span></span>|<span data-ttu-id="471b5-232">3</span><span class="sxs-lookup"><span data-stu-id="471b5-232">3</span></span>|  
|<span data-ttu-id="471b5-233">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-233">Column</span></span>|@Column|<span data-ttu-id="471b5-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-234">COLUMN_NAME</span></span>|<span data-ttu-id="471b5-235">4</span><span class="sxs-lookup"><span data-stu-id="471b5-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="471b5-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="471b5-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="471b5-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-237">Restriction Name</span></span>|<span data-ttu-id="471b5-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-238">Parameter Name</span></span>|<span data-ttu-id="471b5-239">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-239">Restriction Default</span></span>|<span data-ttu-id="471b5-240">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-241">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-241">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="471b5-243">1</span><span class="sxs-lookup"><span data-stu-id="471b5-243">1</span></span>|  
|<span data-ttu-id="471b5-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-244">Owner</span></span>|@Owner|<span data-ttu-id="471b5-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="471b5-246">2</span><span class="sxs-lookup"><span data-stu-id="471b5-246">2</span></span>|  
|<span data-ttu-id="471b5-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-247">Name</span></span>|@Name|<span data-ttu-id="471b5-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="471b5-249">3</span><span class="sxs-lookup"><span data-stu-id="471b5-249">3</span></span>|  
|<span data-ttu-id="471b5-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="471b5-250">Parameter</span></span>|@Parameter|<span data-ttu-id="471b5-251">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="471b5-251">PARAMETER_NAME</span></span>|<span data-ttu-id="471b5-252">4</span><span class="sxs-lookup"><span data-stu-id="471b5-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="471b5-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="471b5-253">Procedures</span></span>  
  
|<span data-ttu-id="471b5-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-254">Restriction Name</span></span>|<span data-ttu-id="471b5-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-255">Parameter Name</span></span>|<span data-ttu-id="471b5-256">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-256">Restriction Default</span></span>|<span data-ttu-id="471b5-257">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-258">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="471b5-260">1</span><span class="sxs-lookup"><span data-stu-id="471b5-260">1</span></span>|  
|<span data-ttu-id="471b5-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-261">Owner</span></span>|@Owner|<span data-ttu-id="471b5-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="471b5-263">2</span><span class="sxs-lookup"><span data-stu-id="471b5-263">2</span></span>|  
|<span data-ttu-id="471b5-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-264">Name</span></span>|@Name|<span data-ttu-id="471b5-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="471b5-266">3</span><span class="sxs-lookup"><span data-stu-id="471b5-266">3</span></span>|  
|<span data-ttu-id="471b5-267">Typ</span><span class="sxs-lookup"><span data-stu-id="471b5-267">Type</span></span>|@Type|<span data-ttu-id="471b5-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="471b5-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="471b5-269">4</span><span class="sxs-lookup"><span data-stu-id="471b5-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="471b5-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="471b5-270">IndexColumns</span></span>  
  
|<span data-ttu-id="471b5-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-271">Restriction Name</span></span>|<span data-ttu-id="471b5-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-272">Parameter Name</span></span>|<span data-ttu-id="471b5-273">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-273">Restriction Default</span></span>|<span data-ttu-id="471b5-274">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-275">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-275">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="471b5-276">db_name()</span></span>|<span data-ttu-id="471b5-277">1</span><span class="sxs-lookup"><span data-stu-id="471b5-277">1</span></span>|  
|<span data-ttu-id="471b5-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-278">Owner</span></span>|@Owner|<span data-ttu-id="471b5-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="471b5-279">user_name()</span></span>|<span data-ttu-id="471b5-280">2</span><span class="sxs-lookup"><span data-stu-id="471b5-280">2</span></span>|  
|<span data-ttu-id="471b5-281">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-281">Table</span></span>|@Table|<span data-ttu-id="471b5-282">o.name</span><span class="sxs-lookup"><span data-stu-id="471b5-282">o.name</span></span>|<span data-ttu-id="471b5-283">3</span><span class="sxs-lookup"><span data-stu-id="471b5-283">3</span></span>|  
|<span data-ttu-id="471b5-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="471b5-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="471b5-285">x.name</span><span class="sxs-lookup"><span data-stu-id="471b5-285">x.name</span></span>|<span data-ttu-id="471b5-286">4</span><span class="sxs-lookup"><span data-stu-id="471b5-286">4</span></span>|  
|<span data-ttu-id="471b5-287">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-287">Column</span></span>|@Column|<span data-ttu-id="471b5-288">c.name</span><span class="sxs-lookup"><span data-stu-id="471b5-288">c.name</span></span>|<span data-ttu-id="471b5-289">5</span><span class="sxs-lookup"><span data-stu-id="471b5-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="471b5-290">Indeksy</span><span class="sxs-lookup"><span data-stu-id="471b5-290">Indexes</span></span>  
  
|<span data-ttu-id="471b5-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-291">Restriction Name</span></span>|<span data-ttu-id="471b5-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-292">Parameter Name</span></span>|<span data-ttu-id="471b5-293">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-293">Restriction Default</span></span>|<span data-ttu-id="471b5-294">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-295">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-295">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="471b5-296">db_name()</span></span>|<span data-ttu-id="471b5-297">1</span><span class="sxs-lookup"><span data-stu-id="471b5-297">1</span></span>|  
|<span data-ttu-id="471b5-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-298">Owner</span></span>|@Owner|<span data-ttu-id="471b5-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="471b5-299">user_name()</span></span>|<span data-ttu-id="471b5-300">2</span><span class="sxs-lookup"><span data-stu-id="471b5-300">2</span></span>|  
|<span data-ttu-id="471b5-301">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-301">Table</span></span>|@Table|<span data-ttu-id="471b5-302">o.name</span><span class="sxs-lookup"><span data-stu-id="471b5-302">o.name</span></span>|<span data-ttu-id="471b5-303">3</span><span class="sxs-lookup"><span data-stu-id="471b5-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="471b5-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="471b5-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="471b5-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-305">Restriction Name</span></span>|<span data-ttu-id="471b5-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-306">Parameter Name</span></span>|<span data-ttu-id="471b5-307">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-307">Restriction Default</span></span>|<span data-ttu-id="471b5-308">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="471b5-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="471b5-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="471b5-310">assemblies.name</span></span>|<span data-ttu-id="471b5-311">1</span><span class="sxs-lookup"><span data-stu-id="471b5-311">1</span></span>|  
|<span data-ttu-id="471b5-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="471b5-312">udt_name</span></span>|@UDTName|<span data-ttu-id="471b5-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="471b5-313">types.assembly_class</span></span>|<span data-ttu-id="471b5-314">2</span><span class="sxs-lookup"><span data-stu-id="471b5-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="471b5-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="471b5-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="471b5-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-316">Restriction Name</span></span>|<span data-ttu-id="471b5-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-317">Parameter Name</span></span>|<span data-ttu-id="471b5-318">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-318">Restriction Default</span></span>|<span data-ttu-id="471b5-319">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-320">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-320">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="471b5-322">1</span><span class="sxs-lookup"><span data-stu-id="471b5-322">1</span></span>|  
|<span data-ttu-id="471b5-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-323">Owner</span></span>|@Owner|<span data-ttu-id="471b5-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="471b5-325">2</span><span class="sxs-lookup"><span data-stu-id="471b5-325">2</span></span>|  
|<span data-ttu-id="471b5-326">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-326">Table</span></span>|@Table|<span data-ttu-id="471b5-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-327">TABLE_NAME</span></span>|<span data-ttu-id="471b5-328">3</span><span class="sxs-lookup"><span data-stu-id="471b5-328">3</span></span>|  
|<span data-ttu-id="471b5-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="471b5-329">Name</span></span>|@Name|<span data-ttu-id="471b5-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="471b5-331">4</span><span class="sxs-lookup"><span data-stu-id="471b5-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="471b5-332">Ograniczenia schematu programu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="471b5-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="471b5-333">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="471b5-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="471b5-334">Ograniczenia te są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="471b5-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="471b5-335">Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="471b5-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="471b5-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="471b5-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="471b5-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-337">Restriction Name</span></span>|<span data-ttu-id="471b5-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-338">Parameter Name</span></span>|<span data-ttu-id="471b5-339">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-339">Restriction Default</span></span>|<span data-ttu-id="471b5-340">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-341">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-341">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-342">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-343">1</span><span class="sxs-lookup"><span data-stu-id="471b5-343">1</span></span>|  
|<span data-ttu-id="471b5-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-344">Owner</span></span>|@Owner|<span data-ttu-id="471b5-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-346">2</span><span class="sxs-lookup"><span data-stu-id="471b5-346">2</span></span>|  
|<span data-ttu-id="471b5-347">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-347">Table</span></span>|@Table|<span data-ttu-id="471b5-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-348">TABLE_NAME</span></span>|<span data-ttu-id="471b5-349">3</span><span class="sxs-lookup"><span data-stu-id="471b5-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="471b5-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="471b5-350">AllColumns</span></span>  
  
|<span data-ttu-id="471b5-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="471b5-351">Restriction Name</span></span>|<span data-ttu-id="471b5-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="471b5-352">Parameter Name</span></span>|<span data-ttu-id="471b5-353">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="471b5-353">Restriction Default</span></span>|<span data-ttu-id="471b5-354">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="471b5-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="471b5-355">Katalogu</span><span class="sxs-lookup"><span data-stu-id="471b5-355">Catalog</span></span>|@Catalog|<span data-ttu-id="471b5-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="471b5-356">TABLE_CATALOG</span></span>|<span data-ttu-id="471b5-357">1</span><span class="sxs-lookup"><span data-stu-id="471b5-357">1</span></span>|  
|<span data-ttu-id="471b5-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="471b5-358">Owner</span></span>|@Owner|<span data-ttu-id="471b5-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="471b5-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="471b5-360">2</span><span class="sxs-lookup"><span data-stu-id="471b5-360">2</span></span>|  
|<span data-ttu-id="471b5-361">tabela</span><span class="sxs-lookup"><span data-stu-id="471b5-361">Table</span></span>|@Table|<span data-ttu-id="471b5-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-362">TABLE_NAME</span></span>|<span data-ttu-id="471b5-363">3</span><span class="sxs-lookup"><span data-stu-id="471b5-363">3</span></span>|  
|<span data-ttu-id="471b5-364">Kolumny</span><span class="sxs-lookup"><span data-stu-id="471b5-364">Column</span></span>|@Column|<span data-ttu-id="471b5-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="471b5-365">COLUMN_NAME</span></span>|<span data-ttu-id="471b5-366">4</span><span class="sxs-lookup"><span data-stu-id="471b5-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="471b5-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="471b5-367">See Also</span></span>  
 [<span data-ttu-id="471b5-368">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="471b5-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c254865800694af8eb754c3e8d4072688fd7e89a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="schema-restrictions"></a><span data-ttu-id="7601f-102">Ograniczenia schematu</span><span class="sxs-lookup"><span data-stu-id="7601f-102">Schema Restrictions</span></span>
<span data-ttu-id="7601f-103">Drugi parametr opcjonalny **GetSchema** metoda jest zwracane ograniczenia, które są używane w celu ograniczenia ilości informacji o schemacie, a jest przekazywana do **GetSchema** metodę jako tablica ciągów .</span><span class="sxs-lookup"><span data-stu-id="7601f-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="7601f-104">Pozycja w tablicy określa wartości, które mogą upłynąć, a jest to równoważne numer ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="7601f-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="7601f-105">Na przykład w poniższej tabeli opisano ograniczenia obsługiwane przez kolekcji schematów "Tabele" za pomocą dostawcy .NET Framework Data Provider for SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7601f-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="7601f-106">Dodatkowe ograniczenia dotyczące kolekcji schematu programu SQL Server są wymienione na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7601f-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="7601f-107">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-107">Restriction Name</span></span>|<span data-ttu-id="7601f-108">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-108">Parameter Name</span></span>|<span data-ttu-id="7601f-109">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-109">Restriction Default</span></span>|<span data-ttu-id="7601f-110">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-111">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-111">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-112">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-113">1</span><span class="sxs-lookup"><span data-stu-id="7601f-113">1</span></span>|  
|<span data-ttu-id="7601f-114">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-114">Owner</span></span>|@Owner|<span data-ttu-id="7601f-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-116">2</span><span class="sxs-lookup"><span data-stu-id="7601f-116">2</span></span>|  
|<span data-ttu-id="7601f-117">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-117">Table</span></span>|@Name|<span data-ttu-id="7601f-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-118">TABLE_NAME</span></span>|<span data-ttu-id="7601f-119">3</span><span class="sxs-lookup"><span data-stu-id="7601f-119">3</span></span>|  
|<span data-ttu-id="7601f-120">Typem</span><span class="sxs-lookup"><span data-stu-id="7601f-120">TableType</span></span>|@TableType|<span data-ttu-id="7601f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7601f-121">TABLE_TYPE</span></span>|<span data-ttu-id="7601f-122">4</span><span class="sxs-lookup"><span data-stu-id="7601f-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="7601f-123">Określanie wartości ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="7601f-124">Do korzystania z jednego z ograniczeń kolekcji schematów "Tabele", po prostu utworzyć tablicy ciągów z czterech elementów, a następnie umieść wartość w elemencie, który jest zgodna z liczbą ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="7601f-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="7601f-125">Na przykład, aby ograniczyć tabele zwrócony przez **GetSchema** metody tylko tych tabel w schemacie "Sprzedaż" ustawienie drugiego elementu tablicy, tak aby "Sprzedaż" przed przekazaniem go do **GetSchema** metody.</span><span class="sxs-lookup"><span data-stu-id="7601f-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7601f-126">Kolekcje ograniczenia dla `SqlClient` i `OracleClient` dodatkowych `ParameterName` kolumny.</span><span class="sxs-lookup"><span data-stu-id="7601f-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="7601f-127">Ograniczenie domyślna kolumna jest nadal istnieje dla zapewnienia zgodności, ale obecnie jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="7601f-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="7601f-128">Zapytania sparametryzowane zamiast zastępowania ciągów należy ograniczyć ryzyko ataku polegającego na iniekcji SQL podczas określania wartości ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="7601f-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7601f-129">Liczba elementów w tablicy musi być mniejsza niż liczba obsługiwana w przypadku kolekcji określony schemat else ograniczeń <xref:System.ArgumentException> zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="7601f-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="7601f-130">Może być krótsza niż maksymalna liczba ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="7601f-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="7601f-131">Brak ograniczeń są rozpatrywane null (bez ograniczeń).</span><span class="sxs-lookup"><span data-stu-id="7601f-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="7601f-132">Można zbadać zarządzanego dostawcy .NET Framework, można ustalić listy ograniczeń obsługiwanych przez wywołanie metody **GetSchema** metodę o nazwie kolekcji ograniczeń schematu, czyli "Ograniczenia".</span><span class="sxs-lookup"><span data-stu-id="7601f-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="7601f-133">Spowoduje to zwrócenie <xref:System.Data.DataTable> listę nazwy kolekcji, nazwy ograniczenia wartości domyślne ograniczenia i ograniczenie liczby.</span><span class="sxs-lookup"><span data-stu-id="7601f-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7601f-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="7601f-134">Example</span></span>  
 <span data-ttu-id="7601f-135">W poniższych przykładach pokazano, jak używać <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> metody dostawcy danych programu .NET Framework dla programu SQL Server <xref:System.Data.SqlClient.SqlConnection> klasy można pobrać informacji schematu o wszystkie tabele zawarte w **AdventureWorks**przykładowe bazy danych i ograniczyć informacje zwracane tylko tych tabel w schemacie "Sprzedaż":</span><span class="sxs-lookup"><span data-stu-id="7601f-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
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
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="7601f-136">Ograniczenia schematu serwera SQL</span><span class="sxs-lookup"><span data-stu-id="7601f-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="7601f-137">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7601f-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="7601f-138">Użytkownicy</span><span class="sxs-lookup"><span data-stu-id="7601f-138">Users</span></span>  
  
|<span data-ttu-id="7601f-139">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-139">Restriction Name</span></span>|<span data-ttu-id="7601f-140">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-140">Parameter Name</span></span>|<span data-ttu-id="7601f-141">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-141">Restriction Default</span></span>|<span data-ttu-id="7601f-142">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-143">Nazwa_użytkownika</span><span class="sxs-lookup"><span data-stu-id="7601f-143">User_Name</span></span>|@Name|<span data-ttu-id="7601f-144">nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-144">name</span></span>|<span data-ttu-id="7601f-145">1</span><span class="sxs-lookup"><span data-stu-id="7601f-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="7601f-146">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="7601f-146">Databases</span></span>  
  
|<span data-ttu-id="7601f-147">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-147">Restriction Name</span></span>|<span data-ttu-id="7601f-148">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-148">Parameter Name</span></span>|<span data-ttu-id="7601f-149">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-149">Restriction Default</span></span>|<span data-ttu-id="7601f-150">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-151">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-151">Name</span></span>|@Name|<span data-ttu-id="7601f-152">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-152">Name</span></span>|<span data-ttu-id="7601f-153">1</span><span class="sxs-lookup"><span data-stu-id="7601f-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="7601f-154">Tabele</span><span class="sxs-lookup"><span data-stu-id="7601f-154">Tables</span></span>  
  
|<span data-ttu-id="7601f-155">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-155">Restriction Name</span></span>|<span data-ttu-id="7601f-156">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-156">Parameter Name</span></span>|<span data-ttu-id="7601f-157">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-157">Restriction Default</span></span>|<span data-ttu-id="7601f-158">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-159">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-159">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-160">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-161">1</span><span class="sxs-lookup"><span data-stu-id="7601f-161">1</span></span>|  
|<span data-ttu-id="7601f-162">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-162">Owner</span></span>|@Owner|<span data-ttu-id="7601f-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-164">2</span><span class="sxs-lookup"><span data-stu-id="7601f-164">2</span></span>|  
|<span data-ttu-id="7601f-165">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-165">Table</span></span>|@Name|<span data-ttu-id="7601f-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-166">TABLE_NAME</span></span>|<span data-ttu-id="7601f-167">3</span><span class="sxs-lookup"><span data-stu-id="7601f-167">3</span></span>|  
|<span data-ttu-id="7601f-168">Typem</span><span class="sxs-lookup"><span data-stu-id="7601f-168">TableType</span></span>|@TableType|<span data-ttu-id="7601f-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7601f-169">TABLE_TYPE</span></span>|<span data-ttu-id="7601f-170">4</span><span class="sxs-lookup"><span data-stu-id="7601f-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="7601f-171">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-171">Columns</span></span>  
  
|<span data-ttu-id="7601f-172">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-172">Restriction Name</span></span>|<span data-ttu-id="7601f-173">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-173">Parameter Name</span></span>|<span data-ttu-id="7601f-174">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-174">Restriction Default</span></span>|<span data-ttu-id="7601f-175">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-176">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-176">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-177">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-178">1</span><span class="sxs-lookup"><span data-stu-id="7601f-178">1</span></span>|  
|<span data-ttu-id="7601f-179">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-179">Owner</span></span>|@Owner|<span data-ttu-id="7601f-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-181">2</span><span class="sxs-lookup"><span data-stu-id="7601f-181">2</span></span>|  
|<span data-ttu-id="7601f-182">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-182">Table</span></span>|@Table|<span data-ttu-id="7601f-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-183">TABLE_NAME</span></span>|<span data-ttu-id="7601f-184">3</span><span class="sxs-lookup"><span data-stu-id="7601f-184">3</span></span>|  
|<span data-ttu-id="7601f-185">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-185">Column</span></span>|@Column|<span data-ttu-id="7601f-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-186">COLUMN_NAME</span></span>|<span data-ttu-id="7601f-187">4</span><span class="sxs-lookup"><span data-stu-id="7601f-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="7601f-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="7601f-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="7601f-189">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-189">Restriction Name</span></span>|<span data-ttu-id="7601f-190">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-190">Parameter Name</span></span>|<span data-ttu-id="7601f-191">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-191">Restriction Default</span></span>|<span data-ttu-id="7601f-192">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-193">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-193">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-194">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-195">1</span><span class="sxs-lookup"><span data-stu-id="7601f-195">1</span></span>|  
|<span data-ttu-id="7601f-196">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-196">Owner</span></span>|@Owner|<span data-ttu-id="7601f-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-198">2</span><span class="sxs-lookup"><span data-stu-id="7601f-198">2</span></span>|  
|<span data-ttu-id="7601f-199">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-199">Table</span></span>|@Table|<span data-ttu-id="7601f-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-200">TABLE_NAME</span></span>|<span data-ttu-id="7601f-201">3</span><span class="sxs-lookup"><span data-stu-id="7601f-201">3</span></span>|  
|<span data-ttu-id="7601f-202">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-202">Column</span></span>|@Column|<span data-ttu-id="7601f-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-203">COLUMN_NAME</span></span>|<span data-ttu-id="7601f-204">4</span><span class="sxs-lookup"><span data-stu-id="7601f-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="7601f-205">Widoki</span><span class="sxs-lookup"><span data-stu-id="7601f-205">Views</span></span>  
  
|<span data-ttu-id="7601f-206">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-206">Restriction Name</span></span>|<span data-ttu-id="7601f-207">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-207">Parameter Name</span></span>|<span data-ttu-id="7601f-208">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-208">Restriction Default</span></span>|<span data-ttu-id="7601f-209">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-210">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-210">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-211">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-212">1</span><span class="sxs-lookup"><span data-stu-id="7601f-212">1</span></span>|  
|<span data-ttu-id="7601f-213">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-213">Owner</span></span>|@Owner|<span data-ttu-id="7601f-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-215">2</span><span class="sxs-lookup"><span data-stu-id="7601f-215">2</span></span>|  
|<span data-ttu-id="7601f-216">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-216">Table</span></span>|@Table|<span data-ttu-id="7601f-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-217">TABLE_NAME</span></span>|<span data-ttu-id="7601f-218">3</span><span class="sxs-lookup"><span data-stu-id="7601f-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="7601f-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="7601f-219">ViewColumns</span></span>  
  
|<span data-ttu-id="7601f-220">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-220">Restriction Name</span></span>|<span data-ttu-id="7601f-221">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-221">Parameter Name</span></span>|<span data-ttu-id="7601f-222">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-222">Restriction Default</span></span>|<span data-ttu-id="7601f-223">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-224">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-224">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-225">VIEW_CATALOG</span></span>|<span data-ttu-id="7601f-226">1</span><span class="sxs-lookup"><span data-stu-id="7601f-226">1</span></span>|  
|<span data-ttu-id="7601f-227">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-227">Owner</span></span>|@Owner|<span data-ttu-id="7601f-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="7601f-229">2</span><span class="sxs-lookup"><span data-stu-id="7601f-229">2</span></span>|  
|<span data-ttu-id="7601f-230">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-230">Table</span></span>|@Table|<span data-ttu-id="7601f-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-231">VIEW_NAME</span></span>|<span data-ttu-id="7601f-232">3</span><span class="sxs-lookup"><span data-stu-id="7601f-232">3</span></span>|  
|<span data-ttu-id="7601f-233">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-233">Column</span></span>|@Column|<span data-ttu-id="7601f-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-234">COLUMN_NAME</span></span>|<span data-ttu-id="7601f-235">4</span><span class="sxs-lookup"><span data-stu-id="7601f-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="7601f-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="7601f-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="7601f-237">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-237">Restriction Name</span></span>|<span data-ttu-id="7601f-238">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-238">Parameter Name</span></span>|<span data-ttu-id="7601f-239">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-239">Restriction Default</span></span>|<span data-ttu-id="7601f-240">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-241">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-241">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="7601f-243">1</span><span class="sxs-lookup"><span data-stu-id="7601f-243">1</span></span>|  
|<span data-ttu-id="7601f-244">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-244">Owner</span></span>|@Owner|<span data-ttu-id="7601f-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="7601f-246">2</span><span class="sxs-lookup"><span data-stu-id="7601f-246">2</span></span>|  
|<span data-ttu-id="7601f-247">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-247">Name</span></span>|@Name|<span data-ttu-id="7601f-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="7601f-249">3</span><span class="sxs-lookup"><span data-stu-id="7601f-249">3</span></span>|  
|<span data-ttu-id="7601f-250">Parametr</span><span class="sxs-lookup"><span data-stu-id="7601f-250">Parameter</span></span>|@Parameter|<span data-ttu-id="7601f-251">NAZWA_PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="7601f-251">PARAMETER_NAME</span></span>|<span data-ttu-id="7601f-252">4</span><span class="sxs-lookup"><span data-stu-id="7601f-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="7601f-253">Procedury</span><span class="sxs-lookup"><span data-stu-id="7601f-253">Procedures</span></span>  
  
|<span data-ttu-id="7601f-254">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-254">Restriction Name</span></span>|<span data-ttu-id="7601f-255">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-255">Parameter Name</span></span>|<span data-ttu-id="7601f-256">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-256">Restriction Default</span></span>|<span data-ttu-id="7601f-257">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-258">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-258">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="7601f-260">1</span><span class="sxs-lookup"><span data-stu-id="7601f-260">1</span></span>|  
|<span data-ttu-id="7601f-261">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-261">Owner</span></span>|@Owner|<span data-ttu-id="7601f-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="7601f-263">2</span><span class="sxs-lookup"><span data-stu-id="7601f-263">2</span></span>|  
|<span data-ttu-id="7601f-264">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-264">Name</span></span>|@Name|<span data-ttu-id="7601f-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="7601f-266">3</span><span class="sxs-lookup"><span data-stu-id="7601f-266">3</span></span>|  
|<span data-ttu-id="7601f-267">Typ</span><span class="sxs-lookup"><span data-stu-id="7601f-267">Type</span></span>|@Type|<span data-ttu-id="7601f-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="7601f-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="7601f-269">4</span><span class="sxs-lookup"><span data-stu-id="7601f-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="7601f-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="7601f-270">IndexColumns</span></span>  
  
|<span data-ttu-id="7601f-271">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-271">Restriction Name</span></span>|<span data-ttu-id="7601f-272">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-272">Parameter Name</span></span>|<span data-ttu-id="7601f-273">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-273">Restriction Default</span></span>|<span data-ttu-id="7601f-274">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-275">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-275">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="7601f-276">db_name()</span></span>|<span data-ttu-id="7601f-277">1</span><span class="sxs-lookup"><span data-stu-id="7601f-277">1</span></span>|  
|<span data-ttu-id="7601f-278">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-278">Owner</span></span>|@Owner|<span data-ttu-id="7601f-279">User_name()</span><span class="sxs-lookup"><span data-stu-id="7601f-279">user_name()</span></span>|<span data-ttu-id="7601f-280">2</span><span class="sxs-lookup"><span data-stu-id="7601f-280">2</span></span>|  
|<span data-ttu-id="7601f-281">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-281">Table</span></span>|@Table|<span data-ttu-id="7601f-282">o.name</span><span class="sxs-lookup"><span data-stu-id="7601f-282">o.name</span></span>|<span data-ttu-id="7601f-283">3</span><span class="sxs-lookup"><span data-stu-id="7601f-283">3</span></span>|  
|<span data-ttu-id="7601f-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="7601f-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="7601f-285">x.name</span><span class="sxs-lookup"><span data-stu-id="7601f-285">x.name</span></span>|<span data-ttu-id="7601f-286">4</span><span class="sxs-lookup"><span data-stu-id="7601f-286">4</span></span>|  
|<span data-ttu-id="7601f-287">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-287">Column</span></span>|@Column|<span data-ttu-id="7601f-288">c.name</span><span class="sxs-lookup"><span data-stu-id="7601f-288">c.name</span></span>|<span data-ttu-id="7601f-289">5</span><span class="sxs-lookup"><span data-stu-id="7601f-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="7601f-290">Indeksy</span><span class="sxs-lookup"><span data-stu-id="7601f-290">Indexes</span></span>  
  
|<span data-ttu-id="7601f-291">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-291">Restriction Name</span></span>|<span data-ttu-id="7601f-292">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-292">Parameter Name</span></span>|<span data-ttu-id="7601f-293">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-293">Restriction Default</span></span>|<span data-ttu-id="7601f-294">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-295">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-295">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="7601f-296">db_name()</span></span>|<span data-ttu-id="7601f-297">1</span><span class="sxs-lookup"><span data-stu-id="7601f-297">1</span></span>|  
|<span data-ttu-id="7601f-298">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-298">Owner</span></span>|@Owner|<span data-ttu-id="7601f-299">User_name()</span><span class="sxs-lookup"><span data-stu-id="7601f-299">user_name()</span></span>|<span data-ttu-id="7601f-300">2</span><span class="sxs-lookup"><span data-stu-id="7601f-300">2</span></span>|  
|<span data-ttu-id="7601f-301">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-301">Table</span></span>|@Table|<span data-ttu-id="7601f-302">o.name</span><span class="sxs-lookup"><span data-stu-id="7601f-302">o.name</span></span>|<span data-ttu-id="7601f-303">3</span><span class="sxs-lookup"><span data-stu-id="7601f-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="7601f-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="7601f-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="7601f-305">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-305">Restriction Name</span></span>|<span data-ttu-id="7601f-306">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-306">Parameter Name</span></span>|<span data-ttu-id="7601f-307">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-307">Restriction Default</span></span>|<span data-ttu-id="7601f-308">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-309">nazwa_zestawu</span><span class="sxs-lookup"><span data-stu-id="7601f-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="7601f-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="7601f-310">assemblies.name</span></span>|<span data-ttu-id="7601f-311">1</span><span class="sxs-lookup"><span data-stu-id="7601f-311">1</span></span>|  
|<span data-ttu-id="7601f-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="7601f-312">udt_name</span></span>|@UDTName|<span data-ttu-id="7601f-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="7601f-313">types.assembly_class</span></span>|<span data-ttu-id="7601f-314">2</span><span class="sxs-lookup"><span data-stu-id="7601f-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="7601f-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="7601f-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="7601f-316">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-316">Restriction Name</span></span>|<span data-ttu-id="7601f-317">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-317">Parameter Name</span></span>|<span data-ttu-id="7601f-318">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-318">Restriction Default</span></span>|<span data-ttu-id="7601f-319">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-320">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-320">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="7601f-322">1</span><span class="sxs-lookup"><span data-stu-id="7601f-322">1</span></span>|  
|<span data-ttu-id="7601f-323">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-323">Owner</span></span>|@Owner|<span data-ttu-id="7601f-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="7601f-325">2</span><span class="sxs-lookup"><span data-stu-id="7601f-325">2</span></span>|  
|<span data-ttu-id="7601f-326">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-326">Table</span></span>|@Table|<span data-ttu-id="7601f-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-327">TABLE_NAME</span></span>|<span data-ttu-id="7601f-328">3</span><span class="sxs-lookup"><span data-stu-id="7601f-328">3</span></span>|  
|<span data-ttu-id="7601f-329">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7601f-329">Name</span></span>|@Name|<span data-ttu-id="7601f-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="7601f-331">4</span><span class="sxs-lookup"><span data-stu-id="7601f-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="7601f-332">Ograniczenia schematu programu SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="7601f-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="7601f-333">W poniższej tabeli wymieniono ograniczenia dotyczące kolekcji schematu programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7601f-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="7601f-334">Ograniczenia te są prawidłowe, począwszy od wersji 3.5 z dodatkiem SP1, .NET Framework i programu SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="7601f-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="7601f-335">Nie są obsługiwane we wcześniejszych wersjach programu .NET Framework i programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7601f-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="7601f-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="7601f-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="7601f-337">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-337">Restriction Name</span></span>|<span data-ttu-id="7601f-338">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-338">Parameter Name</span></span>|<span data-ttu-id="7601f-339">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-339">Restriction Default</span></span>|<span data-ttu-id="7601f-340">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-341">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-341">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-342">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-343">1</span><span class="sxs-lookup"><span data-stu-id="7601f-343">1</span></span>|  
|<span data-ttu-id="7601f-344">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-344">Owner</span></span>|@Owner|<span data-ttu-id="7601f-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-346">2</span><span class="sxs-lookup"><span data-stu-id="7601f-346">2</span></span>|  
|<span data-ttu-id="7601f-347">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-347">Table</span></span>|@Table|<span data-ttu-id="7601f-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-348">TABLE_NAME</span></span>|<span data-ttu-id="7601f-349">3</span><span class="sxs-lookup"><span data-stu-id="7601f-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="7601f-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="7601f-350">AllColumns</span></span>  
  
|<span data-ttu-id="7601f-351">Nazwa ograniczenia</span><span class="sxs-lookup"><span data-stu-id="7601f-351">Restriction Name</span></span>|<span data-ttu-id="7601f-352">Nazwa parametru</span><span class="sxs-lookup"><span data-stu-id="7601f-352">Parameter Name</span></span>|<span data-ttu-id="7601f-353">Ograniczenie domyślne</span><span class="sxs-lookup"><span data-stu-id="7601f-353">Restriction Default</span></span>|<span data-ttu-id="7601f-354">Liczba ograniczeń</span><span class="sxs-lookup"><span data-stu-id="7601f-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="7601f-355">Katalogu</span><span class="sxs-lookup"><span data-stu-id="7601f-355">Catalog</span></span>|@Catalog|<span data-ttu-id="7601f-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="7601f-356">TABLE_CATALOG</span></span>|<span data-ttu-id="7601f-357">1</span><span class="sxs-lookup"><span data-stu-id="7601f-357">1</span></span>|  
|<span data-ttu-id="7601f-358">Właściciel</span><span class="sxs-lookup"><span data-stu-id="7601f-358">Owner</span></span>|@Owner|<span data-ttu-id="7601f-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="7601f-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="7601f-360">2</span><span class="sxs-lookup"><span data-stu-id="7601f-360">2</span></span>|  
|<span data-ttu-id="7601f-361">tabela</span><span class="sxs-lookup"><span data-stu-id="7601f-361">Table</span></span>|@Table|<span data-ttu-id="7601f-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-362">TABLE_NAME</span></span>|<span data-ttu-id="7601f-363">3</span><span class="sxs-lookup"><span data-stu-id="7601f-363">3</span></span>|  
|<span data-ttu-id="7601f-364">Kolumny</span><span class="sxs-lookup"><span data-stu-id="7601f-364">Column</span></span>|@Column|<span data-ttu-id="7601f-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="7601f-365">COLUMN_NAME</span></span>|<span data-ttu-id="7601f-366">4</span><span class="sxs-lookup"><span data-stu-id="7601f-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7601f-367">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7601f-367">See Also</span></span>  
 [<span data-ttu-id="7601f-368">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="7601f-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

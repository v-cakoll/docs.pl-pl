---
title: "Wyliczanie wystąpień programu SQL Server (ADO.NET)"
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
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7b0a81fd9b92e626b52c5a74c65798ddedbd94a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="5f1c6-102">Wyliczanie wystąpień programu SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5f1c6-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="5f1c6-103">zezwala aplikacji można znaleźć [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpień w ramach bieżącej sieci.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-103"> permits applications to find [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances within the current network.</span></span> <span data-ttu-id="5f1c6-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Klasy udostępnia te informacje do deweloperów aplikacji, zapewniając <xref:System.Data.DataTable> zawierających informacje dotyczące wszystkich serwerów widoczne.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="5f1c6-105">Ta wartość zwracana tabela zawiera listę wystąpień serwera dostępne w sieci, z którą jest zgodne z listą pod warunkiem, gdy użytkownik próbuje utworzyć nowe połączenie i rozwija listy rozwijanej zawierające wszystkie dostępne serwery na **połączenia Właściwości** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="5f1c6-106">Wyniki wyświetlane nie zawsze są kompletne.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f1c6-107">Jako większości usługami wdrażania systemu Windows, najlepiej do uruchamiania usługi SQL Browser z najniższe możliwe uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="5f1c6-108">Zobacz [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] — książki Online, aby uzyskać więcej informacji na temat usługa SQL Browser i jak zarządzać jego zachowania.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-108">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="5f1c6-109">Pobieranie wystąpienia modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="5f1c6-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="5f1c6-110">Aby można było pobrać tabeli zawierającej informacje o dostępnych [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpienia, należy najpierw pobrać moduł wyliczający, przy użyciu udostępnionych/statycznych <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości:</span><span class="sxs-lookup"><span data-stu-id="5f1c6-110">In order to retrieve the table containing information about the available [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="5f1c6-111">Po pobraniu statycznego wystąpienia, należy wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metody, która zwraca <xref:System.Data.DataTable> zawierający informacje o dostępnych serwerów:</span><span class="sxs-lookup"><span data-stu-id="5f1c6-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="5f1c6-112">Tabela zwracana z wywołania metody, które zawiera następujące kolumny, które zawierają `string` wartości:</span><span class="sxs-lookup"><span data-stu-id="5f1c6-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="5f1c6-113">Kolumny</span><span class="sxs-lookup"><span data-stu-id="5f1c6-113">Column</span></span>|<span data-ttu-id="5f1c6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5f1c6-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5f1c6-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="5f1c6-115">**ServerName**</span></span>|<span data-ttu-id="5f1c6-116">Nazwa serwera.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-116">Name of the server.</span></span>|  
|<span data-ttu-id="5f1c6-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="5f1c6-117">**InstanceName**</span></span>|<span data-ttu-id="5f1c6-118">Nazwa wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-118">Name of the server instance.</span></span> <span data-ttu-id="5f1c6-119">Puste, jeśli serwer działa jako domyślnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="5f1c6-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="5f1c6-120">**IsClustered**</span></span>|<span data-ttu-id="5f1c6-121">Wskazuje, czy serwer jest częścią klastra.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="5f1c6-122">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="5f1c6-122">**Version**</span></span>|<span data-ttu-id="5f1c6-123">Wersja serwera.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-123">Version of the server.</span></span> <span data-ttu-id="5f1c6-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5f1c6-124">For example:</span></span><br /><br /> <span data-ttu-id="5f1c6-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="5f1c6-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="5f1c6-126">-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="5f1c6-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="5f1c6-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="5f1c6-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="5f1c6-128">-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span><span class="sxs-lookup"><span data-stu-id="5f1c6-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="5f1c6-129">Ograniczenia — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5f1c6-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="5f1c6-130">Wszystkie dostępne serwery mogą lub nie mogą być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="5f1c6-131">Lista może się różnić w zależności od czynników, takie jak ruch w sieci i limitów czasu.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="5f1c6-132">Może to spowodować listy maja być inne dla dwóch kolejnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="5f1c6-133">Zostaną wyświetlone tylko dla serwerów w tej samej sieci.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="5f1c6-134">Pakietów emisji zazwyczaj nie przechodzą przez routery, dlatego serwer, na liście mogą nie być widoczne, ale będzie ona stabilna między wywołania.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="5f1c6-135">Wymienione serwery mogą lub nie ma dodatkowych informacji takich jak `IsClustered` i wersji.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="5f1c6-136">Jest to zależne od tego, jak uzyskano listy.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="5f1c6-137">Serwery wymienione za pośrednictwem [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] usługa przeglądarki będzie mieć więcej szczegółów niż występujące za pośrednictwem infrastruktury systemu Windows, w którym wyświetlana jest tylko nazwa.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-137">Servers listed through the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f1c6-138">Wyliczenie serwera jest dostępna tylko podczas uruchamiania w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="5f1c6-139">W środowisku częściowo zaufane zestawy nie będzie mógł jej użyć, nawet jeśli ma <xref:System.Data.SqlClient.SqlClientPermission> uprawnienia zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="5f1c6-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="5f1c6-140">zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> za pomocą zewnętrznej usługi systemu Windows o nazwie SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-140"> provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="5f1c6-141">Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć tę funkcję ukrywanie wystąpienie serwera do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f1c6-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f1c6-142">Example</span></span>  
 <span data-ttu-id="5f1c6-143">Następującej aplikacji konsoli pobiera informacje o wszystkich widoczne [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] wystąpień i wyświetla informacje w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="5f1c6-143">The following console application retrieves information about all of the visible [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
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
  
## <a name="see-also"></a><span data-ttu-id="5f1c6-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f1c6-144">See Also</span></span>  
 [<span data-ttu-id="5f1c6-145">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5f1c6-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="5f1c6-146">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="5f1c6-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

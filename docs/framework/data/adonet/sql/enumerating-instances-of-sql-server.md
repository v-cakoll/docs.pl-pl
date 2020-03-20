---
title: Wyliczanie wystąpień programu SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a707df533216613e34d9f357c7b9e035f73b9561
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148689"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="a2da7-102">Wyliczanie wystąpień programu SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a2da7-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="a2da7-103">Program SQL Server zezwala aplikacjom na znajdowanie wystąpień programu SQL Server w bieżącej sieci.</span><span class="sxs-lookup"><span data-stu-id="a2da7-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="a2da7-104">Klasa <xref:System.Data.Sql.SqlDataSourceEnumerator> udostępnia te informacje deweloperowi aplikacji, <xref:System.Data.DataTable> zapewniając zawierające informacje o wszystkich widocznych serwerach.</span><span class="sxs-lookup"><span data-stu-id="a2da7-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="a2da7-105">Ta zwrócona tabela zawiera listę wystąpień serwera dostępnych w sieci, która jest zgodna z listą podana, gdy użytkownik próbuje utworzyć nowe połączenie, i rozwija listę rozwijaną zawierającą wszystkie dostępne serwery w oknie dialogowym **Właściwości połączenia.**</span><span class="sxs-lookup"><span data-stu-id="a2da7-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="a2da7-106">Wyświetlane wyniki nie zawsze są kompletne.</span><span class="sxs-lookup"><span data-stu-id="a2da7-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2da7-107">Podobnie jak w przypadku większości usług systemu Windows, najlepiej jest uruchomić usługę przeglądarki SQL z jak najmniejszymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="a2da7-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="a2da7-108">Zobacz SQL Server Books Online, aby uzyskać więcej informacji na temat usługi przeglądarki SQL i jak zarządzać jej zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="a2da7-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="a2da7-109">Pobieranie wystąpienia wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a2da7-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="a2da7-110">Aby pobrać tabelę zawierającą informacje o dostępnych wystąpieniach programu SQL Server, należy najpierw pobrać wyliczacz przy użyciu <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości udostępnionej/statycznej:</span><span class="sxs-lookup"><span data-stu-id="a2da7-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="a2da7-111">Po pobraniu wystąpienia statycznego można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodę, <xref:System.Data.DataTable> która zwraca zawierające informacje o dostępnych serwerach:</span><span class="sxs-lookup"><span data-stu-id="a2da7-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="a2da7-112">Tabela zwrócona z wywołania metody zawiera następujące `string` kolumny, z których wszystkie zawierają wartości:</span><span class="sxs-lookup"><span data-stu-id="a2da7-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="a2da7-113">Kolumna</span><span class="sxs-lookup"><span data-stu-id="a2da7-113">Column</span></span>|<span data-ttu-id="a2da7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a2da7-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a2da7-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="a2da7-115">**ServerName**</span></span>|<span data-ttu-id="a2da7-116">Nazwa serwera.</span><span class="sxs-lookup"><span data-stu-id="a2da7-116">Name of the server.</span></span>|  
|<span data-ttu-id="a2da7-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="a2da7-117">**InstanceName**</span></span>|<span data-ttu-id="a2da7-118">Nazwa wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="a2da7-118">Name of the server instance.</span></span> <span data-ttu-id="a2da7-119">Puste, jeśli serwer jest uruchomiony jako wystąpienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="a2da7-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="a2da7-120">**Isclustered**</span><span class="sxs-lookup"><span data-stu-id="a2da7-120">**IsClustered**</span></span>|<span data-ttu-id="a2da7-121">Wskazuje, czy serwer jest częścią klastra.</span><span class="sxs-lookup"><span data-stu-id="a2da7-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="a2da7-122">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="a2da7-122">**Version**</span></span>|<span data-ttu-id="a2da7-123">Wersja serwera.</span><span class="sxs-lookup"><span data-stu-id="a2da7-123">Version of the server.</span></span> <span data-ttu-id="a2da7-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a2da7-124">For example:</span></span><br /><br /> <span data-ttu-id="a2da7-125">- 9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="a2da7-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="a2da7-126">- 10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="a2da7-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="a2da7-127">- 10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="a2da7-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="a2da7-128">- 11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="a2da7-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="a2da7-129">Ograniczenia wyliczenia</span><span class="sxs-lookup"><span data-stu-id="a2da7-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="a2da7-130">Wszystkie dostępne serwery mogą być lub nie mogą być wymienione.</span><span class="sxs-lookup"><span data-stu-id="a2da7-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="a2da7-131">Lista może się różnić w zależności od czynników, takich jak limity czasu i ruch sieciowy.</span><span class="sxs-lookup"><span data-stu-id="a2da7-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="a2da7-132">Może to spowodować, że lista będzie inna w dwóch kolejnych wywołaniach.</span><span class="sxs-lookup"><span data-stu-id="a2da7-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="a2da7-133">Zostaną wyświetlone tylko serwery w tej samej sieci.</span><span class="sxs-lookup"><span data-stu-id="a2da7-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="a2da7-134">Pakiety emisji zazwyczaj nie przechodzą przez routery, dlatego może nie być widoczny serwer na liście, ale będzie stabilny w połączeniach.</span><span class="sxs-lookup"><span data-stu-id="a2da7-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="a2da7-135">Wymienione serwery mogą, ale nie `IsClustered` muszą mieć dodatkowych informacji, takich jak i wersja.</span><span class="sxs-lookup"><span data-stu-id="a2da7-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="a2da7-136">Zależy to od sposobu uzyskania listy.</span><span class="sxs-lookup"><span data-stu-id="a2da7-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="a2da7-137">Serwery wymienione za pośrednictwem usługi przeglądarki SQL Server będą miały więcej szczegółów niż te znalezione za pośrednictwem infrastruktury systemu Windows, która wyświetli tylko nazwę.</span><span class="sxs-lookup"><span data-stu-id="a2da7-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2da7-138">Wyliczenie serwera jest dostępne tylko wtedy, gdy jest uruchomione w pełnym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="a2da7-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="a2da7-139">Zestawy działające w częściowo zaufanym środowisku nie będą mogły go <xref:System.Data.SqlClient.SqlClientPermission> używać, nawet jeśli mają uprawnienie CAS (Code Access Security).</span><span class="sxs-lookup"><span data-stu-id="a2da7-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="a2da7-140">Program SQL Server <xref:System.Data.Sql.SqlDataSourceEnumerator> udostępnia informacje za pośrednictwem zewnętrznej usługi systemu Windows o nazwie SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="a2da7-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="a2da7-141">Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć, co spowoduje, że wystąpienie serwera będzie niewidoczne dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="a2da7-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2da7-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2da7-142">Example</span></span>  
 <span data-ttu-id="a2da7-143">Następująca aplikacja konsoli pobiera informacje o wszystkich widocznych wystąpieniach programu SQL Server i wyświetla informacje w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a2da7-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a2da7-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2da7-144">See also</span></span>

- [<span data-ttu-id="a2da7-145">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2da7-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="a2da7-146">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2da7-146">ADO.NET Overview</span></span>](../ado-net-overview.md)

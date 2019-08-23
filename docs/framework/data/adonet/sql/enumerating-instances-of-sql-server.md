---
title: Wyliczanie wystąpień programu SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: 304387197c7c6ca31d76ce429cd1516be27ba7b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938173"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="a6915-102">Wyliczanie wystąpień programu SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a6915-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="a6915-103">SQL Server zezwala aplikacjom na Znajdowanie SQL Server wystąpień w bieżącej sieci.</span><span class="sxs-lookup"><span data-stu-id="a6915-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="a6915-104">Klasa ujawnia te informacje deweloperowi aplikacji, <xref:System.Data.DataTable> dostarczając zawierające informacje o wszystkich widocznych serwerach. <xref:System.Data.Sql.SqlDataSourceEnumerator></span><span class="sxs-lookup"><span data-stu-id="a6915-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="a6915-105">Zwracana tabela zawiera listę wystąpień serwera dostępnych w sieci, które pasują do listy udostępnionej, gdy użytkownik próbuje utworzyć nowe połączenie, a następnie rozwija listę rozwijaną zawierającą wszystkie dostępne serwery we **właściwościach połączenia.** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a6915-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="a6915-106">Wyświetlane wyniki nie zawsze są kompletne.</span><span class="sxs-lookup"><span data-stu-id="a6915-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6915-107">Podobnie jak w przypadku większości usług systemu Windows, najlepszym rozwiązaniem jest uruchomienie usługi SQL Browser z najniższymi możliwymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="a6915-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="a6915-108">Więcej informacji na temat usługi SQL Browser można znaleźć w dokumentacji SQL Server Books Online oraz jak zarządzać jej zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="a6915-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="a6915-109">Pobieranie wystąpienia modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="a6915-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="a6915-110">Aby można było pobrać tabelę zawierającą informacje o dostępnych wystąpieniach SQL Server, należy najpierw pobrać moduł wyliczający przy użyciu właściwości Shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :</span><span class="sxs-lookup"><span data-stu-id="a6915-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="a6915-111">Po pobraniu wystąpienia statycznego można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodę, która <xref:System.Data.DataTable> zwraca zawierające informacje o dostępnych serwerach:</span><span class="sxs-lookup"><span data-stu-id="a6915-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="a6915-112">Tabela zwrócona przez wywołanie metody zawiera następujące kolumny, z których wszystkie zawierają `string` wartości:</span><span class="sxs-lookup"><span data-stu-id="a6915-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="a6915-113">Kolumna</span><span class="sxs-lookup"><span data-stu-id="a6915-113">Column</span></span>|<span data-ttu-id="a6915-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a6915-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6915-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="a6915-115">**ServerName**</span></span>|<span data-ttu-id="a6915-116">Nazwa serwera.</span><span class="sxs-lookup"><span data-stu-id="a6915-116">Name of the server.</span></span>|  
|<span data-ttu-id="a6915-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="a6915-117">**InstanceName**</span></span>|<span data-ttu-id="a6915-118">Nazwa wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="a6915-118">Name of the server instance.</span></span> <span data-ttu-id="a6915-119">Puste, jeśli serwer działa jako wystąpienie domyślne.</span><span class="sxs-lookup"><span data-stu-id="a6915-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="a6915-120">**Isclusterd**</span><span class="sxs-lookup"><span data-stu-id="a6915-120">**IsClustered**</span></span>|<span data-ttu-id="a6915-121">Wskazuje, czy serwer jest częścią klastra.</span><span class="sxs-lookup"><span data-stu-id="a6915-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="a6915-122">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="a6915-122">**Version**</span></span>|<span data-ttu-id="a6915-123">Wersja serwera programu.</span><span class="sxs-lookup"><span data-stu-id="a6915-123">Version of the server.</span></span> <span data-ttu-id="a6915-124">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a6915-124">For example:</span></span><br /><br /> <span data-ttu-id="a6915-125">-9.00. x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="a6915-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="a6915-126">-10.0. XX (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="a6915-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="a6915-127">-10.50. x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="a6915-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="a6915-128">-11.0. XX (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="a6915-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="a6915-129">Ograniczenia wyliczania</span><span class="sxs-lookup"><span data-stu-id="a6915-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="a6915-130">Wszystkie dostępne serwery mogą lub nie mogą być wymienione na liście.</span><span class="sxs-lookup"><span data-stu-id="a6915-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="a6915-131">Lista może się różnić w zależności od takich czynników, jak limity czasu i ruch sieciowy.</span><span class="sxs-lookup"><span data-stu-id="a6915-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="a6915-132">Może to spowodować, że lista będzie się różnić między dwoma kolejnymi wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="a6915-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="a6915-133">Zostaną wyświetlone tylko serwery w tej samej sieci.</span><span class="sxs-lookup"><span data-stu-id="a6915-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="a6915-134">Pakiety emisji zwykle nie przechodzą na routery, co oznacza, że nie widzisz serwera na liście, ale będzie on stabilny dla wywołań.</span><span class="sxs-lookup"><span data-stu-id="a6915-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="a6915-135">Wymienione serwery mogą lub nie mieć dodatkowych informacji, takich jak `IsClustered` i wersja.</span><span class="sxs-lookup"><span data-stu-id="a6915-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="a6915-136">Jest to zależne od tego, jak uzyskano listę.</span><span class="sxs-lookup"><span data-stu-id="a6915-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="a6915-137">Serwery wymienione za pomocą usługi SQL Server Browser będą miały więcej szczegółów niż te, które znajdują się w infrastrukturze systemu Windows, która będzie zawierać tylko nazwę.</span><span class="sxs-lookup"><span data-stu-id="a6915-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6915-138">Wyliczenie serwera jest dostępne tylko w przypadku uruchamiania w trybie pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="a6915-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="a6915-139">Zestawy działające w środowisku częściowo zaufanym nie będą mogły ich używać nawet wtedy, gdy mają <xref:System.Data.SqlClient.SqlClientPermission> uprawnienie zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="a6915-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="a6915-140">SQL Server zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> korzystania z zewnętrznej usługi systemu Windows o nazwie SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="a6915-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="a6915-141">Ta usługa jest domyślnie włączona, ale Administratorzy mogą ją wyłączyć lub wyłączyć, co sprawia, że wystąpienie serwera jest niewidoczne dla tej klasy.</span><span class="sxs-lookup"><span data-stu-id="a6915-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6915-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6915-142">Example</span></span>  
 <span data-ttu-id="a6915-143">Następująca aplikacja konsolowa pobiera informacje o wszystkich widocznych wystąpieniach SQL Server i wyświetla informacje w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a6915-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6915-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6915-144">See also</span></span>

- [<span data-ttu-id="a6915-145">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6915-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="a6915-146">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a6915-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

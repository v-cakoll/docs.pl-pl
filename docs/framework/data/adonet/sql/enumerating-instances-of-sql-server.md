---
title: Wyliczanie wystąpień programu SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a723679fe18352e115df78af72975097dc28b617
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162858"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="353e1-102">Wyliczanie wystąpień programu SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="353e1-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="353e1-103">Program SQL Server zezwala na aplikacji, aby znaleźć wystąpień programu SQL Server w ramach bieżącej sieci.</span><span class="sxs-lookup"><span data-stu-id="353e1-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="353e1-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Klasa udostępnia te informacje do deweloperów aplikacji, zapewniając <xref:System.Data.DataTable> zawierające informacje dotyczące wszystkich serwerów widoczne.</span><span class="sxs-lookup"><span data-stu-id="353e1-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="353e1-105">Ta wartość zwrócona tabela zawiera listę wystąpień serwera dostępne w sieci, z którą jest zgodne z listą udostępniany, gdy użytkownik próbuje utworzyć nowe połączenie, a następnie rozwija listy rozwijanej zawierające wszystkie dostępne serwery na **połączenia Właściwości** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="353e1-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="353e1-106">Wyniki wyświetlane nie zawsze są pełne.</span><span class="sxs-lookup"><span data-stu-id="353e1-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="353e1-107">W przypadku większości usług Windows jest najlepsze do uruchamiania usługi SQL Browser przy najniższe możliwe uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="353e1-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="353e1-108">Zobacz dokumentację SQL Server — książki Online, aby uzyskać więcej informacji na temat usługi SQL Browser, a także jak zarządzać jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="353e1-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="353e1-109">Pobieranie wystąpienia modułu wyliczającego</span><span class="sxs-lookup"><span data-stu-id="353e1-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="353e1-110">Aby można było pobrać Tabela zawierająca informacje na temat dostępnych wystąpień programu SQL Server, należy najpierw pobrać moduł wyliczający przy użyciu udostępnionych/statyczne <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości:</span><span class="sxs-lookup"><span data-stu-id="353e1-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="353e1-111">Po pobraniu wystąpień statycznych, można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metody, która zwraca <xref:System.Data.DataTable> zawierający informacje o dostępnych serwerów:</span><span class="sxs-lookup"><span data-stu-id="353e1-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="353e1-112">Tabela zwrócony z wywołania metody które zawiera następujące kolumny, które zawierają `string` wartości:</span><span class="sxs-lookup"><span data-stu-id="353e1-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="353e1-113">Kolumna</span><span class="sxs-lookup"><span data-stu-id="353e1-113">Column</span></span>|<span data-ttu-id="353e1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="353e1-114">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="353e1-115">ServerName</span><span class="sxs-lookup"><span data-stu-id="353e1-115">ServerName</span></span>**|<span data-ttu-id="353e1-116">Nazwa serwera.</span><span class="sxs-lookup"><span data-stu-id="353e1-116">Name of the server.</span></span>|  
|**<span data-ttu-id="353e1-117">InstanceName</span><span class="sxs-lookup"><span data-stu-id="353e1-117">InstanceName</span></span>**|<span data-ttu-id="353e1-118">Nazwa wystąpienia serwera.</span><span class="sxs-lookup"><span data-stu-id="353e1-118">Name of the server instance.</span></span> <span data-ttu-id="353e1-119">Pole puste, jeśli serwer działa jako domyślnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="353e1-119">Blank if the server is running as the default instance.</span></span>|  
|**<span data-ttu-id="353e1-120">IsClustered</span><span class="sxs-lookup"><span data-stu-id="353e1-120">IsClustered</span></span>**|<span data-ttu-id="353e1-121">Wskazuje, czy serwer jest częścią klastra.</span><span class="sxs-lookup"><span data-stu-id="353e1-121">Indicates whether the server is part of a cluster.</span></span>|  
|**<span data-ttu-id="353e1-122">Wersja</span><span class="sxs-lookup"><span data-stu-id="353e1-122">Version</span></span>**|<span data-ttu-id="353e1-123">Wersja serwera.</span><span class="sxs-lookup"><span data-stu-id="353e1-123">Version of the server.</span></span> <span data-ttu-id="353e1-124">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="353e1-124">For example:</span></span><br /><br /> <span data-ttu-id="353e1-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="353e1-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="353e1-126">-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="353e1-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="353e1-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="353e1-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="353e1-128">-   11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="353e1-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="353e1-129">Wyliczenie ograniczeń</span><span class="sxs-lookup"><span data-stu-id="353e1-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="353e1-130">Wszystkie dostępne serwery mogą lub nie mogą być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="353e1-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="353e1-131">Lista może się różnić w zależności od czynników, takich jak przekroczenia limitu czasu i siecią ruchu.</span><span class="sxs-lookup"><span data-stu-id="353e1-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="353e1-132">Może to spowodować, że na liście, aby różniłaby się w dwóch kolejnych wywołań.</span><span class="sxs-lookup"><span data-stu-id="353e1-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="353e1-133">Zostaną wyświetlone tylko serwery w tej samej sieci.</span><span class="sxs-lookup"><span data-stu-id="353e1-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="353e1-134">Pakietów emisji zazwyczaj nie przechodzą przez routery, dlatego nie może zostać wyświetlony serwer, na liście, ale będzie stabilny przez wywołania.</span><span class="sxs-lookup"><span data-stu-id="353e1-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="353e1-135">Wymienione serwery może być lub może nie mieć dodatkowe informacje takie jak `IsClustered` i wersji.</span><span class="sxs-lookup"><span data-stu-id="353e1-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="353e1-136">To zależy od tego, jak zostały pobrane listy.</span><span class="sxs-lookup"><span data-stu-id="353e1-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="353e1-137">Serwery wymienione za pośrednictwem usługa przeglądarki SQL Server ma więcej szczegółów niż występujące za pomocą infrastruktury Windows, który wyświetla tylko nazwę.</span><span class="sxs-lookup"><span data-stu-id="353e1-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="353e1-138">Wyliczenie Server jest dostępna tylko podczas uruchamiania w pełni zaufanym.</span><span class="sxs-lookup"><span data-stu-id="353e1-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="353e1-139">W środowisku z częściowo zaufanych zestawów nie będzie go obsługują, nawet jeśli mają one <xref:System.Data.SqlClient.SqlClientPermission> uprawnień zabezpieczeń dostępu kodu (CAS).</span><span class="sxs-lookup"><span data-stu-id="353e1-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="353e1-140">Program SQL Server zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> przy użyciu usługi zewnętrznej Windows o nazwie SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="353e1-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="353e1-141">Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć tę funkcję ukrywanie wystąpienia serwera do tej klasy.</span><span class="sxs-lookup"><span data-stu-id="353e1-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="353e1-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="353e1-142">Example</span></span>  
 <span data-ttu-id="353e1-143">Następującej aplikacji konsoli pobiera informacje o wszystkich widoczne wystąpienia programu SQL Server i wyświetla informacje w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="353e1-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="353e1-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="353e1-144">See also</span></span>

- [<span data-ttu-id="353e1-145">SQL Server i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="353e1-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="353e1-146">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="353e1-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)

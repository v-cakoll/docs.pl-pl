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
# <a name="enumerating-instances-of-sql-server-adonet"></a>Wyliczanie wystąpień programu SQL Server (ADO.NET)
Program SQL Server zezwala aplikacjom na znajdowanie wystąpień programu SQL Server w bieżącej sieci. Klasa <xref:System.Data.Sql.SqlDataSourceEnumerator> udostępnia te informacje deweloperowi aplikacji, <xref:System.Data.DataTable> zapewniając zawierające informacje o wszystkich widocznych serwerach. Ta zwrócona tabela zawiera listę wystąpień serwera dostępnych w sieci, która jest zgodna z listą podana, gdy użytkownik próbuje utworzyć nowe połączenie, i rozwija listę rozwijaną zawierającą wszystkie dostępne serwery w oknie dialogowym **Właściwości połączenia.** Wyświetlane wyniki nie zawsze są kompletne.  
  
> [!NOTE]
> Podobnie jak w przypadku większości usług systemu Windows, najlepiej jest uruchomić usługę przeglądarki SQL z jak najmniejszymi uprawnieniami. Zobacz SQL Server Books Online, aby uzyskać więcej informacji na temat usługi przeglądarki SQL i jak zarządzać jej zachowaniem.  
  
## <a name="retrieving-an-enumerator-instance"></a>Pobieranie wystąpienia wyliczenia  
 Aby pobrać tabelę zawierającą informacje o dostępnych wystąpieniach programu SQL Server, należy najpierw pobrać wyliczacz przy użyciu <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości udostępnionej/statycznej:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po pobraniu wystąpienia statycznego można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodę, <xref:System.Data.DataTable> która zwraca zawierające informacje o dostępnych serwerach:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabela zwrócona z wywołania metody zawiera następujące `string` kolumny, z których wszystkie zawierają wartości:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**ServerName**|Nazwa serwera.|  
|**InstanceName**|Nazwa wystąpienia serwera. Puste, jeśli serwer jest uruchomiony jako wystąpienie domyślne.|  
|**Isclustered**|Wskazuje, czy serwer jest częścią klastra.|  
|**Wersja**|Wersja serwera. Przykład:<br /><br /> - 9.00.x (SQL Server 2005)<br />- 10.0.xx (SQL Server 2008)<br />- 10.50.x (SQL Server 2008 R2)<br />- 11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Ograniczenia wyliczenia  
 Wszystkie dostępne serwery mogą być lub nie mogą być wymienione. Lista może się różnić w zależności od czynników, takich jak limity czasu i ruch sieciowy. Może to spowodować, że lista będzie inna w dwóch kolejnych wywołaniach. Zostaną wyświetlone tylko serwery w tej samej sieci. Pakiety emisji zazwyczaj nie przechodzą przez routery, dlatego może nie być widoczny serwer na liście, ale będzie stabilny w połączeniach.  
  
 Wymienione serwery mogą, ale nie `IsClustered` muszą mieć dodatkowych informacji, takich jak i wersja. Zależy to od sposobu uzyskania listy. Serwery wymienione za pośrednictwem usługi przeglądarki SQL Server będą miały więcej szczegółów niż te znalezione za pośrednictwem infrastruktury systemu Windows, która wyświetli tylko nazwę.  
  
> [!NOTE]
> Wyliczenie serwera jest dostępne tylko wtedy, gdy jest uruchomione w pełnym zaufaniu. Zestawy działające w częściowo zaufanym środowisku nie będą mogły go <xref:System.Data.SqlClient.SqlClientPermission> używać, nawet jeśli mają uprawnienie CAS (Code Access Security).  
  
 Program SQL Server <xref:System.Data.Sql.SqlDataSourceEnumerator> udostępnia informacje za pośrednictwem zewnętrznej usługi systemu Windows o nazwie SQL Browser. Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć, co spowoduje, że wystąpienie serwera będzie niewidoczne dla tej klasy.  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja konsoli pobiera informacje o wszystkich widocznych wystąpieniach programu SQL Server i wyświetla informacje w oknie konsoli.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)

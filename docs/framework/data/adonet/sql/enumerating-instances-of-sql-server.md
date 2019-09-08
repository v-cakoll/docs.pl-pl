---
title: Wyliczanie wystąpień programu SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: c464762e82a24aab399a23ecb26420b5dce61f55
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782386"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Wyliczanie wystąpień programu SQL Server (ADO.NET)
SQL Server zezwala aplikacjom na Znajdowanie SQL Server wystąpień w bieżącej sieci. Klasa ujawnia te informacje deweloperowi aplikacji, <xref:System.Data.DataTable> dostarczając zawierające informacje o wszystkich widocznych serwerach. <xref:System.Data.Sql.SqlDataSourceEnumerator> Zwracana tabela zawiera listę wystąpień serwera dostępnych w sieci, które pasują do listy udostępnionej, gdy użytkownik próbuje utworzyć nowe połączenie, a następnie rozwija listę rozwijaną zawierającą wszystkie dostępne serwery we **właściwościach połączenia.** okno dialogowe. Wyświetlane wyniki nie zawsze są kompletne.  
  
> [!NOTE]
> Podobnie jak w przypadku większości usług systemu Windows, najlepszym rozwiązaniem jest uruchomienie usługi SQL Browser z najniższymi możliwymi uprawnieniami. Więcej informacji na temat usługi SQL Browser można znaleźć w dokumentacji SQL Server Books Online oraz jak zarządzać jej zachowaniem.  
  
## <a name="retrieving-an-enumerator-instance"></a>Pobieranie wystąpienia modułu wyliczającego  
 Aby można było pobrać tabelę zawierającą informacje o dostępnych wystąpieniach SQL Server, należy najpierw pobrać moduł wyliczający przy użyciu właściwości Shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po pobraniu wystąpienia statycznego można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodę, która <xref:System.Data.DataTable> zwraca zawierające informacje o dostępnych serwerach:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabela zwrócona przez wywołanie metody zawiera następujące kolumny, z których wszystkie zawierają `string` wartości:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**ServerName**|Nazwa serwera.|  
|**InstanceName**|Nazwa wystąpienia serwera. Puste, jeśli serwer działa jako wystąpienie domyślne.|  
|**Isclusterd**|Wskazuje, czy serwer jest częścią klastra.|  
|**Wersja**|Wersja serwera programu. Na przykład:<br /><br /> -9.00. x (SQL Server 2005)<br />-10.0. XX (SQL Server 2008)<br />-10.50. x (SQL Server 2008 R2)<br />-11.0. XX (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Ograniczenia wyliczania  
 Wszystkie dostępne serwery mogą lub nie mogą być wymienione na liście. Lista może się różnić w zależności od takich czynników, jak limity czasu i ruch sieciowy. Może to spowodować, że lista będzie się różnić między dwoma kolejnymi wywołaniami. Zostaną wyświetlone tylko serwery w tej samej sieci. Pakiety emisji zwykle nie przechodzą na routery, co oznacza, że nie widzisz serwera na liście, ale będzie on stabilny dla wywołań.  
  
 Wymienione serwery mogą lub nie mieć dodatkowych informacji, takich jak `IsClustered` i wersja. Jest to zależne od tego, jak uzyskano listę. Serwery wymienione za pomocą usługi SQL Server Browser będą miały więcej szczegółów niż te, które znajdują się w infrastrukturze systemu Windows, która będzie zawierać tylko nazwę.  
  
> [!NOTE]
> Wyliczenie serwera jest dostępne tylko w przypadku uruchamiania w trybie pełnego zaufania. Zestawy działające w środowisku częściowo zaufanym nie będą mogły ich używać nawet wtedy, gdy mają <xref:System.Data.SqlClient.SqlClientPermission> uprawnienie zabezpieczeń dostępu kodu (CAS).  
  
 SQL Server zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> korzystania z zewnętrznej usługi systemu Windows o nazwie SQL Browser. Ta usługa jest domyślnie włączona, ale Administratorzy mogą ją wyłączyć lub wyłączyć, co sprawia, że wystąpienie serwera jest niewidoczne dla tej klasy.  
  
## <a name="example"></a>Przykład  
 Następująca aplikacja konsolowa pobiera informacje o wszystkich widocznych wystąpieniach SQL Server i wyświetla informacje w oknie konsoli.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [SQL Server i ADO.NET](index.md)
- [Omówienie ADO.NET](../ado-net-overview.md)

---
title: Wyliczanie wystąpień programu SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: d9456926b228fadca940f6c4698829494382e237
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Wyliczanie wystąpień programu SQL Server (ADO.NET)
SQL Server umożliwia aplikacji można znaleźć wystąpień programu SQL Server w ramach bieżącej sieci. <xref:System.Data.Sql.SqlDataSourceEnumerator> Klasy udostępnia te informacje do deweloperów aplikacji, zapewniając <xref:System.Data.DataTable> zawierających informacje dotyczące wszystkich serwerów widoczne. Ta wartość zwracana tabela zawiera listę wystąpień serwera dostępne w sieci, z którą jest zgodne z listą pod warunkiem, gdy użytkownik próbuje utworzyć nowe połączenie i rozwija listy rozwijanej zawierające wszystkie dostępne serwery na **połączenia Właściwości** okno dialogowe. Wyniki wyświetlane nie zawsze są kompletne.  
  
> [!NOTE]
>  Jako większości usługami wdrażania systemu Windows, najlepiej do uruchamiania usługi SQL Browser z najniższe możliwe uprawnienia. Aby uzyskać więcej informacji o usługa SQL Browser i zarządzać jego zachowanie Zobacz SQL Server — książki Online.  
  
## <a name="retrieving-an-enumerator-instance"></a>Pobieranie wystąpienia modułu wyliczającego  
 W celu pobrania tabeli zawierającej informacje o dostępnych wystąpień programu SQL Server, należy najpierw pobrać moduł wyliczający, przy użyciu udostępnionych/statycznych <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po pobraniu statycznego wystąpienia, należy wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metody, która zwraca <xref:System.Data.DataTable> zawierający informacje o dostępnych serwerów:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabela zwracana z wywołania metody, które zawiera następujące kolumny, które zawierają `string` wartości:  
  
|Kolumny|Opis|  
|------------|-----------------|  
|**ServerName**|Nazwa serwera.|  
|**InstanceName**|Nazwa wystąpienia serwera. Puste, jeśli serwer działa jako domyślnego wystąpienia.|  
|**IsClustered**|Wskazuje, czy serwer jest częścią klastra.|  
|**Wersja**|Wersja serwera. Na przykład:<br /><br /> -9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])<br />-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])<br />-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])<br />-11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Ograniczenia — wyliczenie  
 Wszystkie dostępne serwery mogą lub nie mogą być wyświetlane. Lista może się różnić w zależności od czynników, takie jak ruch w sieci i limitów czasu. Może to spowodować listy maja być inne dla dwóch kolejnych wywołań. Zostaną wyświetlone tylko dla serwerów w tej samej sieci. Pakietów emisji zazwyczaj nie przechodzą przez routery, dlatego serwer, na liście mogą nie być widoczne, ale będzie ona stabilna między wywołania.  
  
 Wymienione serwery mogą lub nie ma dodatkowych informacji takich jak `IsClustered` i wersji. Jest to zależne od tego, jak uzyskano listy. Serwery wymienione za pośrednictwem usługi SQL Server browser będą mieć więcej szczegółów niż występujące za pośrednictwem infrastruktury systemu Windows, w którym wyświetlana jest tylko nazwa.  
  
> [!NOTE]
>  Wyliczenie serwera jest dostępna tylko podczas uruchamiania w trybie pełnego zaufania. W środowisku częściowo zaufane zestawy nie będzie mógł jej użyć, nawet jeśli ma <xref:System.Data.SqlClient.SqlClientPermission> uprawnienia zabezpieczeń dostępu kodu (CAS).  
  
 SQL Server zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> za pomocą zewnętrznej usługi systemu Windows o nazwie SQL Browser. Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć tę funkcję ukrywanie wystąpienie serwera do tej klasy.  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji konsoli pobiera informacje o wszystkich wystąpień programu SQL Server widoczne i wyświetla informacje w oknie konsoli.  
  
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
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Wyliczanie wystąpień programu SQL Server (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: d6d76d677bcf7dfa7df632bde8de76401a46db05
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661891"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a>Wyliczanie wystąpień programu SQL Server (ADO.NET)
Program SQL Server zezwala na aplikacji, aby znaleźć wystąpień programu SQL Server w ramach bieżącej sieci. <xref:System.Data.Sql.SqlDataSourceEnumerator> Klasa udostępnia te informacje do deweloperów aplikacji, zapewniając <xref:System.Data.DataTable> zawierające informacje dotyczące wszystkich serwerów widoczne. Ta wartość zwrócona tabela zawiera listę wystąpień serwera dostępne w sieci, z którą jest zgodne z listą udostępniany, gdy użytkownik próbuje utworzyć nowe połączenie, a następnie rozwija listy rozwijanej zawierające wszystkie dostępne serwery na **połączenia Właściwości** okno dialogowe. Wyniki wyświetlane nie zawsze są pełne.  
  
> [!NOTE]
>  W przypadku większości usług Windows jest najlepsze do uruchamiania usługi SQL Browser przy najniższe możliwe uprawnienia. Zobacz dokumentację SQL Server — książki Online, aby uzyskać więcej informacji na temat usługi SQL Browser, a także jak zarządzać jego zachowanie.  
  
## <a name="retrieving-an-enumerator-instance"></a>Pobieranie wystąpienia modułu wyliczającego  
 Aby można było pobrać Tabela zawierająca informacje na temat dostępnych wystąpień programu SQL Server, należy najpierw pobrać moduł wyliczający przy użyciu udostępnionych/statyczne <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> właściwości:  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 Po pobraniu wystąpień statycznych, można wywołać <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metody, która zwraca <xref:System.Data.DataTable> zawierający informacje o dostępnych serwerów:  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 Tabela zwrócony z wywołania metody które zawiera następujące kolumny, które zawierają `string` wartości:  
  
|Kolumna|Opis|  
|------------|-----------------|  
|**ServerName**|Nazwa serwera.|  
|**InstanceName**|Nazwa wystąpienia serwera. Pole puste, jeśli serwer działa jako domyślnego wystąpienia.|  
|**IsClustered**|Wskazuje, czy serwer jest częścią klastra.|  
|**Wersja**|Wersja serwera. Na przykład:<br /><br /> -9.00.x (SQL Server 2005)<br />-   10.0.xx (SQL Server 2008)<br />-10.50.x (SQL Server 2008 R2)<br />-   11.0.xx (SQL Server 2012)|  
  
## <a name="enumeration-limitations"></a>Wyliczenie ograniczeń  
 Wszystkie dostępne serwery mogą lub nie mogą być wyświetlane. Lista może się różnić w zależności od czynników, takich jak przekroczenia limitu czasu i siecią ruchu. Może to spowodować, że na liście, aby różniłaby się w dwóch kolejnych wywołań. Zostaną wyświetlone tylko serwery w tej samej sieci. Pakietów emisji zazwyczaj nie przechodzą przez routery, dlatego nie może zostać wyświetlony serwer, na liście, ale będzie stabilny przez wywołania.  
  
 Wymienione serwery może być lub może nie mieć dodatkowe informacje takie jak `IsClustered` i wersji. To zależy od tego, jak zostały pobrane listy. Serwery wymienione za pośrednictwem usługa przeglądarki SQL Server ma więcej szczegółów niż występujące za pomocą infrastruktury Windows, który wyświetla tylko nazwę.  
  
> [!NOTE]
>  Wyliczenie Server jest dostępna tylko podczas uruchamiania w pełni zaufanym. W środowisku z częściowo zaufanych zestawów nie będzie go obsługują, nawet jeśli mają one <xref:System.Data.SqlClient.SqlClientPermission> uprawnień zabezpieczeń dostępu kodu (CAS).  
  
 Program SQL Server zawiera informacje dotyczące <xref:System.Data.Sql.SqlDataSourceEnumerator> przy użyciu usługi zewnętrznej Windows o nazwie SQL Browser. Ta usługa jest domyślnie włączona, ale administratorzy mogą ją wyłączyć lub wyłączyć tę funkcję ukrywanie wystąpienia serwera do tej klasy.  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji konsoli pobiera informacje o wszystkich widoczne wystąpienia programu SQL Server i wyświetla informacje w oknie konsoli.  
  
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

- [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

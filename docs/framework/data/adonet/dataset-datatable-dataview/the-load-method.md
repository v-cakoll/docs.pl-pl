---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150730"
---
# <a name="the-load-method"></a>Metoda Load
Za pomocą <xref:System.Data.DataTable.Load%2A> metody można <xref:System.Data.DataTable> załadować wiersze z ze źródła danych. Jest to przeciążona metoda, która w najprostszej formie akceptuje pojedynczy parametr, **DataReader**. W tej formie po prostu ładuje **DataTable** z wierszami. Opcjonalnie można określić **parametr LoadOption,** aby kontrolować sposób dodawania danych do **tabeli DataTable**.  
  
 **Parametr LoadOption** jest szczególnie przydatny w przypadkach, gdy **datatable** zawiera już wiersze danych, ponieważ opisuje, jak przychodzące dane ze źródła danych zostaną połączone z danymi już w tabeli. Na przykład **PreserveCurrentValues** (domyślnie) określa, że w przypadkach, gdy wiersz jest oznaczony jako **Dodany** w **Tabeli danych,** wartość **Oryginalna** lub każda kolumna jest ustawiona na zawartość pasującego wiersza ze źródła danych. **Bieżąca** wartość zachowa wartości przypisane po dodaniu wiersza, a **stan wiersza** wiersza zostanie ustawiony na **Zmieniono**.  
  
 W poniższej tabeli przedstawiono krótki opis wartości wyliczenia. <xref:System.Data.LoadOption>  
  
|Wartość LoadOption|Opis|  
|----------------------|-----------------|  
|**Zastąprowrow**|Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli data,** oryginalne **i** **bieżące** wartości każdej kolumny są zastępowane wartościami w wierszu przychodzącym, a właściwość **RowState** jest ustawiona na **Niezmieniona**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **tabeli DataTable,** są dodawane z wartością **RowState** **niezmienioną**.<br /><br /> Ta opcja w efekcie odświeża zawartość **DataTable** tak, aby była zgodna z zawartością źródła danych.|  
|**Zachowajwartości bieżące (domyślnie)**|Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli Data,** **oryginalna** wartość jest ustawiona na zawartość wiersza przychodzącego, a **bieżąca** wartość nie zostanie zmieniona.<br /><br /> Jeśli **stan wiersza** zostanie **dodany** lub **zmodyfikowany,** jest on ustawiony na **Zmodyfikowany**.<br /><br /> Jeśli **stan wiersza** został **usunięty,** pozostaje **usunięty**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **Tabeli danych,** są dodawane, a **stan wiersza** jest ustawiony na **Niezmieniony**.|  
|**UpdateCurrentValues**|Jeśli przychodzące wiersze mają taką samą wartość **PrimaryKey** jak wiersz już w **Tabeli data,** **bieżąca** wartość jest kopiowana do **oryginalnej** wartości, a wartość **Bieżąca** jest następnie ustawiana na zawartość wiersza przychodzącego.<br /><br /> Jeśli **wiersz Stan** w **DataTable** został **dodany**, **RowState** pozostaje **dodany**. W przypadku wierszy oznaczonych jako **Zmodyfikowane** lub **Usunięte** **stan wiersza** jest **modyfikowany**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **Tabeli danych,** są dodawane, a **stan wiersza** jest ustawiony na **Dodano**.|  
  
 W poniższym przykładzie użyto **Load** metody do wyświetlania listy urodzin dla pracowników w bazie danych **Northwind.**  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a>Zobacz też

- [Operowanie na danych w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Omówienie ADO.NET](../ado-net-overview.md)

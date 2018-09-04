---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 21868f808a6d39c935b612f745d720180df2dd73
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507265"
---
# <a name="the-load-method"></a>Metoda Load
Możesz użyć <xref:System.Data.DataTable.Load%2A> metodę, aby załadować <xref:System.Data.DataTable> wierszy ze źródła danych. To jest przeciążona metoda, która w najprostszej postaci przyjmuje jeden parametr **DataReader**. W tym formularzu, po prostu ładuje **DataTable** wierszy. Opcjonalnie można określić **LoadOption** parametru, aby kontrolować, jak dane są dodawane do **DataTable**.  
  
 **LoadOption** parametr jest szczególnie przydatne w przypadkach, gdzie **DataTable** już zawiera wiersze danych, ponieważ opisuje jak przychodzące dane ze źródła danych, które mają zostać połączone z danymi już w tabeli. Na przykład **PreserveCurrentValues** (opcja domyślna) określa, że w przypadku, gdy wiersz jest oznaczony jako **dodano** w **DataTable**, **oryginalnego** wartość lub każda kolumna jest równa zawartości zgodnego wiersza ze źródła danych. **Bieżącego** wartość zachowają wartości przypisane, gdy wiersz został dodany, a **RowState** wiersza zostanie ustawiony na **zmieniono**.  
  
 W poniższej tabeli przedstawiono krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.  
  
|Wartość LoadOption|Opis|  
|----------------------|-----------------|  
|**OverwriteRow**|Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz w już **DataTable**, **oryginalnego** i **bieżącego** wartości każdego z nich kolumny są zastępowane wartości w wierszu przychodzących i **RowState** właściwość jest ustawiona na **Unchanged**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane przy użyciu **RowState** wartość **Unchanged**.<br /><br /> Ta opcja w praktyce Odświeża zawartość **DataTable** tak, aby pasuje do zawartości ze źródłem danych.|  
|**PreserveCurrentValues (ustawienie domyślne)**|Jeśli przychodzący mają takie same **PrimaryKey** wartość jako wiersz już w **DataTable**, **oryginalnego** wartość zostanie ustawiona na zawartość wiersza przychodzących i **Bieżącego** wartość nie ulega zmianie.<br /><br /> Jeśli **RowState** jest **dodano** lub **zmodyfikowane**, jest równa **zmodyfikowane**.<br /><br /> Jeśli **RowState** został **usunięte**, pozostaje **usunięte**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Unchanged**.|  
|**UpdateCurrentValues**|Jeśli przychodzący mają takie same **PrimaryKey** wartość jako wiersz już w **DataTable**, **bieżącego** wartość jest kopiowany do **oryginalny**wartości, a **bieżącego** następnie wartość na zawartość wiersza przychodzących.<br /><br /> Jeśli **RowState** w **DataTable** został **dodano**, **RowState** pozostaje **dodano**. Dla wierszy oznaczone jako **zmodyfikowane** lub **usunięte**, **RowState** jest **zmodyfikowane**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **dodano**.|  
  
 Następujące przykładowe używa **obciążenia** metodę, aby wyświetlić listę dat urodzenia dla pracowników w **Northwind** bazy danych.  
  
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
 [Operowanie danymi w elemencie DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: Metoda Load
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e6c6ce0b722d901e38b728a710e3c49848fb918a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="the-load-method"></a>Metoda Load
Można użyć <xref:System.Data.DataTable.Load%2A> metodę, aby załadować <xref:System.Data.DataTable> z wierszy ze źródła danych. To jest przeciążona metoda, która w swojej najprostszej formie przyjmuje jeden parametr, **DataReader**. W tym formularzu, po prostu ładuje **DataTable** z wierszami. Opcjonalnie można określić **LoadOption** parametr, aby kontrolować sposób dodawania danych do **DataTable**.  
  
 **LoadOption** parametr jest szczególnie przydatne w sytuacjach, gdy **DataTable** już zawiera wiersze danych, ponieważ opisuje sposób przychodzących danych ze źródła danych zostaną połączone z danymi już w tabeli. Na przykład **PreserveCurrentValues** (opcja domyślna) określa, że w przypadku, gdy wiersz jest oznaczony jako **Added** w **DataTable**, **oryginalne** wartość lub każdej kolumny ustawiono zawartość pasującego wiersza ze źródła danych. **Bieżącego** wartości zostaną zachowane wartości przypisane, gdy wiersz został dodany i **RowState** wiersza zostanie ustawiona do **zmienione**.  
  
 W poniższej tabeli przedstawiono krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.  
  
|Wartość LoadOption|Opis|  
|----------------------|-----------------|  
|**OverwriteRow**|Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **oryginalnego** i **bieżącego** wartości każdego z nich kolumny są zamieniane na wartości w wierszu przychodzące i **RowState** właściwość jest ustawiona na **Unchanged**.<br /><br /> Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane z **RowState** wartość **Unchanged**.<br /><br /> Ta opcja skutkuje Odświeża zawartość **DataTable** tak, aby było zgodne zawartość źródła danych.|  
|**PreserveCurrentValues (ustawienie domyślne)**|Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **oryginalnego** wartość jest ustawiona na zawartość wiersza przychodzące i **Bieżącego** wartość nie ulega zmianie.<br /><br /> Jeśli **RowState** jest **Added** lub **zmodyfikowane**, jest równa **zmodyfikowane**.<br /><br /> Jeśli **RowState** został **usunięte**, pozostaje **usunięte**.<br /><br /> Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Unchanged**.|  
|**UpdateCurrentValues**|Jeśli przychodzące mają takie same **PrimaryKey** wartość jako wiersz już **DataTable**, **bieżącego** wartość jest kopiowany do **oryginalne**wartości i **bieżącego** następnie ustawiono wartość zawartości wiersza przychodzących.<br /><br /> Jeśli **RowState** w **DataTable** został **Added**, **RowState** pozostaje **Added**. Do wierszy oznaczony jako **zmodyfikowane** lub **usunięte**, **RowState** jest **zmodyfikowane**.<br /><br /> Wierszy ze źródła danych, które jeszcze nie istnieją w **DataTable** są dodawane i **RowState** ustawiono **Added**.|  
  
 Następujące przykładowe używa **obciążenia** metodę, aby wyświetlić listę dat urodzenia pracowników **Northwind** bazy danych.  
  
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
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

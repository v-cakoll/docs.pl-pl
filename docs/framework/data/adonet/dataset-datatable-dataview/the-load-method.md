---
title: Metoda Load
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: da0695aff9447355b1fc44a033c1b4a1cc224435
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785882"
---
# <a name="the-load-method"></a>Metoda Load
Możesz użyć <xref:System.Data.DataTable.Load%2A> metody do <xref:System.Data.DataTable> załadowania z wierszami ze źródła danych. Jest to przeciążona metoda, która w najprostszej postaci akceptuje pojedynczy parametr, element **DataReader**. W tym formularzu po prostu ładuje **DataTable** z wierszami. Opcjonalnie można określić parametr **LoadOption** , aby kontrolować sposób dodawania danych do obiektu **DataTable**.  
  
 Parametr **LoadOption** jest szczególnie przydatny w przypadkach, gdy element **DataTable** zawiera już wiersze danych, ponieważ opisuje sposób, w jaki dane przychodzące ze źródła danych będą łączone z danymi znajdującymi się już w tabeli. Na przykład **PreserveCurrentValues** (wartość domyślna) określa, że w przypadkach, gdy wiersz jest oznaczony jako **dodany** w **tabeli DataTable**, **oryginalna** wartość lub każda kolumna jest ustawiona na zawartość pasującego wiersza ze źródła danych. **Bieżąca** wartość spowoduje zachowanie wartości przypisanych, gdy wiersz został dodany, a **RowState** wierszy zostanie ustawiona na wartość **zmienione**.  
  
 Poniższa tabela zawiera krótki opis <xref:System.Data.LoadOption> wartości wyliczenia.  
  
|LoadOption wartość|Opis|  
|----------------------|-----------------|  
|**OverwriteRow**|Jeśli wiersze przychodzące mają tę samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **pierwotne** i **bieżące** wartości każdej kolumny są zastępowane wartościami w wierszu przychodzące, a właściwość **RowState** jest ustawiona na **Bez zmian**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w tabeli **DataTable** , są dodawane z **niezmienionym**wartością **RowState** .<br /><br /> Ta opcja powoduje odświeżenie zawartości **elementu DataTable** tak, aby odpowiadał zawartości źródła danych.|  
|**PreserveCurrentValues (domyślnie)**|Jeśli wiersze przychodzące mają taką samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **oryginalna** wartość jest ustawiana na zawartość wiersza przychodzącego, a **Bieżąca** wartość nie jest zmieniana.<br /><br /> Jeśli **RowState** jest **dodawany** lub **modyfikowany**, jest ustawiony na wartość **zmodyfikowano**.<br /><br /> Jeśli **RowState** został **usunięty**, pozostanie **usunięty**.<br /><br /> Wiersze ze źródła danych, które jeszcze nie istnieją w tabeli **DataTable** , są dodawane, a **RowState** jest ustawiona na wartość **Unchanged**.|  
|**UpdateCurrentValues**|Jeśli wiersze przychodzące mają tę samą wartość **PrimaryKey** jak wiersz już w **tabeli DataTable**, **Bieżąca** wartość jest kopiowana do **pierwotnej** wartości, a **Bieżąca** wartość jest ustawiana na zawartość wiersza przychodzącego.<br /><br /> Jeśli **RowState** w **elemencie DataTable** został **dodany**, **RowState** zostanie **dodana**. W przypadku wierszy oznaczonych jako **zmodyfikowane** lub usunięte **RowState** jest **modyfikowany**.<br /><br /> Wiersze ze źródła danych, które nie znajdują się jeszcze w **elemencie DataTable** , są dodawane i **RowState** jest ustawiony na wartość **dodana**.|  
  
 Poniższy przykład używa metody **Load** do wyświetlania listy urodzin dla pracowników w bazie danych **Northwind** .  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Operowanie danymi w elemencie DataTable](manipulating-data-in-a-datatable.md)
- [Omówienie ADO.NET](../ado-net-overview.md)

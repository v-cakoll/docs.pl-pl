---
title: Wstawianie obrazu z pliku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.openlocfilehash: d47f5b7eaf6b5f6a3174982e6b4cf43859c031a5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794151"
---
# <a name="inserting-an-image-from-a-file"></a>Wstawianie obrazu z pliku
Można napisać obiekt binarny (BLOB) do bazy danych jako dane binarne lub znakowe, w zależności od typu pola w źródle danych. Obiekt BLOB to ogólny termin, który odwołuje `text`się `ntext`do typów `image` danych,, i, które zwykle zawierają dokumenty i obrazy.  
  
 Aby zapisać wartość obiektu BLOB do bazy danych, należy wydać odpowiednią instrukcję INSERT lub UPDATE i przekazać wartość obiektu BLOB jako parametr wejściowy (zobacz [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)). Jeśli obiekt BLOB jest przechowywany jako tekst, na przykład pole SQL Server `text` , można przekazać obiekt BLOB jako parametr ciągu. Jeśli obiekt BLOB jest przechowywany w formacie binarnym, takim jak SQL Server `image` pole, można przekazać tablicę typu `byte` jako parametr binarny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu dodaje informacje o pracowniku do tabeli Employees w bazie danych Northwind. Zdjęcie pracownika jest odczytywane z pliku i dodawane do pola zdjęcia w tabeli, czyli pola obrazu.  
  
```vb  
Public Shared Sub AddEmployee( _  
  lastName As String, _  
  firstName As String, _  
  title As String, _  
  hireDate As DateTime, _  
  reportsTo As Integer, _  
  photoFilePath As String, _  
  connectionString As String)  
  
  Dim photo() as Byte = GetPhoto(photoFilePath)  
  
  Using connection As SqlConnection = New SqlConnection( _  
    connectionString)  
  
  Dim command As SqlCommand = New SqlCommand( _  
    "INSERT INTO Employees (LastName, FirstName, Title, " & _  
    "HireDate, ReportsTo, Photo) " & _  
    "Values(@LastName, @FirstName, @Title, " & _  
    "@HireDate, @ReportsTo, @Photo)", connection)   
  
  command.Parameters.Add("@LastName",  _  
    SqlDbType.NVarChar, 20).Value = lastName  
  command.Parameters.Add("@FirstName", _  
    SqlDbType.NVarChar, 10).Value = firstName  
  command.Parameters.Add("@Title", _  
    SqlDbType.NVarChar, 30).Value = title  
  command.Parameters.Add("@HireDate", _  
    SqlDbType.DateTime).Value = hireDate  
  command.Parameters.Add("@ReportsTo", _  
    SqlDbType.Int).Value = reportsTo  
  
  command.Parameters.Add("@Photo", _  
    SqlDbType.Image, photo.Length).Value = photo  
  
  connection.Open()  
  command.ExecuteNonQuery()  
  
  End Using  
End Sub  
  
Public Shared Function GetPhoto(filePath As String) As Byte()  
  Dim stream As FileStream = new FileStream( _  
     filePath, FileMode.Open, FileAccess.Read)  
  Dim reader As BinaryReader = new BinaryReader(stream)  
  
  Dim photo() As Byte = reader.ReadBytes(stream.Length)  
  
  reader.Close()  
  stream.Close()  
  
  Return photo  
End Function  
```  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="see-also"></a>Zobacz także

- [Używanie poleceń do modyfikacji danych](../using-commands-to-modify-data.md)
- [Pobieranie danych binarnych](../retrieving-binary-data.md)
- [Dane binarne i dużej wartości w programie SQL Server](sql-server-binary-and-large-value-data.md)
- [Mapowanie typu danych serwera SQL](../sql-server-data-type-mappings.md)
- [Omówienie ADO.NET](../ado-net-overview.md)

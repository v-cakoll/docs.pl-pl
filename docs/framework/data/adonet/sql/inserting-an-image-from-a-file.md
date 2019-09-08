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
# <a name="inserting-an-image-from-a-file"></a><span data-ttu-id="d015a-102">Wstawianie obrazu z pliku</span><span class="sxs-lookup"><span data-stu-id="d015a-102">Inserting an Image from a File</span></span>
<span data-ttu-id="d015a-103">Można napisać obiekt binarny (BLOB) do bazy danych jako dane binarne lub znakowe, w zależności od typu pola w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d015a-103">You can write a binary large object (BLOB) to a database as either binary or character data, depending on the type of field at your data source.</span></span> <span data-ttu-id="d015a-104">Obiekt BLOB to ogólny termin, który odwołuje `text`się `ntext`do typów `image` danych,, i, które zwykle zawierają dokumenty i obrazy.</span><span class="sxs-lookup"><span data-stu-id="d015a-104">BLOB is a generic term that refers to the `text`, `ntext`, and `image` data types, which typically contain documents and pictures.</span></span>  
  
 <span data-ttu-id="d015a-105">Aby zapisać wartość obiektu BLOB do bazy danych, należy wydać odpowiednią instrukcję INSERT lub UPDATE i przekazać wartość obiektu BLOB jako parametr wejściowy (zobacz [Konfigurowanie parametrów i typów danych parametrów](../configuring-parameters-and-parameter-data-types.md)).</span><span class="sxs-lookup"><span data-stu-id="d015a-105">To write a BLOB value to your database, issue the appropriate INSERT or UPDATE statement and pass the BLOB value as an input parameter (see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md)).</span></span> <span data-ttu-id="d015a-106">Jeśli obiekt BLOB jest przechowywany jako tekst, na przykład pole SQL Server `text` , można przekazać obiekt BLOB jako parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="d015a-106">If your BLOB is stored as text, such as a SQL Server `text` field, you can pass the BLOB as a string parameter.</span></span> <span data-ttu-id="d015a-107">Jeśli obiekt BLOB jest przechowywany w formacie binarnym, takim jak SQL Server `image` pole, można przekazać tablicę typu `byte` jako parametr binarny.</span><span class="sxs-lookup"><span data-stu-id="d015a-107">If the BLOB is stored in binary format, such as a SQL Server `image` field, you can pass an array of type `byte` as a binary parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d015a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d015a-108">Example</span></span>  
 <span data-ttu-id="d015a-109">Poniższy przykład kodu dodaje informacje o pracowniku do tabeli Employees w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="d015a-109">The following code example adds employee information to the Employees table in the Northwind database.</span></span> <span data-ttu-id="d015a-110">Zdjęcie pracownika jest odczytywane z pliku i dodawane do pola zdjęcia w tabeli, czyli pola obrazu.</span><span class="sxs-lookup"><span data-stu-id="d015a-110">A photo of the employee is read from a file and added to the Photo field in the table, which is an image field.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d015a-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d015a-111">See also</span></span>

- [<span data-ttu-id="d015a-112">Używanie poleceń do modyfikacji danych</span><span class="sxs-lookup"><span data-stu-id="d015a-112">Using Commands to Modify Data</span></span>](../using-commands-to-modify-data.md)
- [<span data-ttu-id="d015a-113">Pobieranie danych binarnych</span><span class="sxs-lookup"><span data-stu-id="d015a-113">Retrieving Binary Data</span></span>](../retrieving-binary-data.md)
- [<span data-ttu-id="d015a-114">Dane binarne i dużej wartości w programie SQL Server</span><span class="sxs-lookup"><span data-stu-id="d015a-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="d015a-115">Mapowanie typu danych serwera SQL</span><span class="sxs-lookup"><span data-stu-id="d015a-115">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d015a-116">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d015a-116">ADO.NET Overview</span></span>](../ado-net-overview.md)

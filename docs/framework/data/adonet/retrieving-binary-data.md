---
title: Podczas pobierania danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 302c26571e9843a4b7c3c440969e4159ef2d10ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362579"
---
# <a name="retrieving-binary-data"></a>Podczas pobierania danych binarnych
Domyślnie **DataReader** ładuje dane przychodzące jako wiersz, jak cały wiersz danych jest dostępna. Duże obiekty binarne (BLOB) wymagają innego podejścia, jednak ponieważ zawierają one GB danych, które nie mogą wchodzić w jednym wierszu. **Command.ExecuteReader** metoda ma przeciążenia, które będą wymaga <xref:System.Data.CommandBehavior> argumentu, aby zmodyfikować domyślne zachowanie **DataReader**. Można przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do **ExecuteReader** metodę, aby zmodyfikować domyślne zachowanie **DataReader** tak, aby zamiast ładowania wierszy danych, jego ładowanie danych sekwencyjnie odbierane. Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub inne struktury dużej ilości danych. Należy pamiętać, że takie zachowanie może zależeć od źródła danych. Na przykład zwracać obiekt BLOB z programu Microsoft Access załaduje całego obiektu BLOB ładowany do pamięci, a nie po kolei odbierane.  
  
 Podczas ustawiania **DataReader** do używania **SequentialAccess**, ważne jest, aby Zanotuj sekwencję dostęp pola zwracane. Domyślne zachowanie **DataReader**, który ładuje cały wiersz, jak jest dostępna, pozwala na dostęp pola zwrócona w dowolnej kolejności, dopóki nie jest do odczytu następnego wiersza. Korzystając z **SequentialAccess** musi jednak dostęp do pola zwrócony przez **DataReader** w kolejności. Na przykład jeśli zapytanie zwraca trzy kolumny, trzecia jest obiektem BLOB, musi zwracać wartości pól pierwszego i drugiego przed uzyskaniem dostępu do danych obiektów BLOB w trzecim polu. Jeśli dostęp do trzecim polu przed pierwszym lub drugim pól wartości pól pierwszego i drugiego nie będą dostępne. Jest to spowodowane **SequentialAccess** został zmodyfikowany **DataReader** zwrócić dane w sekwencji i dane nie są dostępne po **DataReader** ma odczytu poza go.  
  
 Podczas uzyskiwania dostępu do danych w polu obiektów BLOB, użyj **GetBytes** lub **GetChars** wpisane metod dostępu **DataReader**, który wypełnił tablicy z danymi. Można również użyć **GetString** danych znakowych; jednak. Aby oszczędzać zasoby systemu nie można załadować całą wartość obiektu BLOB do zmiennej będący pojedynczym ciągiem. Zamiast tego można określić rozmiar buforu określonych danych do zwrócenia i początkową lokalizację pierwszego bajtu lub znaków do odczytu zwróconych danych. **GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę bajtów lub znaki zwrócone. W przypadku przekazania tablicy o wartości null do **GetBytes** lub **GetChars**, długo wartość zwracana będzie całkowitą liczbę bajtów lub znaków w obiekcie BLOB. Opcjonalnie można określić indeks w tablicy jako pozycja początkowa dla odczytywane dane.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca identyfikator wydawcy i logo z **pubs** przykładową bazą danych programu Microsoft SQL Server. Identyfikator wydawcy (`pub_id`) jest polem znaku i logo to obraz, który jest obiektem BLOB. Ponieważ **logo** pole jest mapą bitową, przykładzie zwraca dane binarne przy użyciu **GetBytes**. Zwróć uwagę, że identyfikator wydawcy jest dostępne dla bieżącego wiersza danych przed logo, ponieważ pola muszą być dostępne po kolei.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z DataReaders](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Dane binarne i dużej wartości w programie SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)

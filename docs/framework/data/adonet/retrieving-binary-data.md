---
title: Pobieranie danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 9acda6631e17031a81ba06d9530739a586fac7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794434"
---
# <a name="retrieving-binary-data"></a>Pobieranie danych binarnych
Domyślnie element **DataReader** ładuje dane przychodzące jako wiersz zaraz po udostępnieniu całego wiersza danych. Duże obiekty binarne (BLOB) wymagają innej obróbki, ale mogą zawierać gigabajty danych, które nie mogą być zawarte w pojedynczym wierszu. Metoda **Command. ExecuteReader** ma Przeciążenie, które będzie miało <xref:System.Data.CommandBehavior> argument modyfikujący domyślne zachowanie elementu **DataReader**. Można przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do metody **ExecuteReader** , aby zmodyfikować domyślne zachowanie elementu **DataReader** , tak aby zamiast ładowania wierszy danych dane były ładowane sekwencyjnie po ich odebraniu. Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub innych dużych struktur danych. Należy zauważyć, że to zachowanie może zależeć od źródła danych. Na przykład zwrócenie obiektu BLOB z programu Microsoft Access spowoduje załadowanie całego obiektu BLOB, który jest ładowany do pamięci, a nie sekwencyjnie po odebraniu.  
  
 Podczas ustawiania elementu **DataReader** do korzystania z **SequentialAccess**należy zwrócić uwagę na sekwencję, do której uzyskuje się dostęp do zwracanych pól. Domyślne zachowanie elementu **DataReader**, który ładuje cały wiersz zaraz po jego udostępnieniu, umożliwia dostęp do pól zwracanych w dowolnej kolejności do momentu odczytania następnego wiersza. W przypadku korzystania z **SequentialAccess** należy jednak uzyskać dostęp do pól zwracanych przez element **DataReader** w kolejności. Na przykład, jeśli zapytanie zwróci trzy kolumny, trzecią, z której jest obiektem BLOB, należy zwrócić wartości pierwszego i drugiego pola przed uzyskaniem dostępu do danych obiektu BLOB w trzecim polu. Jeśli uzyskujesz dostęp do trzeciego pola przed pierwszym lub drugim polem, wartości pierwszego i drugiego pola nie będą już dostępne. Wynika to z faktu, że program **SequentialAccess** zmodyfikował element **DataReader** , aby zwracał dane w sekwencji, a dane nie są dostępne, gdy element **DataReader** zakończył jego poprzednią wartość.  
  
 Podczas uzyskiwania dostępu do danych w polu obiekt BLOB należy użyć typu metody dostępu **GetBytes** lub **GetChars** elementu **DataReader**, który wypełnia tablicę danymi. Można również użyć **GetString** dla danych znakowych; ale. Aby zaoszczędzić zasoby systemowe, możesz nie chcieć załadować całej wartości obiektu BLOB do pojedynczej zmiennej ciągu. Zamiast tego można określić określony rozmiar buforu danych do zwrócenia oraz lokalizację początkową dla pierwszego bajtu lub znaku, który ma zostać odczytany z zwracanych danych. **GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę zwracanych bajtów lub znaków. Jeśli przejdziesz tablicę o wartości null do **GetBytes** lub **GetChars**, zwrócona wartość Long będzie całkowitą liczbą bajtów lub znaków w obiekcie blob. Opcjonalnie można określić indeks w tablicy jako pozycję początkową dla odczytywanych danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca identyfikator wydawcy i logo z przykładowej bazy danych **pubs** w Microsoft SQL Server. Identyfikator wydawcy (`pub_id`) to pole znaku, a logo jest obrazem, który jest obiektem BLOB. Ponieważ pole **logo** jest mapą bitową, przykład zwraca dane binarne przy użyciu **GetBytes**. Zwróć uwagę, że identyfikator wydawcy jest dostępny dla bieżącego wiersza danych przed logo, ponieważ pola muszą być dostępne sekwencyjnie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dane binarne i dużej wartości w programie SQL Server](./sql/sql-server-binary-and-large-value-data.md)
- [Omówienie ADO.NET](ado-net-overview.md)

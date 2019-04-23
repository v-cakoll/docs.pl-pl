---
title: Pobieranie danych binarnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
ms.openlocfilehash: 068b84e8704b54e6aea148ec5fc5bf9f0c4cb958
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085977"
---
# <a name="retrieving-binary-data"></a>Pobieranie danych binarnych
Domyślnie **DataReader** ładuje przychodzących danych jako wiersz, jak tylko cały wiersz danych jest dostępna. Duże obiekty binarne (BLOB) muszą jednak różnego traktowania, ponieważ zawierają one gigabajtów danych, który nie może się znajdować w jednym wierszu. **Command.ExecuteReader** metoda ma przeciążenia, które będą miały <xref:System.Data.CommandBehavior> argumentu, aby zmodyfikować domyślne zachowanie **DataReader**. Możesz przekazać <xref:System.Data.CommandBehavior.SequentialAccess> do **ExecuteReader** metodę, aby zmodyfikować domyślne zachowanie **DataReader** tak, aby zamiast ładowania wierszy danych, będzie on ładować dane sekwencyjnie po otrzymaniu. Jest to idealne rozwiązanie w przypadku ładowania obiektów blob lub innych struktur dużych ilości danych. Należy pamiętać, że takie zachowanie może zależeć od źródła danych. Na przykład zwracając obiekt BLOB z programu Microsoft Access załaduje cały obiekt BLOB ładowany do pamięci, a nie po kolei, gdy są odbierane.  
  
 Podczas ustawiania **DataReader** używać **SequentialAccess**, należy zauważyć kolejność, w którym uzyskujesz dostęp do pola, zwracany jest. Domyślne zachowanie **DataReader**, który ładuje cały wiersz, jak jest dostępna, umożliwia dostęp do pola, zwracany w dowolnej kolejności, dopóki nie jest do odczytu następnego wiersza. Korzystając z **SequentialAccess** musi jednak dostęp do pola, zwracany przez **DataReader** w kolejności. Na przykład jeśli zapytanie zwraca trzy kolumny, w trzeciej jest obiektem BLOB, przed uzyskaniem dostępu do danych obiektów BLOB w trzecim polu musi zwracać wartości pól pierwszego i drugiego. Jeśli uzyskujesz dostęp do trzecim polu przed pola pierwszej lub drugiej, wartości pierwszego i drugiego pola nie są już dostępne. Jest to spowodowane **SequentialAccess** zmodyfikował **DataReader** zwrócić dane w kolejności i dane nie są dostępne po **DataReader** zapoznał się poza jej.  
  
 Podczas uzyskiwania dostępu do danych w polu obiektów BLOB, użyj **GetBytes** lub **GetChars** wpisane metod dostępu **DataReader**, który Wypełnij tablicę przy użyciu danych. Można również użyć **GetString —** danych znakowych; jednak. pozwala zaoszczędzić zasoby systemowe nie można załadować całą wartość obiektu BLOB do zmiennej pojedynczy ciąg. Zamiast tego można określić rozmiar buforu określone dane zwracane i początkową lokalizację pierwszego bajtu lub znaków do odczytu zwracanych danych. **GetBytes** i **GetChars** zwróci `long` wartość, która reprezentuje liczbę bajtów lub znaków, zwracane. W przypadku przekazania tablicę o wartości null do **GetBytes** lub **GetChars**, długa wartość zwracana będzie całkowita liczba bajtów lub znaków w obiekcie BLOB. Opcjonalnie możesz określić indeks w tablicy jako pozycja początkowa odczytywanych danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca identyfikator wydawcy i logo z **pubs** przykładowej bazy danych w programie Microsoft SQL Server. Identyfikator wydawcy (`pub_id`) jest polem znak i logo obraz, który jest obiektem BLOB. Ponieważ **logo** pole jest mapy bitowej, w przykładzie zwracany jest przy użyciu danych binarnych **GetBytes**. Należy zauważyć, że identyfikator wydawcy jest dostępne dla bieżącego wiersza danych przed logo, ponieważ pola, które muszą być dostępne po kolei.  
  
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

- [Dane binarne i dużej wartości w programie SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)

---
title: 'Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: b1e9033d7aba8b4f423f29cd4fb4f7efbbe17a29
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624361"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)
W tym przykładzie odczytuje dane obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
## <a name="example"></a>Przykład  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Nazwa pliku "c:\temp\SerializationOverview.xml" należy zastąpić nazwę pliku zawierającego dane serializowane. Aby uzyskać więcej informacji na temat serializowania danych zobacz [jak: Zapisywania obiektów danych do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Klasa musi mieć publicznego konstruktora bez parametrów.  
  
 Tylko właściwości publiczne i pola są deserializacji.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.  
  
- Dane w pliku nie reprezentuje dane z klasy, która ma zostać przeprowadzona.  
  
- Plik nie istnieje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze sprawdzić dane wejściowe i nigdy nie deserializowanie danych z niezaufanego źródła. Ponownie utworzyć obiekt działa na komputerze lokalnym z uprawnieniami kod, który deserializacji go. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Instrukcje: Zapisywania obiektów danych do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)

---
title: 'Porady: odczytywanie danych o obiektach z pliku XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: 7097ec146987aea7855da40dd30f9cd3c17d8ce4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413170"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)
Ten przykład odczytuje dane obiektu, które wcześniej Zapisano do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego serializowane dane. Aby uzyskać więcej informacji na temat serializowania danych, zobacz [How to: Write dane obiektu do pliku XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).  
  
 Klasa musi mieć Konstruktor publiczny bez parametrów.  
  
 Tylko publiczne właściwości i pola są deserializowane.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Serializowana Klasa nie ma publicznego konstruktora bez parametrów.  
  
- Dane w pliku nie reprezentują danych z klasy, która ma zostać poddana deserializacji.  
  
- Plik nie istnieje ( <xref:System.IO.IOException> ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze Weryfikuj dane wejściowe i nigdy nie wykonuj deserializacji danych z niezaufanego źródła. Nowo utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który został deserializowany. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- [Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)
- [Serializacja (Visual Basic)](index.md)
- [Przewodnik programowania w Visual Basic](../../index.md)

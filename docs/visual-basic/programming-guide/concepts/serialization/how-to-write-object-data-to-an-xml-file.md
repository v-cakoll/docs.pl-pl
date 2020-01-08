---
title: 'Porady: wpisywanie danych o obiektach do pliku XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 989920709428f0e9cb4ddb8aeacfc71a2df220d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345975"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)
Ten przykład zapisuje obiekt z klasy do pliku XML przy użyciu klasy <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Przykład  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Klasa musi mieć Konstruktor publiczny bez parametrów.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Serializowana Klasa nie ma publicznego konstruktora bez parametrów.  
  
- Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).  
  
- Dysk jest pełny (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia. Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` dostęp do pojedynczego pliku, a nie `Create` dostępu do folderu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)

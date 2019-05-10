---
title: 'Instrukcje: Zapisywania obiektów danych do pliku XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 17f8463a4b905028d37a2e005562867f87f4bd2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624375"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Instrukcje: Zapisywania obiektów danych do pliku XML (Visual Basic)
Ten przykład Przepisuje obiekt z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Klasa musi mieć publicznego konstruktora bez parametrów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.  
  
- Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
- Dysk jest pełny (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` dostępu, mniejsze uprawnienia. Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` dostępu do pojedynczego pliku, zamiast `Create` dostępu do folderu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Instrukcje: Odczytywanie danych o obiektach z pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)

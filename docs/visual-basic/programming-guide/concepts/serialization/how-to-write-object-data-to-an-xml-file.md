---
title: 'Porady: wpisywanie danych o obiektach do pliku XML'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 9608a48cb8b3fac1c71affa7a0a17e9789f94b18
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413157"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Instrukcje: zapisywanie danych obiektu w pliku XML (Visual Basic)
Ten przykład zapisuje obiekt z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
  
## <a name="compile-the-code"></a>Kompiluj kod  
 Klasa musi mieć Konstruktor publiczny bez parametrów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Serializowana Klasa nie ma publicznego konstruktora bez parametrów.  
  
- Plik istnieje i jest tylko do odczytu ( <xref:System.IO.IOException> ).  
  
- Ścieżka jest za długa ( <xref:System.IO.PathTooLongException> ).  
  
- Dysk jest pełny ( <xref:System.IO.IOException> ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, aplikacja musi `Create` mieć dostęp do tego folderu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` dostępu, ale ma mniejsze uprawnienia. Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie `Read` dostępu do pojedynczego pliku, a nie `Create` dostęp do folderu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- [Instrukcje: odczytywanie danych obiektu z pliku XML (Visual Basic)](how-to-read-object-data-from-an-xml-file.md)
- [Serializacja (Visual Basic)](index.md)

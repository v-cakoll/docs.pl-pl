---
title: 'Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df461f9b560dac45add0d7c82ff4938b0a7b1e62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)
W tym przykładzie zapisuje obiekt z klasy w pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
  
-   Klasa poddany serializacji ma publicznego konstruktora bez parametrów.  
  
-   Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
-   Ścieżka jest za długa (<xref:System.IO.PathTooLongException>).  
  
-   Dysk jest pełny (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 [Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)

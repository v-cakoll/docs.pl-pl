---
title: 'Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Porady: odczytywanie danych o obiektach z pliku XML (Visual Basic)
Ten przykład odczytuje danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
 Zamień na nazwę pliku zawierającego dane serializowane nazwa pliku "c:\temp\SerializationOverview.xml". Aby uzyskać więcej informacji na temat serializacja danych, zobacz [porady: zapis danych obiektów do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Klasa musi mieć publicznego konstruktora bez parametrów.  
  
 Rozszeregować są tylko właściwości publiczne i pola.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Klasa poddany serializacji ma publicznego konstruktora bez parametrów.  
  
-   Dane w pliku nie reprezentuje dane z klasy do zdeserializowania.  
  
-   Plik nie istnieje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze Sprawdź dane wejściowe i nigdy nie deserializować danych z niezaufanego źródła. Uruchamia ponownie utworzyć obiekt na komputerze lokalnym przy użyciu uprawnień kodu, który go deserializacji. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 [Porady: wpisywanie danych o obiektach do pliku XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)

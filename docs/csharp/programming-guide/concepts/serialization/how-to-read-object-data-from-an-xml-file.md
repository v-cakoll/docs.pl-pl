---
title: 'Porady: odczytywanie danych o obiektach z pliku XML (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6a3389de2f3272a546a7380ef386f5d88666e6d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Porady: odczytywanie danych o obiektach z pliku XML (C#)
Ten przykład odczytuje danych obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
## <a name="example"></a>Przykład  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zamień na nazwę pliku zawierającego dane serializowane nazwa pliku "c:\temp\SerializationOverview.xml". Aby uzyskać więcej informacji na temat serializacja danych, zobacz [porady: zapis danych obiektów do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
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
 [Porady: wpisywanie danych o obiektach do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [Serializacja (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)

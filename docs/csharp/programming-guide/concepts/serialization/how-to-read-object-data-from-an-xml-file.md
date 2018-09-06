---
title: 'Porady: odczytywanie danych o obiektach z pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 7c3bad56c6a0bee51262586aea4ce97ff0491f24
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872121"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Porady: odczytywanie danych o obiektach z pliku XML (C#)
W tym przykładzie odczytuje dane obiektów, które zostały wcześniej zapisane do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
 Nazwa pliku "c:\temp\SerializationOverview.xml" należy zastąpić nazwę pliku zawierającego dane serializowane. Aby uzyskać więcej informacji na temat serializowania danych zobacz [porady: zapis danych obiektu, do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 Klasa musi mieć publicznego konstruktora bez parametrów.  
  
 Tylko właściwości publiczne i pola są deserializacji.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.  
  
-   Dane w pliku nie reprezentuje dane z klasy, która ma zostać przeprowadzona.  
  
-   Plik nie istnieje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze sprawdzić dane wejściowe i nigdy nie deserializowanie danych z niezaufanego źródła. Ponownie utworzyć obiekt działa na komputerze lokalnym z uprawnieniami kod, który deserializacji go. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>  
- [Porady: zapis danych obiektu do pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
- [Serializacja (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)  
- [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)

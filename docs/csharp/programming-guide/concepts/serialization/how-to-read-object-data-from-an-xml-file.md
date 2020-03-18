---
title: Jak odczytywać dane obiektu z pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167821"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Jak odczytywać dane obiektu z pliku XML (C#)
W tym przykładzie odczytuje dane obiektu, który <xref:System.Xml.Serialization.XmlSerializer> został wcześniej zapisany do pliku XML przy użyciu klasy.  
  
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
Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego dane serializowane. Aby uzyskać więcej informacji na temat serializacji danych, zobacz [Jak zapisywać dane obiektów w pliku XML (C#).](./how-to-write-object-data-to-an-xml-file.md)
  
 Klasa musi mieć konstruktora publicznego bez parametrów.  
  
 Deserializowane są tylko właściwości i pola publiczne.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Klasa serializacji nie ma konstruktora publicznego, bezparametrów.  
  
- Dane w pliku nie reprezentują danych z klasy, która ma zostać zdeserializowana.  
  
- Plik nie istnieje<xref:System.IO.IOException>( ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze sprawdzaj dane wejściowe i nigdy nie deserializuj danych z niezaufanego źródła. Ponownie utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który go deserializował. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- [Jak zapisywać dane obiektu do pliku XML (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serializacja (C#)](./index.md)
- [Przewodnik programowania języka C#](../../index.md)

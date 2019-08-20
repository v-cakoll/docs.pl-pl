---
title: 'Instrukcje: Odczytaj dane obiektu z pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 1d6ec71b9e408e1536063fc3d8f1badc0f38551e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590742"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a>Instrukcje: Odczytaj dane obiektu z pliku XML (C#)
Ten przykład odczytuje dane obiektu, które wcześniej Zapisano do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
 Zastąp nazwę pliku "c:\temp\SerializationOverview.xml" nazwą pliku zawierającego serializowane dane. Aby uzyskać więcej informacji na temat serializowania danych [, zobacz How to: Zapisz dane obiektu w pliku XML (C#).](./how-to-write-object-data-to-an-xml-file.md)  
  
 Klasa musi mieć Konstruktor publiczny bez parametrów.  
  
 Tylko publiczne właściwości i pola są deserializowane.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Serializowana Klasa nie ma publicznego konstruktora bez parametrów.  
  
- Dane w pliku nie reprezentują danych z klasy, która ma zostać poddana deserializacji.  
  
- Plik nie istnieje (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Zawsze Weryfikuj dane wejściowe i nigdy nie wykonuj deserializacji danych z niezaufanego źródła. Nowo utworzony obiekt jest uruchamiany na komputerze lokalnym z uprawnieniami kodu, który został deserializowany. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Instrukcje: Zapisz dane obiektu w pliku XML (C#)](./how-to-write-object-data-to-an-xml-file.md)
- [Serializacja (C#)](./index.md)
- [Przewodnik programowania w języku C#](../../index.md)

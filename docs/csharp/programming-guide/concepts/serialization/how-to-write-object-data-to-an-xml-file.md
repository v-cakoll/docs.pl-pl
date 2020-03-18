---
title: Jak zapisywać dane obiektu do pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: f7ffb47a22d3cd94cd7cb6f702b64180a8790eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167517"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Jak zapisywać dane obiektu do pliku XML (C#)
W tym przykładzie zapisuje obiekt z klasy do <xref:System.Xml.Serialization.XmlSerializer> pliku XML przy użyciu klasy.  
  
## <a name="example"></a>Przykład  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Klasa serializacji musi mieć konstruktora publicznego bez parametrów.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Klasa serializacji nie ma konstruktora publicznego, bezparametrów.  
  
- Plik istnieje i jest tylko<xref:System.IO.IOException>do odczytu ( ).  
  
- Ścieżka jest zbyt<xref:System.IO.PathTooLongException>długa ( ).  
  
- Dysk jest zapełniony (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta `Create` aplikacja wymaga dostępu do folderu. Jeśli plik już istnieje, aplikacja `Write` wymaga tylko dostępu, mniejsze uprawnienia. Jeśli to możliwe, jest bardziej bezpieczne, aby utworzyć `Read` plik podczas wdrażania i `Create` przyznać dostęp tylko do jednego pliku, a nie dostęp do folderu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- [Jak odczytywać dane obiektu z pliku XML (C#)](./how-to-read-object-data-from-an-xml-file.md)
- [Serializacja (C#)](./index.md)

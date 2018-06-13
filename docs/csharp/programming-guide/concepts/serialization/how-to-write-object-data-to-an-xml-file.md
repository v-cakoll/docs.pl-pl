---
title: 'Porady: wpisywanie danych o obiektach do pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 1c8bfd00452cee63456bc3bf64ccf4a0c61aa06e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320551"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Porady: wpisywanie danych o obiektach do pliku XML (C#)
W tym przykładzie zapisuje obiekt z klasy w pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
 [Porady: odczytywanie danych o obiektach z pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Serializacja (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)

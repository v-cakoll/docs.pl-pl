---
title: 'Instrukcje: Zapisywania obiektów danych do pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: a4fdb496e3b015b2e3b46c9705ba1c05c20423f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595523"
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a>Instrukcje: Zapisywania obiektów danych do pliku XML (C#)
Ten przykład Przepisuje obiekt z klasy do pliku XML przy użyciu <xref:System.Xml.Serialization.XmlSerializer> klasy.  
  
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
  
- Klasa jest serializowana, nie ma publiczny konstruktor bez parametrów.  
  
- Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
- Ścieżka jest zbyt długa (<xref:System.IO.PathTooLongException>).  
  
- Dysk jest pełny (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` dostępu, mniejsze uprawnienia. Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` dostępu do pojedynczego pliku, zamiast `Create` dostępu do folderu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.StreamWriter>
- [Instrukcje: Odczytywanie danych o obiektach z pliku XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serializacja (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)

---
title: 'Porady: wykonywanie przekształceń strumieniowych dużych dokumentów XML (C#)'
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 1a12e8c0ae98be37599b05e5d63469336247d915
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244143"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Porady: wykonywanie przekształceń strumieniowych dużych dokumentów XML (C#)
Czasami trzeba Przekształcanie dużych plików XML i pisania aplikacji, więc, że zużycie pamięci aplikacji jest przewidywalne. Jeśli zostanie podjęta próba wypełnianie drzewa XML z bardzo dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku (oznacza to, że nadmierne). W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.  
  
 Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu. Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji. Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci aplikacji.  
  
 Nawet w przypadku używania techniki opisanej w [jak: Stream XML fragmentów z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md), Jeśli spróbujesz utworzyć drzewa XML zawierający przekształcone dokumentu jest zbyt duże użycie pamięci.  
  
 Dostępne są dwie główne opcje. Jedno z podejść jest użycie właściwości przetwarzanie odroczone <xref:System.Xml.Linq.XStreamingElement>. Innym rozwiązaniem jest utworzenie <xref:System.Xml.XmlWriter>oraz korzystać z możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>. W tym temacie przedstawiono oba podejścia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład opiera się na przykład w [jak: Stream XML fragmentów z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 W tym przykładzie użyto funkcji odroczonego wykonania <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych. W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.  
  
 Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów. Bardziej niezawodna implementacji będzie jednak przygotowane przeanalizować nieprawidłowy dokument.  
  
 Dokument źródłowy Source.xml jest następująca:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null)  
                        {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XStreamingElement root = new XStreamingElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    root.Save("Test.xml");  
    Console.WriteLine(File.ReadAllText("Test.xml"));  
}  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład opiera się również na przykład w [jak: Stream XML fragmentów z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md).  
  
 W tym przykładzie użyto możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do zapisania elementów <xref:System.Xml.XmlWriter>. W tym przykładzie można przekształcać bardzo dużych dokumentów przy zachowaniu zużycie pamięci.  
  
 Należy pamiętać, że niestandardowe osi (`StreamCustomerItem`) napisano specjalnie tak, aby oczekuje, że dokument zawierający `Customer`, `Name`, i `Item` elementów i że tak jak w następującym dokumencie Source.xml rozmieszczenia tych elementów. Jednak implementacja bardziej niezawodne, albo czy sprawdzanie poprawności dokumentu źródłowego przy użyciu XSD lub jest gotowy do analizowania nieprawidłowy dokument.  
  
 W tym przykładzie użyto tego samego dokumentu źródłowego Source.xml, jak w poprzednim przykładzie w tym temacie. Generuje ten sam wynik.  
  
 Za pomocą <xref:System.Xml.Linq.XStreamingElement> dla przesyłania strumieniowego wyjściowy plik XML jest preferowana względem zapisywania <xref:System.Xml.XmlWriter>.  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    IEnumerable<XElement> srcTree =  
        from el in StreamCustomerItem("Source.xml")  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        );  
    XmlWriterSettings xws = new XmlWriterSettings();  
    xws.OmitXmlDeclaration = true;  
    xws.Indent = true;  
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {  
        xw.WriteStartElement("Root");  
        foreach (XElement el in srcTree)  
            el.WriteTo(xw);  
        xw.WriteEndElement();  
    }  
  
    string str = File.ReadAllText("Output.xml");  
    Console.WriteLine(str);  
}  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0001</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0002</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0008</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0009</Key>  
  </Item>  
  <Item>  
    <Customer>Southridge Video</Customer>  
    <Key>0010</Key>  
  </Item>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

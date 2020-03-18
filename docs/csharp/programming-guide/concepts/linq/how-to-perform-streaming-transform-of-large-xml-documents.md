---
title: Jak wykonać transformację przesyłania strumieniowego dużych dokumentów XML (C#)
ms.date: 07/20/2015
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: 9eb2e832f798e550ef3b534b0c9a0e3416378b43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169107"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-c"></a>Jak wykonać transformację przesyłania strumieniowego dużych dokumentów XML (C#)
Czasami trzeba przekształcić duże pliki XML i napisać aplikację, tak aby rozmiar pamięci aplikacji jest przewidywalny. Jeśli spróbujesz wypełnić drzewo XML bardzo dużym plikiem XML, użycie pamięci będzie proporcjonalne do rozmiaru pliku (czyli nadmiernego). W związku z tym należy użyć techniki przesyłania strumieniowego zamiast tego.  
  
 Techniki przesyłania strumieniowego są najlepiej stosowane w sytuacjach, w których trzeba przetworzyć dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu. Niektóre standardowe operatory <xref:System.Linq.Enumerable.OrderBy%2A>zapytań, takie jak , iterate ich źródła, zbierać wszystkie dane, sortować go, a następnie wreszcie przynieść pierwszy element w sekwencji. Należy zauważyć, że jeśli używasz operatora kwerendy, który materializuje jego źródła przed uzyskaniem pierwszego elementu, nie zachowa niewielką ilość pamięci dla aplikacji.  
  
Nawet jeśli używasz techniki opisanej w [Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#),](./how-to-stream-xml-fragments-with-access-to-header-information.md)jeśli spróbujesz złożyć drzewo XML zawierające przekształcony dokument, użycie pamięci będzie zbyt duże.
  
 Istnieją dwa główne podejścia. Jednym z podejść jest użycie charakterystyki odroczonego przetwarzania <xref:System.Xml.Linq.XStreamingElement>. Innym podejściem <xref:System.Xml.XmlWriter>jest utworzenie , i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wykorzystać możliwości do <xref:System.Xml.XmlWriter>zapisu elementów do . W tym temacie przedstawiono oba podejścia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład opiera się na przykładzie w [Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 W tym przykładzie używa możliwości <xref:System.Xml.Linq.XStreamingElement> odroczonego wykonywania do strumienia danych wyjściowych. W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu niewielki rozmiar pamięci.  
  
 Należy zauważyć, że`StreamCustomerItem`oś niestandardowa ( ) jest specjalnie `Customer` `Name`napisana `Item` tak, aby oczekiwała dokumentu, który ma , i elementy, i że te elementy zostaną rozmieszczone, jak w poniższym dokumencie Source.xml. Bardziej niezawodne wdrożenie, jednak byłby przygotowany do analizy nieprawidłowego dokumentu.  
  
 Poniżej znajduje się dokument źródłowy Source.xml:  
  
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
Poniższy przykład opiera się również na przykładzie w [Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md).
  
 W tym przykładzie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] użyto możliwości <xref:System.Xml.XmlWriter>zapisu elementów do . W tym przykładzie można przekształcić bardzo duży dokument przy zachowaniu niewielki rozmiar pamięci.  
  
 Należy zauważyć, że`StreamCustomerItem`oś niestandardowa ( ) jest specjalnie `Customer` `Name`napisana `Item` tak, aby oczekiwała dokumentu, który ma , i elementy, i że te elementy zostaną rozmieszczone, jak w poniższym dokumencie Source.xml. Bardziej niezawodna implementacja, jednak będzie sprawdzić poprawność dokumentu źródłowego z XSD lub będzie przygotowany do analizy nieprawidłowego dokumentu.  
  
 W tym przykładzie użyto tego samego dokumentu źródłowego, Source.xml, jak w poprzednim przykładzie w tym temacie. Produkuje również dokładnie takie same dane wyjściowe.  
  
 Używanie <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych XML jest preferowane niż zapisywanie do . <xref:System.Xml.XmlWriter>  
  
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
  
---
title: 'Instrukcje: Strumieniowe fragmenty XML z dostępem do informacji nagłówkaC#()'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d40fa5b7ae60836c0fd947d36f88765eafc60334
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592339"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Instrukcje: Strumieniowe fragmenty XML z dostępem do informacji nagłówkaC#()
Czasami konieczne jest odczytanie arbitralnie dużych plików XML i zapisanie aplikacji w celu przewidzenia rozmiaru pamięci aplikacji. W przypadku próby wypełnienia drzewa XML przy użyciu dużego pliku XML użycie pamięci będzie proporcjonalne do rozmiaru pliku, czyli nadmierne. W związku z tym należy zamiast tego użyć techniki przesyłania strumieniowego.  
  
 Jedną z opcji jest zapisanie aplikacji przy <xref:System.Xml.XmlReader>użyciu programu. Można jednak użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , aby zbadać drzewo XML. W takim przypadku można napisać własną metodę osi niestandardowej. Aby uzyskać więcej informacji, zobacz [jak: Napisz metodę osi LINQ to XML (C#).](./how-to-write-a-linq-to-xml-axis-method.md)  
  
 Aby napisać własną metodę osi, napisz małą metodę, która używa <xref:System.Xml.XmlReader> do odczytu węzłów do momentu osiągnięcia jednego z węzłów, w których Cię interesują. Metoda następnie wywołuje <xref:System.Xml.Linq.XNode.ReadFrom%2A>, który odczytuje <xref:System.Xml.XmlReader> z i tworzy wystąpienie fragmentu XML. Następnie przekazuje każdy fragment `yield return` do metody, która wylicza metodę osi niestandardowej. Następnie można napisać zapytania LINQ na niestandardowej metodzie osi.  
  
 Techniki przesyłania strumieniowego najlepiej zastosować w sytuacjach, gdy trzeba przetwarzać dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu. Niektóre standardowe operatory zapytań, takie jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteruje źródło, zbierają wszystkie dane, sortują je, a następnie zwracają pierwszy element w sekwencji. Należy pamiętać, że jeśli używasz operatora zapytania, który materializuje jego źródło przed uzyskaniem pierwszego elementu, nie będzie zachowana mała ilość pamięci.  
  
## <a name="example"></a>Przykład  
 Czasami problem jest znacznie bardziej interesujący. W poniższym dokumencie XML konsument niestandardowej metody osi musi znać nazwę klienta, do którego należy każdy element.  
  
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
  
 Podejście, które ten przykład przyjmuje, ma również na celu śledzenie informacji o tym nagłówku, zapisanie informacji nagłówka, a następnie utworzenie małego drzewa XML zawierającego zarówno informacje nagłówka, jak i szczegóły wyliczane. Następnie metoda osi daje nowe, małe drzewo XML. Następnie zapytanie ma dostęp do informacji nagłówka oraz informacji szczegółowych.  
  
 Takie podejście ma niewielkie rozmiary pamięci. Ze względu na to, że każdy szczegółowy fragment kodu XML jest przewidziany, żadne odwołania nie są przechowywane w poprzednim fragmencie i jest dostępny do wyrzucania elementów bezużytecznych. Należy zauważyć, że ta technika tworzy wiele obiektów krótkotrwałych na stercie.  
  
 Poniższy przykład przedstawia sposób implementacji i używania niestandardowej metody osi, która strumieniuje fragmenty XML z pliku określonego przez identyfikator URI. Ta oś niestandardowa jest zapisywana w taki sposób, że oczekuje dokumentu `Customer` `Name`,, i `Item` elementów, i że te elementy będą ułożone jak w powyższym `Source.xml` dokumencie. Jest to implementacja uproszczony. Bardziej niezawodna implementacja zostanie przygotowana do analizy nieprawidłowego dokumentu.  
  
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
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
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
</Root>  
```  
  
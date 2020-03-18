---
title: Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 5bc10bcadae0e33ee63f953608ca841d44dd6527
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712393"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)
Czasami trzeba odczytać arbitralnie dużych plików XML i napisać aplikację, tak aby rozmiar pamięci aplikacji jest przewidywalny. Jeśli spróbujesz wypełnić drzewo XML dużym plikiem XML, użycie pamięci będzie proporcjonalne do rozmiaru pliku — czyli nadmiernego. W związku z tym należy użyć techniki przesyłania strumieniowego zamiast tego.  
  
Jedną z opcji jest <xref:System.Xml.XmlReader>napisanie aplikacji za pomocą . Można jednak użyć LINQ do wykonywania zapytań do drzewa XML. W takim przypadku można napisać własną metodę osi niestandardowej. Aby uzyskać więcej informacji, zobacz [Jak napisać linq do metody osi XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).
  
 Aby napisać własną metodę osi, należy napisać <xref:System.Xml.XmlReader> małą metodę, która używa do odczytu węzłów, dopóki nie osiągnie jeden z węzłów, w którym jesteś zainteresowany. Metoda następnie <xref:System.Xml.Linq.XNode.ReadFrom%2A>wywołuje , który <xref:System.Xml.XmlReader> odczytuje z i tworzy fragment XML. Następnie daje każdy fragment `yield return` do metody, która wylicza metodę osi niestandardowej. Następnie można napisać zapytania LINQ na niestandardowej metody osi.  
  
 Techniki przesyłania strumieniowego są najlepiej stosowane w sytuacjach, w których trzeba przetworzyć dokument źródłowy tylko raz i można przetwarzać elementy w kolejności dokumentu. Niektóre standardowe operatory <xref:System.Linq.Enumerable.OrderBy%2A>zapytań, takie jak , iterate ich źródła, zbierać wszystkie dane, sortować go, a następnie wreszcie przynieść pierwszy element w sekwencji. Jeśli używasz operatora kwerendy, który materializuje jego źródła przed uzyskaniem pierwszego elementu, nie zachowa małej pamięci.  
  
## <a name="example"></a>Przykład  

Czasami problem staje się nieco bardziej interesujący. W poniższym dokumencie XML konsument metody osi niestandardowej musi również znać nazwę odbiorcy, do którego należy każdy element.  
  
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
  
 Podejście, które przyjmuje w tym przykładzie jest również obserwować dla tych informacji nagłówka, zapisać informacje nagłówka, a następnie utworzyć małe drzewo XML, który zawiera zarówno informacje nagłówka i szczegóły, które są wyliczane. Metoda osi następnie daje to nowe, małe drzewo XML. Kwerenda ma dostęp do informacji nagłówka, a także informacji szczegółowych.  
  
 Takie podejście ma niewielki rozmiar pamięci. Jak każdy fragment XML szczegółu jest pled, żadne odwołania są przechowywane do poprzedniego fragmentu i jest dostępna dla wyrzucania elementów bezużytecznych. Ta technika tworzy wiele krótkotrwałych obiektów na stercie.  
  
 W poniższym przykładzie pokazano, jak zaimplementować i używać metody osi niestandardowej, która przesyła strumienifragmenty XML z pliku określonego przez identyfikator URI. Ta oś niestandardowa jest napisana w `Customer` `Name`taki `Item` sposób, że oczekuje dokumentu, który ma `Source.xml` , i elementy, i że te elementy zostaną rozmieszczone, jak w powyższym dokumencie. Jest to uproszczone wdrożenie. Bardziej niezawodne wdrożenie byłoby przygotowane do analizy nieprawidłowego dokumentu.  
  
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

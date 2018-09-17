---
title: 'Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 9c141b21a009f836fbf385c1f4179e288ec6c3b5
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45698279"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)
Czasami trzeba przeczytać arbitralnie dużych plików XML i zapisu aplikacji, tak aby zużycie pamięci aplikacji jest przewidywalne. Jeśli użytkownik podejmie próbę wypełnianie drzewa XML przy użyciu dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku — oznacza to, że nadmierne. W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.  
  
 Jedną z opcji jest do zapisu w swojej aplikacji za pomocą <xref:System.Xml.XmlReader>. Jednakże, możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy drzewa XML. Jeśli jest to możliwe, można napisać metodę niestandardowe osi. Aby uzyskać więcej informacji, zobacz [porady: zapis LINQ do XML metody osi (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Aby napisać własne metody osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzły, aż do napotkania jednego z węzłów, w których interesuje Cię. Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment. Następnie daje poszczególne fragmenty, za pośrednictwem `yield return` do metody, która wylicza metodę niestandardowe osi. Następnie można pisać zapytania LINQ metodę niestandardowe osi.  
  
 Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu. Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji. Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 Czasami problem pobiera nieco więcej interesujące. W następującym dokumencie XML konsumenta metodę niestandardowe osi ma również znać nazwę klienta, który należy do każdego elementu.  
  
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
  
 Metody, która przyjmuje w tym przykładzie jest również obejrzeć te informacje nagłówka, Zapisz informacje nagłówka, a następnie skompilować małych drzewa XML, który zawiera zarówno informacje nagłówka, jak i szczegółów, które wyliczają to. Metody osi następnie daje to nowe, małe drzewa XML. Zapytanie uzyska dostęp do informacji nagłówka, a także szczegółowe informacje.  
  
 Takie podejście ma zużycie pamięci. Zgodnie z każdego fragmentu XML szczegółów jest uzyskane, pozostają żadnych odwołań do poprzedniego fragmentu i jest dostępny dla wyrzucania elementów bezużytecznych. Należy pamiętać, że ta technika tworzy wiele krótki czas życia obiektów na stosie.  
  
 Poniższy przykład pokazuje, jak implementować oraz użyć metody osi niestandardowej, która przesyła strumieniowo fragmentów kodu XML z pliku określonego przez identyfikator URI. Ta oś niestandardowe specjalnie są zapisywane, w której oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów tak jak w powyższym `Source.xml` dokumentu. Jest uproszczony implementacji. Bardziej niezawodne wdrożenia będzie przygotowana do analizowania nieprawidłowy dokument.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Zaawansowane LINQ to XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

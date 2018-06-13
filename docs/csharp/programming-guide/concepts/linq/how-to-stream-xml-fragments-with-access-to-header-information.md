---
title: 'Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: af8f83ba746292289bb97f591103cc91d6febbad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325035"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (C#)
Czasami trzeba arbitralnie duże pliki XML do odczytu i zapisu aplikacji, dzięki czemu zużycie pamięci aplikacji jest atrybutem wartości prognozowanych. Przy próbie wypełnić drzewo XML z dużego pliku XML, użycie pamięci będzie proporcjonalny do rozmiaru pliku — to znaczy nadmierne. W związku z tym należy w zamian użyj technika przesyłania strumieniowego.  
  
 Jedną z opcji jest napisanie swojej aplikacji za pomocą <xref:System.Xml.XmlReader>. Jednak możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do badania drzewo składni XML. Jeśli jest to możliwe, można napisać metodę niestandardowych osi. Aby uzyskać więcej informacji, zobacz [porady: pisanie LINQ do metody osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).  
  
 Aby napisać metodę osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzłów, dopóki nie osiągnie jednego z węzłów, w których jesteś zainteresowany. Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment. Następnie daje każdego fragmentu za pośrednictwem `yield return` do metody, która wylicza metodę niestandardowych osi. Następnie można pisać zapytania LINQ metodę niestandardowych osi.  
  
 Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy musisz przetworzyć dokumentu źródłowego tylko raz i może przetwarzać elementów w kolejności dokumentu. Niektóre standardowy kwerendy operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródłem Zbieraj wszystkie dane, sortowanie ich i ostatecznie yield pierwszego elementu w sekwencji. Należy pamiętać, że użycie operatora zapytania, który zostaje źródła przed reaguje pierwszy element, możesz nie zostaną zachowane zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 Czasami problem pobiera małą ilością interesujące więcej. W następującym dokumencie XML konsumenta metodę niestandardowych osi również musi znać nazwę każdego elementu należącego do klienta.  
  
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
  
 Podejście, które przyjmuje w tym przykładzie jest również obejrzeć takie informacje nagłówka, Zapisz informacje nagłówka i późniejszego kompilowania małych drzewa XML, który zawiera informacje o nagłówku i szczegóły są wyliczania. Metoda osi następnie daje w wyniku tego nowego, mała drzewa XML. Zapytanie następnie ma dostęp do informacji w nagłówku, a także szczegółowe informacje.  
  
 Takie podejście charakteryzuje się zużycie pamięci. Jak każdego fragmentu XML szczegółów jest zwróciło, nie będą przechowywane żadnych odwołań do poprzedniego fragmentu, i jest dostępny dla wyrzucanie elementów bezużytecznych. Należy pamiętać, że ta metoda tworzy wiele obiektów krótko na stosie.  
  
 Poniższy przykład pokazuje, jak do wdrożenia i używa metody osi niestandardowych strumieni fragmenty XML z pliku określonego przez identyfikator URI. Tej osi niestandardowe są zapisywane w szczególności taki sposób, że oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów jak powyższych `Source.xml` dokumentu. Jest simplistic implementacji. Czy można przygotować bardziej niezawodne implementacji przeanalizować nieprawidłowy dokument.  
  
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
 [Zaawansowane LINQ do XML programowania (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

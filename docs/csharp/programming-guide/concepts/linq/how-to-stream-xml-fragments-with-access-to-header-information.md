---
title: 'Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: af8f83ba746292289bb97f591103cc91d6febbad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="59f8f-102">Porady: strumienia fragmenty XML z dostępem do informacji w nagłówku (C#)</span><span class="sxs-lookup"><span data-stu-id="59f8f-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="59f8f-103">Czasami trzeba arbitralnie duże pliki XML do odczytu i zapisu aplikacji, dzięki czemu zużycie pamięci aplikacji jest atrybutem wartości prognozowanych.</span><span class="sxs-lookup"><span data-stu-id="59f8f-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="59f8f-104">Przy próbie wypełnić drzewo XML z dużego pliku XML, użycie pamięci będzie proporcjonalny do rozmiaru pliku — to znaczy nadmierne.</span><span class="sxs-lookup"><span data-stu-id="59f8f-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="59f8f-105">W związku z tym należy w zamian użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="59f8f-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="59f8f-106">Jedną z opcji jest napisanie swojej aplikacji za pomocą <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="59f8f-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="59f8f-107">Jednak możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do badania drzewo składni XML.</span><span class="sxs-lookup"><span data-stu-id="59f8f-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="59f8f-108">Jeśli jest to możliwe, można napisać metodę niestandardowych osi.</span><span class="sxs-lookup"><span data-stu-id="59f8f-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="59f8f-109">Aby uzyskać więcej informacji, zobacz [porady: pisanie LINQ do metody osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="59f8f-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="59f8f-110">Aby napisać metodę osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzłów, dopóki nie osiągnie jednego z węzłów, w których jesteś zainteresowany.</span><span class="sxs-lookup"><span data-stu-id="59f8f-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="59f8f-111">Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment.</span><span class="sxs-lookup"><span data-stu-id="59f8f-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="59f8f-112">Następnie daje każdego fragmentu za pośrednictwem `yield return` do metody, która wylicza metodę niestandardowych osi.</span><span class="sxs-lookup"><span data-stu-id="59f8f-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="59f8f-113">Następnie można pisać zapytania LINQ metodę niestandardowych osi.</span><span class="sxs-lookup"><span data-stu-id="59f8f-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="59f8f-114">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy musisz przetworzyć dokumentu źródłowego tylko raz i może przetwarzać elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="59f8f-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="59f8f-115">Niektóre standardowy kwerendy operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>, iteracji ich źródłem Zbieraj wszystkie dane, sortowanie ich i ostatecznie yield pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="59f8f-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="59f8f-116">Należy pamiętać, że użycie operatora zapytania, który zostaje źródła przed reaguje pierwszy element, możesz nie zostaną zachowane zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="59f8f-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59f8f-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="59f8f-117">Example</span></span>  
 <span data-ttu-id="59f8f-118">Czasami problem pobiera małą ilością interesujące więcej.</span><span class="sxs-lookup"><span data-stu-id="59f8f-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="59f8f-119">W następującym dokumencie XML konsumenta metodę niestandardowych osi również musi znać nazwę każdego elementu należącego do klienta.</span><span class="sxs-lookup"><span data-stu-id="59f8f-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="59f8f-120">Podejście, które przyjmuje w tym przykładzie jest również obejrzeć takie informacje nagłówka, Zapisz informacje nagłówka i późniejszego kompilowania małych drzewa XML, który zawiera informacje o nagłówku i szczegóły są wyliczania.</span><span class="sxs-lookup"><span data-stu-id="59f8f-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="59f8f-121">Metoda osi następnie daje w wyniku tego nowego, mała drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="59f8f-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="59f8f-122">Zapytanie następnie ma dostęp do informacji w nagłówku, a także szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="59f8f-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="59f8f-123">Takie podejście charakteryzuje się zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="59f8f-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="59f8f-124">Jak każdego fragmentu XML szczegółów jest zwróciło, nie będą przechowywane żadnych odwołań do poprzedniego fragmentu, i jest dostępny dla wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="59f8f-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="59f8f-125">Należy pamiętać, że ta metoda tworzy wiele obiektów krótko na stosie.</span><span class="sxs-lookup"><span data-stu-id="59f8f-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="59f8f-126">Poniższy przykład pokazuje, jak do wdrożenia i używa metody osi niestandardowych strumieni fragmenty XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="59f8f-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="59f8f-127">Tej osi niestandardowe są zapisywane w szczególności taki sposób, że oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów jak powyższych `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="59f8f-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="59f8f-128">Jest simplistic implementacji.</span><span class="sxs-lookup"><span data-stu-id="59f8f-128">It is a simplistic implementation.</span></span> <span data-ttu-id="59f8f-129">Czy można przygotować bardziej niezawodne implementacji przeanalizować nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="59f8f-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="59f8f-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="59f8f-130">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59f8f-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59f8f-131">See Also</span></span>  
 [<span data-ttu-id="59f8f-132">Zaawansowane LINQ do XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="59f8f-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

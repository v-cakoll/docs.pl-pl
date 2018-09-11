---
title: 'Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)'
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 9c141b21a009f836fbf385c1f4179e288ec6c3b5
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365744"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a><span data-ttu-id="d52d9-102">Porady: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)</span><span class="sxs-lookup"><span data-stu-id="d52d9-102">How to: Stream XML Fragments with Access to Header Information (C#)</span></span>
<span data-ttu-id="d52d9-103">Czasami trzeba przeczytać arbitralnie dużych plików XML i zapisu aplikacji, tak aby zużycie pamięci aplikacji jest przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="d52d9-103">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="d52d9-104">Jeśli użytkownik podejmie próbę wypełnianie drzewa XML przy użyciu dużego pliku XML, wykorzystanie pamięci będzie proporcjonalny do rozmiaru pliku — oznacza to, że nadmierne.</span><span class="sxs-lookup"><span data-stu-id="d52d9-104">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="d52d9-105">W związku z tym należy zamiast tego użyj technika przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="d52d9-105">Therefore, you should use a streaming technique instead.</span></span>  
  
 <span data-ttu-id="d52d9-106">Jedną z opcji jest do zapisu w swojej aplikacji za pomocą <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="d52d9-106">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="d52d9-107">Jednakże, możesz chcieć użyć [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="d52d9-107">However, you might want to use [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to query the XML tree.</span></span> <span data-ttu-id="d52d9-108">Jeśli jest to możliwe, można napisać metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="d52d9-108">If this is the case, you can write your own custom axis method.</span></span> <span data-ttu-id="d52d9-109">Aby uzyskać więcej informacji, zobacz [porady: zapis LINQ do XML metody osi (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="d52d9-109">For more information, see [How to: Write a LINQ to XML Axis Method (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-linq-to-xml-axis-method.md).</span></span>  
  
 <span data-ttu-id="d52d9-110">Aby napisać własne metody osi, zapisu małych metody, która używa <xref:System.Xml.XmlReader> odczytać węzły, aż do napotkania jednego z węzłów, w których interesuje Cię.</span><span class="sxs-lookup"><span data-stu-id="d52d9-110">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you are interested.</span></span> <span data-ttu-id="d52d9-111">Następnie wywołuje metodę <xref:System.Xml.Linq.XNode.ReadFrom%2A>, która odczytuje z <xref:System.Xml.XmlReader> i tworzy XML fragment.</span><span class="sxs-lookup"><span data-stu-id="d52d9-111">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="d52d9-112">Następnie daje poszczególne fragmenty, za pośrednictwem `yield return` do metody, która wylicza metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="d52d9-112">It then yields each fragment through `yield return` to the method that is enumerating your custom axis method.</span></span> <span data-ttu-id="d52d9-113">Następnie można pisać zapytania LINQ metodę niestandardowe osi.</span><span class="sxs-lookup"><span data-stu-id="d52d9-113">You can then write LINQ queries on your custom axis method.</span></span>  
  
 <span data-ttu-id="d52d9-114">Techniki przesyłania strumieniowego najlepiej są stosowane w sytuacji, gdy trzeba przetworzyć tylko jeden raz w dokumencie źródłowym i pozwala na przetwarzanie elementów w kolejności dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d52d9-114">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="d52d9-115">Niektóre standardowe zapytanie operatorów, takich jak <xref:System.Linq.Enumerable.OrderBy%2A>iteracji ich źródła, zbieraj wszystkie dane, ją posortować i na koniec uzyskanie pierwszego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d52d9-115">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="d52d9-116">Należy pamiętać, że użycie operatora zapytania, który materializuje źródła przed reaguje na pierwszy element, możesz nie zostaną zachowane zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="d52d9-116">Note that if you use a query operator that materializes its source before yielding the first item, you will not retain a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d52d9-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d52d9-117">Example</span></span>  
 <span data-ttu-id="d52d9-118">Czasami problem pobiera nieco więcej interesujące.</span><span class="sxs-lookup"><span data-stu-id="d52d9-118">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="d52d9-119">W następującym dokumencie XML konsumenta metodę niestandardowe osi ma również znać nazwę klienta, który należy do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="d52d9-119">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>  
  
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
  
 <span data-ttu-id="d52d9-120">Metody, która przyjmuje w tym przykładzie jest również obejrzeć te informacje nagłówka, Zapisz informacje nagłówka, a następnie skompilować małych drzewa XML, który zawiera zarówno informacje nagłówka, jak i szczegółów, które wyliczają to.</span><span class="sxs-lookup"><span data-stu-id="d52d9-120">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you are enumerating.</span></span> <span data-ttu-id="d52d9-121">Metody osi następnie daje to nowe, małe drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="d52d9-121">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="d52d9-122">Zapytanie uzyska dostęp do informacji nagłówka, a także szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="d52d9-122">The query then has access to the header information as well as the detail information.</span></span>  
  
 <span data-ttu-id="d52d9-123">Takie podejście ma zużycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="d52d9-123">This approach has a small memory footprint.</span></span> <span data-ttu-id="d52d9-124">Zgodnie z każdego fragmentu XML szczegółów jest uzyskane, pozostają żadnych odwołań do poprzedniego fragmentu i jest dostępny dla wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="d52d9-124">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it is available for garbage collection.</span></span> <span data-ttu-id="d52d9-125">Należy pamiętać, że ta technika tworzy wiele krótki czas życia obiektów na stosie.</span><span class="sxs-lookup"><span data-stu-id="d52d9-125">Note that this technique creates many short lived objects on the heap.</span></span>  
  
 <span data-ttu-id="d52d9-126">Poniższy przykład pokazuje, jak implementować oraz użyć metody osi niestandardowej, która przesyła strumieniowo fragmentów kodu XML z pliku określonego przez identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="d52d9-126">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="d52d9-127">Ta oś niestandardowe specjalnie są zapisywane, w której oczekuje, że dokument, który ma `Customer`, `Name`, i `Item` elementów i rozmieszczenia elementów tak jak w powyższym `Source.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d52d9-127">This custom axis is specifically written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="d52d9-128">Jest uproszczony implementacji.</span><span class="sxs-lookup"><span data-stu-id="d52d9-128">It is a simplistic implementation.</span></span> <span data-ttu-id="d52d9-129">Bardziej niezawodne wdrożenia będzie przygotowana do analizowania nieprawidłowy dokument.</span><span class="sxs-lookup"><span data-stu-id="d52d9-129">A more robust implementation would be prepared to parse an invalid document.</span></span>  
  
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
  
 <span data-ttu-id="d52d9-130">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d52d9-130">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d52d9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d52d9-131">See Also</span></span>

- [<span data-ttu-id="d52d9-132">Zaawansowane LINQ to XML programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="d52d9-132">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

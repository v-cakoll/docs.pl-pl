---
title: Konstrukcja funkcjonalna (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c2579da6e3cdfea6469742d29935b0137e320bbb
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777094"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="2b2cd-102">Konstrukcja funkcjonalna (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2b2cd-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2b2cd-103">zapewnia zaawansowany sposób tworzyć elementy XML o nazwie *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-103"> provides a powerful way to create XML elements called \*functional construction\*.</span></span> <span data-ttu-id="2b2cd-104">Konstrukcja funkcjonalna jest możliwość tworzenia drzewa XML w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="2b2cd-105">Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejs programowania, które umożliwiają konstrukcja funkcjonalna:</span><span class="sxs-lookup"><span data-stu-id="2b2cd-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="2b2cd-106"><xref:System.Xml.Linq.XElement> Konstruktor przyjmuje różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="2b2cd-107">Na przykład, można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się nie zawiera elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="2b2cd-108">Możesz przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybut elementu.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="2b2cd-109">Lub możesz przekazać inny rodzaj obiektu, który jest konwertowany na ciąg i staje się zawartością tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="2b2cd-110"><xref:System.Xml.Linq.XElement> Konstruktor przyjmuje `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="2b2cd-111">Dzięki temu można utworzyć elementu, który ma zawartość złożoną.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="2b2cd-112">Jeśli obiekt implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, są wyliczane kolekcji w obiekcie, a wszystkie elementy w kolekcji są dodawane.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="2b2cd-113">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiektów, każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="2b2cd-114">Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="2b2cd-115">Te funkcje umożliwiają pisanie kodu w celu tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2b2cd-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="2b2cd-116">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="2b2cd-116">The following is an example:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="2b2cd-117">Te funkcje umożliwiają także napisać kod, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podczas tworzenia drzewa XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2b2cd-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="2b2cd-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="2b2cd-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b2cd-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b2cd-119">See Also</span></span>

- [<span data-ttu-id="2b2cd-120">Tworzenie drzew XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2b2cd-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

---
title: Konstrukcja funkcjonalna (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635759"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="d7f98-102">Konstrukcja funkcjonalna (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="d7f98-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d7f98-103">zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="d7f98-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="d7f98-104">Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d7f98-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="d7f98-105">Istnieje kilka najważniejszych funkcji interfejsu programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], które umożliwiają konstruowanie funkcjonalne:</span><span class="sxs-lookup"><span data-stu-id="d7f98-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="d7f98-106">Konstruktor <xref:System.Xml.Linq.XElement> ma różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="d7f98-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="d7f98-107">Na przykład można przekazać inny obiekt <xref:System.Xml.Linq.XElement>, który stanie się elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="d7f98-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="d7f98-108">Można przekazać obiekt <xref:System.Xml.Linq.XAttribute>, który stanie się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="d7f98-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="d7f98-109">Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="d7f98-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="d7f98-110">Konstruktor <xref:System.Xml.Linq.XElement> pobiera tablicę `params` typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d7f98-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="d7f98-111">Dzięki temu można utworzyć element, który ma złożoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="d7f98-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="d7f98-112">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie zostanie wyliczona i wszystkie elementy w kolekcji zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="d7f98-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="d7f98-113">Jeśli kolekcja zawiera obiekty <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute>, każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="d7f98-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="d7f98-114">Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania LINQ do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="d7f98-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="d7f98-115">Te funkcje umożliwiają pisanie kodu w celu utworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="d7f98-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="d7f98-116">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="d7f98-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="d7f98-117">Te funkcje umożliwiają również pisanie kodu, który używa wyników zapytań LINQ podczas tworzenia drzewa XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d7f98-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d7f98-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d7f98-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
---
title: Konstrukcja funkcjonalna (LINQ to XML) (C#)
description: Dowiedz się, w jaki sposób interfejs programowania LINQ to XML umożliwia konstruowanie funkcjonalne, możliwość tworzenia drzewa XML w pojedynczej instrukcji w języku C#.
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: f209a7ef2a4597ec8eeccb3083b77223a27e7a65
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103774"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="a7831-103">Konstrukcja funkcjonalna (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a7831-103">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="a7831-104">zapewnia zaawansowany sposób tworzenia elementów XML o nazwie *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="a7831-104">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="a7831-105">Konstrukcja funkcjonalna to możliwość tworzenia drzewa XML w pojedynczej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7831-105">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="a7831-106">Istnieje kilka najważniejszych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, które umożliwiają konstruowanie funkcjonalne:</span><span class="sxs-lookup"><span data-stu-id="a7831-106">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="a7831-107"><xref:System.Xml.Linq.XElement>Konstruktor ma różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="a7831-107">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="a7831-108">Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiekt, który stanie się elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="a7831-108">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="a7831-109">Można przekazać <xref:System.Xml.Linq.XAttribute> obiekt, który stanie się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="a7831-109">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="a7831-110">Lub można przekazać każdy inny typ obiektu, który jest konwertowany na ciąg i stanie się zawartością tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="a7831-110">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="a7831-111"><xref:System.Xml.Linq.XElement>Konstruktor pobiera `params` tablicę typu <xref:System.Object> , dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a7831-111">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="a7831-112">Dzięki temu można utworzyć element, który ma złożoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="a7831-112">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="a7831-113">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601> , kolekcja w obiekcie jest wyliczana i dodawane są wszystkie elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a7831-113">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="a7831-114">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> obiekty lub <xref:System.Xml.Linq.XAttribute> , każdy element w kolekcji zostanie dodany osobno.</span><span class="sxs-lookup"><span data-stu-id="a7831-114">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="a7831-115">Jest to ważne, ponieważ umożliwia przekazywanie wyników zapytania LINQ do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="a7831-115">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="a7831-116">Te funkcje umożliwiają pisanie kodu w celu utworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="a7831-116">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="a7831-117">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="a7831-117">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="a7831-118">Te funkcje umożliwiają również pisanie kodu, który używa wyników zapytań LINQ podczas tworzenia drzewa XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a7831-118">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a7831-119">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a7831-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
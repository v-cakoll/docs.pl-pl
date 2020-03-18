---
title: Konstrukcja funkcjonalna (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635759"
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="1afb4-102">Konstrukcja funkcjonalna (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="1afb4-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="1afb4-103">zapewnia potężny sposób tworzenia elementów XML zwanych *konstrukcją funkcjonalną.*</span><span class="sxs-lookup"><span data-stu-id="1afb4-103">provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="1afb4-104">Funkcjonalna konstrukcja to możliwość tworzenia drzewa XML w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1afb4-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="1afb4-105">Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, które umożliwiają funkcjonalną konstrukcję:</span><span class="sxs-lookup"><span data-stu-id="1afb4-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
- <span data-ttu-id="1afb4-106">Konstruktor <xref:System.Xml.Linq.XElement> przyjmuje różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="1afb4-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="1afb4-107">Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiekt, który staje się elementem podrzędnym.</span><span class="sxs-lookup"><span data-stu-id="1afb4-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="1afb4-108">Można przekazać <xref:System.Xml.Linq.XAttribute> obiekt, który staje się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="1afb4-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="1afb4-109">Lub można przekazać dowolny inny typ obiektu, który jest konwertowany na ciąg i staje się zawartość tekstową elementu.</span><span class="sxs-lookup"><span data-stu-id="1afb4-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
- <span data-ttu-id="1afb4-110">Konstruktor <xref:System.Xml.Linq.XElement> `params` przyjmuje tablicę typu, <xref:System.Object>dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1afb4-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="1afb4-111">Dzięki temu można utworzyć element, który ma złożoną zawartość.</span><span class="sxs-lookup"><span data-stu-id="1afb4-111">This enables you to create an element that has complex content.</span></span>  
  
- <span data-ttu-id="1afb4-112">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana, a wszystkie elementy w kolekcji są dodawane.</span><span class="sxs-lookup"><span data-stu-id="1afb4-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="1afb4-113">Jeśli kolekcja <xref:System.Xml.Linq.XElement> zawiera <xref:System.Xml.Linq.XAttribute> lub obiektów, każdy element w kolekcji jest dodawany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="1afb4-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="1afb4-114">Jest to ważne, ponieważ umożliwia przekazywanie wyników kwerendy LINQ do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="1afb4-114">This is important because it lets you pass the results of a LINQ query to the constructor.</span></span>  
  
 <span data-ttu-id="1afb4-115">Te funkcje umożliwiają pisanie kodu w celu utworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="1afb4-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="1afb4-116">Poniżej przedstawiono przykład:</span><span class="sxs-lookup"><span data-stu-id="1afb4-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="1afb4-117">Funkcje te umożliwiają również pisanie kodu, który używa wyników kwerend LINQ podczas tworzenia drzewa XML, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1afb4-117">These features also enable you to write code that uses the results of LINQ queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="1afb4-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="1afb4-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
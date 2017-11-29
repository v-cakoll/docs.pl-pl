---
title: "Konstrukcja funkcjonalności (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f357de98fae60b3d0b6548ef195b462b4e2f6a5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="functional-construction-linq-to-xml-c"></a><span data-ttu-id="0f8c8-102">Konstrukcja funkcjonalności (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0f8c8-102">Functional Construction (LINQ to XML) (C#)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0f8c8-103">udostępnia zaawansowane metody do tworzenia elementów XML o nazwie *funkcjonalności konstrukcji*.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-103"> provides a powerful way to create XML elements called *functional construction*.</span></span> <span data-ttu-id="0f8c8-104">Konstrukcja funkcjonalności jest możliwość tworzenia drzewo XML w jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-104">Functional construction is the ability to create an XML tree in a single statement.</span></span>  
  
 <span data-ttu-id="0f8c8-105">Istnieje kilka kluczowych funkcji [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] interfejsu programowania, umożliwiające konstrukcji funkcjonalności:</span><span class="sxs-lookup"><span data-stu-id="0f8c8-105">There are several key features of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface that enable functional construction:</span></span>  
  
-   <span data-ttu-id="0f8c8-106"><xref:System.Xml.Linq.XElement> Konstruktor ma różne typy argumentów dla zawartości.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-106">The <xref:System.Xml.Linq.XElement> constructor takes various types of arguments for content.</span></span> <span data-ttu-id="0f8c8-107">Na przykład można przekazać inny <xref:System.Xml.Linq.XElement> obiektu, który staje się elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-107">For example, you can pass another <xref:System.Xml.Linq.XElement> object, which becomes a child element.</span></span> <span data-ttu-id="0f8c8-108">Można przekazać <xref:System.Xml.Linq.XAttribute> obiektu, który staje się atrybutem elementu.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-108">You can pass an <xref:System.Xml.Linq.XAttribute> object, which becomes an attribute of the element.</span></span> <span data-ttu-id="0f8c8-109">Lub może przekazać inny rodzaj obiektu, który jest konwertowana na ciąg i staje się zawartości tekstowej elementu.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-109">Or you can pass any other type of object, which is converted to a string and becomes the text content of the element.</span></span>  
  
-   <span data-ttu-id="0f8c8-110"><xref:System.Xml.Linq.XElement> Konstruktor pobiera `params` tablicy typu <xref:System.Object>, dzięki czemu można przekazać dowolną liczbę obiektów do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-110">The <xref:System.Xml.Linq.XElement> constructor takes a `params` array of type <xref:System.Object>, so that you can pass any number of objects to the constructor.</span></span> <span data-ttu-id="0f8c8-111">Dzięki temu można utworzyć element, który ma zawartość złożoną.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-111">This enables you to create an element that has complex content.</span></span>  
  
-   <span data-ttu-id="0f8c8-112">Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>wyliczeniu kolekcji w obiekcie i zostaną dodane wszystkie elementy w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-112">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="0f8c8-113">Jeśli kolekcja zawiera <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty oddzielnie dodaniu każdego elementu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-113">If the collection contains <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="0f8c8-114">Jest to ważne, ponieważ dzięki temu można przekazać wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-114">This is important because it lets you pass the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to the constructor.</span></span>  
  
 <span data-ttu-id="0f8c8-115">Te funkcje umożliwiają napisać kod, aby utworzyć drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="0f8c8-115">These features enable you to write code to create an XML tree.</span></span> <span data-ttu-id="0f8c8-116">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="0f8c8-116">The following is an example:</span></span>  
  
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
  
 <span data-ttu-id="0f8c8-117">Te funkcje umożliwiają również napisać kod, który używa wyników [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania podczas tworzenia drzewo XML w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0f8c8-117">These features also enable you to write code that uses the results of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries when you create an XML tree, as follows:</span></span>  
  
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
  
 <span data-ttu-id="0f8c8-118">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="0f8c8-118">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f8c8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f8c8-119">See Also</span></span>  
 [<span data-ttu-id="0f8c8-120">Tworzenie drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0f8c8-120">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

---
title: Atomizowane obiekty XName i XNamespace (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204269"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="571ee-102">Atomizowane obiekty XName i XNamespace (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="571ee-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="571ee-103"><xref:System.Xml.Linq.XName>i <xref:System.Xml.Linq.XNamespace> obiekty są *roztamywane;* oznacza to, że jeśli zawierają tę samą kwalifikowaną nazwę, odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="571ee-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="571ee-104">Daje to korzyści wydajności dla zapytań: Podczas porównywania dwóch atomized nazwy równości, podstawowego języka pośredniego ma tylko określić, czy dwa odwołania wskazują na ten sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="571ee-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="571ee-105">Podstawowy kod nie musi wykonywać porównań ciągów, co byłoby czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="571ee-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="571ee-106">Semantyka atomizacji</span><span class="sxs-lookup"><span data-stu-id="571ee-106">Atomization Semantics</span></span>  
 <span data-ttu-id="571ee-107">Atomizacja oznacza, <xref:System.Xml.Linq.XName> że jeśli dwa obiekty mają taką samą nazwę lokalną i znajdują się w tym samym obszarze nazw, mają to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="571ee-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="571ee-108">W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI obszaru nazw, mają to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="571ee-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="571ee-109">Dla klasy, aby włączyć atomized obiektów konstruktora dla klasy musi być prywatny, a nie publiczny.</span><span class="sxs-lookup"><span data-stu-id="571ee-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="571ee-110">Dzieje się tak, ponieważ jeśli konstruktor były publiczne, można utworzyć obiekt niezatomizowany.</span><span class="sxs-lookup"><span data-stu-id="571ee-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="571ee-111">I <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> klasy implementują niejawnego operatora <xref:System.Xml.Linq.XName> konwersji, aby przekonwertować ciąg na ciąg lub <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="571ee-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="571ee-112">W ten sposób można uzyskać wystąpienie tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="571ee-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="571ee-113">Nie można uzyskać wystąpienie przy użyciu konstruktora, ponieważ konstruktor jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="571ee-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="571ee-114"><xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> także wdrożyć równość i nierówności operatorów, aby ustalić, czy dwa obiekty porównywane są odwołania do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="571ee-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="571ee-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="571ee-115">Example</span></span>  
 <span data-ttu-id="571ee-116">Poniższy kod tworzy <xref:System.Xml.Linq.XElement> niektóre obiekty i pokazuje, że identyczne nazwy mają to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="571ee-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 <span data-ttu-id="571ee-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="571ee-117">This example produces the following output:</span></span>  
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="571ee-118">Jak wspomniano wcześniej, zaletą obiektów atomizowanych jest to, że podczas korzystania <xref:System.Xml.Linq.XName> z jednej z metod osi, które przyjmują jako parametr, metoda osi musi tylko określić, że dwie nazwy odwołują się do tego samego wystąpienia, aby wybrać żądane elementy.</span><span class="sxs-lookup"><span data-stu-id="571ee-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="571ee-119">Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> wywołanie <xref:System.Xml.Linq.XContainer.Descendants%2A> metody, która następnie ma lepszą wydajność ze względu na wzorzec atomizacji.</span><span class="sxs-lookup"><span data-stu-id="571ee-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 <span data-ttu-id="571ee-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="571ee-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  

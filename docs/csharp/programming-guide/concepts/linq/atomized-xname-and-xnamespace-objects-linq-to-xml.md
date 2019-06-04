---
title: Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: 0d21397e6885b892f6ac1904e38bd85a78ae07ab
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487597"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a><span data-ttu-id="589b3-102">Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="589b3-102">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="589b3-103"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *rozproszone obiekty*; oznacza to, jeśli zawierają one taką samą nazwę kwalifikowaną, odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="589b3-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="589b3-104">Daje to zalety korzystania z zapytania: Podczas porównywania dwóch nazw rozproszone obiekty pod kątem równości, podstawowy język pośredni ma tylko do określenia, czy dwa odwołania wskazują ten sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="589b3-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="589b3-105">Podstawowy kod ma ciągów porównań, i może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="589b3-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="589b3-106">Rozproszenie semantyki</span><span class="sxs-lookup"><span data-stu-id="589b3-106">Atomization Semantics</span></span>  
 <span data-ttu-id="589b3-107">Rozproszenie oznacza, że jeśli dwa <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="589b3-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="589b3-108">W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, mają tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="589b3-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="589b3-109">Klasy umożliwiające rozproszone obiekty obiektów Konstruktor dla klasy musi być prywatna, nie jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="589b3-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="589b3-110">Jest to spowodowane gdyby publiczny konstruktor można utworzyć obiektu nierozproszonym.</span><span class="sxs-lookup"><span data-stu-id="589b3-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="589b3-111"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementuje operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="589b3-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="589b3-112">Jest to, jak uzyskać wystąpienie tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="589b3-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="589b3-113">Za pomocą konstruktora, nie można pobrać wystąpienia, ponieważ Konstruktor jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="589b3-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="589b3-114"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby ustalić, czy dwa obiekty są porównywane są odwołaniami do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="589b3-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="589b3-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="589b3-115">Example</span></span>  
 <span data-ttu-id="589b3-116">Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiektów i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="589b3-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
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
  
 <span data-ttu-id="589b3-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="589b3-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="589b3-118">Jak wspomniano wcześniej, zaletą rozproszone obiekty obiektów jest fakt, że możesz użyć jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić, to samo wystąpienie, aby wybrać żądaną elementy dwie nazwy odwołania.</span><span class="sxs-lookup"><span data-stu-id="589b3-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="589b3-119">Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu rozproszenie.</span><span class="sxs-lookup"><span data-stu-id="589b3-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
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
  
 <span data-ttu-id="589b3-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="589b3-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  

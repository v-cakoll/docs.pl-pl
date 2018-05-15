---
title: Atomized XName i XNamespace obiektów (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: e311de901a9a54bd4fc6ee56d425cc16b4978e8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="11253-102">Atomized XName i XNamespace obiektów (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11253-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="11253-103"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *atomized*; oznacza to, że jeśli zawierają takiej samej nazwie kwalifikowanej odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="11253-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="11253-104">Daje to zwiększenia wydajności kwerend: podczas porównywania dwóch nazw atomized pod kątem równości ustalić, czy dwa odwołania wskazywać tego samego obiektu ma tylko podstawowy język pośredni.</span><span class="sxs-lookup"><span data-stu-id="11253-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="11253-105">Kod źródłowy ma ciągu porównań, które może być czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="11253-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>  
  
## <a name="atomization-semantics"></a><span data-ttu-id="11253-106">Semantyka Atomizacja</span><span class="sxs-lookup"><span data-stu-id="11253-106">Atomization Semantics</span></span>  
 <span data-ttu-id="11253-107">Atomizacja oznacza, że jeśli dwie <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="11253-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="11253-108">W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają się tym samym identyfikatorem URI przestrzeni nazw, mają tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11253-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>  
  
 <span data-ttu-id="11253-109">Klasy umożliwiające atomized obiektów konstruktora dla klasy musi być prywatny, nie jest publiczna.</span><span class="sxs-lookup"><span data-stu-id="11253-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="11253-110">Jest to spowodowane gdyby publicznego konstruktora, można utworzyć obiektu nierozproszonym.</span><span class="sxs-lookup"><span data-stu-id="11253-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="11253-111"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementować operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="11253-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="11253-112">Jest to, jak pobrać wystąpienia tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="11253-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="11253-113">Nie można pobrać wystąpienia przy użyciu konstruktora, ponieważ Konstruktor jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="11253-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>  
  
 <span data-ttu-id="11253-114"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby określić, czy dwa obiekty są porównywane są odwołania do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="11253-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11253-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="11253-115">Example</span></span>  
 <span data-ttu-id="11253-116">Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiekty i pokazuje, że identycznych nazw współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="11253-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>  
  
```vb  
Dim r1 As New XElement("Root", "data1")  
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")  
  
If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
  
Dim n As XName = "Root"  
  
If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")  
Else  
    Console.WriteLine("Different")  
End If  
```  
  
 <span data-ttu-id="11253-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="11253-117">This example produces the following output:</span></span>  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 <span data-ttu-id="11253-118">Jak wspomniano wcześniej, zaletą atomized obiektów jest fakt, że korzystanie z jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić to samo wystąpienie, aby wybrać odpowiednie elementy dwie nazwy odwołania.</span><span class="sxs-lookup"><span data-stu-id="11253-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>  
  
 <span data-ttu-id="11253-119">W poniższym przykładzie <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu Atomizacja.</span><span class="sxs-lookup"><span data-stu-id="11253-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>  
  
```vb  
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))  
  
Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e  
  
For Each z As var In query  
    Console.WriteLine(z)  
Next  
```  
  
 <span data-ttu-id="11253-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="11253-120">This example produces the following output:</span></span>  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11253-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11253-121">See Also</span></span>  
 [<span data-ttu-id="11253-122">Wydajność (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11253-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

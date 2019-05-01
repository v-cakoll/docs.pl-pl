---
title: Rozproszone obiekty XName i Xnamespace (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: fe0c4429c89e0028b3b012c87684bd14048de27a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951934"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="f8d0c-102">Rozproszone obiekty XName i Xnamespace (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8d0c-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="f8d0c-103"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *rozproszone obiekty*; oznacza to, jeśli zawierają one taką samą nazwę kwalifikowaną, odnoszą się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="f8d0c-104">Daje to zalety korzystania z zapytania: Podczas porównywania dwóch nazw rozproszone obiekty pod kątem równości, podstawowy język pośredni ma tylko do określenia, czy dwa odwołania wskazują ten sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="f8d0c-105">Podstawowy kod ma ciągów porównań, i może zająć dużo czasu.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="f8d0c-106">Rozproszenie semantyki</span><span class="sxs-lookup"><span data-stu-id="f8d0c-106">Atomization Semantics</span></span>

<span data-ttu-id="f8d0c-107">Rozproszenie oznacza, że jeśli dwa <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="f8d0c-108">W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, mają tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="f8d0c-109">Klasy umożliwiające rozproszone obiekty obiektów Konstruktor dla klasy musi być prywatna, nie jest publiczny.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="f8d0c-110">Jest to spowodowane gdyby publiczny konstruktor można utworzyć obiektu nierozproszonym.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="f8d0c-111"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementuje operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="f8d0c-112">Jest to, jak uzyskać wystąpienie tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="f8d0c-113">Za pomocą konstruktora, nie można pobrać wystąpienia, ponieważ Konstruktor jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="f8d0c-114"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby ustalić, czy dwa obiekty są porównywane są odwołaniami do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="f8d0c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8d0c-115">Example</span></span>

<span data-ttu-id="f8d0c-116">Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiektów i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

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

<span data-ttu-id="f8d0c-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f8d0c-117">This example produces the following output:</span></span>

```
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="f8d0c-118">Jak wspomniano wcześniej, zaletą rozproszone obiekty obiektów jest fakt, że możesz użyć jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić, to samo wystąpienie, aby wybrać żądaną elementy dwie nazwy odwołania.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="f8d0c-119">Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu rozproszenie.</span><span class="sxs-lookup"><span data-stu-id="f8d0c-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="f8d0c-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f8d0c-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="f8d0c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8d0c-121">See also</span></span>

- [<span data-ttu-id="f8d0c-122">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8d0c-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

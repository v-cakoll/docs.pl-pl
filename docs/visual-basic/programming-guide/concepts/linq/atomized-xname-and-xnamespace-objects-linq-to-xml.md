---
title: Rozproszone obiekty XName i XNamespace (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 0ffed5d00364f6614b439480607ed521f52754ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345733"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="d62b2-102">Atomed XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d62b2-102">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="d62b2-103">obiekty <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> są *atomowe*; oznacza to, że jeśli zawierają one taką samą kwalifikowaną nazwę, odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d62b2-103"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> objects are *atomized*; that is, if they contain the same qualified name, they refer to the same object.</span></span> <span data-ttu-id="d62b2-104">Zapewnia to korzyści z wydajności dla zapytań: w przypadku porównania dwóch nazw atomowych dla równości, podstawowy język pośredni musi określić, czy te dwa odwołania wskazują na ten sam obiekt.</span><span class="sxs-lookup"><span data-stu-id="d62b2-104">This yields performance benefits for queries: When you compare two atomized names for equality, the underlying intermediate language only has to determine whether the two references point to the same object.</span></span> <span data-ttu-id="d62b2-105">Kod źródłowy nie musi wykonywać porównań ciągów, co byłoby czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="d62b2-105">The underlying code does not have to do string comparisons, which would be time consuming.</span></span>

## <a name="atomization-semantics"></a><span data-ttu-id="d62b2-106">Semantyka rozproszenie</span><span class="sxs-lookup"><span data-stu-id="d62b2-106">Atomization Semantics</span></span>

<span data-ttu-id="d62b2-107">Rozproszenie oznacza, że jeśli dwa obiekty <xref:System.Xml.Linq.XName> mają tę samą nazwę lokalną i znajdują się w tej samej przestrzeni nazw, współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d62b2-107">Atomization means that if two <xref:System.Xml.Linq.XName> objects have the same local name, and they are in the same namespace, they share the same instance.</span></span> <span data-ttu-id="d62b2-108">W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d62b2-108">In the same way, if two <xref:System.Xml.Linq.XNamespace> objects have the same namespace URI, they share the same instance.</span></span>

<span data-ttu-id="d62b2-109">Aby można było włączyć obiekt Atoms, Konstruktor dla klasy musi być prywatny, a nie publiczny.</span><span class="sxs-lookup"><span data-stu-id="d62b2-109">For a class to enable atomized objects, the constructor for the class must be private, not public.</span></span> <span data-ttu-id="d62b2-110">Wynika to z faktu, że jeśli Konstruktor był publiczny, można utworzyć obiekt niebędący atomem.</span><span class="sxs-lookup"><span data-stu-id="d62b2-110">This is because if the constructor were public, you could create a non-atomized object.</span></span> <span data-ttu-id="d62b2-111">Klasy <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> implementują Operator niejawnej konwersji w celu przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>.</span><span class="sxs-lookup"><span data-stu-id="d62b2-111">The <xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> classes implement an implicit conversion operator to convert a string into an <xref:System.Xml.Linq.XName> or <xref:System.Xml.Linq.XNamespace>.</span></span> <span data-ttu-id="d62b2-112">W ten sposób można uzyskać wystąpienie tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="d62b2-112">This is how you get an instance of these objects.</span></span> <span data-ttu-id="d62b2-113">Nie można uzyskać wystąpienia przy użyciu konstruktora, ponieważ Konstruktor jest niedostępny.</span><span class="sxs-lookup"><span data-stu-id="d62b2-113">You cannot get an instance by using a constructor, because the constructor is inaccessible.</span></span>

<span data-ttu-id="d62b2-114"><xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> implementują również operatory równości i nierówności, aby określić, czy dwa obiekty, które są porównywane, są odwołaniami do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d62b2-114"><xref:System.Xml.Linq.XName> and <xref:System.Xml.Linq.XNamespace> also implement the equality and inequality operators, to determine whether the two objects being compared are references to the same instance.</span></span>

## <a name="example"></a><span data-ttu-id="d62b2-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d62b2-115">Example</span></span>

<span data-ttu-id="d62b2-116">Poniższy kod tworzy kilka <xref:System.Xml.Linq.XElement> obiektów i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d62b2-116">The following code creates some <xref:System.Xml.Linq.XElement> objects and demonstrates that identical names share the same instance.</span></span>

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

<span data-ttu-id="d62b2-117">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d62b2-117">This example produces the following output:</span></span>

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

<span data-ttu-id="d62b2-118">Jak wspomniano wcześniej, korzyść w przypadku obiektów atomowych polega na tym, że w przypadku używania jednej z metod osi, która przyjmuje <xref:System.Xml.Linq.XName> jako parametr, metoda osi ma tylko określić, że dwie nazwy odwołują się do tego samego wystąpienia, aby wybrać żądane elementy.</span><span class="sxs-lookup"><span data-stu-id="d62b2-118">As mentioned earlier, the benefit of atomized objects is that when you use one of the axis methods that take an <xref:System.Xml.Linq.XName> as a parameter, the axis method only has to determine that two names reference the same instance to select the desired elements.</span></span>

<span data-ttu-id="d62b2-119">Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> do wywołania metody <xref:System.Xml.Linq.XContainer.Descendants%2A>, które następnie ma lepszą wydajność ze względu na wzorzec rozproszenie.</span><span class="sxs-lookup"><span data-stu-id="d62b2-119">The following example passes an <xref:System.Xml.Linq.XName> to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method call, which then has better performance because of the atomization pattern.</span></span>

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

<span data-ttu-id="d62b2-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="d62b2-120">This example produces the following output:</span></span>

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a><span data-ttu-id="d62b2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d62b2-121">See also</span></span>

- [<span data-ttu-id="d62b2-122">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d62b2-122">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)

---
title: 'Instrukcje: Tworzenie dokumentu z przestrzeniami nazwC#() (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 9b9e81a131d4e17ce2d87dd3f511ed66e370d884
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710006"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="22613-102">Instrukcje: Tworzenie dokumentu z przestrzeniami nazwC#() (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="22613-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="22613-103">W tym temacie pokazano, jak tworzyć dokumenty z przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22613-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="22613-104">Example</span></span>  
 <span data-ttu-id="22613-105">Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiekt.</span><span class="sxs-lookup"><span data-stu-id="22613-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="22613-106">Następnie należy użyć przeciążenia operatora dodawania, aby połączyć przestrzeń nazw z nazwą lokalną wyrażoną jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="22613-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="22613-107">Poniższy przykład tworzy dokument z jedną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="22613-108">Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializować ten dokument przy użyciu domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="22613-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22613-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="22613-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="22613-110">Example</span></span>  
 <span data-ttu-id="22613-111">Poniższy przykład tworzy dokument z jedną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="22613-112">Tworzy również atrybut, który deklaruje przestrzeń nazw z prefiksem przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="22613-113">Aby utworzyć atrybut, który deklaruje przestrzeń nazw z prefiksem, utworzysz atrybut, w którym nazwa atrybutu jest prefiksem przestrzeni nazw, a ta nazwa znajduje się w <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="22613-114">Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="22613-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22613-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="22613-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="22613-116">Example</span></span>  
 <span data-ttu-id="22613-117">Poniższy przykład pokazuje, jak utworzyć dokument zawierający dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="22613-118">Jest to domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-118">One is the default namespace.</span></span> <span data-ttu-id="22613-119">Innym jest przestrzenią nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="22613-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="22613-120">Uwzględniając atrybuty przestrzeni nazw w elemencie głównym, przestrzenie nazw są serializowane, `http://www.adventure-works.com` więc jest to domyślna przestrzeń nazw `www.fourthcoffee.com` i jest serializowany z prefiksem "FC".</span><span class="sxs-lookup"><span data-stu-id="22613-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="22613-121">Aby utworzyć atrybut, który deklaruje domyślną przestrzeń nazw, należy utworzyć atrybut o nazwie "xmlns" bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="22613-122">Wartość atrybutu jest domyślnym identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-122">The value of the attribute is the default namespace URI.</span></span>  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="22613-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22613-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="22613-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="22613-124">Example</span></span>  
 <span data-ttu-id="22613-125">Poniższy przykład tworzy dokument zawierający dwie przestrzenie nazw, zarówno z prefiksami przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="22613-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="22613-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22613-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="22613-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="22613-127">Example</span></span>  
 <span data-ttu-id="22613-128">Innym sposobem osiągnięcia tego samego wyniku jest użycie rozwiniętych nazw zamiast deklarowania i tworzenia <xref:System.Xml.Linq.XNamespace> obiektu.</span><span class="sxs-lookup"><span data-stu-id="22613-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="22613-129">Takie podejście ma wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="22613-129">This approach has performance implications.</span></span> <span data-ttu-id="22613-130">Za każdym razem, gdy przekazujesz ciąg, który zawiera rozwiniętą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nazwę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], należy przeanalizować nazwę, znaleźć wykorzystaną przestrzeń nazw i znaleźć nazwę atomową.</span><span class="sxs-lookup"><span data-stu-id="22613-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="22613-131">Ten proces pobiera czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="22613-131">This process takes CPU time.</span></span> <span data-ttu-id="22613-132">Jeśli wydajność jest ważna, warto zadeklarować obiekt i używać go <xref:System.Xml.Linq.XNamespace> jawnie.</span><span class="sxs-lookup"><span data-stu-id="22613-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="22613-133">Jeśli wydajność jest ważnym problemem, zobacz [pre-rozproszenie of XName Objects (LINQ to XML)C#(),](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="22613-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="22613-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="22613-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22613-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22613-135">See also</span></span>

- [<span data-ttu-id="22613-136">Przegląd przestrzeni nazw (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="22613-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)

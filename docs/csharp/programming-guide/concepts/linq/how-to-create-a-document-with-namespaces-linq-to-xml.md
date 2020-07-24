---
title: Jak utworzyć dokument z przestrzeniami nazw (C#) (LINQ to XML)
description: Dowiedz się, jak utworzyć dokument z przestrzenią nazw w LINQ to XML w języku C# przy użyciu obiektu XNamespace, aby połączyć przestrzeń nazw z nazwą lokalną.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103392"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="b9bdb-103">Jak utworzyć dokument z przestrzeniami nazw (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b9bdb-103">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="b9bdb-104">W tym temacie pokazano, jak tworzyć dokumenty z przestrzeniami nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-104">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9bdb-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bdb-105">Example</span></span>  
 <span data-ttu-id="b9bdb-106">Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiekt.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-106">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="b9bdb-107">Następnie należy użyć przeciążenia operatora dodawania, aby połączyć przestrzeń nazw z nazwą lokalną wyrażoną jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="b9bdb-108">Poniższy przykład tworzy dokument z jedną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="b9bdb-109">Domyślnie program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializować ten dokument przy użyciu domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-109">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b9bdb-110">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9bdb-110">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b9bdb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bdb-111">Example</span></span>  
 <span data-ttu-id="b9bdb-112">Poniższy przykład tworzy dokument z jedną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="b9bdb-113">Tworzy również atrybut, który deklaruje przestrzeń nazw z prefiksem przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="b9bdb-114">Aby utworzyć atrybut, który deklaruje przestrzeń nazw z prefiksem, utworzysz atrybut, w którym nazwa atrybutu jest prefiksem przestrzeni nazw, a ta nazwa znajduje się w <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="b9bdb-115">Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-115">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b9bdb-116">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9bdb-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b9bdb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bdb-117">Example</span></span>  
 <span data-ttu-id="b9bdb-118">Poniższy przykład pokazuje, jak utworzyć dokument zawierający dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="b9bdb-119">Jest to domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-119">One is the default namespace.</span></span> <span data-ttu-id="b9bdb-120">Innym jest przestrzenią nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-120">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="b9bdb-121">Uwzględniając atrybuty przestrzeni nazw w elemencie głównym, przestrzenie nazw są serializowane, więc `http://www.adventure-works.com` jest to domyślna przestrzeń nazw i `www.fourthcoffee.com` jest serializowany z prefiksem "FC".</span><span class="sxs-lookup"><span data-stu-id="b9bdb-121">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="b9bdb-122">Aby utworzyć atrybut, który deklaruje domyślną przestrzeń nazw, należy utworzyć atrybut o nazwie "xmlns" bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-122">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="b9bdb-123">Wartość atrybutu jest domyślnym identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-123">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="b9bdb-124">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9bdb-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b9bdb-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bdb-125">Example</span></span>  
 <span data-ttu-id="b9bdb-126">Poniższy przykład tworzy dokument zawierający dwie przestrzenie nazw, zarówno z prefiksami przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-126">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="b9bdb-127">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9bdb-127">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="b9bdb-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9bdb-128">Example</span></span>  
 <span data-ttu-id="b9bdb-129">Innym sposobem osiągnięcia tego samego wyniku jest użycie rozwiniętych nazw zamiast deklarowania i tworzenia <xref:System.Xml.Linq.XNamespace> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-129">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="b9bdb-130">Takie podejście ma wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-130">This approach has performance implications.</span></span> <span data-ttu-id="b9bdb-131">Za każdym razem, gdy przekazujesz ciąg, który zawiera rozwiniętą nazwę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] należy przeanalizować nazwę, znaleźć wykorzystaną przestrzeń nazw i znaleźć nazwę atomową.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-131">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="b9bdb-132">Ten proces pobiera czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-132">This process takes CPU time.</span></span> <span data-ttu-id="b9bdb-133">Jeśli wydajność jest ważna, warto zadeklarować obiekt i używać go <xref:System.Xml.Linq.XNamespace> jawnie.</span><span class="sxs-lookup"><span data-stu-id="b9bdb-133">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="b9bdb-134">Jeśli wydajność jest ważnym problemem, zobacz [pre-rozproszenie of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) , aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="b9bdb-134">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="b9bdb-135">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b9bdb-135">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9bdb-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9bdb-136">See also</span></span>

- [<span data-ttu-id="b9bdb-137">Przegląd przestrzeni nazw (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9bdb-137">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)

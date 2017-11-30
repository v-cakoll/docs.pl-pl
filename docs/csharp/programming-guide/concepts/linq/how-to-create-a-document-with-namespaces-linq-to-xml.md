---
title: 'Porady: Tworzenie dokumentu z przestrzeni nazw (C#) (LINQ do XML)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d913cdf8b9018aa2bf91fd5a05b823e90ba63df2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="96331-102">Porady: Tworzenie dokumentu z przestrzeni nazw (C#) (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="96331-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="96331-103">W tym temacie przedstawiono sposób tworzenia dokumentów z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96331-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="96331-104">Example</span></span>  
 <span data-ttu-id="96331-105">Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjuj <xref:System.Xml.Linq.XNamespace> obiektu.</span><span class="sxs-lookup"><span data-stu-id="96331-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="96331-106">Następnie należy dodanie przeciążenia operatora połączyć przestrzeni nazw z nazwą lokalną, wyrażone jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="96331-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="96331-107">Poniższy przykład powoduje utworzenie dokumentu o jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="96331-108">Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje ten dokument z domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="96331-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96331-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="96331-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="96331-110">Example</span></span>  
 <span data-ttu-id="96331-111">Poniższy przykład powoduje utworzenie dokumentu o jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="96331-112">Tworzy również atrybut, który deklaruje przestrzeni nazw z prefiksem przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="96331-113">Aby utworzyć atrybutu, który deklaruje przestrzeni nazw z prefiksem, należy utworzyć atrybutu, gdzie nazwa atrybutu jest prefiks przestrzeni nazw, a ta nazwa jest <xref:System.Xml.Linq.XNamespace.Xmlns%2A> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="96331-114">Wartość tego atrybutu jest identyfikatorem URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="96331-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96331-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="96331-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="96331-116">Example</span></span>  
 <span data-ttu-id="96331-117">Poniższy przykład przedstawia tworzenie dokumentu, który zawiera dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="96331-118">Jedna jest domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-118">One is the default namespace.</span></span> <span data-ttu-id="96331-119">Inny jest przestrzenią nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="96331-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="96331-120">W tym przestrzeń nazw atrybutów w elemencie głównym, przestrzenie nazw są serializowane http://www.adventure-works.com jest domyślny obszar nazw, a www.fourthcoffee.com jest serializowany z prefiksem "fc".</span><span class="sxs-lookup"><span data-stu-id="96331-120">By including namespace attributes in the root element, the namespaces are serialized so that http://www.adventure-works.com is the default namespace, and www.fourthcoffee.com is serialized with a prefix of "fc".</span></span> <span data-ttu-id="96331-121">Aby utworzyć atrybutu, który deklaruje domyślnej przestrzeni nazw, należy utworzyć atrybut o nazwie "xmlns", bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="96331-122">Wartość atrybutu jest domyślny identyfikator URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="96331-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96331-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="96331-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="96331-124">Example</span></span>  
 <span data-ttu-id="96331-125">Poniższy przykład tworzy dokument, który zawiera dwie przestrzenie nazw, zarówno z prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="96331-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="96331-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96331-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="96331-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="96331-127">Example</span></span>  
 <span data-ttu-id="96331-128">Innym sposobem wykonania takiego samego wyniku jest używanie rozszerzonych nazw zamiast deklarowanie i tworzenie <xref:System.Xml.Linq.XNamespace> obiektu.</span><span class="sxs-lookup"><span data-stu-id="96331-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="96331-129">Takie podejście ma wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="96331-129">This approach has performance implications.</span></span> <span data-ttu-id="96331-130">Zawsze przekazać ciąg, który zawiera rozwiniętą nazwą do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] należy przeanalizować nazwy, znajdowanie atomized przestrzeni nazw i znaleźć atomized nazwy.</span><span class="sxs-lookup"><span data-stu-id="96331-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="96331-131">Ten proces trwa czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="96331-131">This process takes CPU time.</span></span> <span data-ttu-id="96331-132">Wydajności odgrywa ważną rolę, możesz chcieć deklarowanie i użycie <xref:System.Xml.Linq.XNamespace> jawnie obiektu.</span><span class="sxs-lookup"><span data-stu-id="96331-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="96331-133">Jeśli wydajność jest ważne problemu, zobacz [wstępne Atomizacja obiektów XName (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) Aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="96331-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="96331-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="96331-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96331-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96331-135">See Also</span></span>  
 [<span data-ttu-id="96331-136">Praca z przestrzeni nazw XML (C#)</span><span class="sxs-lookup"><span data-stu-id="96331-136">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

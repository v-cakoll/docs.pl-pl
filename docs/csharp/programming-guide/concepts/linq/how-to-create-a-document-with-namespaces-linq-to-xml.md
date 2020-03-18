---
title: Jak utworzyć dokument z obszarami nazw (C#) (LINQ do XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141323"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="54cc3-102">Jak utworzyć dokument z obszarami nazw (C#) (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="54cc3-102">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="54cc3-103">W tym temacie pokazano, jak tworzyć dokumenty z obszarami nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54cc3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="54cc3-104">Example</span></span>  
 <span data-ttu-id="54cc3-105">Aby utworzyć element lub atrybut, który znajduje się w przestrzeni nazw, należy najpierw zadeklarować i zainicjować <xref:System.Xml.Linq.XNamespace> obiekt.</span><span class="sxs-lookup"><span data-stu-id="54cc3-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="54cc3-106">Następnie należy użyć przeciążenia operatora dodawania, aby połączyć obszar nazw z nazwą lokalną, wyrażoną jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="54cc3-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="54cc3-107">Poniższy przykład tworzy dokument z jednym obszarem nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="54cc3-108">Domyślnie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializuje ten dokument z domyślnym obszarem nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="54cc3-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54cc3-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="54cc3-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="54cc3-110">Example</span></span>  
 <span data-ttu-id="54cc3-111">Poniższy przykład tworzy dokument z jednym obszarem nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="54cc3-112">Tworzy również atrybut, który deklaruje obszar nazw z prefiksem obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="54cc3-113">Aby utworzyć atrybut, który deklaruje obszar nazw z prefiksem, należy utworzyć atrybut, w którym nazwa atrybutu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> jest prefiksem obszaru nazw, a ta nazwa znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="54cc3-114">Wartość tego atrybutu jest identyfikator URI obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="54cc3-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54cc3-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="54cc3-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="54cc3-116">Example</span></span>  
 <span data-ttu-id="54cc3-117">W poniższym przykładzie przedstawiono utworzenie dokumentu, który zawiera dwie przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="54cc3-118">Jednym z nich jest domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-118">One is the default namespace.</span></span> <span data-ttu-id="54cc3-119">Innym jest obszar nazw z prefiksem.</span><span class="sxs-lookup"><span data-stu-id="54cc3-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="54cc3-120">Dołączając atrybuty obszaru nazw do elementu głównego, przestrzenie nazw są serializowane tak, że `http://www.adventure-works.com` jest to domyślny obszar nazw i `www.fourthcoffee.com` jest serializowany z prefiksem "fc".</span><span class="sxs-lookup"><span data-stu-id="54cc3-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="54cc3-121">Aby utworzyć atrybut, który deklaruje domyślny obszar nazw, należy utworzyć atrybut o nazwie "xmlns", bez obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="54cc3-122">Wartość atrybutu jest domyślnym identyfikatorem URI obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="54cc3-123">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54cc3-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="54cc3-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="54cc3-124">Example</span></span>  
 <span data-ttu-id="54cc3-125">Poniższy przykład tworzy dokument, który zawiera dwie przestrzenie nazw, zarówno z prefiksami obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="54cc3-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="54cc3-126">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54cc3-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="54cc3-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="54cc3-127">Example</span></span>  
 <span data-ttu-id="54cc3-128">Innym sposobem osiągnięcia tego samego wyniku jest użycie rozwiniętych <xref:System.Xml.Linq.XNamespace> nazw zamiast deklarowania i tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="54cc3-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="54cc3-129">Takie podejście ma wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="54cc3-129">This approach has performance implications.</span></span> <span data-ttu-id="54cc3-130">Za każdym razem, gdy przekażesz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ciąg zawierający rozwiniętą nazwę, musi przeanalizować nazwę, znaleźć roztomięty obszar nazw i znaleźć roztomiętą nazwę.</span><span class="sxs-lookup"><span data-stu-id="54cc3-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="54cc3-131">Ten proces zajmuje czas procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="54cc3-131">This process takes CPU time.</span></span> <span data-ttu-id="54cc3-132">Jeśli wydajność jest ważna, można zadeklarować <xref:System.Xml.Linq.XNamespace> i używać obiektu jawnie.</span><span class="sxs-lookup"><span data-stu-id="54cc3-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="54cc3-133">Jeśli wydajność jest ważnym problemem, zobacz [Wstępne atomizacja obiektów XName (LINQ do XML) (C#),](./pre-atomization-of-xname-objects-linq-to-xml.md) aby uzyskać więcej informacji</span><span class="sxs-lookup"><span data-stu-id="54cc3-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="54cc3-134">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54cc3-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54cc3-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54cc3-135">See also</span></span>

- [<span data-ttu-id="54cc3-136">Omówienie przestrzeni nazw (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="54cc3-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)

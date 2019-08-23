---
title: Wstawianie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ff9232272124c8706e64162d096eced8640c806
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966955"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="f9415-102">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f9415-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="f9415-103"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera zestaw metod służących do wstawiania węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f9415-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="f9415-104">Aby można było korzystać z tych metod, <xref:System.Xml.XPath.XPathNavigator> obiekt musi być edytowalny, oznacza to, <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> że jego właściwość `true`musi być.</span><span class="sxs-lookup"><span data-stu-id="f9415-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="f9415-105"><xref:System.Xml.XPath.XPathNavigator>obiekty, które mogą edytować dokument XML, są tworzone przy <xref:System.Xml.XmlDocument.CreateNavigator%2A> użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f9415-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f9415-106"><xref:System.Xml.XPath.XPathNavigator>obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasę są tylko do odczytu, a każda próba użycia metod <xref:System.Xml.XPath.XPathNavigator> edycji obiektu utworzonego przez <xref:System.Xml.XPath.XPathDocument> obiekt daje w wyniku <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="f9415-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="f9415-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator> tworzenia edytowalnych obiektów, zobacz [odczytywanie danych XML przy użyciu XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="f9415-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="f9415-108">Wstawianie węzłów</span><span class="sxs-lookup"><span data-stu-id="f9415-108">Inserting Nodes</span></span>  
 <span data-ttu-id="f9415-109"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera metody umożliwiające Wstawianie węzłów równorzędnych, podrzędnych i atrybutów w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f9415-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="f9415-110">Te metody umożliwiają wstawianie węzłów i atrybutów w różnych lokalizacjach w odniesieniu do bieżącego położenia <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="f9415-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="f9415-111">Wstawianie węzłów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="f9415-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="f9415-112"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f9415-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="f9415-113">Te metody wstawiają węzły równorzędne przed i po węźle <xref:System.Xml.XPath.XPathNavigator> , w którym jest obecnie umieszczony obiekt.</span><span class="sxs-lookup"><span data-stu-id="f9415-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="f9415-114"><xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> Metody <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> sąprzeciążoneiakceptują,obiektlubobiektzawierającywęzeł`string`równorzędny, aby dodać jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f9415-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="f9415-115">Obie metody zwracają <xref:System.Xml.XmlWriter> również obiekt używany do wstawiania węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="f9415-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="f9415-116">Metody <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> <xref:System.Xml.XPath.XPathNavigator> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> wstawiają pojedynczy węzeł równorzędny przed i po węźle, w którym aktualnie znajduje się obiekt, przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f9415-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="f9415-117">`pages` W poniższym przykładzie nowy element jest wstawiany `price` przed elementem podrzędnym pierwszego `book` elementu w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="f9415-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="f9415-118">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9415-119">Więcej <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>informacji o metodach <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> , <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f9415-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="f9415-120">Wstawianie węzłów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="f9415-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="f9415-121"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f9415-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="f9415-122">Te metody dołączą i dołączają węzły podrzędne do końca i początku listy węzłów podrzędnych w węźle <xref:System.Xml.XPath.XPathNavigator> , w którym znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="f9415-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="f9415-123">Podobnie jak metody w sekcji "Wstawianie węzłów <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> równorzędnych", a <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody akceptują `string`, <xref:System.Xml.XmlReader> obiekt lub <xref:System.Xml.XPath.XPathNavigator> obiekt zawierający węzeł podrzędny, aby dodać jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f9415-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="f9415-124">Obie metody zwracają <xref:System.Xml.XmlWriter> również obiekt używany do wstawiania węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="f9415-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="f9415-125">Podobnie jak w przypadku metod w sekcji <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> "Wstawianie węzłów równorzędnych" i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody wstawiania pojedynczego węzła podrzędnego do końca i początku listy <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych węzła obiekt jest obecnie umieszczony przy użyciu prefiks przestrzeni nazw, nazwa lokalna, identyfikator URI przestrzeni nazw oraz wartość określona jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f9415-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="f9415-126">W poniższym przykładzie nowy `pages` element podrzędny jest dołączany do listy elementów podrzędnych pierwszego `book` elementu w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="f9415-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="f9415-127">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9415-128">Więcej <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>informacji o metodach <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> , <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> znajduje się w <xref:System.Xml.XPath.XPathNavigator> dokumentacji dotyczącej klasy.</span><span class="sxs-lookup"><span data-stu-id="f9415-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="f9415-129">Wstawianie węzłów atrybutów</span><span class="sxs-lookup"><span data-stu-id="f9415-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="f9415-130"><xref:System.Xml.XPath.XPathNavigator> Klasa zawiera następujące metody wstawiania węzłów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f9415-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="f9415-131">Te metody wstawiają węzły atrybutów w węźle elementu, <xref:System.Xml.XPath.XPathNavigator> w którym obiekt jest obecnie umieszczony.</span><span class="sxs-lookup"><span data-stu-id="f9415-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="f9415-132">Metoda tworzy węzeł atrybutu w <xref:System.Xml.XPath.XPathNavigator> węźle elementu obiekt jest obecnie umieszczony przy użyciu prefiksu przestrzeni nazw, nazwy lokalnej, identyfikatora URI przestrzeni nazw i wartości określonej jako parametry. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A></span><span class="sxs-lookup"><span data-stu-id="f9415-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="f9415-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda<xref:System.Xml.XmlWriter> zwraca obiekt używany do wstawiania węzłów atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f9415-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="f9415-134">W `discount` poniższym przykładzie nowe i `currency` `price` atrybuty są tworzone w elemencie `contosoBooks.xml` podrzędnym pierwszego `book` elementu w pliku przy użyciu <xref:System.Xml.XmlWriter> obiektu zwróconego z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Method.</span><span class="sxs-lookup"><span data-stu-id="f9415-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="f9415-135">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9415-136">Więcej informacji o <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> metodach i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> znajduje się <xref:System.Xml.XPath.XPathNavigator> w dokumentacji dotyczącej klas.</span><span class="sxs-lookup"><span data-stu-id="f9415-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="f9415-137">Kopiowanie węzłów</span><span class="sxs-lookup"><span data-stu-id="f9415-137">Copying Nodes</span></span>  
 <span data-ttu-id="f9415-138">W niektórych przypadkach może być konieczne wypełnienie dokumentu XML zawartością z innego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f9415-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="f9415-139"><xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlDocument> Zarówno Klasa, jak i Klasamogąkopiowaćwęzłydoobiektuzistniejącegoobiektulubobiektu.<xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="f9415-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="f9415-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> Metody,<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> ,<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>i <xref:System.Xml.XmlReader> klasyAllmająprzeciążenia,któremogąakceptowaćobiektlubobiektjakoparametr.<xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="f9415-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="f9415-141"><xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader>Metoda klasy ma przeciążenia, które mogą akceptować obiekt ,,lub.<xref:System.Xml.XmlNode> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlWriter.WriteNode%2A></span><span class="sxs-lookup"><span data-stu-id="f9415-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="f9415-142">Poniższy przykład kopiuje wszystkie `book` elementy z jednego dokumentu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="f9415-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="f9415-143">Wstawianie wartości</span><span class="sxs-lookup"><span data-stu-id="f9415-143">Inserting Values</span></span>  
 <span data-ttu-id="f9415-144">Klasa zawiera metody<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> i,<xref:System.Xml.XmlDocument> które umożliwiają wstawianie wartości dla węzła do obiektu. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="f9415-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="f9415-145">Wstawianie wartości niewpisanych</span><span class="sxs-lookup"><span data-stu-id="f9415-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="f9415-146">Metoda po prostu wstawia `string` wartość bez typu jako parametr jako wartość węzła, na którym <xref:System.Xml.XPath.XPathNavigator> znajduje się obiekt. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A></span><span class="sxs-lookup"><span data-stu-id="f9415-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="f9415-147">Wartość jest wstawiana bez żadnego typu lub bez weryfikowania, czy nowa wartość jest prawidłowa zgodnie z typem węzła, jeśli dostępne są informacje o schemacie.</span><span class="sxs-lookup"><span data-stu-id="f9415-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="f9415-148">W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda jest używana do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="f9415-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="f9415-149">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="f9415-150">Wstawianie wpisanych wartości</span><span class="sxs-lookup"><span data-stu-id="f9415-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="f9415-151">Gdy typ węzła jest typem prostym schematu XML W3C, Nowa wartość wstawiona przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metodę jest sprawdzana względem aspektów typu prostego przed ustawieniem wartości.</span><span class="sxs-lookup"><span data-stu-id="f9415-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="f9415-152">Jeśli nowa wartość jest nieprawidłowa w zależności od typu węzła (na przykład ustawienie wartości `-1` w elemencie, którego typem jest `xs:positiveInteger`), powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9415-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="f9415-153">Poniższy przykład próbuje `price` zmienić wartość elementu pierwszego `book` elementu <xref:System.DateTime> w `contosoBooks.xml` pliku na wartość.</span><span class="sxs-lookup"><span data-stu-id="f9415-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="f9415-154">Ponieważ typ `price` schematu XML elementu jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` plikach, spowoduje to wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9415-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="f9415-155">Przykład pobiera `contosoBooks.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9415-156">Przykład pobiera `contosoBooks.xsd` również jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9415-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="f9415-157">Właściwości InnerXml i OuterXml</span><span class="sxs-lookup"><span data-stu-id="f9415-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="f9415-158">Właściwości <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> klasy zmieniają znaczniki XML w węzłach, w których obiektjestobecnieumieszczony.<xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="f9415-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="f9415-159">Właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych obiekt jest obecnie umieszczony w przeanalizowanej zawartości danego kodu XML `string`. <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A></span><span class="sxs-lookup"><span data-stu-id="f9415-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="f9415-160">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwość zmienia znaczniki XML <xref:System.Xml.XPath.XPathNavigator> węzłów podrzędnych, w których obiekt jest obecnie umieszczony, a także bieżący węzeł.</span><span class="sxs-lookup"><span data-stu-id="f9415-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="f9415-161">Poza metodami opisanymi w tym temacie, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> właściwości i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> mogą służyć do wstawiania węzłów i wartości w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f9415-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="f9415-162">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> używania <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości i do wstawiania węzłów i wartości, zobacz temat [modyfikowanie danych XML przy użyciu elementu XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) .</span><span class="sxs-lookup"><span data-stu-id="f9415-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="f9415-163">Przestrzeń nazw i XML: konflikty lang</span><span class="sxs-lookup"><span data-stu-id="f9415-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="f9415-164">Niektóre konflikty związane z zakresem przestrzeni nazw `xml:lang` i deklaracji mogą wystąpić podczas wstawiania danych XML <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>przy użyciu <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>metod <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> , <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i metody <xref:System.Xml.XPath.XPathNavigator> klasy, która przyjmuje <xref:System.Xml.XmlReader>obiekty jako parametry.</span><span class="sxs-lookup"><span data-stu-id="f9415-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="f9415-165">Poniżej wymieniono potencjalne konflikty przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f9415-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="f9415-166">Jeśli w kontekście <xref:System.Xml.XmlReader> obiektu znajduje się przestrzeń nazw, w której prefiks do mapowania identyfikatora URI przestrzeni nazw nie znajduje się <xref:System.Xml.XPath.XPathNavigator> w kontekście obiektu, zostanie dodana nowa Deklaracja przestrzeni nazw do nowo wstawionego węzła.</span><span class="sxs-lookup"><span data-stu-id="f9415-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="f9415-167">Jeśli ten sam identyfikator URI przestrzeni nazw znajduje się w zakresie zarówno <xref:System.Xml.XmlReader> w kontekście obiektu, <xref:System.Xml.XPath.XPathNavigator> jak i kontekście obiektu, ale ma inny prefiks mapowany na niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, z prefiksem i identyfikator URI przestrzeni nazw pobrany <xref:System.Xml.XmlReader> z obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9415-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="f9415-168">Jeśli ten sam prefiks przestrzeni nazw znajduje się w zakresie zarówno <xref:System.Xml.XmlReader> w kontekście obiektu, <xref:System.Xml.XPath.XPathNavigator> jak i kontekście obiektu, ale ma inny identyfikator URI przestrzeni nazw mapowany do niego w obu kontekstach, Nowa deklaracja przestrzeni nazw jest dodawana do nowo wstawionego węzła, który redeklaruje ten prefiks przy użyciu identyfikatora URI przestrzeni nazw <xref:System.Xml.XmlReader> pobranego z obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9415-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="f9415-169">Jeśli prefiks <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator> oraz identyfikator URI przestrzeni nazw w kontekście obiektu i kontekście obiektu są takie same, do nowo wstawionego węzła nie zostanie dodana żadna Nowa deklaracja przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f9415-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9415-170">Powyższy opis dotyczy również deklaracji przestrzeni nazw z pustym `string` prefiksem (na przykład deklaracji domyślnej przestrzeni nazw).</span><span class="sxs-lookup"><span data-stu-id="f9415-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="f9415-171">Możliwe `xml:lang` są następujące konflikty.</span><span class="sxs-lookup"><span data-stu-id="f9415-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="f9415-172">Jeśli `xml:lang` istnieje atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> w kontekście obiektu, ale nie w kontekście obiektu, `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawionego węzła.</span><span class="sxs-lookup"><span data-stu-id="f9415-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="f9415-173">Jeśli `xml:lang` istnieje atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlReader> zarówno w kontekście obiektu, jak i kontekście obiektu, `xml:lang` ale każdy z nich ma inną wartość, atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiektu jest dodawany do nowo wstawiony węzeł.</span><span class="sxs-lookup"><span data-stu-id="f9415-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="f9415-174">Jeśli istnieje `xml:lang` atrybut w zakresie <xref:System.Xml.XmlReader> zarówno w kontekście <xref:System.Xml.XPath.XPathNavigator> obiektu, jak i kontekstu obiektu, ale każdy z tą samą wartością, żaden nowy `xml:lang` atrybut nie zostanie dodany do nowo wstawionego węzła.</span><span class="sxs-lookup"><span data-stu-id="f9415-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="f9415-175">Jeśli istnieje `xml:lang` atrybut w zakresie <xref:System.Xml.XPath.XPathNavigator> w kontekście obiektu, <xref:System.Xml.XmlReader> ale żaden istniejący w kontekście obiektu nie `xml:lang` zostanie dodany do nowo wstawionego węzła.</span><span class="sxs-lookup"><span data-stu-id="f9415-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="f9415-176">Wstawianie węzłów z XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f9415-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="f9415-177">Metody służące do wstawiania elementów równorzędnych, podrzędnych i atrybutów, które opisano w sekcji "Wstawianie węzłów i wartości" są przeciążone.</span><span class="sxs-lookup"><span data-stu-id="f9415-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="f9415-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>Metody ,<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, iklasy<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> zwracają obiektużywany<xref:System.Xml.XmlWriter> do wstawiania węzłów. <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> <xref:System.Xml.XPath.XPathNavigator></span><span class="sxs-lookup"><span data-stu-id="f9415-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="f9415-179">Nieobsługiwane metody XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f9415-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="f9415-180">Nie wszystkie metody służące do zapisywania informacji w dokumencie XML przy użyciu <xref:System.Xml.XmlWriter> klasy są obsługiwane <xref:System.Xml.XPath.XPathNavigator> przez klasę z powodu różnic między modelem danych XPath a Document Object Model (dom).</span><span class="sxs-lookup"><span data-stu-id="f9415-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="f9415-181">W poniższej tabeli opisano <xref:System.Xml.XmlWriter> metody klasy, które nie są <xref:System.Xml.XPath.XPathNavigator> obsługiwane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="f9415-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="f9415-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="f9415-182">Method</span></span>|<span data-ttu-id="f9415-183">Opis</span><span class="sxs-lookup"><span data-stu-id="f9415-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="f9415-184"><xref:System.NotSupportedException> Zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f9415-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="f9415-185">Ignorowany na poziomie głównym i zgłasza wyjątek <xref:System.NotSupportedException> , jeśli jest wywoływana na dowolnym innym poziomie dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f9415-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="f9415-186">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.</span><span class="sxs-lookup"><span data-stu-id="f9415-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="f9415-187">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.</span><span class="sxs-lookup"><span data-stu-id="f9415-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="f9415-188">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metody dla równoważnego znaku lub znaków.</span><span class="sxs-lookup"><span data-stu-id="f9415-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="f9415-189">Więcej informacji o <xref:System.Xml.XmlWriter> klasie można znaleźć w <xref:System.Xml.XmlWriter> dokumentacji dotyczącej klas.</span><span class="sxs-lookup"><span data-stu-id="f9415-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="f9415-190">Wiele obiektów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="f9415-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="f9415-191">Istnieje możliwość, że wiele <xref:System.Xml.XPath.XPathNavigator> obiektów wskazuje różne części dokumentu XML z co najmniej jednym otwartym <xref:System.Xml.XmlWriter> obiektem.</span><span class="sxs-lookup"><span data-stu-id="f9415-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="f9415-192">Wiele <xref:System.Xml.XmlWriter> obiektów jest dozwolonych i obsługiwanych w scenariuszach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="f9415-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="f9415-193">Poniżej znajdują się ważne uwagi, które należy wziąć <xref:System.Xml.XmlWriter> pod uwagę podczas korzystania z wielu obiektów.</span><span class="sxs-lookup"><span data-stu-id="f9415-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="f9415-194">Fragmenty XML zapisywane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do dokumentu XML, <xref:System.Xml.XmlWriter.Close%2A> gdy wywoływana jest metoda każdego <xref:System.Xml.XmlWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f9415-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="f9415-195">Do tego <xref:System.Xml.XmlWriter> momentu obiekt zapisuje odłączony fragment.</span><span class="sxs-lookup"><span data-stu-id="f9415-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="f9415-196">Jeśli operacja jest wykonywana na dokumencie XML, nie ma to wpływ na wszystkie fragmenty, <xref:System.Xml.XmlWriter> które są zapisywane przez <xref:System.Xml.XmlWriter.Close%2A> obiekt przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="f9415-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="f9415-197">Jeśli istnieje otwarty <xref:System.Xml.XmlWriter> obiekt w określonym poddrzewie XML i że poddrzewo zostanie usunięte <xref:System.Xml.XmlWriter> , obiekt może nadal dodawać do poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="f9415-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="f9415-198">Poddrzewo po prostu zostaje usuniętym fragmentem.</span><span class="sxs-lookup"><span data-stu-id="f9415-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="f9415-199">Jeśli wiele <xref:System.Xml.XmlWriter> obiektów jest otwartych w tym samym punkcie dokumentu XML, są one dodawane do dokumentu XML w kolejności, w <xref:System.Xml.XmlWriter> której obiekty są zamknięte, a nie w kolejności, w jakiej zostały otwarte.</span><span class="sxs-lookup"><span data-stu-id="f9415-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="f9415-200">Poniższy przykład <xref:System.Xml.XmlDocument> tworzy obiekt, <xref:System.Xml.XmlWriter> <xref:System.Xml.XPath.XPathNavigator> tworzy obiekt, a następnie używa obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> `books.xml` metodę w celu utworzenia struktury pierwszej książki w pliku.</span><span class="sxs-lookup"><span data-stu-id="f9415-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="f9415-201">Przykład zapisuje go jako `book.xml` plik.</span><span class="sxs-lookup"><span data-stu-id="f9415-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="f9415-202">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="f9415-202">Saving an XML Document</span></span>  
 <span data-ttu-id="f9415-203">Zapisywanie zmian wprowadzonych <xref:System.Xml.XmlDocument> w obiekcie w wyniku metod opisanych w tym temacie jest wykonywane przy użyciu metod <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="f9415-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f9415-204">Aby uzyskać więcej informacji na temat zapisywania zmian wprowadzonych w <xref:System.Xml.XmlDocument> obiekcie, zobacz [Zapisywanie i pisanie dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="f9415-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9415-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9415-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f9415-206">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="f9415-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f9415-207">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f9415-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f9415-208">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f9415-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)

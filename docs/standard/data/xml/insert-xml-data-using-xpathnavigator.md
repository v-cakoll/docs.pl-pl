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
ms.openlocfilehash: 8b9eedfab68dc6aeacf9ed51ffc7205b73c062ca
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886121"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="b3576-102">Wstawianie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b3576-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="b3576-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które służy do wstawiania element równorzędny, podrzędne i węzłów atrybutu w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b3576-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="b3576-104">Aby można było używać tych metod <xref:System.Xml.XPath.XPathNavigator> obiekt musi być niemożliwa, czyli jego <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> właściwość musi być `true`.</span><span class="sxs-lookup"><span data-stu-id="b3576-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="b3576-105"><xref:System.Xml.XPath.XPathNavigator> obiekty, które można edytować dokumentu XML są tworzone przez <xref:System.Xml.XmlDocument.CreateNavigator%2A> metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="b3576-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b3576-106"><xref:System.Xml.XPath.XPathNavigator> obiekty utworzone przez <xref:System.Xml.XPath.XPathDocument> klasy są przeznaczone tylko do odczytu i dowolne próba należy użyć metod edycji <xref:System.Xml.XPath.XPathNavigator> obiekt utworzony przez <xref:System.Xml.XPath.XPathDocument> skutkuje obiektu <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="b3576-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="b3576-107">Aby uzyskać więcej informacji o tworzeniu edytowalne <xref:System.Xml.XPath.XPathNavigator> obiekty, zobacz [odczytywania danych XML przy użyciu klas XPathDocument i XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span><span class="sxs-lookup"><span data-stu-id="b3576-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="b3576-108">Wstawianie węzłów</span><span class="sxs-lookup"><span data-stu-id="b3576-108">Inserting Nodes</span></span>  
 <span data-ttu-id="b3576-109"><xref:System.Xml.XPath.XPathNavigator> Klasa dostarcza metody, aby wstawić element równorzędny, podrzędne i węzłów atrybutu w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b3576-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="b3576-110">Te metody umożliwiają wstawianie węzłów i atrybuty w różnych lokalizacjach w odniesieniu do bieżącego położenia obiektu <xref:System.Xml.XPath.XPathNavigator> obiektu i są opisane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="b3576-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="b3576-111">Wstawianie węzłów elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="b3576-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="b3576-112"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3576-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="b3576-113">Te metody insert węzłów elementów równorzędnych, przed i po węźle <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="b3576-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="b3576-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> metody są przeciążone i zaakceptuj `string`, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiekt, który zawiera węzeł równorzędny do dodania jako parametry.</span><span class="sxs-lookup"><span data-stu-id="b3576-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="b3576-115">Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3576-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="b3576-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metody Wstaw węzeł równorzędne jednym przed i po węźle <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.</span><span class="sxs-lookup"><span data-stu-id="b3576-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="b3576-117">W poniższym przykładzie nowej `pages` element jest wstawiany przed `price` pierwszy element podrzędny `book` element `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="b3576-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="b3576-118">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b3576-119">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="b3576-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="b3576-120">Wstawianie węzłów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="b3576-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="b3576-121"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3576-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="b3576-122">Te metody dołączyć i Dodaj węzły podrzędne końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="b3576-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="b3576-123">Takie jak metody w sekcji "Wstawianie węzłów elementów równorzędnych" <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> akceptować metod `string`, <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiekt, który zawiera węzeł podrzędny do dodania jako parametry.</span><span class="sxs-lookup"><span data-stu-id="b3576-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="b3576-124">Obie metody zwracają również <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="b3576-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="b3576-125">Metody w sekcji "Wstawianie węzłów elementów równorzędnych" się także podobać <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metody Wstawianie pojedynczy element podrzędny węzła do końca i początku listy węzłów podrzędnych węzła <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z Prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.</span><span class="sxs-lookup"><span data-stu-id="b3576-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="b3576-126">W poniższym przykładzie nowy `pages` elementu podrzędnego jest dołączany do listy elementów podrzędnych pierwszego `book` element `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="b3576-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="b3576-127">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b3576-128">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="b3576-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="b3576-129">Wstawianie węzłów atrybutu</span><span class="sxs-lookup"><span data-stu-id="b3576-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="b3576-130"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia następujące metody, aby wstawić węzłów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b3576-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="b3576-131">Te metody insert węzłów atrybutu w węźle element <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="b3576-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="b3576-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> Metoda tworzy węzeł atrybutu na węzeł elementu <xref:System.Xml.XPath.XPathNavigator> obiekt znajduje się obecnie na temat korzystania z prefiks przestrzeni nazw, lokalna nazwa, identyfikator URI przestrzeni nazw i wartości określonej jako parametry.</span><span class="sxs-lookup"><span data-stu-id="b3576-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="b3576-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda zwraca <xref:System.Xml.XmlWriter> obiekt używany do wstawienia węzłów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b3576-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="b3576-134">W poniższym przykładzie nowy `discount` i `currency` atrybuty są tworzone na `price` pierwszy element podrzędny `book` element `contosoBooks.xml` plików przy użyciu <xref:System.Xml.XmlWriter> obiekt zwracany z <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="b3576-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="b3576-135">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b3576-136">Aby uzyskać więcej informacji na temat <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metod, zobacz <xref:System.Xml.XPath.XPathNavigator> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="b3576-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="b3576-137">Kopiowanie węzłów</span><span class="sxs-lookup"><span data-stu-id="b3576-137">Copying Nodes</span></span>  
 <span data-ttu-id="b3576-138">W niektórych przypadkach można wypełnić dokumentu XML z zawartością z innego dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="b3576-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="b3576-139">Zarówno <xref:System.Xml.XPath.XPathNavigator> klasy i <xref:System.Xml.XmlWriter> klasy można skopiować węzłów <xref:System.Xml.XmlDocument> obiektu z istniejącego <xref:System.Xml.XmlReader> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="b3576-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> i <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy wszystkie mają przeciążenia, które mogą akceptować <xref:System.Xml.XPath.XPathNavigator> obiektu lub <xref:System.Xml.XmlReader> obiektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="b3576-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="b3576-141"><xref:System.Xml.XmlWriter.WriteNode%2A> Metody <xref:System.Xml.XmlWriter> klasa ma przeciążenia, które mogą akceptować <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, lub <xref:System.Xml.XPath.XPathNavigator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="b3576-142">Poniższy przykład kopiuje wszystkie `book` elementy z jednego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b3576-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
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
  
## <a name="inserting-values"></a><span data-ttu-id="b3576-143">Wstawianie wartości</span><span class="sxs-lookup"><span data-stu-id="b3576-143">Inserting Values</span></span>  
 <span data-ttu-id="b3576-144"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> i <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody do wstawienia wartości dla węzła do <xref:System.Xml.XmlDocument> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="b3576-145">Wstawianie wartości bez typu</span><span class="sxs-lookup"><span data-stu-id="b3576-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="b3576-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Metoda po prostu wstawia nietypizowane `string` wartość przekazywana jako parametr jako wartość węzła <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="b3576-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="b3576-147">Wartość jest wstawiany bez dowolnego typu lub bez weryfikacji, nowa wartość jest nieprawidłowa według typu węzła, jeśli informacje schematu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="b3576-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="b3576-148">W poniższym przykładzie <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> metody używane do aktualizowania wszystkich `price` elementów w `contosoBooks.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="b3576-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="b3576-149">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="b3576-150">Wstawianie wartości Typizowane</span><span class="sxs-lookup"><span data-stu-id="b3576-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="b3576-151">Gdy typ węzła jest schematu XML W3C prosty typ, nowej wartości, które są wstawiane przez <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> metody jest sprawdzana względem aspekty typu prostego, zanim ma wartość.</span><span class="sxs-lookup"><span data-stu-id="b3576-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="b3576-152">Jeśli nowa wartość nie jest nieprawidłowa według typu węzła (na przykład ustawienie wartości `-1` w elemencie o typie `xs:positiveInteger`), powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b3576-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="b3576-153">Poniższy przykład podejmie próbę Zmień wartość właściwości `price` element pierwszego `book` element `contosoBooks.xml` plik <xref:System.DateTime> wartość.</span><span class="sxs-lookup"><span data-stu-id="b3576-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="b3576-154">Ponieważ typ schematu XML `price` element jest zdefiniowany jako `xs:decimal` w `contosoBooks.xsd` pliki, powoduje to wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b3576-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
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
  
 <span data-ttu-id="b3576-155">Przykład przyjmuje `contosoBooks.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="b3576-156">Przykład pobiera również `contosoBooks.xsd` jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b3576-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="b3576-157">Właściwości OuterXml i elementu</span><span class="sxs-lookup"><span data-stu-id="b3576-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="b3576-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości <xref:System.Xml.XPath.XPathNavigator> klasy zmienić węzłów znaczniki XML <xref:System.Xml.XPath.XPathNavigator> obiektu jest obecnie ustawiony na.</span><span class="sxs-lookup"><span data-stu-id="b3576-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="b3576-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> przeanalizowany zawartość XML danego obiektu aktualnie jest ustawiony na `string`.</span><span class="sxs-lookup"><span data-stu-id="b3576-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="b3576-160">Podobnie <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> zmienia właściwość znaczników XML węzłów podrzędnych <xref:System.Xml.XPath.XPathNavigator> obiektu aktualnie jest ustawiony na oraz bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="b3576-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="b3576-161">Oprócz metod opisanych w tym temacie <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości może służyć do wstawienia wartości i węzły w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b3576-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="b3576-162">Aby uzyskać więcej informacji o korzystaniu z <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> i <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> właściwości, aby wstawić węzłów i wartości, zobacz [modyfikowanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="b3576-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="b3576-163">Namespace i konfliktów XML: lang</span><span class="sxs-lookup"><span data-stu-id="b3576-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="b3576-164">Niektóre konflikty związane z zakresu przestrzeni nazw i `xml:lang` deklaracje mogą wystąpić podczas wstawiania danych XML przy użyciu <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> i <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy, które umożliwiają wykorzystywanie <xref:System.Xml.XmlReader>obiektów jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="b3576-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="b3576-165">Poniżej przedstawiono możliwe przestrzeń nazw powoduje konflikt.</span><span class="sxs-lookup"><span data-stu-id="b3576-165">The following are the possible namespace conflicts.</span></span>  
  
-   <span data-ttu-id="b3576-166">W przypadku przestrzeni nazw w zakresie w ramach <xref:System.Xml.XmlReader> obiektu kontekstu, w którym długości prefiksu do mapowania identyfikatora URI przestrzeni nazw nie znajduje się w <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, nowe deklaracji przestrzeni nazw jest dodawany do nowo wstawionej węzła.</span><span class="sxs-lookup"><span data-stu-id="b3576-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="b3576-167">Jeśli ten sam identyfikator URI przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu, ale ma inny prefiks mapowane w obu kontekstach, nowe deklaracji przestrzeni nazw jest dodawany do nowo wstawionej węzła, z prefiksem i pobierane z identyfikatora URI obszaru nazw <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="b3576-168">Jeśli ten sam prefiks przestrzeni nazw jest w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale ma inny identyfikator URI przestrzeni nazw jest mapowany do niego w obu kontekstów, deklarację przestrzeni nazw nowych zostaje dodany do węzła nowo wstawionej który ponownie deklaruje tego prefiksu z przestrzenią nazw identyfikatora URI z <xref:System.Xml.XmlReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
-   <span data-ttu-id="b3576-169">Jeśli prefiks, a także identyfikator URI przestrzeni nazw w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> obiektu kontekstu jest taka sama, nie nowe deklaracja przestrzeni nazw jest dodawana do nowo wstawionej węzła.</span><span class="sxs-lookup"><span data-stu-id="b3576-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3576-170">Powyższy opis dotyczy także deklaracje przestrzeni nazw z pustym `string` jako prefiksu (na przykład deklarację domyślnej przestrzeni nazw).</span><span class="sxs-lookup"><span data-stu-id="b3576-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="b3576-171">Poniżej przedstawiono możliwe `xml:lang` konflikty.</span><span class="sxs-lookup"><span data-stu-id="b3576-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
-   <span data-ttu-id="b3576-172">W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XmlReader> kontekst obiektu, ale nie <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do nowo wstawionej węzła.</span><span class="sxs-lookup"><span data-stu-id="b3576-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="b3576-173">W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale każdy ma inną wartość `xml:lang` atrybut, którego wartość jest pobierana z <xref:System.Xml.XmlReader> obiekt jest dodawany do węzeł nowo wstawione.</span><span class="sxs-lookup"><span data-stu-id="b3576-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
-   <span data-ttu-id="b3576-174">W przypadku `xml:lang` atrybutu w zakresie w obu <xref:System.Xml.XmlReader> obiektu kontekstu i <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale każdy z taką samą wartość żadnego nowego `xml:lang` na nowo wstawionej węzła jest dodawany atrybut.</span><span class="sxs-lookup"><span data-stu-id="b3576-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
-   <span data-ttu-id="b3576-175">W przypadku `xml:lang` atrybutu w zakresie w <xref:System.Xml.XPath.XPathNavigator> kontekst obiektu, ale nie istnieje w <xref:System.Xml.XmlReader> obiektu kontekstu, nie `xml:lang` atrybutu jest dodawany do nowo wstawionej węzła.</span><span class="sxs-lookup"><span data-stu-id="b3576-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="b3576-176">Wstawianie węzłów za pomocą XmlWriter</span><span class="sxs-lookup"><span data-stu-id="b3576-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="b3576-177">Są przeciążone metody używane do wstawiania węzłów podrzędnych i atrybutów rodzeństwa opisane w sekcji "Wstawianie węzłów i Values".</span><span class="sxs-lookup"><span data-stu-id="b3576-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="b3576-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> i <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy zwrócenia <xref:System.Xml.XmlWriter> obiektu służy do wstawiania węzłów.</span><span class="sxs-lookup"><span data-stu-id="b3576-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="b3576-179">Nieobsługiwany parametr XmlWriter metody</span><span class="sxs-lookup"><span data-stu-id="b3576-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="b3576-180">Nie wszystkie metody używane do zapisywania dokumentów XML za pomocą informacji <xref:System.Xml.XmlWriter> klasy są obsługiwane przez <xref:System.Xml.XPath.XPathNavigator> klasy z powodu różnic między modelu danych XPath i Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="b3576-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="b3576-181">W poniższej tabeli opisano <xref:System.Xml.XmlWriter> nie są obsługiwane przez metody klasy <xref:System.Xml.XPath.XPathNavigator> klasy.</span><span class="sxs-lookup"><span data-stu-id="b3576-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="b3576-182">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3576-182">Method</span></span>|<span data-ttu-id="b3576-183">Opis</span><span class="sxs-lookup"><span data-stu-id="b3576-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="b3576-184">Zgłasza <xref:System.NotSupportedException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b3576-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="b3576-185">Ignorowane na poziomie głównym i zgłasza <xref:System.NotSupportedException> wyjątek, jeśli wywołano na dowolnym poziomie, w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="b3576-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="b3576-186">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.</span><span class="sxs-lookup"><span data-stu-id="b3576-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="b3576-187">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.</span><span class="sxs-lookup"><span data-stu-id="b3576-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="b3576-188">Traktowane jako wywołanie <xref:System.Xml.XmlWriter.WriteString%2A> metodę równoważne znak lub znaki.</span><span class="sxs-lookup"><span data-stu-id="b3576-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="b3576-189">Aby uzyskać więcej informacji na temat <xref:System.Xml.XmlWriter> klasy, zobacz <xref:System.Xml.XmlWriter> klasy dokumentację referencyjną.</span><span class="sxs-lookup"><span data-stu-id="b3576-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="b3576-190">Wiele obiektów XmlWriter</span><span class="sxs-lookup"><span data-stu-id="b3576-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="b3576-191">Użytkownik może mieć wielu <xref:System.Xml.XPath.XPathNavigator> obiekty, które wskazuje do różnych części pliku XML dokumentu z co najmniej jeden open <xref:System.Xml.XmlWriter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b3576-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="b3576-192">Wiele <xref:System.Xml.XmlWriter> obiekty są dozwolone i obsługiwane w scenariuszach apartamentem.</span><span class="sxs-lookup"><span data-stu-id="b3576-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="b3576-193">Poniżej przedstawiono ważne uwagi, które należy wziąć pod uwagę przy użyciu wielu <xref:System.Xml.XmlWriter> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b3576-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
-   <span data-ttu-id="b3576-194">Fragmenty XML, napisane przez <xref:System.Xml.XmlWriter> obiekty są dodawane do pliku XML dokumentu, gdy <xref:System.Xml.XmlWriter.Close%2A> metoda każdego <xref:System.Xml.XmlWriter> nosi nazwę obiektu.</span><span class="sxs-lookup"><span data-stu-id="b3576-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="b3576-195">Do tego momentu <xref:System.Xml.XmlWriter> obiekt zapisuje odłączonego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="b3576-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="b3576-196">Jeśli operacja jest wykonywana na dokumencie XML, wszystkie fragmenty są zapisywane przez <xref:System.Xml.XmlWriter> obiekt przed <xref:System.Xml.XmlWriter.Close%2A> została wywołana, nie ulegają zmianom.</span><span class="sxs-lookup"><span data-stu-id="b3576-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
-   <span data-ttu-id="b3576-197">W przypadku otwartą <xref:System.Xml.XmlWriter> obiektu w określonej poddrzewo XML i że poddrzewo zostanie usunięty, <xref:System.Xml.XmlWriter> obiekt nadal może dodawać do poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="b3576-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="b3576-198">Poddrzewo staje się po prostu usuniętych fragmentu.</span><span class="sxs-lookup"><span data-stu-id="b3576-198">The subtree simply becomes a deleted fragment.</span></span>  
  
-   <span data-ttu-id="b3576-199">Jeśli wiele <xref:System.Xml.XmlWriter> obiektów są otwarte w tym samym punkcie w dokumencie XML, są dodawane do dokumentu XML w kolejności, w którym <xref:System.Xml.XmlWriter> obiekty zostały zamknięte, nie w kolejności, w jakiej zostały otwarte.</span><span class="sxs-lookup"><span data-stu-id="b3576-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="b3576-200">Poniższy przykład tworzy <xref:System.Xml.XmlDocument> obiekt, tworzy <xref:System.Xml.XPath.XPathNavigator> obiektu, a następnie używa <xref:System.Xml.XmlWriter> obiektu zwróconego przez <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> metodą tworzenia struktury pierwszej książki w `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="b3576-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="b3576-201">Przykład następnie zapisuje ją jako `book.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="b3576-201">The example then saves it as the `book.xml` file.</span></span>  
  
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
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="b3576-202">Zapisywanie dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="b3576-202">Saving an XML Document</span></span>  
 <span data-ttu-id="b3576-203">Zapisywanie zmian <xref:System.Xml.XmlDocument> obiektu jako wynik metod opisanych w tym temacie odbywa się przy użyciu metody <xref:System.Xml.XmlDocument> klasy.</span><span class="sxs-lookup"><span data-stu-id="b3576-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="b3576-204">Aby uzyskać więcej informacji na temat zapisywania zmian <xref:System.Xml.XmlDocument> obiektu, zobacz [zapisywania i zapisywania dokumentu](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span><span class="sxs-lookup"><span data-stu-id="b3576-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3576-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3576-205">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="b3576-206">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="b3576-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="b3576-207">Modyfikowanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b3576-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="b3576-208">Usuwanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b3576-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)

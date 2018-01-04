---
title: "Wyrażenie XPath Namespace nawigacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cae3fa68d3820e98bee333d0252aeb74b15fe2a7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="77159-102">Wyrażenie XPath Namespace nawigacji</span><span class="sxs-lookup"><span data-stu-id="77159-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="77159-103">Aby korzystać z zapytania XPath z dokumentów XML, masz prawidłowego adresowania przestrzeni nazw XML i elementy zawarty w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77159-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="77159-104">Przestrzenie nazw uniknąć niejednoznaczności, które mogą wystąpić podczas nazw są używane w kontekście więcej niż jeden; na przykład nazwa `ID` może odwoływać się do więcej niż jeden identyfikator skojarzony z różnych elementów dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="77159-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="77159-105">Składnia Namespace Określa identyfikatory URI, nazwy i które odróżniania elementów dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="77159-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="77159-106">W przykładzie w tym temacie pokazano użycie prefiksy przechodzenia dokumentu XML z <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="77159-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="77159-107">Aby uzyskać więcej informacji na temat obszarów nazw i składni, zobacz [opis obszarów nazw XML](http://go.microsoft.com/fwlink/?linkid=140245).</span><span class="sxs-lookup"><span data-stu-id="77159-107">For more information about namespaces and syntax, see [Understanding XML Namespaces](http://go.microsoft.com/fwlink/?linkid=140245).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="77159-108">Deklaracje Namespace</span><span class="sxs-lookup"><span data-stu-id="77159-108">Namespace Declarations</span></span>  
 <span data-ttu-id="77159-109">Deklaracje Namespace utworzyć elementów dokumentu XML odróżnienia i mogą być adresowane za pomocą wystąpienia <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="77159-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="77159-110">Prefiksy Namespace Podaj krótki składni adresowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77159-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="77159-111">Prefiksy są definiowane przez formularz: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` w tej składni prefiks "`e`" jest formą skróconą posiadanie identyfikatora URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="77159-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="77159-112">Można zidentyfikować `Body` element jako element członkowski `Envelope` przestrzeni nazw przy użyciu składni: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="77159-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="77159-113">Następujący dokument XML będzie określany jako `response.xml` w przykładzie nawigacji w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="77159-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="77159-114">Nawigacji według prefiksu Namespace</span><span class="sxs-lookup"><span data-stu-id="77159-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="77159-115">Korzysta z kodu w tej sekcji <xref:System.Xml.XPath.XPathNavigator> i <xref:System.Xml.XmlNamespaceManager> obiektów do wybrania `Search` elementu z dokumentu XML w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="77159-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="77159-116">Zapytanie `xpath` zawiera prefiksy przestrzeni nazw dla każdego elementu w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="77159-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="77159-117">Określanie tożsamości dokładne przestrzenie nazw, które zawierają każdy element zapewnia poprawne nawigacji do `Search` elementu przez <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="77159-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 <span data-ttu-id="77159-118">Dokładność pełni kwalifikowanie nazwy i przestrzeni nazw jest większa niż udogodnienie.</span><span class="sxs-lookup"><span data-stu-id="77159-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="77159-119">Nieco eksperymenty z definicji dokumentu i kodu w poprzednich przykładach zweryfikuje, że nawigacji bez nazwy FQDN elementów zgłasza wyjątków.</span><span class="sxs-lookup"><span data-stu-id="77159-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="77159-120">Na przykład definicji elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`i zapytań: ciąg `xpath = "/s:Envelope/s:Body/Search";` bez prefiksu przestrzeni nazw na `Search` zwraca element `null` zamiast `Search` elementu.</span><span class="sxs-lookup"><span data-stu-id="77159-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77159-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77159-121">See Also</span></span>  
 [<span data-ttu-id="77159-122">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="77159-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="77159-123">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="77159-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

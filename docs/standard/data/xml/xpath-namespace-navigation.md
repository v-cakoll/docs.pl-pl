---
title: Nawigacja po przestrzeni nazw XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: f35318b1439b762bf7c87cff217ed1787e8d007c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156325"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="80492-102">Nawigacja po przestrzeni nazw XPath</span><span class="sxs-lookup"><span data-stu-id="80492-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="80492-103">Aby używać zapytań XPath z dokumentami XML, należy poprawnie adresować przestrzenie nazw XML i elementy zawarte w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80492-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="80492-104">Przestrzenie nazw uniemożliwiają niejasności, które mogą wystąpić, gdy nazwy są używane w więcej niż jednym kontekście; na przykład nazwa `ID` może odnosić się do więcej niż jednego identyfikatora skojarzonego z różnymi elementami dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="80492-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="80492-105">Składnia przestrzeni nazw Określa identyfikatory URI, nazwy i prefiksy odróżniające elementy dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="80492-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="80492-106">W przykładzie w tym temacie przedstawiono sposób użycia prefiksów w nawigowaniu po dokumencie XML za pomocą <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="80492-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="80492-107">Aby uzyskać więcej informacji na temat przestrzeni nazw i składni, zobacz [pliki XML: Opis przestrzeni nazw XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="80492-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="80492-108">Deklaracje przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="80492-108">Namespace Declarations</span></span>  
 <span data-ttu-id="80492-109">Deklaracje przestrzeni nazw sprawiają, że elementy dokumentu XML są odróżniane i adresowane podczas korzystania z <xref:System.Xml.XPath.XPathNavigator>wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="80492-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="80492-110">Prefiksy przestrzeni nazw zawierają krótką składnię do adresowania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80492-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="80492-111">Prefiksy są definiowane przez formularz: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` w tej składni prefiks "`e`" jest skrótem dla formalnego identyfikatora URI przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80492-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="80492-112">`Body` Element może być identyfikowany jako element członkowski `Envelope` przestrzeni nazw za pomocą składni: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="80492-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="80492-113">Następujący dokument XML zostanie przywoływany jak `response.xml` w przykładzie nawigacji w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="80492-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="80492-114">Nawigacja według prefiksu przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="80492-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="80492-115">Kod w tej sekcji używa <xref:System.Xml.XPath.XPathNavigator> obiektów i <xref:System.Xml.XmlNamespaceManager> do wybierania `Search` elementu z dokumentu XML w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="80492-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="80492-116">Zapytanie `xpath` zawiera prefiksy przestrzeni nazw dla każdego elementu w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="80492-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="80492-117">Określenie dokładnej tożsamości przestrzeni nazw, które zawierają każdy element, zapewnia poprawną nawigację do `Search` elementu przez <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="80492-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="80492-118">Precyzja w pełni kwalifikujących się przestrzeni nazw i nazw jest większa niż wygoda.</span><span class="sxs-lookup"><span data-stu-id="80492-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="80492-119">Niewielki eksperyment z definicją dokumentu i kodem w poprzednich przykładach sprawdzi, czy nawigacja bez w pełni kwalifikowanych nazw elementów zgłasza wyjątki.</span><span class="sxs-lookup"><span data-stu-id="80492-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="80492-120">Na przykład definicja elementu `<Search xmlns="http://schemas.microsoft.com/v1/Search">`:, i zapytanie: ciąg `xpath = "/s:Envelope/s:Body/Search";` bez prefiksu przestrzeni nazw w `Search` elemencie zwraca `null` zamiast `Search` elementu.</span><span class="sxs-lookup"><span data-stu-id="80492-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80492-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80492-121">See also</span></span>

- [<span data-ttu-id="80492-122">Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="80492-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="80492-123">Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="80492-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

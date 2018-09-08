---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63a394bd30b3586f084dc1a2320fa9133da19b64
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191889"
---
# <a name="xslt-parameters"></a><span data-ttu-id="8daf3-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="8daf3-102">XSLT Parameters</span></span>
<span data-ttu-id="8daf3-103">Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8daf3-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="8daf3-104">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametrów w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="8daf3-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="8daf3-105">Aby użyć parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="8daf3-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="8daf3-106">Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodawanie przy użyciu parametru <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8daf3-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="8daf3-107">Wywołaj parametru z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="8daf3-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="8daf3-108">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8daf3-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="8daf3-109">Typy parametrów</span><span class="sxs-lookup"><span data-stu-id="8daf3-109">Parameter Types</span></span>  
 <span data-ttu-id="8daf3-110">Obiekt parametr powinien odpowiadać typowi W3C.</span><span class="sxs-lookup"><span data-stu-id="8daf3-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="8daf3-111">W poniższej tabeli przedstawiono odpowiednie typy W3C równoważnymi klasami programu Microsoft .NET (typ) i czy typ W3C jest typu XPath lub XSLT.</span><span class="sxs-lookup"><span data-stu-id="8daf3-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="8daf3-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="8daf3-112">W3C type</span></span>|<span data-ttu-id="8daf3-113">Odpowiednik klasy .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="8daf3-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="8daf3-114">Typ XPath lub XSLT</span><span class="sxs-lookup"><span data-stu-id="8daf3-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="8daf3-115">XPath</span><span class="sxs-lookup"><span data-stu-id="8daf3-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="8daf3-116">XPath</span><span class="sxs-lookup"><span data-stu-id="8daf3-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="8daf3-117">XPath</span><span class="sxs-lookup"><span data-stu-id="8daf3-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="8daf3-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="8daf3-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="8daf3-119">XPath</span><span class="sxs-lookup"><span data-stu-id="8daf3-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="8daf3-120">**[] Parametrem XPathNavigator**</span><span class="sxs-lookup"><span data-stu-id="8daf3-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="8daf3-121">XPath</span><span class="sxs-lookup"><span data-stu-id="8daf3-121">XPath</span></span>|  
  
 <span data-ttu-id="8daf3-122">\* Jest odpowiednikiem zestawu węzłów, który zawiera jeden węzeł.</span><span class="sxs-lookup"><span data-stu-id="8daf3-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="8daf3-123">Jeśli obiekt parametr nie jest jedną z powyższych klas, jest konwertowany zgodnie z następującymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="8daf3-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="8daf3-124">Typowe typy liczbowe języka wspólnego (CLR) są konwertowane na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="8daf3-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="8daf3-125"><xref:System.DateTime> Typu jest konwertowany na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="8daf3-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="8daf3-126"><xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="8daf3-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="8daf3-127">**[] Klasy XPathNavigator** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="8daf3-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="8daf3-128">Wszystkie pozostałe typy zgłosić błąd.</span><span class="sxs-lookup"><span data-stu-id="8daf3-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8daf3-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="8daf3-129">Example</span></span>  
 <span data-ttu-id="8daf3-130">W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr do przechowywania obliczeniową z rabatami daty.</span><span class="sxs-lookup"><span data-stu-id="8daf3-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="8daf3-131">Data rabatu jest obliczana za 20 dni od daty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="8daf3-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="8daf3-132">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="8daf3-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="8daf3-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="8daf3-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="8daf3-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="8daf3-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="8daf3-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8daf3-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8daf3-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8daf3-136">See also</span></span>

- [<span data-ttu-id="8daf3-137">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="8daf3-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)

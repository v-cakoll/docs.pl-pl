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
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075439"
---
# <a name="xslt-parameters"></a><span data-ttu-id="58b1f-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="58b1f-102">XSLT Parameters</span></span>
<span data-ttu-id="58b1f-103">Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58b1f-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="58b1f-104">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametrów w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="58b1f-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="58b1f-105">Aby użyć parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="58b1f-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="58b1f-106">Tworzenie <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodawanie przy użyciu parametru <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58b1f-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="58b1f-107">Wywołaj parametru z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="58b1f-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="58b1f-108">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="58b1f-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="58b1f-109">Typy parametrów</span><span class="sxs-lookup"><span data-stu-id="58b1f-109">Parameter Types</span></span>  
 <span data-ttu-id="58b1f-110">Obiekt parametr powinien odpowiadać typowi W3C.</span><span class="sxs-lookup"><span data-stu-id="58b1f-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="58b1f-111">W poniższej tabeli przedstawiono odpowiednie typy W3C równoważnymi klasami programu Microsoft .NET (typ) i czy typ W3C jest typu XPath lub XSLT.</span><span class="sxs-lookup"><span data-stu-id="58b1f-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="58b1f-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="58b1f-112">W3C type</span></span>|<span data-ttu-id="58b1f-113">Odpowiednik klasy .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="58b1f-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="58b1f-114">Typ XPath lub XSLT</span><span class="sxs-lookup"><span data-stu-id="58b1f-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="58b1f-115">XPath</span><span class="sxs-lookup"><span data-stu-id="58b1f-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="58b1f-116">XPath</span><span class="sxs-lookup"><span data-stu-id="58b1f-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="58b1f-117">XPath</span><span class="sxs-lookup"><span data-stu-id="58b1f-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="58b1f-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="58b1f-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="58b1f-119">XPath</span><span class="sxs-lookup"><span data-stu-id="58b1f-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="58b1f-120">**[] Parametrem XPathNavigator**</span><span class="sxs-lookup"><span data-stu-id="58b1f-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="58b1f-121">XPath</span><span class="sxs-lookup"><span data-stu-id="58b1f-121">XPath</span></span>|  
  
 <span data-ttu-id="58b1f-122">\* Jest odpowiednikiem zestawu węzłów, który zawiera jeden węzeł.</span><span class="sxs-lookup"><span data-stu-id="58b1f-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="58b1f-123">Jeśli obiekt parametr nie jest jedną z powyższych klas, jest konwertowany zgodnie z następującymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="58b1f-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="58b1f-124">Typowe typy liczbowe języka wspólnego (CLR) są konwertowane na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="58b1f-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="58b1f-125"><xref:System.DateTime> Typu jest konwertowany na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="58b1f-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="58b1f-126"><xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="58b1f-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="58b1f-127">**[] Klasy XPathNavigator** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="58b1f-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="58b1f-128">Wszystkie pozostałe typy zgłosić błąd.</span><span class="sxs-lookup"><span data-stu-id="58b1f-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58b1f-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="58b1f-129">Example</span></span>  
 <span data-ttu-id="58b1f-130">W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr do przechowywania obliczeniową z rabatami daty.</span><span class="sxs-lookup"><span data-stu-id="58b1f-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="58b1f-131">Data rabatu jest obliczana za 20 dni od daty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="58b1f-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="58b1f-132">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="58b1f-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="58b1f-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="58b1f-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="58b1f-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="58b1f-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="58b1f-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="58b1f-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58b1f-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58b1f-136">See also</span></span>

- [<span data-ttu-id="58b1f-137">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="58b1f-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)

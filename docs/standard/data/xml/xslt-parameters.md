---
title: Parametry XSLT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b16ad921e5b16ab7564b2ceedab91c6b6073537d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-parameters"></a><span data-ttu-id="64499-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="64499-102">XSLT Parameters</span></span>
<span data-ttu-id="64499-103">Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="64499-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="64499-104">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametru o tej godzinie.</span><span class="sxs-lookup"><span data-stu-id="64499-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="64499-105">Aby użyć parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="64499-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="64499-106">Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą parametru <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="64499-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="64499-107">Wywołania parametr z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="64499-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="64499-108">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="64499-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="64499-109">Typy parametrów</span><span class="sxs-lookup"><span data-stu-id="64499-109">Parameter Types</span></span>  
 <span data-ttu-id="64499-110">Obiekt parametru powinna odpowiadać typowi W3C.</span><span class="sxs-lookup"><span data-stu-id="64499-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="64499-111">W poniższej tabeli przedstawiono odpowiednie typy W3C równoważnymi klasami programu Microsoft .NET (typ), oraz czy typ W3C jest typu XPath lub XSLT.</span><span class="sxs-lookup"><span data-stu-id="64499-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="64499-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="64499-112">W3C type</span></span>|<span data-ttu-id="64499-113">Odpowiednik klasę platformy .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="64499-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="64499-114">Typ wyrażenia XPath lub XSLT</span><span class="sxs-lookup"><span data-stu-id="64499-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="64499-115">XPath</span><span class="sxs-lookup"><span data-stu-id="64499-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="64499-116">XPath</span><span class="sxs-lookup"><span data-stu-id="64499-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="64499-117">XPath</span><span class="sxs-lookup"><span data-stu-id="64499-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="64499-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="64499-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="64499-119">XPath</span><span class="sxs-lookup"><span data-stu-id="64499-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="64499-120">**Element XPathNavigator]**</span><span class="sxs-lookup"><span data-stu-id="64499-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="64499-121">XPath</span><span class="sxs-lookup"><span data-stu-id="64499-121">XPath</span></span>|  
  
 <span data-ttu-id="64499-122">* To jest odpowiednikiem zestawu węzłów zawierającego jeden węzeł.</span><span class="sxs-lookup"><span data-stu-id="64499-122">*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="64499-123">Jeśli parametr obiektu nie jest jednym z powyższych klas, jest konwertowana zgodnie z następującymi zasadami.</span><span class="sxs-lookup"><span data-stu-id="64499-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="64499-124">Popularne typy liczbowe języka wspólnego (CLR) są konwertowane na <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="64499-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="64499-125"><xref:System.DateTime> Typu jest konwertowana na <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="64499-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="64499-126"><xref:System.Xml.XPath.IXPathNavigable>typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="64499-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="64499-127">**Element XPathNavigator []** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="64499-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="64499-128">Wszystkie inne typy Zgłoś błąd.</span><span class="sxs-lookup"><span data-stu-id="64499-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64499-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="64499-129">Example</span></span>  
 <span data-ttu-id="64499-130">W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> Data rabatu metodę w celu utworzenia parametru do przechowywania obliczeniowej.</span><span class="sxs-lookup"><span data-stu-id="64499-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="64499-131">Data rabatu jest obliczany 20 dni od daty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="64499-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="64499-132">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="64499-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="64499-133">ORDER.XML</span><span class="sxs-lookup"><span data-stu-id="64499-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="64499-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="64499-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="64499-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="64499-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64499-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64499-136">See Also</span></span>  
 [<span data-ttu-id="64499-137">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="64499-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)

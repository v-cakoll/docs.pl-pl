---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 7651360b375071c48ba0d23b64881ac794e51e86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282535"
---
# <a name="xslt-parameters"></a><span data-ttu-id="429cf-102">Parametry XSLT</span><span class="sxs-lookup"><span data-stu-id="429cf-102">XSLT Parameters</span></span>
<span data-ttu-id="429cf-103">Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody using.</span><span class="sxs-lookup"><span data-stu-id="429cf-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="429cf-104">Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametru w tym czasie.</span><span class="sxs-lookup"><span data-stu-id="429cf-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="429cf-105">Aby użyć parametru XSLT</span><span class="sxs-lookup"><span data-stu-id="429cf-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="429cf-106">Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiekt i Dodaj parametr przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="429cf-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="429cf-107">Wywołaj parametr z arkusza stylów.</span><span class="sxs-lookup"><span data-stu-id="429cf-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="429cf-108">Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="429cf-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="429cf-109">Typy parametrów</span><span class="sxs-lookup"><span data-stu-id="429cf-109">Parameter Types</span></span>  
 <span data-ttu-id="429cf-110">Obiekt parametru powinien odpowiadać typowi W3C.</span><span class="sxs-lookup"><span data-stu-id="429cf-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="429cf-111">W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy Microsoft .NET (typ) i określające, czy typ W3C jest typem XPath czy XSLT.</span><span class="sxs-lookup"><span data-stu-id="429cf-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="429cf-112">Typ W3C</span><span class="sxs-lookup"><span data-stu-id="429cf-112">W3C type</span></span>|<span data-ttu-id="429cf-113">Równoważna Klasa platformy .NET (typ)</span><span class="sxs-lookup"><span data-stu-id="429cf-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="429cf-114">XPath lub typ XSLT</span><span class="sxs-lookup"><span data-stu-id="429cf-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="429cf-115">XPath</span><span class="sxs-lookup"><span data-stu-id="429cf-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="429cf-116">XPath</span><span class="sxs-lookup"><span data-stu-id="429cf-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="429cf-117">XPath</span><span class="sxs-lookup"><span data-stu-id="429cf-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="429cf-118">XSL</span><span class="sxs-lookup"><span data-stu-id="429cf-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="429cf-119">XPath</span><span class="sxs-lookup"><span data-stu-id="429cf-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="429cf-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="429cf-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="429cf-121">XPath</span><span class="sxs-lookup"><span data-stu-id="429cf-121">XPath</span></span>|  
  
 <span data-ttu-id="429cf-122">\* Jest to odpowiednik zestawu węzłów, który zawiera pojedynczy węzeł.</span><span class="sxs-lookup"><span data-stu-id="429cf-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="429cf-123">Jeśli obiekt parametru nie jest jedną z powyższych klas, jest konwertowany zgodnie z poniższymi regułami.</span><span class="sxs-lookup"><span data-stu-id="429cf-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="429cf-124">Typy liczbowe środowiska uruchomieniowego języka wspólnego (CLR) są konwertowane na <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="429cf-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="429cf-125"><xref:System.DateTime>Typ jest konwertowany na <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="429cf-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="429cf-126"><xref:System.Xml.XPath.IXPathNavigable>typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="429cf-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="429cf-127">Element **XPathNavigator []** jest konwertowany na <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="429cf-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="429cf-128">Wszystkie inne typy zgłaszają błąd.</span><span class="sxs-lookup"><span data-stu-id="429cf-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="429cf-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="429cf-129">Example</span></span>  
 <span data-ttu-id="429cf-130">W poniższym przykładzie zastosowano <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr służący do przechowywania obliczonej daty rabatu.</span><span class="sxs-lookup"><span data-stu-id="429cf-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="429cf-131">Data rabatu jest obliczana na 20 dni od daty zamówienia.</span><span class="sxs-lookup"><span data-stu-id="429cf-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="429cf-132">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="429cf-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="429cf-133">Order. XML</span><span class="sxs-lookup"><span data-stu-id="429cf-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="429cf-134">Discount. xsl</span><span class="sxs-lookup"><span data-stu-id="429cf-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="429cf-135">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="429cf-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="429cf-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="429cf-136">See also</span></span>

- [<span data-ttu-id="429cf-137">Przekształcenia XSLT</span><span class="sxs-lookup"><span data-stu-id="429cf-137">XSLT Transformations</span></span>](xslt-transformations.md)

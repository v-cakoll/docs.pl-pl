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
ms.openlocfilehash: ef57d16c52100398919563205a97205be3c5dd7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xslt-parameters"></a>Parametry XSLT
Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametru o tej godzinie.  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
1.  Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiektu i dodać za pomocą parametru <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.  
  
2.  Wywołania parametr z arkusza stylów.  
  
3.  Przekaż <xref:System.Xml.Xsl.XsltArgumentList> do obiektu <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="parameter-types"></a>Typy parametrów  
 Obiekt parametru powinna odpowiadać typowi W3C. W poniższej tabeli przedstawiono odpowiednie typy W3C równoważnymi klasami programu Microsoft .NET (typ), oraz czy typ W3C jest typu XPath lub XSLT.  
  
|Typ W3C|Odpowiednik klasę platformy .NET (typ)|Typ wyrażenia XPath lub XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **Element XPathNavigator]**|XPath|  
  
 * To jest odpowiednikiem zestawu węzłów zawierającego jeden węzeł.  
  
 Jeśli parametr obiektu nie jest jednym z powyższych klas, jest konwertowana zgodnie z następującymi zasadami. Popularne typy liczbowe języka wspólnego (CLR) są konwertowane na <xref:System.Double>. <xref:System.DateTime> Typu jest konwertowana na <xref:System.String>. <xref:System.Xml.XPath.IXPathNavigable> typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator>. **Element XPathNavigator []** jest konwertowana na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Wszystkie inne typy Zgłoś błąd.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> Data rabatu metodę w celu utworzenia parametru do przechowywania obliczeniowej. Data rabatu jest obliczany 20 dni od daty zamówienia.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="orderxml"></a>order.xml  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>discount.xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Dane wyjściowe  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)

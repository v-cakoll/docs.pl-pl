---
title: Parametry XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: cc412042e69a43bbecec9dbe68618e2d307ca793
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709702"
---
# <a name="xslt-parameters"></a>Parametry XSLT
Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> przy użyciu metody <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametru w tym czasie.  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
1. Utwórz obiekt <xref:System.Xml.Xsl.XsltArgumentList> i Dodaj parametr przy użyciu metody <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Wywołaj parametr z arkusza stylów.  
  
3. Przekaż obiekt <xref:System.Xml.Xsl.XsltArgumentList> do metody <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="parameter-types"></a>Typy parametrów  
 Obiekt parametru powinien odpowiadać typowi W3C. W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy Microsoft .NET (typ) i określające, czy typ W3C jest typem XPath czy XSLT.  
  
|Typ W3C|Równoważna Klasa platformy .NET (typ)|XPath lub typ XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|{1&gt;XPath&lt;1}|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator[]**|{1&gt;XPath&lt;1}|  
  
 \* Jest to odpowiednik zestawu węzłów, który zawiera pojedynczy węzeł.  
  
 Jeśli obiekt parametru nie jest jedną z powyższych klas, jest konwertowany zgodnie z poniższymi regułami. Typy liczbowe środowiska uruchomieniowego języka wspólnego (CLR) są konwertowane na <xref:System.Double>. Typ <xref:System.DateTime> jest konwertowany na <xref:System.String>. typy <xref:System.Xml.XPath.IXPathNavigable> są konwertowane na <xref:System.Xml.XPath.XPathNavigator>. Element **XPathNavigator []** został przekonwertowany na <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Wszystkie inne typy zgłaszają błąd.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano metodę <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>, aby utworzyć parametr służący do przechowywania obliczonej daty rabatu. Data rabatu jest obliczana na 20 dni od daty zamówienia.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="orderxml"></a>order.xml  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>Discount. xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Dane wyjściowe  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przekształcenia XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)

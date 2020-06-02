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
# <a name="xslt-parameters"></a>Parametry XSLT
Parametry XSLT są dodawane do <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody using. Kwalifikowana nazwa i identyfikator URI przestrzeni nazw są skojarzone z obiektem parametru w tym czasie.  
  
### <a name="to-use-an-xslt-parameter"></a>Aby użyć parametru XSLT  
  
1. Utwórz <xref:System.Xml.Xsl.XsltArgumentList> obiekt i Dodaj parametr przy użyciu <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metody.  
  
2. Wywołaj parametr z arkusza stylów.  
  
3. Przekaż <xref:System.Xml.Xsl.XsltArgumentList> obiekt do <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metody.  
  
## <a name="parameter-types"></a>Typy parametrów  
 Obiekt parametru powinien odpowiadać typowi W3C. W poniższej tabeli przedstawiono odpowiednie typy W3C, równoważne klasy Microsoft .NET (typ) i określające, czy typ W3C jest typem XPath czy XSLT.  
  
|Typ W3C|Równoważna Klasa platformy .NET (typ)|XPath lub typ XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSL|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator []**|XPath|  
  
 * Jest to odpowiednik zestawu węzłów, który zawiera pojedynczy węzeł.  
  
 Jeśli obiekt parametru nie jest jedną z powyższych klas, jest konwertowany zgodnie z poniższymi regułami. Typy liczbowe środowiska uruchomieniowego języka wspólnego (CLR) są konwertowane na <xref:System.Double> . <xref:System.DateTime>Typ jest konwertowany na <xref:System.String> . <xref:System.Xml.XPath.IXPathNavigable>typy są konwertowane na <xref:System.Xml.XPath.XPathNavigator> . Element **XPathNavigator []** jest konwertowany na <xref:System.Xml.XPath.XPathNodeIterator> .  
  
 Wszystkie inne typy zgłaszają błąd.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> metodę, aby utworzyć parametr służący do przechowywania obliczonej daty rabatu. Data rabatu jest obliczana na 20 dni od daty zamówienia.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Dane wejściowe  
  
##### <a name="orderxml"></a>Order. XML  
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

- [Przekształcenia XSLT](xslt-transformations.md)

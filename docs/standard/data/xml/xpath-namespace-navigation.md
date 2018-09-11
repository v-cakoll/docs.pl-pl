---
title: Wyrażenie XPath Namespace nawigacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6d4f63dacc09208176b47dbca38783f1e9bc0a1
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365345"
---
# <a name="xpath-namespace-navigation"></a>Wyrażenie XPath Namespace nawigacji
Zapytania XPath za pomocą dokumentów XML, masz prawidłowego adresowania przestrzeni nazw XML i elementy zawarte w przestrzeni nazw. Przestrzenie nazw zapobiec niejasności, które mogą wystąpić podczas nazwy są używane w więcej niż jednym kontekście; na przykład nazwa `ID` mogą odwoływać się do więcej niż jeden identyfikator skojarzony z różnych elementów dokumentu XML. Składnia Namespace określa identyfikatorów, nazw i prefiksy, które odróżniania elementów dokumentu XML.  
  
 W przykładzie w tym temacie pokazano użycie prefiksy przechodzenia dokumentu XML z <xref:System.Xml.XPath.XPathNavigator>. Aby uzyskać więcej informacji na temat przestrzenie nazw i składnię, zobacz [przestrzeni nazw XML opis](https://msdn.microsoft.com/library/aa468565.aspx).  
  
## <a name="namespace-declarations"></a>Deklaracji Namespace  
 Deklaracji Namespace uzupełnić elementów dokumentu XML rozróżnialnych i mogą być adresowane podczas korzystania z wystąpienia <xref:System.Xml.XPath.XPathNavigator>. Prefiksy Namespace Podaj krótki opis składni adresowania przestrzeni nazw.  
  
 Prefiksy są definiowane przez formularz: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` w tej składni prefiks "`e`" jest formą skróconą posiadanie identyfikatora URI obszaru nazw. Można zidentyfikować `Body` element będący członkiem `Envelope` przestrzeni nazw przy użyciu składni: `e:Body`.  
  
 Następujący dokument XML będzie odwoływać się jak `response.xml` w przykładzie nawigacji w następnej sekcji.  
  
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
  
## <a name="navigation-by-namespace-prefix"></a>Nawigacja według prefiksu Namespace  
 W kodzie w tej sekcji użyto <xref:System.Xml.XPath.XPathNavigator> i <xref:System.Xml.XmlNamespaceManager> obiektów do wybrania `Search` elementu z dokumentu XML w poprzedniej sekcji. Zapytanie `xpath` zawiera prefiksy przestrzeni nazw dla każdego elementu w ścieżce. Określanie tożsamości dokładne przestrzeni nazw, która zawiera każdy element gwarantuje poprawną nawigację do `Search` elementu przez <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody.  
  
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
  
 Dokładność pełni kwalifikujących się do przestrzeni nazw i nazwy jest większa niż udogodnienie. Eksperymentowanie z definicji dokumentu i kodu w poprzednich przykładach sprawdzi, czy nawigacji bez nazwy elementów w pełni kwalifikowaną zgłasza wyjątek wyjątków. Na przykład definicji elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`i zapytań: ciąg `xpath = "/s:Envelope/s:Body/Search";` bez prefiksu przestrzeni nazw na `Search` element zwraca `null` zamiast `Search` elementu.  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

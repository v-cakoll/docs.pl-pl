---
title: Wyrażenie XPath Namespace nawigacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed73c0a9c9bb4fba2644d76f470a8bdcace2b83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xpath-namespace-navigation"></a>Wyrażenie XPath Namespace nawigacji
Aby korzystać z zapytania XPath z dokumentów XML, masz prawidłowego adresowania przestrzeni nazw XML i elementy zawarty w przestrzeni nazw. Przestrzenie nazw uniknąć niejednoznaczności, które mogą wystąpić podczas nazw są używane w kontekście więcej niż jeden; na przykład nazwa `ID` może odwoływać się do więcej niż jeden identyfikator skojarzony z różnych elementów dokumentu XML. Składnia Namespace Określa identyfikatory URI, nazwy i które odróżniania elementów dokumentu XML.  
  
 W przykładzie w tym temacie pokazano użycie prefiksy przechodzenia dokumentu XML z <xref:System.Xml.XPath.XPathNavigator>. Aby uzyskać więcej informacji na temat obszarów nazw i składni, zobacz [opis obszarów nazw XML](https://msdn.microsoft.com/library/aa468565.aspx).  
  
## <a name="namespace-declarations"></a>Deklaracje Namespace  
 Deklaracje Namespace utworzyć elementów dokumentu XML odróżnienia i mogą być adresowane za pomocą wystąpienia <xref:System.Xml.XPath.XPathNavigator>. Prefiksy Namespace Podaj krótki składni adresowania przestrzeni nazw.  
  
 Prefiksy są definiowane przez formularz: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` w tej składni prefiks "`e`" jest formą skróconą posiadanie identyfikatora URI przestrzeni nazw. Można zidentyfikować `Body` element jako element członkowski `Envelope` przestrzeni nazw przy użyciu składni: `e:Body`.  
  
 Następujący dokument XML będzie określany jako `response.xml` w przykładzie nawigacji w następnej sekcji.  
  
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
  
## <a name="navigation-by-namespace-prefix"></a>Nawigacji według prefiksu Namespace  
 Korzysta z kodu w tej sekcji <xref:System.Xml.XPath.XPathNavigator> i <xref:System.Xml.XmlNamespaceManager> obiektów do wybrania `Search` elementu z dokumentu XML w poprzedniej sekcji. Zapytanie `xpath` zawiera prefiksy przestrzeni nazw dla każdego elementu w ścieżce. Określanie tożsamości dokładne przestrzenie nazw, które zawierają każdy element zapewnia poprawne nawigacji do `Search` elementu przez <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody.  
  
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
  
 Dokładność pełni kwalifikowanie nazwy i przestrzeni nazw jest większa niż udogodnienie. Nieco eksperymenty z definicji dokumentu i kodu w poprzednich przykładach zweryfikuje, że nawigacji bez nazwy FQDN elementów zgłasza wyjątków. Na przykład definicji elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`i zapytań: ciąg `xpath = "/s:Envelope/s:Body/Search";` bez prefiksu przestrzeni nazw na `Search` zwraca element `null` zamiast `Search` elementu.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

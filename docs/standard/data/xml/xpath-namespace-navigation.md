---
title: Nawigacja po przestrzeni nazw XPath
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: dce7d81d4249cb40c3be6dee4b8bd25951ccb10a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283211"
---
# <a name="xpath-namespace-navigation"></a>Nawigacja po przestrzeni nazw XPath
Aby używać zapytań XPath z dokumentami XML, należy poprawnie adresować przestrzenie nazw XML i elementy zawarte w przestrzeni nazw. Przestrzenie nazw uniemożliwiają niejasności, które mogą wystąpić, gdy nazwy są używane w więcej niż jednym kontekście; na przykład nazwa `ID` może odnosić się do więcej niż jednego identyfikatora skojarzonego z różnymi elementami dokumentu XML. Składnia przestrzeni nazw Określa identyfikatory URI, nazwy i prefiksy odróżniające elementy dokumentu XML.  
  
 W przykładzie w tym temacie przedstawiono sposób użycia prefiksów w nawigowaniu po dokumencie XML za pomocą <xref:System.Xml.XPath.XPathNavigator> . Aby uzyskać więcej informacji na temat przestrzeni nazw i składni, zobacz [pliki XML: Opis przestrzeni nazw XML](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).  
  
## <a name="namespace-declarations"></a>Deklaracje przestrzeni nazw  
 Deklaracje przestrzeni nazw sprawiają, że elementy dokumentu XML są odróżniane i adresowane podczas korzystania z wystąpienia <xref:System.Xml.XPath.XPathNavigator> . Prefiksy przestrzeni nazw zawierają krótką składnię do adresowania przestrzeni nazw.  
  
 Prefiksy są definiowane przez formularz: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` w tej składni prefiks " `e` " jest skrótem dla formalnego identyfikatora URI przestrzeni nazw. Element może być identyfikowany `Body` jako element członkowski `Envelope` przestrzeni nazw za pomocą składni: `e:Body` .  
  
 Następujący dokument XML zostanie przywoływany jak `response.xml` w przykładzie nawigacji w następnej sekcji.  
  
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
  
## <a name="navigation-by-namespace-prefix"></a>Nawigacja według prefiksu przestrzeni nazw  
 Kod w tej sekcji używa <xref:System.Xml.XPath.XPathNavigator> obiektów i <xref:System.Xml.XmlNamespaceManager> do wybierania `Search` elementu z dokumentu XML w poprzedniej sekcji. Zapytanie `xpath` zawiera prefiksy przestrzeni nazw dla każdego elementu w ścieżce. Określenie dokładnej tożsamości przestrzeni nazw, które zawierają każdy element, zapewnia poprawną nawigację do `Search` elementu przez <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metodę.  
  
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
  
 Precyzja w pełni kwalifikujących się przestrzeni nazw i nazw jest większa niż wygoda. Niewielki eksperyment z definicją dokumentu i kodem w poprzednich przykładach sprawdzi, czy nawigacja bez w pełni kwalifikowanych nazw elementów zgłasza wyjątki. Na przykład definicja elementu: `<Search xmlns="http://schemas.microsoft.com/v1/Search">` , i zapytanie: ciąg `xpath = "/s:Envelope/s:Body/Search";` bez prefiksu przestrzeni nazw w `Search` elemencie zwraca `null` zamiast `Search` elementu.  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych XML przy użyciu klasy XPathNavigator](accessing-xml-data-using-xpathnavigator.md)
- [Wybieranie, obliczanie i dopasowywanie danych XML przy użyciu klasy XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)

---
title: LINQ do XML w porównaniu z innymi technologiami XML3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 4cade6ecbee95ee288db34246986858609697731
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635681"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ do XML w porównaniu z innymi technologiami XML
W tym [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] temacie porównano z <xref:System.Xml.XmlReader>następującymi technologiami XML: , XSLT, MSXML i XmlLite. Te informacje mogą pomóc w podjęciu decyzji, której technologii użyć.  
  
 Aby porównać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] model obiektu dokumentu (DOM), zobacz [LINQ do XML vs. DOM (C#)](./linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ do XML vs. XmlReader  
 <xref:System.Xml.XmlReader>jest przewijanym, tylko do przodu, nie buforującym analizatorem.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest wdrażana na <xref:System.Xml.XmlReader>wierzchu i są ściśle zintegrowane. Jednak można również <xref:System.Xml.XmlReader> użyć samodzielnie.  
  
 Załóżmy na przykład, że tworzysz usługę sieci Web, która będzie analizować setki dokumentów XML na sekundę, a dokumenty mają tę samą strukturę, co oznacza, że wystarczy napisać jedną implementację kodu, aby przeanalizować XML. W takim przypadku prawdopodobnie chcesz użyć <xref:System.Xml.XmlReader> samodzielnie.  
  
 Natomiast jeśli tworzysz system, który analizuje wiele mniejszych dokumentów XML, a każdy z nich jest inny, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] warto skorzystać z ulepszeń wydajności, które zapewnia.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ do XML vs. XSLT  
 Oba [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i XSLT zapewniają rozbudowane możliwości przekształcania dokumentów XML. XSLT jest podejściem deklaratywnym opartym na regułach. Zaawansowani programiści XSLT piszą XSLT w funkcjonalnym stylu programowania, który podkreśla bezstanowe podejście. Transformacje mogą być zapisywane przy użyciu czystych funkcji, które są implementowane bez skutków ubocznych. To podejście oparte na regułach lub funkcjonalne nie jest znane wielu deweloperom i może być trudne i czasochłonne.  
  
 XSLT może być bardzo wydajnym systemem, który zapewnia wysoką wydajność aplikacji. Na przykład niektóre duże firmy internetowe używają XSLT jako sposobu generowania kodu HTML z pliku XML, który został ściągnięty z różnych magazynów danych. Zarządzany aparat XSLT kompiluje XSLT do kodu CLR i działa jeszcze lepiej w niektórych scenariuszach niż natywny aparat XSLT.  
  
 Jednak XSLT nie korzysta z języka C# i Visual Basic wiedzy, że wielu deweloperów mają. Wymaga od deweloperów pisania kodu w innym i złożonym języku programowania. Korzystanie z dwóch niezintegrowanych systemów programistycznych, takich jak C# (lub Visual Basic) i XSLT powoduje w systemach oprogramowania, które są trudniejsze do opracowania i konserwacji.  
  
 Po opanowaniu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wyrażeń [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytań przekształcenia są zaawansowaną technologią, która jest łatwa w użyciu. Zasadniczo tworzysz dokument XML przy użyciu konstrukcji funkcjonalnej, pobierając <xref:System.Xml.Linq.XElement> dane z różnych źródeł, dynamicznie konstruując obiekty i łącząc całość w nowe drzewo XML. Transformacja może wygenerować zupełnie nowy dokument. Konstruowanie przekształceń [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] w jest stosunkowo łatwe i intuicyjne, a wynikowy kod jest czytelny. Zmniejsza to koszty rozwoju i konserwacji.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie ma na celu zastąpienia XSLT. XSLT jest nadal narzędziem wyboru dla skomplikowanych i zorientowanych na dokumenty przekształceń XML, zwłaszcza jeśli struktura dokumentu nie jest dobrze zdefiniowana.  
  
 XSLT ma tę zaletę, że jest standardem World Wide Web Consortium (W3C). Jeśli masz wymóg, że używasz tylko technologie, które są standardami, XSLT może być bardziej odpowiednie.  
  
 XSLT jest XML i dlatego można go programowo manipulować.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ do XML vs. MSXML  
 MSXML to technologia oparta na com do przetwarzania języka XML dołączona do systemu Microsoft Windows. MSXML zapewnia natywną implementację dom z obsługą XPath i XSLT. Zawiera również SAX2 nie buforowania, analizator oparty na zdarzeniach.  
  
 MSXML działa dobrze, jest domyślnie bezpieczny w większości scenariuszy i jest dostępny w programie Internet Explorer do wykonywania przetwarzania XML po stronie klienta w aplikacjach w stylu AJAX. MsXML może być używany z dowolnego języka programowania, który obsługuje COM, w tym C ++, JavaScript i Visual Basic 6.0.  
  
 Msxml nie jest zalecane do użycia w kodzie zarządzanym na podstawie wspólnego języka runtime (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ do XML vs. XmlLite  
 XmlLite jest nie buforowania, tylko do przodu, pociągnij parser. Deweloperzy używają przede wszystkim XmlLite z c++. Nie zaleca się deweloperom używania XmlLite z kodem zarządzanym.  
  
 Główną zaletą XmlLite jest to, że jest to lekki, szybki analizator XML, który jest bezpieczny w większości scenariuszy. Jego powierzchnia zagrożenia jest bardzo mała. Jeśli musisz przeanalizować niezaufane dokumenty i chcesz chronić przed atakami, takimi jak odmowa usługi lub ujawnienie danych, Dobrym rozwiązaniem może być XmlLite.  
  
 XmlLite nie jest zintegrowany z language-Integrated Query (LINQ). Nie daje to ulepszeniu wydajności programisty, które są siłą motywującą linq.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie (LINQ to XML)](./linq-to-xml-overview.md)

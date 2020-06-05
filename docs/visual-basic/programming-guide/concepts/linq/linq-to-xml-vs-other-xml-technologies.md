---
title: LINQ to XML a inne Technologies2 XML
ms.date: 07/20/2015
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
ms.openlocfilehash: ee855c40e61a6b63c2891d8f30072fc8e235fe4b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389322"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML a inne technologie XML
W tym temacie porównano [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] następujące technologie XML: <xref:System.Xml.XmlReader> , XSLT, MSXML i XmlLite. Te informacje mogą pomóc zdecydować, która technologia ma być używana.  
  
 Aby porównać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do Document Object Model (dom), zobacz [LINQ to XML a DOM (Visual Basic)](linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML a XmlReader  
 <xref:System.Xml.XmlReader>jest to szybki, progresywny parser, bez buforowania.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest zaimplementowana w systemie <xref:System.Xml.XmlReader> i ściśle zintegrowane. Można jednak również użyć <xref:System.Xml.XmlReader> samego siebie.  
  
 Załóżmy na przykład, że tworzysz usługę sieci Web, która będzie analizować setki dokumentów XML na sekundę, a dokumenty mają tę samą strukturę, co oznacza, że wystarczy napisać tylko jedną implementację kodu w celu przeanalizowania kodu XML. W takim przypadku prawdopodobnie chcesz użyć <xref:System.Xml.XmlReader> samego siebie.  
  
 Natomiast w przypadku kompilowania systemu, który analizuje wiele mniejszych dokumentów XML, a każdy z nich jest różny, warto skorzystać z ulepszeń wydajności, które [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML a XSLT  
 Zarówno [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] język, jak i XSLT zapewniają szerokie możliwości transformacji dokumentu XML. XSLT jest podejściem deklaratywnym opartym na regułach. Zaawansowane programiści XSLT zapisują kod XSLT w stylu programowania funkcjonalnego, który podkreśla podejście bezstanowe. Przekształcenia można napisać przy użyciu czystych funkcji, które są implementowane bez efektów ubocznych. Takie podejście oparte na regułach lub funkcjonalnej jest nieznane dla wielu deweloperów i może być trudne i czasochłonne.  
  
 Język XSLT może być bardzo wydajnym systemem, który daje aplikacje o wysokiej wydajności. Na przykład niektóre duże firmy sieci Web używają XSLT jako sposobu generowania kodu HTML z pliku XML, który został pobrany z różnych magazynów danych. Zarządzany aparat XSLT kompiluje kod XSLT do kodu CLR i wykonuje jeszcze lepsze scenariusze niż w przypadku natywnego aparatu XSLT.  
  
 Jednak język XSLT nie korzysta z języka C# i Visual Basic znajomości wielu deweloperów. Wymagają od deweloperów pisania kodu w innym i złożonym języku programowania. Korzystanie z dwóch niezintegrowanych systemów programistycznych, takich jak C# (lub Visual Basic) i wyników XSLT w systemach oprogramowania, które są trudniejsze do opracowania i utrzymania.  
  
 Po utworzeniu wzorców [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytań, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przekształcenia są zaawansowaną technologią łatwą do użycia. Zasadniczo należy utworzyć dokument XML przy użyciu konstruowania funkcjonalnego, ściągania danych z różnych źródeł, konstruowania <xref:System.Xml.Linq.XElement> obiektów dynamicznie i asemblera całości w nowym drzewie XML. Transformacja może generować zupełnie nowy dokument. Konstruowanie transformacji w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest stosunkowo proste i intuicyjne, a kod, który można odczytać. Zmniejsza to koszty związane z programowaniem i konserwacją.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie jest przeznaczony do zastępowania języka XSLT. Język XSLT jest nadal narzędziem wybranym dla skomplikowanych i skoncentrowanych na dokumentach przekształceń XML, zwłaszcza jeśli struktura dokumentu nie jest dobrze zdefiniowana.  
  
 Język XSLT ma zalety organizacja World Wide Web Consortium (W3C). Jeśli jest wymagane użycie tylko technologii, które są standardami, XSLT może być bardziej odpowiednie.  
  
 XSLT jest XML i w związku z tym można programistycznie manipulować.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML a MSXML  
 MSXML to technologia oparta na modelu COM służąca do przetwarzania kodu XML, który jest dołączony do systemu Microsoft Windows. Program MSXML oferuje natywną implementację modelu DOM z obsługą języka XPath i XSLT. Zawiera również SAX2, które nie są buforowaniem, oparte na zdarzeniach.  
  
 Program MSXML działa prawidłowo, jest domyślnie bezpieczny w większości scenariuszy i można do niego uzyskać dostęp w programie Internet Explorer w celu wykonywania przetwarzania kodu XML po stronie klienta w aplikacjach w stylu AJAX. Program MSXML może być używany z dowolnego języka programowania, który obsługuje COM, w tym C++, JavaScript i Visual Basic 6,0.  
  
 Nie zaleca się stosowania programu MSXML w kodzie zarządzanym w oparciu o środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML a XmlLite  
 XmlLite to nie tylko buforowanie, analizator składni ściągania. Deweloperzy wykorzystują głównie XmlLite z C++. Nie zaleca się, aby deweloperzy używali XmlLite z kodem zarządzanym.  
  
 Główną zaletą XmlLite jest to lekki, szybki parser XML, który jest bezpieczny w większości scenariuszy. Obszar narażony na zagrożenia jest bardzo mały. Jeśli konieczne jest przeanalizowanie dokumentów niezaufanych i chcesz chronić przed atakami, takimi jak odmowa usługi lub narażeniem na dane, może być dobrym rozwiązaniem.  
  
 XmlLite nie jest zintegrowany z zapytaniem Integrated Language (LINQ). Nie zapewnia to ulepszeń zwiększających produktywność, które są podstawą siły w odniesieniu do LINQ.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie (LINQ to XML)](getting-started-linq-to-xml.md)

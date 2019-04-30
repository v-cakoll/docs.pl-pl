---
title: LINQ to XML a Inne Technologies3 XML
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 8e2a6b11e450890373de449c0a55839460b97566
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682407"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML a inne technologie XML
W tym temacie porównano [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] następujące technologie XML: <xref:System.Xml.XmlReader>, XSLT, MSXML i XmlLite. Te informacje mogą pomóc w podjęciu decyzji technologie stosowaną do.  
  
 Porównanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do modelu DOM (Document Object), zobacz [LINQ to XML a. MODELU DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML a XmlReader  
 <xref:System.Xml.XmlReader> jest analizatorem szybkie tylko do przodu, bez buforowania.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest implementowana w górnej części <xref:System.Xml.XmlReader>, i są one ściśle zintegrowane. Jednak możesz również użyć <xref:System.Xml.XmlReader> samodzielnie.  
  
 Na przykład załóżmy, że są tworzenia usługi sieci Web analizy setki dokumentów XML na sekundę i dokumenty mają tę samą strukturę, co oznacza, że masz do zapisania jedna implementacja kodu, które można przeanalizować pliku XML. W takim przypadku prawdopodobnie chcesz użyć <xref:System.Xml.XmlReader> samodzielnie.  
  
 Z kolei jeśli tworzysz systemu, która analizuje wiele mniejszych dokumentów XML, a każdy z nich jest inny, chcesz korzystać z zalet udoskonalenia dotyczące produktywności, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML a XSLT  
 Zarówno [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i XSLT zapewnia rozbudowane możliwości transformacji dokumentów XML. XSLT jest oparty na regułach podejścia deklaratywnego. Zaawansowane XSLT programistów zapisu XSLT w stylu programowania funkcjonalnego która kładzie nacisk bezstanowe podejście. Przekształcenia można pisać przy użyciu czystej funkcji, które są wykonywane bez efektów ubocznych. To podejście oparte na regułach lub funkcjonalności nie jest zaznajomiony do wielu deweloperów i może być trudna i czasochłonna dowiedzieć się więcej.  
  
 XSLT, może być bardzo wydajni system, który daje aplikacji o wysokiej wydajności. Na przykład niektóre duże firmy w sieci Web użyj XSLT jako sposób generują kod HTML z pliku XML, który ma zostały pobrane z różnych magazynów danych. Zarządzanego aparatu XSLT kompiluje XSLT do kodu CLR i wykonuje jeszcze lepiej w niektórych scenariuszach niż silnik natywny XSLT.  
  
 Jednak XSLT nie korzystaj z wiedzy języka C# i Visual Basic, mających przez wielu deweloperów. Wymaga to deweloperom pisanie kodu w języku programowania różnych i złożone. W systemach oprogramowania, które są trudne do rozwijania i utrzymywania przy użyciu dwóch niezintegrowany programowanie systemów, takich jak C# (lub Visual Basic) i wyniki XSLT.  
  
 Po opanowaniu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wyrażenia zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przekształcenia są zaawansowaną technologię, która jest łatwa w użyciu. Po prostu opracowywania dokument XML za pomocą konstrukcja funkcjonalna ściąganie danych z różnych źródeł, konstruowanie <xref:System.Xml.Linq.XElement> dynamicznie obiekty i złożenia całego do nowego drzewa XML. Transformacja może generować całkowicie nowy dokument. Konstruowanie przekształcenia w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest względnie proste i intuicyjne, a następnie kod wynikowy jest czytelna. Zmniejsza koszty tworzenia i konserwacji.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie ma na celu zastąpienia XSLT. XSLT jest nadal narzędzie wyborem dla przekształcenia skomplikowane i skoncentrowane na dokumencie XML, zwłaszcza, jeśli nie zdefiniowano również strukturę dokumentu.  
  
 XSLT zaletą jest World Wide Web Consortium (W3C) standardowa. Jeśli masz wymagane używanie tylko tych technologii, które są standardy, bardziej odpowiednie może być XSLT.  
  
 XSLT jest plikiem XML, a w związku z tym można programowo manipulować.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML a MSXML  
 MSXML jest technologii opartych na modelu COM dla przetwarzania XML, który jest dołączony program Microsoft Windows. MSXML oferuje natywnej implementacji modelu DOM, z obsługą języka XPath i XSLT. Zawiera ona także SAX2 parser bez buforowania, oparte na zdarzeniach.  
  
 MSXML wykonuje również jest domyślnie w większości przypadków bezpieczne i dostępne w programie Internet Explorer do wykonywania przetwarzania w aplikacje w stylu AJAX XML po stronie klienta. MSXML może służyć w dowolnym języku programowania, który obsługuje COM, takich jak C++, JavaScript i Visual Basic 6.0.  
  
 MSXML nie jest zalecane do użytku w kodzie zarządzanym, w oparciu o środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML a XmlLite  
 XmlLite jest bez buforowania, do przodu tylko ściągania analizatora. Deweloperzy używają głównie XmlLite przy użyciu języka C++. Nie jest zalecane dla deweloperów XmlLite za pomocą kodu zarządzanego.  
  
 Główną zaletą XmlLite jest lekkie, szybkie analizatora XML, który jest bezpieczny w większości scenariuszy. Jej zagrożeń powierzchni jest bardzo mały. Jeśli chcesz chronić przed atakami, takie jak "odmowa usługi" i narażaniu danych należy przeanalizować niezaufanych dokumentów, XmlLite może być dobrym rozwiązaniem.  
  
 XmlLite nie jest zintegrowany z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Nie przekazuje on programistę udoskonalenia dotyczące produktywności, które są motywującego życie za [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

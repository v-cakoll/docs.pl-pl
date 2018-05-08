---
title: LINQ do XML zabezpieczeń (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d99b4af2-d447-4a3b-991b-6da0231a8637
ms.openlocfilehash: 3f75377502b30b03090bb2a5fe720faf4e12a028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-security-visual-basic"></a>LINQ do XML zabezpieczeń (Visual Basic)
W tym temacie opisano problemy dotyczące zabezpieczeń skojarzone z LINQ do XML. Ponadto zawiera on pewne wskazówki dotyczące zmniejszenia zagrożenie bezpieczeństwa.  
  
## <a name="linq-to-xml-security-overview"></a>LINQ do XML-Przegląd zabezpieczeń  
 LINQ do XML więcej zaprojektowano pod kątem programowania wygody niż dla aplikacji serwerowych z wymaganiami bezpieczeństwa. Większość scenariuszy XML składają się z przetwarzania zaufanych dokumentów XML, a nie przetwarzania niezaufanych dokumentów XML, które są przekazywane do serwera. LINQ do XML jest zoptymalizowana pod kątem tych scenariuszy.  
  
 Jeśli niezaufany danych z nieznanych źródeł musi przetworzyć, firma Microsoft zaleca używanie wystąpienia elementu <xref:System.Xml.XmlReader> klasy, który został skonfigurowany, aby odfiltrować znane XML "odmowa usługi" (DoS).  
  
 Jeśli skonfigurowano <xref:System.Xml.XmlReader> złagodzić ataki, umożliwia tego czytnika wypełnić LINQ do XML drzewa i nadal korzystać z udoskonaleń dotyczących produktywności programisty programu LINQ do XML. Wiele metod środki zaradcze obejmują tworzenie tych, które są skonfigurowane w celu złagodzenia problem z zabezpieczeniami i tworzenie wystąpień drzewo XML za pomocą skonfigurowanych czytnika.  
  
 XML jest bardzo narażone na ataki, ponieważ dokumenty są niepowiązane w rozmiarze, głębokość, rozmiar nazwy elementu i. Niezależnie od tego składnika, który umożliwia proces XML użytkownik powinien zawsze można przygotować do odtworzenia domeny aplikacji, gdy jest używana funkcja nadmiernego zasobów.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Środki zaradcze, XML, XSD, XPath i ataków XSLT  
 LINQ do XML jest oparty na <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. LINQ do XML obsługuje XSD i XPath za pośrednictwem metody rozszerzenia w <xref:System.Xml.Schema?displayProperty=nameWithType> i <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Przy użyciu <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, i <xref:System.Xml.XmlWriter> klas w połączeniu z LINQ do XML, można wywołać XSLT do transformacji XML drzewa.  
  
 Jeśli pracujesz w środowisku mniej bezpieczne, istnieje szereg problemów z zabezpieczeniami, które są skojarzone z językiem XML i korzystanie z klas w <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, i <xref:System.Xml.Xsl?displayProperty=nameWithType>. Te problemy obejmują, ale nie są ograniczone do następujących:  
  
-   XSD, XPath i XSLT są oparte na ciągach języki, w których można określić operacji używające dużo czasu i pamięci. Jest odpowiedzialny za programistów aplikacji, którzy pobierają ciągi XSD, XPath lub XSLT ze źródeł niezaufanych, aby sprawdzić, czy ciągi nie są złośliwe, lub do monitorowania i ograniczyć możliwość, że te ciągi oceny doprowadzi do nadmiernego systemu zużycie zasobów.  
  
-   Schematy XSD (w tym wbudowane schematy) są z założenia podatne na ataki; nie powinna obsługiwać schematy ze źródeł niezaufanych.  
  
-   XSD i XSLT może zawierać odwołania do innych plików, a tych odwołań może spowodować ataków między strefy i między domenami.  
  
-   Jednostek zewnętrznych w definicji DTD może spowodować ataków między strefy i między domenami.  
  
-   Definicje DTD są narażone na ataki.  
  
-   Dokumenty XML wyjątkowo głębokiego mogą wiązać się z odmowa problemów dotyczących usługi; można ograniczyć liczbę dokumentów XML.  
  
-   Nie akceptuj pomocnicze składniki, takie jak <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, i <xref:System.Xml.XmlResolver> obiektów z niezaufanych zestawów.  
  
-   Przeczytaj dane fragmentów w osłabianiu ataków dużego dokumentu.  
  
-   Bloki skryptu w arkuszach stylów XSLT mogą uwidaczniać liczby ataków.  
  
-   Sprawdź dokładnie, przed tworzenia dynamicznej wyrażenia XPath.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ do XML problemy dotyczące zabezpieczeń  
 Problemy dotyczące zabezpieczeń w tym temacie nie są prezentowane w określonej kolejności. Wszystkie problemy są ważne i powinny być kierowane jako odpowiednie.  
  
 Pomyślne atakom podniesienie uprawnień zapewnia złośliwego zestawu większą kontrolę nad środowiskiem. Pomyślne atakom podniesienie uprawnień może spowodować ujawnienie danych, odmowę usługi i inne.  
  
 Aplikacje nie powinny ujawniać dane do użytkowników, którzy nie jest uprawniony do wyświetlenia danych.  
  
 Ataki powodować analizatora składni XML lub LINQ XML zużyje nadmiernej ilości pamięci lub czasu procesora CPU. Ataki są uważane za mniej poważne niż atakom powodującym podniesienie uprawnień lub ujawnieniem danych ataków. Są ważne w scenariuszu, w których serwer wymaga przetwarzania dokumentów XML ze źródeł niezaufanych.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Wyjątki i komunikaty o błędach może ujawnić dane  
 Opis błędu może ujawnić dane, takie jak transformacji danych, plików, nazwy lub szczegóły implementacji. Nie należy uwidaczniać komunikaty o błędach dotyczące obiektów wywołujących, które nie są zaufane. Należy przechwytywać wszystkie błędy i przesłania raportów o błędach z własnych niestandardowych komunikatów o błędach.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nie wywołuj CodeAccessPermissions.Assert w obsłudze zdarzeń  
 Zestaw może mieć mniejsze lub większe uprawnienia. Zestaw, który ma większe uprawnienia ma większą kontrolę nad komputerem i środowiska.  
  
 Jeśli kod w zestawie większe uprawnienia wywołuje <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> w program obsługi zdarzeń, a następnie XML drzewa są przekazywane do zestawu złośliwego czy ma ograniczone uprawnienia, złośliwy zestawu może spowodować się zdarzenia. Ponieważ zdarzenia uruchamia kod w zestawie większe uprawnienia, złośliwego zestawu następnie czy działających z podniesionymi uprawnieniami.  
  
 Firma Microsoft zaleca się, że nigdy nie wywołania <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> w obsłudze zdarzeń.  
  
### <a name="dtds-are-not-secure"></a>Definicje DTD są nie zabezpieczyć  
 Jednostki w definicji DTD z założenia nie jest bezpieczna. Istnieje możliwość złośliwego dokument XML, który zawiera DTD spowodować analizator użycie wszystkich pamięci i czasu Procesora, co doprowadzi do odmowy usługi. W związku z tym w składniku LINQ to XML, przetwarzanie elementu DTD jest domyślnie wyłączona. Definicje DTD ze źródeł niezaufanych nie powinna obsługiwać.  
  
 Przykładem akceptowania elementów DTD ze źródeł niezaufanych jest aplikacji sieci Web, która umożliwia użytkownikom sieci Web przekazać plik XML, który odwołuje się do definicji DTD i plik definicji DTD. Podczas sprawdzania poprawności pliku złośliwy DTD można wykonać odmowa usługi ataków na serwerze. Innym przykładem akceptowania elementów DTD ze źródeł niezaufanych jest odwołanie DTD na udział sieciowy, który umożliwia także anonimowy dostęp do.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Unikaj nadmiernego buforu alokacji  
 Deweloperzy aplikacji należy zwrócić uwagę, że bardzo dużych źródeł danych może doprowadzić do wyczerpania zasobów i ataki.  
  
 Złośliwy użytkownik przesyła lub przekazuje bardzo dużych dokument XML, program może spowodować LINQ do XML zużywanie zasobów systemowych nadmiernego. Może to stanowić typu "odmowa usługi". Aby tego uniknąć, można ustawić <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> właściwości i Utwórz reader, który następnie jest ograniczona w rozmiar dokumentu, który można go załadować. Czytnik jest następnie używać do tworzenia drzewa XML.  
  
 Na przykład, jeśli wiadomo, że maksymalna oczekiwany rozmiar dokumentów XML pochodzące z niezaufanego źródła będą mieć mniej niż 50 KB, ustaw <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> do 100 000. To nie będzie obciążać przetwarzania dokumentów XML, a jednocześnie ograniczy zagrożenie odmowa, gdzie może przekazać dokumenty zagrożeń usługi używające duże ilości pamięci.  
  
### <a name="avoid-excess-entity-expansion"></a>Unikaj rozszerzenia nadmiarowe jednostki  
 Jednym z znane ataki odmowy usługi przy użyciu DTD jest dokument, który powoduje, że rozszerzenia nadmiernego jednostki. Aby tego uniknąć, można ustawić <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> właściwości i Utwórz reader, który następnie jest ograniczona w liczbie znaków, wynikających z rozszerzenia jednostki. Czytnik jest następnie używać do tworzenia drzewa XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Limit głębokość hierarchii XML  
 Jeden możliwy atak odmowy usług jest po przesłaniu dokumentu, który ma nadmiernego głębokość hierarchii. Aby tego uniknąć, można zawijać <xref:System.Xml.XmlReader> własne klasy, które zlicza głębokość elementów. Głębokość przekracza ustalonej rozsądnym poziomie, po zakończeniu przetwarzania złośliwy dokument.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochronę przed niezaufanych, XmlReader lub XmlWriter implementacji  
 Administratorzy powinni sprawdzić wszelkie zewnętrznie dostarczenia <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> implementacje mieć silne nazwy i został zarejestrowany w konfiguracji komputera. Zapobiega to złośliwy kod udający odczytywania lub zapisywania z ładowany.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Obiekty okresowo wolnego XName tego odwołania  
 Aby zapewnić ochronę przed określonych rodzajów ataków, programistom powinna zwolnić wszystkie obiekty, które odwołują się <xref:System.Xml.Linq.XName> obiektu w domenie aplikacji na bieżąco.  
  
### <a name="protect-against-random-xml-names"></a>Ochrona przed nazwy losowe XML  
 Aplikacje, które pobierają dane ze źródeł niezaufanych należy rozważyć użycie <xref:System.Xml.XmlReader> czyli opakowana w kodu niestandardowego do sprawdzenia pod kątem możliwości losowe nazw XML i przestrzenie nazw. Jeśli takie losowe nazw XML i przestrzenie nazw są wykrywane, aplikacji można następnie przerwanie przetwarzania złośliwy dokument.  
  
 Można ograniczyć liczbę nazw w danej przestrzeni nazw (w tym nazwy w bez przestrzeni nazw) do limitu uzasadnione.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Adnotacje są dostępne dla składników oprogramowania, które współużytkują LINQ do XML drzewa  
 LINQ do XML może służyć do tworzenia potoków przetwarzania, w których składniki różnych aplikacji obciążenia, sprawdzanie poprawności zapytania, przekształcania, aktualizacji i zapisać dane XML, które są przekazywane między składnikami jako drzewa XML. Może to ułatwić optymalizacji wydajności, ponieważ koszty ładowania i serializacji obiektów do tekstu XML jest wykonywana tylko na końcu potoku. Deweloperzy muszą należy jednak pamiętać, że wszystkie adnotacje i obsługi zdarzeń utworzonych przez jeden składnik są dostępne dla innych składników. Można utworzyć liczbę luk w zabezpieczeniach, jeśli składniki mają różne poziomy zaufania. Do tworzenia bezpiecznego potoki przez składniki zaufany, musi serializować LINQ do obiektów XML do tekstu XML przed przekazaniem ich do niezaufany składnik.  
  
 Niektóre zabezpieczeń są udostępniane przez środowisko uruchomieniowe języka wspólnego (CLR). Na przykład składnik, który nie zawiera klasy prywatnego nie może uzyskać dostępu adnotacje, wyznaczaną przez tę klasę. Jednak adnotacje mogą zostać usunięte przez składniki, których nie można ich odczytać. Może to służyć jako manipulacją ataku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

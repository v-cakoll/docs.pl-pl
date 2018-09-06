---
title: Zabezpieczenia LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 0c4ee8df85d6e5c6f84947dcaaeb6875bbd687de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881765"
---
# <a name="linq-to-xml-security-c"></a>Zabezpieczenia LINQ to XML (C#)
W tym temacie opisano problemy dotyczące zabezpieczeń skojarzonych z LINQ to XML. Ponadto zawiera pewne wskazówki łagodzenia zagrożenie bezpieczeństwa.  
  
## <a name="linq-to-xml-security-overview"></a>LINQ do XML-Przegląd zabezpieczeń  
 LINQ to XML zaprojektowano bardziej programowania wygody niż dla aplikacji po stronie serwera, z wymaganiami bezpieczeństwa. Większość scenariuszy XML składają się z przetwarzania zaufanych dokumentów XML, a nie przetwarzania niezaufanych dokumentów XML, które są przekazywane do serwera. LINQ to XML jest zoptymalizowany pod kątem tych scenariuszy.  
  
 Jeśli musisz przetworzyć niezaufane dane z nieznanych źródeł, firma Microsoft zaleca użycie wystąpienia <xref:System.Xml.XmlReader> klasy, który został skonfigurowany tak, aby odfiltrować znanych XML atakom typu odmowa usługi (DoS).  
  
 Jeśli skonfigurowano <xref:System.Xml.XmlReader> uniknąć atakom typu odmowa usługi, umożliwia ten czytnik do wypełniania LINQ do drzewa XML i nadal korzystać z udoskonaleń dotyczących produktywności programisty LINQ to XML. Wiele technik środki zaradcze obejmują tworzenie czytelnicy skonfigurowanych w taki sposób, aby rozwiązać problem z zabezpieczeniami i następnie utworzenie wystąpienia drzewa XML przy użyciu skonfigurowanego czytnika.  
  
 XML jest wewnętrznie narażony na ataki, ponieważ jest nieograniczona rozmiaru, głębi, rozmiar nazwy elementu i dokumentów. Niezależnie od tego, składnik, który umożliwia procesu XML możesz powinna zawsze być przygotowana do Kosza domeny aplikacji, jeśli używa zasobów.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Środki zaradcze, XML, XSD, XPath i ataki XSLT  
 LINQ to XML jest oparty na <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. LINQ to XML obsługuje XSD i XPath za pośrednictwem metody rozszerzające w <xref:System.Xml.Schema?displayProperty=nameWithType> i <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Za pomocą <xref:System.Xml.XmlReader>, <xref:System.Xml.XPath.XPathNavigator>, i <xref:System.Xml.XmlWriter> klas w połączeniu z LINQ to XML, można wywołać XSLT do przekształcania drzew XML.  
  
 Jeśli pracujesz w środowisku mniej bezpieczna opcja, istnieje szereg problemów z zabezpieczeniami, które są skojarzone z danymi XML i korzystanie z klas w <xref:System.Xml?displayProperty=nameWithType>, <xref:System.Xml.Schema?displayProperty=nameWithType>, <xref:System.Xml.XPath?displayProperty=nameWithType>, i <xref:System.Xml.Xsl?displayProperty=nameWithType>. Te problemy obejmują, ale nie są ograniczone do następujących:  
  
-   XSD, XPath i XSLT są oparte na ciągach języków, w których można określić operacji, które to zajmować dużo czasu i pamięci. Jest odpowiedzialny za programistów aplikacji, którzy pobierają ciągi XSD, XPath lub XSLT ze źródeł niezaufanych, aby sprawdzić, czy ciągi nie są złośliwe, lub do monitorowania i ograniczyć możliwość, że ocena te ciągi doprowadzi do nadmiernego systemu użycie zasobów.  
  
-   Schematy XSD (w tym wbudowane schematy) są założenia podatne na ataki; nie należy zaakceptować schematów z niezaufanego źródła.  
  
-   XSD i XSLT może zawierać odwołania do innych plików, a tych odwołań może spowodować ataków międzystrefowego i między domenami.  
  
-   Podmiotów zewnętrznych w definicji DTD może spowodować ataków międzystrefowego i między domenami.  
  
-   Pliki DTD są narażone na ataki.  
  
-   Wyjątkowo głębokiego dokumentów XML może stwarzać typu "odmowa" problemy z usługą; Możesz chcieć ograniczyć głębię dokumentów XML.  
  
-   Nie są akceptowane składniki pomocnicze, takie jak <xref:System.Xml.NameTable>, <xref:System.Xml.XmlNamespaceManager>, i <xref:System.Xml.XmlResolver> obiektów z niezaufanych zestawów.  
  
-   Dane odczytu we fragmentach, aby uniknąć dużych dokumentów ataków.  
  
-   Bloki skryptów w arkuszy stylów XSLT może narazić liczby ataków.  
  
-   Sprawdź dokładnie, przed konstruowanie dynamiczne wyrażenia XPath.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ do XML-problemy dotyczące zabezpieczeń  
 Problemy z zabezpieczeniami, w tym temacie nie są prezentowane w określonej kolejności. Wszystkie problemy są ważne i powinny być kierowane odpowiednio.  
  
 Pomyślne podniesienie poziomu uprawnień zapewnia złośliwemu zestawowi większą kontrolę nad jego środowiska. Pomyślne podniesienie poziomu uprawnień może spowodować ujawnienie danych, odmowę usługi i inne.  
  
 Aplikacje nie powinny ujawniać dane dla użytkowników, którzy nie jest uprawniony do wyświetlenia tych danych.  
  
 Atakom typu odmowa usługi spowodować, że XML parser lub programu LINQ do pliku XML z nadmiernej ilości pamięci lub czasu procesora CPU. Atakom typu odmowa usługi są uważane za mniej poważne niż atakom powodującym podniesienie uprawnień lub ujawnieniem danych ataków. Są ważne w scenariuszu, w których serwer wymaga przetwarzania dokumentów XML ze źródeł niezaufanych.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Wyjątki i komunikaty o błędach może spowodować ujawnienie danych  
 Opis błędu może spowodować ujawnienie danych, takich jak dane przekształcanego, plików, nazwy lub szczegółów implementacji. Nie należy uwidaczniać komunikaty o błędach dotyczące obiektów wywołujących, które nie są zaufane. Należy przechwytywać wszystkie błędy i raportowanie błędów przy użyciu własnych niestandardowych komunikatów o błędach.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nie wywołuj CodeAccessPermissions.Assert w obsłudze zdarzeń  
 Zestaw może mieć mniejsze lub większe uprawnienia. Zestaw, który ma większe uprawnienia ma większą kontrolę nad komputerem i jego środowiska.  
  
 Jeśli kod w zestawie przy użyciu większe uprawnienia wywołuje <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> w program obsługi zdarzeń, a następnie XML drzewa jest przekazywany do złośliwemu zestawowi, ma ograniczone uprawnienia, mogą złośliwemu zestawowi spowodować, że zdarzenia. Ponieważ zdarzenia działa kod, który znajduje się w zestawie przy użyciu większe uprawnienia, to złośliwemu zestawowi może następnie działających z podwyższonym poziomem uprawnień.  
  
 Firma Microsoft zaleca się, że użytkownik nigdy nie wywołują metody <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> w obsłudze zdarzeń.  
  
### <a name="dtds-are-not-secure"></a>Pliki DTD są, nie jest bezpieczny  
 Jednostki w definicji DTD natury nie są bezpieczne. Istnieje możliwość złośliwego dokumentu XML, który zawiera DTD, aby spowodować, że analizator składni do użycia wszystkich pamięci i czasu procesora CPU, co doprowadzi do odmowy usługi. W związku z tym w składniku LINQ to XML, przetwarzanie elementu DTD jest domyślnie wyłączona. Nie powinna obsługiwać pliki DTD ze źródeł niezaufanych.  
  
 Przykładem zaakceptowania elementów DTD ze źródeł niezaufanych jest aplikacją sieci Web, który umożliwia użytkownikom w sieci Web można przekazać pliku XML, który odwołuje się do DTD i DTD pliku. Po rozpatrzeniu pliku złośliwy DTD można wykonać "odmowa usługi" na serwerze. Inny przykład akceptować pliki DTD ze źródeł niezaufanych to do odwołania DTD w udziale sieciowym, umożliwiającą dostęp anonimowy FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Unikaj nadmiernego buforu alokacji  
 Deweloperzy aplikacji należy pamiętać, że bardzo duże źródła danych może prowadzić do wyczerpania zasobów i ataki.  
  
 Jeśli złośliwy użytkownik przesyła lub przekazuje bardzo dużych dokumentów XML, może spowodować LINQ do pliku XML, korzystanie z zasobów systemowych nadmierne. Może to stanowić "odmowa usługi". Aby tego uniknąć, można ustawić <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> właściwości i tworzenie czytnika, który następnie jest ograniczony do rozmiaru dokumentu, który można załadować. Czytnik jest następnie użyć do utworzenia drzewa XML.  
  
 Na przykład, jeśli wiesz, że maksymalny oczekiwany rozmiar dokumentów XML pochodzące z niezaufanego źródła będą mieć mniej niż 50 KB, ustaw <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> do 100 000. To nie będzie obciążać przetwarzanie dokumentów XML, a w tym samym czasie ograniczą typu "odmowa", gdzie może przekazać dokumenty zagrożeń usługi używające dużej ilości pamięci.  
  
### <a name="avoid-excess-entity-expansion"></a>Należy unikać rozszerzania jednostki nadmiarowe  
 Jednym z znanych atakom typu odmowa usługi podczas korzystania z DTD jest dokument, który powoduje, że rozszerzenie nadmierne jednostki. Aby tego uniknąć, można ustawić <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> właściwości i tworzenie czytnika, który następnie jest ograniczona w liczbę znaków, które wynikają z rozszerzania jednostki. Czytnik jest następnie użyć do utworzenia drzewa XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Limit głębokość hierarchii XML  
 Jeden możliwe "odmowa usługi" jest w przypadku przesłania dokumentu, który ma nadmierną głębokość hierarchii. Aby tego uniknąć, można opakować <xref:System.Xml.XmlReader> własne klasy, który zlicza głębokość elementów. Głębokość przekracza wstępnie rozsądny poziom, po zakończeniu przetwarzania złośliwy dokument.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochronę przed niezaufanych, XmlReader lub implementacji XmlWriter  
 Administratorzy powinni sprawdzić, czy wszelkie zewnętrznie podane <xref:System.Xml.XmlReader> lub <xref:System.Xml.XmlWriter> implementacje mieć silne nazwy i został zarejestrowany w konfiguracji maszyny. Zapobiega to złośliwy kod udający odczytywania lub zapisywania wczytanie.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Okresowo zwalniać obiekty XName tego odwołania  
 Aby chronić przed niektórych rodzajów ataków, programistom powinna zwolnić wszystkie obiekty, które odwołują się <xref:System.Xml.Linq.XName> obiektu w domenie aplikacji w regularnych odstępach czasu.  
  
### <a name="protect-against-random-xml-names"></a>Ochrona przed XML losowych nazw  
 Aplikacje, które pobierają dane ze źródeł niezaufanych należy wziąć pod uwagę przy użyciu <xref:System.Xml.XmlReader> oznacza to otoczone niestandardowe kod, aby sprawdzić możliwość losowych nazw XML i przestrzenie nazw. W przypadku wykrycia tych losowych nazw XML i przestrzenie nazw aplikacji może następnie Zakończ działanie przetwarzania złośliwy dokument.  
  
 Można ograniczyć liczbę nazw w dowolnym danym nazw (w tym nazwy w żadnej przestrzeni nazw) limitowi uzasadnione.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Adnotacje są dostępne dla składników oprogramowania, mających LINQ do drzewa XML  
 LINQ to XML może służyć do tworzenia potoków przetwarzania, w których składników innej aplikacji obciążenia, sprawdź poprawność, zapytania, przekształcania, aktualizacji i zapisać dane XML, który jest przekazywany między składnikami jako drzew XML. Może to pomóc zoptymalizować wydajność, ponieważ obciążenie, ładowanie i wykonywanie serializacji obiektów do tekstu XML jest wykonywane tylko na końcu potoku. Deweloperzy muszą należy jednak pamiętać, że wszystkie adnotacje i procedury obsługi zdarzeń utworzonych przez jeden składnik są dostępne dla innych składników. Można utworzyć szereg luk w zabezpieczeniach, jeśli składniki mają różne poziomy zaufania. Do tworzenia bezpiecznego potoki na mniej zaufanym składnikom, możesz serializować LINQ do obiektów XML do tekstu XML przed przekazaniem ich do niezaufany składnik.  
  
 Niektóre zabezpieczeń są udostępniane przez środowisko uruchomieniowe języka wspólnego (CLR). Na przykład składnik, który nie zawiera klasę prywatną nie może uzyskać dostępu adnotacje kluczach tej klasy. Jednak można usunąć adnotacji przez składniki, które nie mogą ich odczytać. To może być używany jako manipulacją ataku.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

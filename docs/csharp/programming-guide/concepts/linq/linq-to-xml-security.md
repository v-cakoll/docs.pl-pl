---
title: LINQ do zabezpieczeń XML (C#)
ms.date: 07/20/2015
ms.assetid: ef2c0dc9-ecf9-4c17-b24e-144184ab725f
ms.openlocfilehash: 5b7eb815b058cba008f1db2cf683c8934c19b743
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73423373"
---
# <a name="linq-to-xml-security-c"></a>LINQ do zabezpieczeń XML (C#)
W tym temacie opisano problemy z zabezpieczeniami związane z LINQ do XML. Ponadto zawiera pewne wskazówki dotyczące łagodzenia narażenia na bezpieczeństwo.  
  
## <a name="linq-to-xml-security-overview"></a>Omówienie zabezpieczeń LINQ do XML  
 LINQ do XML jest przeznaczony bardziej dla wygody programowania niż dla aplikacji po stronie serwera z rygorystycznymi wymaganiami bezpieczeństwa. Większość scenariuszy XML polega na przetwarzaniu zaufanych dokumentów XML, zamiast przetwarzania niezaufanych dokumentów XML, które są przekazywane do serwera. LINQ do XML jest zoptymalizowany dla tych scenariuszy.  
  
 Jeśli musisz przetworzyć niezaufane dane z nieznanych źródeł, <xref:System.Xml.XmlReader> firma Microsoft zaleca użycie wystąpienia klasy skonfigurowanej do odfiltrowywania znanych ataków typu odmowa usługi XML (DoS).  
  
 Jeśli skonfigurowano ataki <xref:System.Xml.XmlReader> typu "odmowa usługi", można użyć tego czytnika do wypełnienia linq do drzewa XML i nadal korzystać z ulepszeń wydajności programisty LINQ do XML. Wiele technik łagodzenia obejmują tworzenie czytników, które są skonfigurowane w celu złagodzenia problemu z zabezpieczeniami, a następnie tworzenie wystąpienia drzewa XML za pośrednictwem skonfigurowanego czytnika.  
  
 XML jest z natury podatny na ataki typu "odmowa usługi", ponieważ dokumenty są nieograniczone pod względem rozmiaru, głębokości, rozmiaru nazwy elementu i innych elementów. Niezależnie od składnika, który służy do przetwarzania XML, zawsze należy przygotować się do recyklingu domeny aplikacji, jeśli używa nadmiernych zasobów.  
  
## <a name="mitigation-of-xml-xsd-xpath-and-xslt-attacks"></a>Łagodzenie ataków XML, XSD, XPath i XSLT  
 LINQ do XML <xref:System.Xml.XmlReader> jest <xref:System.Xml.XmlWriter>zbudowany na i . LINQ do XML obsługuje XSD i XPath <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType> za pośrednictwem metod rozszerzenia w przestrzeniach nazw i. Za <xref:System.Xml.XmlReader>pomocą <xref:System.Xml.XPath.XPathNavigator>, <xref:System.Xml.XmlWriter> i klas w połączeniu z LINQ do XML, można wywołać XSLT do przekształcania drzew XML.  
  
 Jeśli pracujesz w mniej bezpiecznym środowisku, istnieje wiele problemów z zabezpieczeniami, które są <xref:System.Xml?displayProperty=nameWithType>związane <xref:System.Xml.Schema?displayProperty=nameWithType> <xref:System.Xml.XPath?displayProperty=nameWithType>z <xref:System.Xml.Xsl?displayProperty=nameWithType>XML i korzystanie z klas w , , , i . Kwestie te obejmują między innymi następujące kwestie:  
  
- XSD, XPath i XSLT to języki oparte na ciągach, w których można określić operacje zużywadużo czasu lub pamięci. Obowiązkiem programistów aplikacji, którzy biorą ciągi XSD, XPath lub XSLT z niezaufanych źródeł, należy sprawdzić, czy ciągi nie są złośliwe, lub monitorować i ograniczać możliwość, że ocena tych ciągów doprowadzi do nadmiernego systemu zużycia zasobów.  
  
- Chemy XSD (w tym schemy inline) są z natury podatne na ataki typu "odmowa usługi"; nie należy akceptować schemów z niezaufanych źródeł.  
  
- XSD i XSLT mogą zawierać odwołania do innych plików, a takie odwołania mogą powodować ataki międzystrefowe i międzydomenowe.  
  
- Jednostki zewnętrzne w DTD mogą powodować ataki międzystrefowe i międzydomenowe.  
  
- DTD są narażone na ataki typu "odmowa usługi".  
  
- Wyjątkowo głębokie dokumenty XML mogą stwarzać problemy z odmową usługi; można ograniczyć głębokość dokumentów XML.  
  
- Nie należy akceptować komponentów <xref:System.Xml.NameTable>pomocniczych, takich jak , <xref:System.Xml.XmlNamespaceManager>i <xref:System.Xml.XmlResolver> obiektów, z niezaufanych złożeń.  
  
- Odczyt danych w fragmentach w celu złagodzenia ataków dużych dokumentów.  
  
- Bloki skryptów w arkuszach stylów XSLT mogą uwidaczniać liczbę ataków.  
  
- Sprawdź dokładnie przed konstruowaniem dynamicznych wyrażeń XPath.  
  
## <a name="linq-to-xml-security-issues"></a>LINQ do XML Problemy z zabezpieczeniami  
 Problemy z zabezpieczeniami w tym temacie nie są prezentowane w określonej kolejności. Wszystkie kwestie są ważne i powinny być odpowiednio rozwiązane.  
  
 Pomyślne podniesienie poziomu uprawnień atakuje daje złośliwego zestawu większą kontrolę nad jego środowiskiem. Pomyślne podniesienie poziomu uprawnień może spowodować ujawnienie danych, odmowa usługi i inne.  
  
 Aplikacje nie powinny ujawniać danych użytkownikom, którzy nie są upoważnieni do ich widzieć.  
  
 Ataki typu "odmowa usługi" powodują, że analizator XML lub LINQ do XML zużywają nadmierne ilości pamięci lub czasu procesora. Ataki typu "odmowa usługi" są uważane za mniej dotkliwe niż podniesienie liczby ataków z uprawnieniami lub ujawnienie ataków na dane. Są one jednak ważne w scenariuszu, w którym serwer musi przetwarzać dokumenty XML z niezaufanych źródeł.  
  
### <a name="exceptions-and-error-messages-might-reveal-data"></a>Wyjątki i komunikaty o błędach mogą ujawniać dane  
 Opis błędu może ujawnić dane, takie jak dane są przekształcane, nazwy plików lub szczegóły implementacji. Komunikaty o błędach nie powinny być udostępniane dla wywoływania, które nie są zaufane. Należy złapać wszystkie błędy i zgłosić błędy za pomocą własnych niestandardowych komunikatów o błędach.  
  
### <a name="do-not-call-codeaccesspermissionsassert-in-an-event-handler"></a>Nie wywoływać CodeAccessPermissions.Assert w programie obsługi zdarzeń  
 Zestaw może mieć mniejsze lub większe uprawnienia. Zestaw, który ma większe uprawnienia ma większą kontrolę nad komputerem i jego środowisk.  
  
 Jeśli kod w zestawie z <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> większymi uprawnieniami wywołuje w programie obsługi zdarzeń, a następnie drzewo XML jest przekazywana do złośliwego zestawu, który ma ograniczone uprawnienia, złośliwy zestaw może spowodować zdarzenie, które mają być wywoływane. Ponieważ zdarzenie uruchamia kod, który znajduje się w zestawie z większymi uprawnieniami, złośliwy zestaw będzie następnie działać z podwyższonym poziomem uprawnień.  
  
 Firma Microsoft zaleca, <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=nameWithType> aby nigdy nie wywoływać w programie obsługi zdarzeń.  
  
### <a name="dtds-are-not-secure"></a>DTD nie są bezpieczne  
 Jednostki w DTD z natury nie są bezpieczne. Istnieje możliwość, że złośliwy dokument XML zawierający DTD spowoduje, że analizator zużywa całą pamięć i czas procesora, powodując atak typu "odmowa usługi". W związku z tym w LINQ do XML, przetwarzanie DTD jest domyślnie wyłączone. Nie należy akceptować identyfikatorów DTD z niezaufanych źródeł.  
  
 Jednym z przykładów akceptowania dtd s z niezaufanych źródeł jest aplikacja sieci Web, która umożliwia użytkownikom sieci Web przekazywanie pliku XML, który odwołuje się do DTD i pliku DTD. Po sprawdzeniu poprawności pliku złośliwy DTD może wykonać atak typu "odmowa usługi" na serwerze. Innym przykładem akceptowania dtd s z niezaufanych źródeł jest odwoływanie się do DTD w udziale sieciowym, który umożliwia również anonimowy dostęp FTP.  
  
### <a name="avoid-excessive-buffer-allocation"></a>Unikaj nadmiernej alokacji buforu  
 Deweloperzy aplikacji powinni mieć świadomość, że bardzo duże źródła danych może prowadzić do wyczerpania zasobów i ataków typu "odmowa usługi".  
  
 Jeśli złośliwy użytkownik przesyła lub przekazuje bardzo duży dokument XML, może to spowodować LINQ do XML do zużycia nadmiernych zasobów systemowych. Może to stanowić atak typu "odmowa usługi". Aby temu zapobiec, <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> można ustawić właściwość i utworzyć czytnik, który jest następnie ograniczony w rozmiarze dokumentu, który można załadować. Następnie użyj czytnika, aby utworzyć drzewo XML.  
  
 Na przykład jeśli wiesz, że maksymalny oczekiwany rozmiar dokumentów XML pochodzących z niezaufanego źródła będzie <xref:System.Xml.XmlReaderSettings.MaxCharactersInDocument%2A?displayProperty=nameWithType> mniejszy niż 50 K bajtów, ustawiony na 100 000. Nie będzie to obciążać przetwarzania dokumentów XML, a jednocześnie ograniczy zagrożenia typu "odmowa usługi", w których mogą zostać przekazane dokumenty, które zużywają duże ilości pamięci.  
  
### <a name="avoid-excess-entity-expansion"></a>Unikaj rozszerzania nadmiaru encji  
 Jednym ze znanych ataków typu "odmowa usługi" podczas korzystania z dtd jest dokument, który powoduje nadmierne rozszerzenie jednostki. Aby temu zapobiec, <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities%2A?displayProperty=nameWithType> można ustawić właściwość i utworzyć czytnik, który jest następnie ograniczony w liczbie znaków, które wynikają z rozszerzenia jednostki. Następnie użyj czytnika, aby utworzyć drzewo XML.  
  
### <a name="limit-the-depth-of-the-xml-hierarchy"></a>Ograniczanie głębokości hierarchii XML  
 Jednym z możliwych ataków typu "odmowa usługi" jest przesłanie dokumentu o nadmiernej głębi hierarchii. Aby temu zapobiec, <xref:System.Xml.XmlReader> można zawinąć w własnej klasy, która liczy głębokość elementów. Jeśli głębokość przekracza wcześniej określony rozsądny poziom, można zakończyć przetwarzanie złośliwego dokumentu.  
  
### <a name="protect-against-untrusted-xmlreader-or-xmlwriter-implementations"></a>Ochrona przed niezaufanymi implementacjami XmlReader lub XmlWriter  
 Administratorzy powinni sprawdzić, <xref:System.Xml.XmlReader> czy <xref:System.Xml.XmlWriter> wszystkie dostarczone zewnętrznie lub implementacje mają silne nazwy i zostały zarejestrowane w konfiguracji komputera. Zapobiega to załadowania złośliwego kodu podszywającego się pod czytelnika lub modułu zapisującego.  
  
### <a name="periodically-free-objects-that-reference-xname"></a>Okresowo wolne obiekty, które odwołują się do XName  
 Aby chronić się przed niektórymi rodzajami ataków, programiści aplikacji powinni zwolnić wszystkie obiekty, które regularnie odwołują <xref:System.Xml.Linq.XName> się do obiektu w domenie aplikacji.  
  
### <a name="protect-against-random-xml-names"></a>Ochrona przed losowymi nazwami XML  
 Aplikacje, które przyjmują dane z <xref:System.Xml.XmlReader> niezaufanych źródeł należy rozważyć przy użyciu, który jest opakowany w niestandardowy kod, aby sprawdzić możliwość losowych nazw XML i przestrzeni nazw. W przypadku wykrycia takich losowych nazw XML i przestrzeni nazw aplikacja może zakończyć przetwarzanie złośliwego dokumentu.  
  
 Można ograniczyć liczbę nazw w danym obszarze nazw (w tym nazwy w obszarze nazw) do rozsądnego limitu.  
  
### <a name="annotations-are-accessible-by-software-components-that-share-a-linq-to-xml-tree"></a>Adnotacje są dostępne dla składników oprogramowania, które współużytkują LINQ do drzewa XML  
 LINQ do XML może służyć do tworzenia potoków przetwarzania, w których różne składniki aplikacji ładowania, sprawdzania poprawności, kwerendy, przekształcania, aktualizacji i zapisywania danych XML, który jest przekazywany między składnikami jako drzewa XML. Może to pomóc w optymalizacji wydajności, ponieważ obciążenie związane z ładowaniem i serializacją obiektów do tekstu XML odbywa się tylko na końcach potoku. Deweloperzy muszą jednak pamiętać, że wszystkie adnotacje i programy obsługi zdarzeń utworzone przez jeden składnik są dostępne dla innych składników. Może to spowodować utworzenie wielu luk w zabezpieczeniach, jeśli składniki mają różne poziomy zaufania. Aby utworzyć bezpieczne potoki w mniej zaufanych składnikach, należy serializować LINQ do obiektów XML do tekstu XML przed przekazaniem danych do niezaufanego składnika.  
  
 Niektóre zabezpieczenia są dostarczane przez czas wykonywania języka wspólnego (CLR). Na przykład składnik, który nie zawiera klasy prywatnej nie może uzyskać dostępu do adnotacji kluczem przez tę klasę. Jednak adnotacje mogą być usuwane przez składniki, które nie mogą ich odczytać. Może to być wykorzystane jako atak manipulacji.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania (LINQ do XML) (C#)](linq-to-xml-overview.md)

---
title: Filtrowanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f67a7f6ac423bd66d9d25b834edc9cf55a5d6a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="filtering"></a>Filtrowanie
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Filtrowania systemu umożliwia deklaratywne filtry zgodne wiadomości i podejmowanie decyzji operacyjnych. Filtry można służą do określania, co należy zrobić z następującym komunikatem, sprawdzając część komunikatu. Proces kolejkowania, na przykład można użyć zapytania XPath 1.0 do sprawdzenia elementu priority znane nagłówka do ustalenia, czy można przenieść komunikatu z przodu kolejki.  
  
 System filtrowania składa się z zestaw klas, których można efektywnie ustalić, który zestaw filtrów są `true` dla określonego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości.  
  
 Filtrowania system jest podstawowym składnikiem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości; jest przeznaczony do bardzo szybkiego działania. Każda implementacja filtru został zoptymalizowany do określonego rodzaju dopasowania przed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości.  
  
 Filtrowania system nie jest bezpieczne dla wątków. Aplikacja musi obsługiwać żadnych semantyką blokowania. Jednak obsługuje wielu czytnika, jednego składnika zapisywania.  
  
## <a name="where-filtering-fits"></a>Gdzie pasuje do filtrowania  
 Filtrowanie odbywa się po komunikat jest odbierany i wchodzi w skład procesu podczas wysyłania komunikatu do składnika odpowiednia aplikacja. Projekt filtrowania systemu rozwiązuje kilka wymagań [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podsystemów, w tym wiadomości, routing, zabezpieczenia, obsługi zdarzeń i zarządzanie systemem.  
  
## <a name="filters"></a>Filtry  
 Aparat filtr ma dwa podstawowe składniki, filtrów i tabele filtru. Filtr sprawia, że logiczna decyzji dotyczących komunikatów, na podstawie warunków logicznych określone przez użytkownika. Implementowanie filtry <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Metody są używane do określania, jeśli wiadomość ma spełnia filtru. Jedną z metod testów nagłówek komunikatu, ale nie można sprawdzić treść komunikatu. Trwa innej metody *bufor komunikatów* jako parametr wejściowy i sprawdzić, czy treść komunikatu.  
  
 Filtry nie są zwykle sprawdzane pojedynczo, ale jako część tabeli filtr, który jest rodzajowy klasy, która <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> metoda tworzy.  
  
 Kilka rodzajów filtry każdego specjalizują się w odpowiadającym na określonego rodzaju warunek typu Boolean. Po utworzenia filtru, nie można zmienić kryteria używane w filtrze; Aby zmodyfikować kryteria filtrowania, utworzyć nowy i usuń istniejący filtr.  
  
### <a name="action-filters"></a>Filtry akcji  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Zawiera listę ciągów akcji. Jeśli wszystkie akcje listy filtrów odpowiada nagłówka Action w wiadomości lub bufor komunikatów `Match` metoda zwraca `true`. Jeśli lista jest pusta, filtr jest uznawany za zgodny buforu filtru i każdej wiadomości lub wiadomości wszystkie dopasowania i `Match` zwraca `true`. Jeśli żadna z akcji listy filtrów nie odpowiada nagłówka Action w wiadomości lub bufor komunikatów `Match` zwraca `false`. Jeśli nie akcji w wiadomości, a lista filtrów nie jest pusta, następnie `Match` zwraca `false`.  
  
### <a name="endpoint-address-filters"></a>Filtry adresu punktu końcowego  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtrów wiadomości oraz buforów komunikatów, na podstawie adresu punktu końcowego reprezentowany w kolekcji ich nagłówka. Wiadomość do przekazania odpowiedni filtr muszą być spełnione następujące warunki:  
  
-   Adres filtru identyfikator URI (Uniform Resource) musi być taka sama jak w komunikacie do nagłówka.  
  
-   Każdy parametr punktu końcowego adresu filtru (`address.Headers` kolekcji) musi odnaleźć nagłówka wiadomości do mapowania na. Dodatkowych nagłówków wiadomości lub bufor komunikatów są dopuszczalne dopasowania pozostaje `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Prefiks filtry adres punktu końcowego  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> Podobnie do funkcji <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrować, z wyjątkiem tego dopasowania może zawierać prefiks URI wiadomości. Na przykład filtr określający http://www.adatum.com adresu pasuje komunikaty adresowane do http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>Filtry komunikatów XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Używa wyrażenia XPath do sprawdzenia, czy dokument XML zawiera określone elementy, atrybuty, tekst, tworzy innych składni XML. Filtr jest zoptymalizowany się bardzo wydajny podzbiór strict XPath. XML Path Language jest opisany w [specyfikacji W3C XML Path Language 1.0](http://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Zwykle aplikacja używa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> w punkcie końcowym na zapytanie o zawartość komunikatu protokołu SOAP, a następnie przełącza odpowiednie działania na podstawie wyników tego zapytania. Aby sprawdzić priorytet elementu znane nagłówka do określenia, czy można przenieść komunikatu z przodu kolejki usługi kolejkowania proces, na przykład może używać Kwerenda XPath.  
  
## <a name="filter-tables"></a>Tabele filtru  
 Filtr tabele są używane do przechowywania par klucz wartość, gdzie filtr jest kluczem, a niektóre dane skojarzone wartości. Filtrowanie danych można wskazać, jakie akcje do wykonania, jeśli komunikat jest zgodny z filtrem i typu danych filtru jest parametru ogólnego dla klasy tabeli filtrów. Filtrowanie danych może składać się z regułami routingu, stan zabezpieczeń sesji, odbiorników w kanale i tak dalej. Dane można gdzie wymagane jest sterowanie przepływem danych.  
  
 Tabele filtru implementować interfejs generyczny <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Tabele filtru skorzystać z kilku metod zgodnymi komunikat wszystkie filtry w tabeli i zwraca nieuporządkowaną kolekcji dopasowywania danych lub filtrów. Niektóre metody dopasowania są wielu match i zwracać wszystkie zgodne elementy. Inne są jednym match, zwracanie tylko jeden element i zgłosić <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> jeśli odpowiada więcej niż jeden filtr.  
  
### <a name="message-filter-table"></a>Tabela filtr komunikatów  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> Jest najbardziej ogólnym wykonania <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Filtry wszystkich typów można przechowywać w tabeli.  
  
 Filtry, których najwyższy priorytet jest oznaczony do największej liczby można przypisać priorytety liczbowe. Wiele typów filtrów może mieć ten sam priorytet. Określony typ filtru może występować w więcej niż jeden poziom priorytetu.  
  
 Dopasowywanie odbywa się z najwyższym priorytetem, a raz spełniających kryteria filtrów o danym priorytecie, znajdują się żadnych filtrów z niższych priorytetach są sprawdzane. W związku z tym w przypadku przy użyciu pojedynczego filtru zgodna metoda, filtru więcej niż jeden zgodny komunikat, ale każdego zgodne z filtrem ma inny priorytet, nie wyjątek i zwracany jest filtr o najwyższym priorytecie. Podobnie filtr wielu odpowiada metoda zwraca tylko te spełniających kryteria filtrów o najwyższym priorytecie.  
  
### <a name="xpath-message-filter-table"></a>Tabela filtr XPath komunikatów  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Jest zoptymalizowana pod kątem deklaratywne filtrach XPath, tak aby klucza tabeli <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Klasy optymalizuje dopasowywanie podzbiór XPath obejmuje większość scenariuszy wysyłania komunikatów, który również obsługuje pełne gramatyki XPath 1.0. Algorytmy wydajne dopasowanie równoległych optymalizacji.  
  
 Ta tabela ma kilka specjalne `Match` metod, które działają na <xref:System.Xml.XPath.XPathNavigator> i <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> rozszerza <xref:System.Xml.XPath.XPathNavigator> klasy, dodając <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> właściwości. Ta właściwość umożliwia pozycji w dokumencie XML na zapisywanie i szybko załadowany bez konieczności sklonować Nawigatora alokacji pamięci kosztowne który <xref:System.Xml.XPath.XPathNavigator> wymaga dla tych operacji. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aparat XPath często muszą rejestrować pozycji kursora w trakcie wykonywania zapytania w dokumentach XML, więc <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> zawiera ważne optymalizacji dla przetwarzania komunikatów.  
  
## <a name="customer-scenarios"></a>Scenariusze klienta  
 Umożliwia filtrowanie w dowolnym momencie chcesz wysłać komunikat do modułów przetwarzania różne w zależności od danych zawartych w wiadomości. Dwa typowe scenariusze są routingu komunikat na podstawie jego działania kodu i zwalnia Multipleksowanie strumienia komunikatów na podstawie adresu punktu końcowego wiadomości.  
  
### <a name="routing"></a>Routing  
 Odbiornik punktu końcowego nasłuchuje wiadomości, które mają co najmniej jeden kod akcji w nagłówku protokołu SOAP. To wdrożenie, tworząc <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> przez przekazanie tablicy, który zawiera kody akcji dla jego konstruktora. Używa tego filtru, aby zarejestrować w usłudze `ListenerFactory`, więc tylko komunikaty, w których akcji odpowiada jednej z tych w filtrze uzyskanie dostępu do tego punktu końcowego.  
  
### <a name="de-multiplexing"></a>Usuń zaznaczenie pola Multipleksowanie  
 Jeśli wiele punktów końcowych wentylatorów z tej samej `ServiceListener` wyłączyć sieć, jedynym sposobem na demultipleksowania wiadomości i wiedzieć, czy należą one do niektórych adres punktu końcowego, jest użycie <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, który wybierz wiadomości kierunku zarejestrowanych punkty końcowe według wykonywane jest wyszukiwanie informacji przechowywanych w nagłówkach. W tych filtrów tylko tych wiadomości, które przekazują są wszystkie niezbędne nagłówki, które odpowiadają zarówno:  
  
-   Identyfikator URI w `EndpointAddress`.  
  
-   Pozostałe parametry punktu końcowego w `EndpointAddress` jak określono w <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Zobacz też  
 [Transfer i serializacja danych](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

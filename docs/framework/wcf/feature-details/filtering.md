---
title: Filtrowanie
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: 735fd4252bb1740c149659f6c6fe81f18285914a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626111"
---
# <a name="filtering"></a>Filtrowanie
Windows Communication Foundation (WCF) systemu filtrowania umożliwia deklaratywne filtry dopasowanie wiadomości i podejmowania decyzji operacyjne. Filtry można użyć, aby określić, co należy zrobić z komunikatem, sprawdzając część komunikatu. Proces kolejkowania, na przykład, można użyć zapytania XPath 1.0 do sprawdzenia elementu priority znanych nagłówka w celu ustalenia, czy można przenieść komunikatu z przodu kolejki.  
  
 System filtrowania składa się z zestawu klas, które mogą efektywnie ustalić, które zestaw filtrów są `true` dla danego komunikatu WCF.  
  
 Filtrowanie system jest podstawowym składnikiem obsługi wiadomości WCF; jest ona przeznaczona do bardzo szybkiego działania. Każda implementacja filtru został zoptymalizowany dla określonego rodzaju dopasowywanie względem komunikatów WCF.  
  
 Filtrowanie system nie jest bezpieczny dla wątków. Aplikacja musi obsługiwać żadnych semantyką blokowania. Jednak obsługuje ona wiele czytnika, pojedynczy składnik zapisywania.  
  
## <a name="where-filtering-fits"></a>Gdzie znajdzie filtrowania  
 Filtrowanie odbywa się po komunikat jest odbierany i jest częścią procesu wysyłania komunikatu do składnika aplikacji odpowiednie. Projekt systemu filtrowania adresów wymagania kilka podsystemów WCF, w tym obsługi komunikatów, routingu, zabezpieczeń, obsługi zdarzeń i zarządzanie systemem.  
  
## <a name="filters"></a>Filtry  
 Aparat filtr ma dwa podstawowe składniki, filtry i filtrowania tabel. Filtr sprawia, że logiczna decyzje dotyczące wiadomości na podstawie określonych przez użytkownika warunków logicznych. Implementuje filtry <xref:System.ServiceModel.Dispatcher.MessageFilter> klasy.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Metody są używane do ustalenia, jeśli wiadomość spełnia filtru. Jedną z metod testów nagłówka komunikatu, ale nie można dokonać inspekcji treść komunikatu. Inna metoda pobiera *buforu komunikatu* jako parametr wejściowy i sprawdzić, czy treść komunikatu.  
  
 Filtry nie jest zazwyczaj sprawdzana osobno, ale jako część tabelę filtru, który jest ogólnej klasy, która <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> metoda tworzy.  
  
 Kilka rodzajów filtry każdego specjalizują się w dopasowywanie na określonego rodzaju warunek logiczny. Gdy konstruowania filtru nie można zmienić kryteria, które używa filtru; Aby zmodyfikować kryteria filtrowania, utworzyć nową, a następnie usuń istniejący filtr.  
  
### <a name="action-filters"></a>Filtry akcji  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Zawiera listę parametrów akcji. Jeśli wszystkie akcje, na liście filtru zgodny nagłówek akcji w wiadomości lub buforu komunikatów `Match` metoda zwraca `true`. Jeśli lista jest pusta, filtr jest uznawany za dopasowuje wszystkie dopasowania buforu filtru i komunikatów lub komunikatów i `Match` zwraca `true`. Jeśli żadna z tych akcji, na liście filtru zgodny nagłówek akcji w wiadomości lub buforu komunikatów `Match` zwraca `false`. Jeśli nie ma akcji w wiadomości, a lista filtrów jest pusta, następnie `Match` zwraca `false`.  
  
### <a name="endpoint-address-filters"></a>Filtry adresu punktu końcowego  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtry wiadomości oraz buforów komunikatów, na podstawie adresu punktu końcowego reprezentowane w ich kolekcję nagłówków. Wiadomości do przekazania filtr muszą być spełnione następujące warunki:  
  
-   Filtru adresu identyfikator (URI) musi być taka sama jak w wiadomości do nagłówka.  
  
-   Każdy parametr punkt końcowy adres filtru (`address.Headers` kolekcji) musi odnaleźć nagłówka komunikatu do mapowania na. Dodatkowe nagłówki wiadomości lub buforu komunikatów są akceptowalne dla dopasowanie, aby pozostać `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Prefiks filtry adres punktu końcowego  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> Podobnie jak funkcje <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrowania, z tą różnicą, że dopasowanie może to być prefiksem komunikat o identyfikatorze URI. Na przykład filtr, określając adres `http://www.adatum.com` odpowiada na komunikaty adresowane do `http://www.adatum.com/userA`.  
  
### <a name="xpath-message-filters"></a>Filtry komunikatów XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Używa wyrażenia XPath do określenia, czy dokument XML zawiera określone elementy, atrybuty, tekst lub inne składni XML tworzy. Filtr jest zoptymalizowany do być bardzo wydajny podzbiór XPath. Język ścieżki XML jest opisana w [specyfikacji W3C XML ścieżka język 1.0](https://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Zazwyczaj aplikacja używa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> w punkcie końcowym, aby zapytanie o zawartość komunikatu protokołu SOAP, a następnie pobiera odpowiednie działania na podstawie wyników tej kwerendy. Aby sprawdzić priorytet elementu znany nagłówek zdecydować, czy można przenieść komunikatu z przodu kolejki proces kolejkowania, na przykład, może używać zapytania XPath.  
  
## <a name="filter-tables"></a>Filtrowanie tabel  
 Filtr tabele są używane do przechowywania par klucz wartość, gdy filtr jest kluczem, a niektóre powiązane dane jest wartością. Filtrowanie danych może służyć do wskazania, jakie działania należy podjąć, jeśli komunikat jest zgodny z filtrem i typu danych filtru jest parametru ogólnego dla klasy tabeli filtru. Filtrowanie danych może składać się z reguł routingu, stanu zabezpieczeń sesji, odbiorniki kanałów i tak dalej. Dane mogą być używane, gdy sterowanie przepływem danych jest konieczne.  
  
 Tabele filtr implementować interfejs ogólny <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtr tabele zawierają kilka metod, które odpowiada wiadomość ze wszystkimi filtrami w tabeli i zwracają nieuporządkowanej kolekcji odpowiadającą jej instrukcją filtry lub danych. Niektóre metody dopasowania wielu spełniają i zwracać wszystkie zgodne elementy. Inne są jednym match, zwracając tylko jeden element i zgłosić <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> Jeśli pasuje do więcej niż jeden filtr.  
  
### <a name="message-filter-table"></a>Tabela filtr komunikatów  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> Jest najbardziej ogólnym implementacją <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Filtry dla wszystkich typów można przechowywać w tabeli.  
  
 Możesz przypisać priorytety liczbowe filtrów, gdzie najwyższym priorytetem jest oznaczony do największej liczby. Wiele typów filtrów może mieć ten sam priorytet. Określony typ filtru może znajdować się w więcej niż jeden poziom priorytetu.  
  
 Dopasowanie jest wykonywane począwszy najwyższy priorytet, a po pasujące do filtrów o danym priorytecie, znajdują się żadnych filtrów o niższych priorytetach są sprawdzane. W związku z tym Jeśli jesteś przy użyciu pojedynczego filtru match — metoda i więcej niż jeden filtr dopasowuje wartość do wiadomości, ale każdego pasującego filtr ma inny priorytet, a następnie jest zgłaszany żaden wyjątek i filtr z najwyższym priorytetem jest zwracana. Podobnie filtr wielu odpowiadają metoda zwraca tylko pasujące do filtrów o najwyższym priorytecie.  
  
### <a name="xpath-message-filter-table"></a>Tabela Filtr komunikatu XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Została zoptymalizowana pod kątem filtrach XPath deklaracyjne, dzięki czemu klucza tabeli <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Klasy optymalizuje dopasowania dla podzbioru XPath, który obejmuje większość scenariuszy obsługi wiadomości i obsługuje także pełne gramatyki języka XPath 1.0. Wydajne dopasowania równoległych algorytmów optymalizacji.  
  
 Ta tabela ma kilka specjalistycznych `Match` metod, które pracują nad <xref:System.Xml.XPath.XPathNavigator> i <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> rozszerza <xref:System.Xml.XPath.XPathNavigator> klasy, dodając <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> właściwości. Ta właściwość umożliwia położenie dokumentu XML na zapisywanie i szybko załadowane bez konieczności sklonować Nawigatora alokacji pamięci kosztowne, <xref:System.Xml.XPath.XPathNavigator> wymaga takich operacji. Aparat WCF XPath często należy zarejestrować pozycję kursora w trakcie wykonywania zapytań w dokumentach XML, więc <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> udostępnia ważne optymalizacji do przetwarzania komunikatów.  
  
## <a name="customer-scenarios"></a>Scenariusze klienta  
 Możesz użyć filtrowania w dowolnym momencie, aby wysłać komunikat do modułów przetwarzania różne w zależności od danych zawartych w wiadomości. Dwa typowe scenariusze są routing komunikatów na podstawie jego działania kodu i cofnąć Multipleksowanie strumienia komunikatów na podstawie adresu punktu końcowego wiadomości.  
  
### <a name="routing"></a>Routing  
 Odbiornik punktu końcowego odbiera komunikaty, które mają co najmniej jeden kod akcji w wiadomości SOAP nagłówka. Implementowanie to przez utworzenie <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> , przekazując tablicę, która zawiera kody akcji dla jego konstruktora. Używa ona z filtrem, aby zarejestrować się w `ListenerFactory`, więc tylko komunikaty, w której działanie pasuje do jednej z nich w filtrze uzyskać dostęp do tego punktu końcowego.  
  
### <a name="de-multiplexing"></a>Usuń zaznaczenie pola Multipleksowanie  
 Jeśli wiele punktów końcowych rozdysponować z tej samej `ServiceListener` wyłączyć sieć, jedynym sposobem, aby cofnąć multipleksować wiadomości i ustalić, czy należą one do pewnych adres punktu końcowego, jest użycie <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, która wybierz wiadomości kierunku zarejestrowanych punkty końcowe według wykonywane jest wyszukiwanie informacji przechowywanych w nagłówkach. Te filtry te komunikaty, które przekazują mają wszystkie niezbędne nagłówki, które odnoszą się do obu:  
  
-   Identyfikator URI w `EndpointAddress`.  
  
-   Pozostałe parametry punktu końcowego w `EndpointAddress` określonej <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Zobacz także
- [Transfer i serializacja danych](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

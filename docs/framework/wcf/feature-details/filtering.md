---
title: Filtrowanie
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: efbedc16fe48d83cdc4223862bc691e9cbe15c10
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964293"
---
# <a name="filtering"></a>Filtrowanie
System filtrowania Windows Communication Foundation (WCF) może używać filtrów deklaratywnych do dopasowywania komunikatów i podejmowania decyzji operacyjnych. Można użyć filtrów, aby określić, co zrobić z komunikatem, sprawdzając część komunikatu. Proces kolejkowania, na przykład, może użyć zapytania XPath 1,0 do sprawdzenia elementu priorytet znanego nagłówka, aby określić, czy przenieść komunikat na pierwszy plan kolejki.  
  
 System filtrowania składa się z zestawu klas, które mogą efektywnie ustalić, który zestaw filtrów jest `true` dla konkretnego komunikatu WCF.  
  
 System filtrowania jest głównym składnikiem obsługi komunikatów WCF; jest ona zaprojektowana tak, aby była niezwykle szybka. Każda implementacja filtru została zoptymalizowana pod kątem określonego rodzaju dopasowania do komunikatów WCF.  
  
 System filtrowania nie jest bezpieczny wątkowo. Aplikacja musi obsługiwać jakąkolwiek semantykę blokującą. Obsługuje ona jednak wiele czytników, ale tylko jeden składnik zapisywania.  
  
## <a name="where-filtering-fits"></a>Gdzie filtrowanie pasuje  
 Filtrowanie jest wykonywane po odebraniu komunikatu i jest częścią procesu wysyłania komunikatu do odpowiedniego składnika aplikacji. Projekt systemu filtrowania dotyczy wymagań kilku podsystemów WCF, w tym komunikatów, routingu, zabezpieczeń, obsługi zdarzeń i zarządzania systemem.  
  
## <a name="filters"></a>Filtry  
 Aparat filtrów ma dwa podstawowe składniki, filtry i tabele filtrów. Filtr podejmuje decyzje logiczne dotyczące wiadomości w oparciu o warunki logiczne określone przez użytkownika. Filtry implementują klasę <xref:System.ServiceModel.Dispatcher.MessageFilter>.  
  
 Metody <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> są używane do określenia, czy komunikat spełnia kryteria filtru. Jedna z metod testuje nagłówek wiadomości, ale nie może zbadać treści komunikatu. Druga metoda przyjmuje *bufor komunikatów* jako parametr wejściowy i może zbadać treść wiadomości.  
  
 Filtry nie są zwykle testowane pojedynczo, ale w ramach tabeli filtrów, która jest klasą rodzajową, którą tworzy Metoda <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A>.  
  
 Kilka rodzajów filtrów, w których każda specjalizacja jest zgodna z określonym rodzajem warunku logicznego. Po skonstruowaniu filtru nie można zmienić kryteriów, których używa filtr; Aby zmodyfikować kryteria filtru, Utwórz nowe i usuń istniejący filtr.  
  
### <a name="action-filters"></a>Filtry akcji  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> zawiera listę ciągów akcji. Jeśli którakolwiek z akcji z listy filtrów pasuje do nagłówka akcji w buforze komunikatów lub komunikatów, Metoda `Match` zwraca `true`. Jeśli lista jest pusta, filtr jest traktowany jako dopasowany filtr i wszystkie komunikaty lub bufory komunikatów, a `Match` zwraca `true`. Jeśli żadna z akcji na liście filtru nie jest zgodna z nagłówkiem akcji w buforze komunikatów lub komunikatów, `Match` zwraca `false`. Jeśli komunikat nie zawiera żadnej akcji, a lista filtrów nie jest pusta, `Match` zwraca `false`.  
  
### <a name="endpoint-address-filters"></a>Filtry adresów punktu końcowego  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtruje komunikaty i bufory komunikatów na podstawie adresu punktu końcowego reprezentowanego w kolekcji nagłówków. Aby komunikat przeszedł do tego filtru, muszą zostać spełnione następujące warunki:  
  
- Uniform Resource Identifier adresu filtru (URI) musi być taka sama jak wartość w polu wiadomość do nagłówka.  
  
- Każdy parametr punktu końcowego w adresie filtru (`address.Headers` Collection) musi znaleźć nagłówek w komunikacie, aby zamapować. Dodatkowe nagłówki w wiadomości lub buforze komunikatów są akceptowane, aby dopasowanie pozostało `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Filtry adresów punktu końcowego prefiksu  
  
1. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> działa podobnie jak filtr <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>, z tą różnicą, że dopasowanie może być na prefiksie identyfikatora URI wiadomości. Na przykład filtr określający adres `http://www.adatum.com` jest zgodny z wiadomościami zaadresowanymi do `http://www.adatum.com/userA`.  
  
### <a name="xpath-message-filters"></a>Filtry komunikatów XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> używa wyrażenia XPath, aby określić, czy dokument XML zawiera konkretne elementy, atrybuty, tekst lub inne konstrukcje składni XML. Filtr jest zoptymalizowany pod kątem niezwykle wydajnego podzbioru wyrażenia XPath. Język ścieżki XML został opisany w [specyfikacji języka XML Path w formacie W3C 1,0](https://www.w3.org/TR/xpath/all/).  
  
 Zazwyczaj aplikacja używa <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> w punkcie końcowym do wysyłania zapytań do zawartości komunikatu protokołu SOAP, a następnie pobiera odpowiednią akcję na podstawie wyników zapytania. Proces kolejkowania, na przykład, może użyć zapytania XPath do sprawdzenia elementu priorytet znanego nagłówka, aby zdecydować, czy przenieść komunikat na pierwszy plan kolejki.  
  
## <a name="filter-tables"></a>Filtruj tabele  
 Tabele filtrów są używane do przechowywania par klucz-wartość, gdzie filtr jest kluczem, a niektóre skojarzone dane są wartościami. Dane filtru mogą służyć do wskazywania, jakie akcje należy wykonać, jeśli komunikat pasuje do filtru i typ danych filtru jest parametrem ogólnym klasy filtru tabeli. Dane filtru mogą zawierać reguły routingu, stan zabezpieczeń sesji, odbiorniki w kanale itd. Dane mogą być używane, gdy wymagane jest sterowanie przepływem danych.  
  
 Tabele filtrów implementują <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>interfejsu ogólnego.  
  
 Tabele filtrów mają kilka metod, które pasują do komunikatów względem wszystkich filtrów w tabeli i zwracają nieuporządkowaną kolekcję pasujących filtrów lub danych. Niektóre metody dopasowania są wielokrotnością dopasowania i zwracają wszystkie zgodne elementy. Inne są pojedynczymi dopasowaniami, zwracają tylko jeden element i generują <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException>, jeśli więcej niż jeden filtr jest zgodny.  
  
### <a name="message-filter-table"></a>Tabela filtru komunikatów  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> to najbardziej ogólna implementacja <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. Można przechowywać filtry wszystkich typów w tabeli.  
  
 Można przypisać priorytety liczbowe do filtrów, gdzie najwyższy priorytet jest oznaczony największą liczbą. Wiele typów filtrów może mieć ten sam priorytet. Określony typ filtru może być wyświetlany na więcej niż jeden poziom priorytetu.  
  
 Dopasowanie jest wykonywane począwszy od najwyższego priorytetu, a po znalezieniu pasujących filtrów o danym priorytecie nie są badane żadne filtry o niższych priorytetach. W związku z tym, jeśli używasz metody dopasowania pojedynczego filtru i więcej niż jeden filtr dopasowuje komunikat, ale każdy pasujący filtr ma inny priorytet, nie zostanie zgłoszony żaden wyjątek i zostanie zwrócony filtr o najwyższym priorytecie. Podobnie Metoda dopasowywania wielu filtrów zwraca tylko te filtry zgodne z najwyższym priorytetem.  
  
### <a name="xpath-message-filter-table"></a>Tabela filtru komunikatów XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> jest zoptymalizowany pod kątem deklaratywnych filtrów XPath, więc klucz tabeli jest <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 Klasa <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> optymalizuje dopasowanie dla podzbioru XPath, który obejmuje większość scenariuszy obsługi komunikatów, a także obsługuje pełną gramatykę XPath 1,0. Ma zoptymalizowane algorytmy do wydajnego dopasowywania równoległego.  
  
 Ta tabela ma kilka wyspecjalizowanych metod `Match`, które działają na <xref:System.Xml.XPath.XPathNavigator> i <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> rozszerza klasę <xref:System.Xml.XPath.XPathNavigator> przez dodanie właściwości <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A>. Ta właściwość umożliwia szybkie zapisywanie i ładowanie pozycji w dokumencie XML bez konieczności klonowania nawigatora, czyli alokacji pamięci wymaganej przez <xref:System.Xml.XPath.XPathNavigator> dla takiej operacji. Aparat języka XPath WCF musi często rejestrować położenie kursora w trakcie wykonywania zapytań w dokumentach XML, dlatego <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> zapewnia ważną optymalizację przetwarzania komunikatów.  
  
## <a name="customer-scenarios"></a>Scenariusze klientów  
 Filtrowania można użyć w dowolnym momencie, w którym chcesz wysłać komunikat do różnych modułów przetwarzania w zależności od danych zawartych w komunikacie. Dwa typowe scenariusze umożliwiają kierowanie komunikatów na podstawie kodu akcji i demultipleksowanie strumienia komunikatów na podstawie adresu punktu końcowego komunikatów.  
  
### <a name="routing"></a>Routing  
 Odbiornik punktu końcowego nasłuchuje komunikatów, które mają co najmniej jeden kod akcji w nagłówku protokołu SOAP komunikatu. W tym celu należy utworzyć <xref:System.ServiceModel.Dispatcher.ActionMessageFilter>, przekazując tablicę zawierającą kody akcji do konstruktora. Używa tego filtru do zarejestrowania się w `ListenerFactory`, więc tylko komunikaty, których akcja pasuje do jednego z tych w filtrach, odnoszą się do danego punktu końcowego.  
  
### <a name="de-multiplexing"></a>Demultipleksowanie  
 Gdy wiele punktów końcowych jest z tego samego `ServiceListener` poza przewodem, jedynym sposobem na demultiplekserowanie komunikatów i wiedzą, czy należą one do określonego adresu punktu końcowego, jest użycie <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, które wybierają komunikaty do zarejestrowanych punktów końcowych, wykonując wyszukiwanie informacji przechowywanych w nagłówkach. W tych filtrach tylko komunikaty, które zostały przekazane, mają wszystkie niezbędne nagłówki, które odpowiadają obu:  
  
- Identyfikator URI w `EndpointAddress`.  
  
- Pozostałe parametry punktu końcowego w `EndpointAddress`, jak określono w <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Zobacz także

- [Transfer i serializacja danych](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)

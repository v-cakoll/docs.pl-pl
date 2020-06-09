---
title: Zagadnienia związane z zabezpieczeniami danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 8cb7ee2ea2418602d944c3c08cec2b9279dca3b9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601065"
---
# <a name="security-considerations-for-data"></a>Zagadnienia związane z zabezpieczeniami danych

Podczas pracy z danymi w Windows Communication Foundation (WCF) należy wziąć pod uwagę wiele kategorii zagrożeń. W poniższej tabeli wymieniono najważniejsze klasy zagrożeń, które odnoszą się do przetwarzania danych. Funkcja WCF oferuje narzędzia pozwalające ograniczyć te zagrożenia.

Odmowa usługi podczas otrzymywania niezaufanych danych może spowodować, że po stronie odbiorczej dostęp do niewspółmiernej ilości różnych zasobów, takich jak pamięć, wątki, dostępne połączenia lub cykle procesora, jest spowodowany długimi obliczeniami. Atak typu "odmowa usługi" na serwer może spowodować awarię i uniemożliwić przetworzenie komunikatów od innych, uprawnionych klientów.

Złośliwe wykonanie kodu przychodzące dane niezaufane powodują, że Strona otrzymująca może uruchomić kod, którego nie ma.

Ujawnienie informacji zdalne osoby atakujące wymuszają reagowanie na żądania w taki sposób, aby ujawnić więcej informacji niż ma to na celu.

## <a name="user-provided-code-and-code-access-security"></a>Kod dostarczony przez użytkownika i zabezpieczenia dostępu kodu

Liczba miejsc w infrastrukturze programu Windows Communication Foundation (WCF), która jest dostarczana przez użytkownika. Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> aparat serializacji może wywoływać metody dostępu do właściwości `set` i metod dostępu dostarczonych przez użytkownika `get` . Infrastruktura kanału WCF może również wywołać klasy pochodne dostarczone przez użytkownika <xref:System.ServiceModel.Channels.Message> klasy.

Jest odpowiedzialny za autora kodu, aby upewnić się, że nie istnieją żadne luki w zabezpieczeniach. Jeśli na przykład utworzysz typ kontraktu danych z właściwością elementu członkowskiego danych typu Integer, a w `set` implementacji metody dostępu zostanie przydzielona tablica oparta na wartości właściwości, zostanie ujawniona możliwość ataku typu "odmowa usługi", Jeśli złośliwy komunikat zawiera bardzo dużą wartość dla tego elementu członkowskiego danych. Ogólnie rzecz biorąc, unikaj przydziałów w oparciu o dane przychodzące lub długotrwałe przetwarzanie w kodzie dostarczonym przez użytkownika (szczególnie w przypadku, gdy długotrwałe przetwarzanie może być spowodowane przez niewielką ilość danych przychodzących). Podczas przeprowadzania analizy zabezpieczeń kodu dostarczonego przez użytkownika należy rozważyć również wszystkie przypadki awarii (czyli wszystkie gałęzie kodu, w których są zgłaszane wyjątki).

Najważniejszym przykładem kodu dostarczonego przez użytkownika jest kod wewnątrz implementacji usługi dla każdej operacji. Obowiązkiem jest bezpieczeństwo implementacji usługi. W łatwy sposób można przypadkowo utworzyć niezabezpieczone implementacje, które mogą spowodować luki w zabezpieczeniach typu "odmowa usługi". Na przykład operacja pobierająca ciąg i zwraca listę klientów z bazy danych, której nazwa rozpoczyna się od tego ciągu. Jeśli pracujesz z dużą bazą danych, a przesłany ciąg jest tylko pojedynczą literą, kod może próbować utworzyć komunikat przekraczający całą dostępną pamięć, powodując niepowodzenie całej usługi. ( <xref:System.OutOfMemoryException> Nie jest możliwy do odzyskania w .NET Framework i zawsze powoduje zakończenie działania aplikacji).

Należy upewnić się, że żaden złośliwy kod nie jest podłączony do różnych punktów rozszerzających. Jest to szczególnie istotne w przypadku uruchamiania w ramach częściowej relacji zaufania, z uwzględnieniem typów z częściowo zaufanych zestawów lub tworzenia składników użytecznych przez częściowo zaufany kod. Aby uzyskać więcej informacji, zobacz "częściowe zagrożenia zaufania" w dalszej części.

Należy pamiętać, że w przypadku uruchamiania w częściowej relacji zaufania infrastruktura serializacji kontraktu danych obsługuje tylko ograniczony podzbiór modelu programowania kontraktu danych — na przykład prywatne elementy członkowskie danych lub typy używające <xref:System.SerializableAttribute> atrybutu nie są obsługiwane. Aby uzyskać więcej informacji, zobacz [częściowe zaufanie](partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Unikanie przypadkowego ujawnienia informacji

Podczas projektowania typów możliwych do serializacji z uwzględnieniem zabezpieczeń, ujawnienie informacji jest możliwym problemem.

Rozważ następujące kwestie:

- <xref:System.Runtime.Serialization.DataContractSerializer>Model programowania umożliwia narażenie danych prywatnych i wewnętrznych poza typem lub zestawem podczas serializacji. Ponadto kształt typu może być narażony podczas eksportowania schematu. Pamiętaj, aby zrozumieć rzutowanie serializacji typu. Jeśli nie chcesz niczego ujawniać, wyłącz Serializowanie go (na przykład przez niestosowanie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu w przypadku kontraktu danych).

- Należy pamiętać, że ten sam typ może mieć wiele prognoz serializacji, w zależności od używanego serializatora. Ten sam typ może uwidaczniać jeden zestaw danych, gdy jest używany z <xref:System.Runtime.Serialization.DataContractSerializer> i innym zestawem danych, gdy jest używany z <xref:System.Xml.Serialization.XmlSerializer> . Przypadkowe użycie niewłaściwego serializatora może prowadzić do ujawnienia informacji.

- Użycie <xref:System.Xml.Serialization.XmlSerializer> w trybie/Encoded w starszej wersji zdalnego wywołania procedury (RPC) może przypadkowo uwidocznić kształt grafu obiektów po stronie wysyłającej.

## <a name="preventing-denial-of-service-attacks"></a>Zapobieganie atakom typu "odmowa usługi"

### <a name="quotas"></a>Przydziały

Spowodowanie przydzielenia przez stronę otrzymującej znacznej ilości pamięci jest potencjalny atak typu "odmowa usługi". Chociaż ta sekcja koncentruje się na problemach z użyciem pamięci, wynikających z dużych komunikatów, mogą wystąpić inne ataki. Na przykład komunikaty mogą wykorzystywać nieproporcjonalną ilość czasu przetwarzania.

Ataki typu "odmowa usługi" są zazwyczaj zmniejszane za pomocą przydziałów. W przypadku przekroczenia limitu przydziału <xref:System.ServiceModel.QuotaExceededException> wyjątek jest zgłaszany zwykle. Bez przydziału złośliwy komunikat może spowodować uzyskanie dostępu do całej dostępnej pamięci, co spowodowało <xref:System.OutOfMemoryException> wyjątek lub dostęp do wszystkich dostępnych stosów, co powoduje wystąpienie <xref:System.StackOverflowException> .

Scenariusz przekroczony limit przydziału jest możliwy do odzyskania; Jeśli napotkasz w uruchomionej usłudze, komunikat, który jest aktualnie przetwarzany, jest odrzucany, a usługa działa i przetwarza dalsze komunikaty. Scenariusze braku pamięci i przepełnienia stosu nie są jednak możliwe do odzyskania w dowolnym miejscu .NET Framework; Usługa kończy działanie w przypadku wystąpienia takich wyjątków.

Limity przydziału w programie WCF nie obejmują żadnej alokacji wstępnej. Na przykład, jeśli <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> limit przydziału (znaleziony w różnych klasach) jest ustawiony na 128 kb, nie oznacza to, że 128 KB jest automatycznie przypisywany dla każdego komunikatu. Przydzieloną ilość rzeczywistą zależy od rzeczywistego rozmiaru wiadomości przychodzącej.

W warstwie transportowej są dostępne wiele przydziałów. Są to przydziały wymuszane przez określony kanał transportu w użyciu (HTTP, TCP itd.). Chociaż w tym temacie omówiono niektóre z tych przydziałów, te limity przydziału są szczegółowo opisane w przystawce [zasoby transportowe](transport-quotas.md).

### <a name="hashtable-vulnerability"></a>Luka w zabezpieczeniach

Występuje luka w zabezpieczeniach, gdy Kontrakty danych zawierają Hashtable lub kolekcje. Ten problem występuje, gdy duża liczba wartości jest wstawiana do tablicy skrótów, w której duża liczba tych wartości generuje tę samą wartość skrótu. Może to służyć jako atak typu DOS.  Tę lukę w zabezpieczeniach można wyeliminować, ustawiając limit przydziału dla powiązania MaxReceivedMessageSize. Należy zachować ostrożność podczas ustawiania tego przydziału, aby zapobiec takim atakom. Ten limit przydziału umieszcza górny limit rozmiaru komunikatów WCF. Ponadto należy unikać używania tablic lub kolekcji w kontraktach danych.

## <a name="limiting-memory-consumption-without-streaming"></a>Ograniczanie użycia pamięci bez przesyłania strumieniowego

Model zabezpieczeń wokół dużych komunikatów zależy od tego, czy przesyłanie strumieniowe jest w użyciu. W przypadku podstawowego, niestrumieniowego przypadku, komunikaty są buforowane w pamięci. W takim przypadku należy użyć <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> przydziału na <xref:System.ServiceModel.Channels.TransportBindingElement> lub w powiązaniach dostarczonych przez system w celu ochrony przed dużymi komunikatami przez ograniczenie maksymalnego rozmiaru komunikatu do dostępu. Należy zauważyć, że usługa może przetwarzać wiele komunikatów w tym samym czasie, w którym to przypadku wszystkie w pamięci. Użyj funkcji ograniczania przepustowości, aby zmniejszyć to zagrożenie.

Należy również pamiętać, że nie należy `MaxReceivedMessageSize` górną granicą zużycia pamięci dla poszczególnych komunikatów, ale ogranicza ją do poziomu stałego czynnika. Na przykład, jeśli `MaxReceivedMessageSize` otrzymasz 1 MB i zostanie wyświetlony komunikat 1-MB, a następnie zostanie on rozszeregowany, wymagana jest dodatkowa pamięć, która będzie zawierać deserializowany wykres obiektu, co spowodowało całkowite zużycie pamięci na 1 MB. Z tego powodu należy unikać tworzenia możliwych do serializacji typów, które mogłyby spowodować znaczne użycie pamięci bez dużo danych przychodzących. Na przykład kontrakt danych "Moja Umowa" z 50 opcjonalnymi polami elementu członkowskiego danych i dodatkowymi polami prywatnymi 100 można utworzyć przy użyciu konstrukcji XML " \<MyContract/> ". Ten kod XML powoduje dostęp do pamięci dla 150 pól. Należy pamiętać, że elementy członkowskie danych są domyślnie opcjonalne. Problem jest składany, gdy taki typ jest częścią tablicy.

`MaxReceivedMessageSize`samo nie jest wystarczające, aby zapobiec atakom typu "odmowa usługi". Na przykład Deserializator może być zmuszony do deserializacji wykresu głęboko zagnieżdżonego obiektu (obiektu, który zawiera inny obiekt, który jest jeszcze inny, itd.) przez komunikat przychodzący. <xref:System.Runtime.Serialization.DataContractSerializer>I <xref:System.Xml.Serialization.XmlSerializer> metody wywołania w zagnieżdżonym sposobie deserializacji takich grafów. Głębokie zagnieżdżenie wywołań metod może spowodować nieodwracalne odzyskanie <xref:System.StackOverflowException> . To zagrożenie jest korygowane przez ustawienie limitu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> przydziału w celu ograniczenia poziomu zagnieżdżenia XML, jak opisano w sekcji "używanie bezpiecznego kodu XML" w dalszej części tematu.

Ustawienie dodatkowych przydziałów `MaxReceivedMessageSize` jest szczególnie ważne w przypadku korzystania z binarnego kodowania XML. Użycie kodowania binarnego jest nieco równoważne kompresji: niewielka grupa bajtów w komunikacie przychodzącym może reprezentować wiele danych. W ten sposób nawet komunikat dopasowywany do `MaxReceivedMessageSize` limitu może zająć dużo więcej pamięci w pełni rozwiniętej postaci. Aby wyeliminować takie zagrożenia specyficzne dla języka XML, wszystkie przydziały czytnika XML muszą być poprawnie ustawione, jak to opisano w sekcji "Korzystanie z bezpiecznego kodu XML" w dalszej części tego tematu.

## <a name="limiting-memory-consumption-with-streaming"></a>Ograniczanie zużycia pamięci przy użyciu przesyłania strumieniowego

W przypadku przesyłania strumieniowego można użyć małego `MaxReceivedMessageSize` Ustawienia do ochrony przed atakami typu "odmowa usługi". Jednak bardziej skomplikowane scenariusze są możliwe w przypadku przesyłania strumieniowego. Na przykład usługa przekazywania plików akceptuje pliki większe niż cała dostępna pamięć. W takim przypadku należy ustawić `MaxReceivedMessageSize` do bardzo dużej wartości, co oznacza, że prawie żadne dane nie są buforowane w pamięci i strumienie komunikatów bezpośrednio na dysku. Jeśli złośliwy komunikat może w jakiś sposób wymusić, aby usługa WCF mogła buforować dane zamiast przesyłania strumieniowego w tym przypadku, `MaxReceivedMessageSize` nie będzie już chronić się przed komunikatem dostępnym do całej dostępnej pamięci.

Aby zmniejszyć to zagrożenie, istnieją określone ustawienia limitu przydziału dla różnych składników przetwarzania danych programu WCF, które ograniczają buforowanie. Najważniejszym z nich jest `MaxBufferSize` Właściwość różnych elementów powiązania transportu i standardowe powiązania. W przypadku przesyłania strumieniowego ten limit przydziału powinien zostać ustawiony z uwzględnieniem maksymalnej ilości pamięci, która ma zostać przydzielona na wiadomość. Podobnie jak w przypadku `MaxReceivedMessageSize` , ustawienie nie ma absolutnej maksymalnej wartości zużycia pamięci, ale ogranicza ją tylko do poziomu stałego czynnika. Podobnie jak w przypadku programu `MaxReceivedMessageSize` , należy pamiętać o możliwości przetworzenia wielu komunikatów jednocześnie.

### <a name="maxbuffersize-details"></a>Szczegóły MaxBufferSize

`MaxBufferSize`Właściwość ogranicza wszystkie usługi WCF do buforowania zbiorczego. Na przykład program WCF zawsze buforuje nagłówki protokołu SOAP i błędy SOAP, a także wszystkie części MIME, które nie znajdują się w naturalnym porządku czytania w komunikacie mechanizmu optymalizacji transmisji komunikatów (MTOM). To ustawienie ogranicza ilość buforowania we wszystkich tych przypadkach.

Platforma WCF osiąga ten element, przekazując `MaxBufferSize` wartość do różnych składników, które mogą buforować. Na przykład niektóre <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> przeciążenia <xref:System.ServiceModel.Channels.Message> klasy przyjmują `maxSizeOfHeaders` parametr. Funkcja WCF przekazuje `MaxBufferSize` wartość do tego parametru, aby ograniczyć liczbę buforów nagłówka protokołu SOAP. Ważne jest, aby ustawić ten parametr w przypadku używania <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio. Ogólnie rzecz biorąc, w przypadku korzystania z składnika w programie WCF, który pobiera parametry przydziału, ważne jest, aby zrozumieć implikacje zabezpieczeń tych parametrów i ustawić je poprawnie.

Koder komunikatu MTOM również ma `MaxBufferSize` ustawienie. W przypadku korzystania z powiązań standardowych jest to automatycznie ustawiane na wartość na poziomie transportu `MaxBufferSize` . Jednak w przypadku użycia elementu powiązania kodera komunikatu MTOM do skonstruowania niestandardowego powiązania należy ustawić `MaxBufferSize` Właściwość na wartość bezpieczną, gdy używane jest przesyłanie strumieniowe.

## <a name="xml-based-streaming-attacks"></a>Ataki strumieniowe oparte na języku XML

`MaxBufferSize`sama nie jest wystarczająca, aby zapewnić, że nie można wymusić buforowania usługi WCF w przypadku, gdy jest oczekiwany strumień. Na przykład czytelnicy XML programu WCF zawsze buforują cały tag początkowy elementu XML przy rozpoczynaniu odczytywania nowego elementu. Dzięki temu obszary nazw i atrybuty są prawidłowo przetwarzane. Jeśli `MaxReceivedMessageSize` Konfiguracja jest duża (na przykład w celu włączenia scenariusza dużego przesyłania strumieniowego plików), złośliwy komunikat może być skonstruowany, gdzie cała treść komunikatu jest dużym tagiem początkowym elementu XML. Próba odczytu powoduje wystąpienie <xref:System.OutOfMemoryException> . Jest to jeden z wielu możliwych ataków typu "odmowa usługi" opartych na języku XML, które można rozwiązać za pomocą przydziałów czytnika XML, omówione w dalszej części tego tematu. W przypadku przesyłania strumieniowego jest szczególnie ważne, aby ustawić wszystkie te limity przydziału.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Mieszanie modeli programowania przesyłania strumieniowego i buforowania

Liczne możliwe ataki powstają w wyniku mieszania modeli programowania przesyłania strumieniowego i niestrumieniowego w ramach tej samej usługi. Załóżmy, że istnieje kontrakt usługi z dwiema operacjami: jeden z nich przyjmuje <xref:System.IO.Stream> tablicę niektórych typów niestandardowych. Załóżmy również, że `MaxReceivedMessageSize` ustawiono dużą wartość, aby włączyć pierwszą operację przetwarzania dużych strumieni. Niestety oznacza to, że można teraz wysyłać duże komunikaty do drugiej operacji, a Deserializator buforuje dane w pamięci jako tablicę przed wywołaniem operacji. Jest to potencjalny atak typu "odmowa usługi": limit `MaxBufferSize` przydziału nie ogranicza rozmiaru treści komunikatu, który jest używany przez deserializatora.

Z tego powodu należy unikać mieszania operacji w oparciu o strumień i niestrumieniowo w tym samym kontrakcie. W przypadku absolutnej konieczności mieszania dwóch modeli programowania należy zastosować następujące środki ostrożności:

- Wyłącz funkcję, <xref:System.Runtime.Serialization.IExtensibleDataObject> ustawiając <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> Właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> na `true` . Dzięki temu tylko członkowie, którzy są częścią kontraktu, są deszeregowani.

- Ustaw <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> Właściwość <xref:System.Runtime.Serialization.DataContractSerializer> na wartość bezpieczną. Ten limit przydziału jest również dostępny dla <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu lub za pomocą konfiguracji. Ten limit przydziału ogranicza liczbę obiektów, które są deserializowane w jednym odcinku deserializacji. Zwykle każdy parametr operacji lub część treści komunikatu w kontrakcie komunikatu jest deserializowana w jednym z epizodów. Podczas deserializacji tablic każda pozycja tablicy jest traktowana jako oddzielny obiekt.

- Ustaw wszystkie przydziały czytnika XML na wartości bezpieczne. Zwróć uwagę na to <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> , <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> i <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> i unikaj ciągów w operacjach nieprzesyłających strumieniowo.

- Przejrzyj listę znanych typów, pamiętając, że w dowolnym momencie można utworzyć wystąpienie dowolnego z nich (zobacz sekcję "uniemożliwianie załadowania nieoczekiwanych typów" w dalszej części tego tematu).

- Nie należy używać żadnych typów, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs buforujący dużą ilość danych. Nie należy dodawać takich typów do listy znanych typów.

- Nie należy używać <xref:System.Xml.XmlElement> tablic, <xref:System.Xml.XmlNode> <xref:System.Byte> tablic ani typów, które implementują <xref:System.Runtime.Serialization.ISerializable> kontrakt.

- Nie używaj <xref:System.Xml.XmlElement> , tablic, <xref:System.Xml.XmlNode> <xref:System.Byte> tablic ani typów, które implementują <xref:System.Runtime.Serialization.ISerializable> na liście znanych typów.

Powyższe środki ostrożności stosuje się, gdy operacja niestrumieniowa używa <xref:System.Runtime.Serialization.DataContractSerializer> . Nie należy mieszać modeli programistycznych przesyłania strumieniowego i niestrumieniowego w tej samej usłudze, jeśli używasz programu <xref:System.Xml.Serialization.XmlSerializer> , ponieważ nie ma on ochrony <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> limitu przydziału.

### <a name="slow-stream-attacks"></a>Wolne ataki strumieniowe

Klasa ataków typu "odmowa usługi" przesyłania strumieniowego nie obejmuje zużycia pamięci. Zamiast tego atak polega na powolnym nadawcy lub odbiorniku danych. Podczas oczekiwania na wysłanie lub odebranie danych zostaną wyczerpane zasoby, takie jak wątki i dostępne połączenia. Taka sytuacja może wystąpić w wyniku złośliwego ataku lub z wiarygodnego nadawcy lub odbiornika w przypadku wolnego połączenia sieciowego.

Aby wyeliminować te ataki, Ustaw odpowiednio limity czasu transportu. Aby uzyskać więcej informacji, zobacz [transport Transports](transport-quotas.md). Na koniec nigdy nie używaj synchronicznych `Read` ani `Write` operacji podczas pracy z strumieniami w programie WCF.

## <a name="using-xml-safely"></a>Bezpieczne używanie kodu XML

> [!NOTE]
> Chociaż ta sekcja dotyczy języka XML, informacje dotyczą również dokumentów JavaScript Object Notation (JSON). Przydziały działają podobnie, przy użyciu [mapowania między JSON i XML](mapping-between-json-and-xml.md).

### <a name="secure-xml-readers"></a>Zabezpieczanie czytników XML

Sprawdzonych XML stanowi podstawę całego przetwarzania komunikatów w programie WCF. Gdy dane XML są akceptowane z niezaufanego źródła, istnieją różne możliwości ataków typu "odmowa usługi", które muszą zostać skorygowane. Funkcja WCF oferuje specjalne, bezpieczne czytelnicy XML. Te czytelnicy są tworzone automatycznie podczas korzystania z jednego z standardowych kodowań w WCF (text, binary lub MTOM).

Niektóre funkcje zabezpieczeń na tych czytnikach są zawsze aktywne. Na przykład czytelnicy nigdy nie przetwarzają definicji typu dokumentu (DTD), które są potencjalnym źródłem ataków typu "odmowa usługi" i nigdy nie powinny występować w prawdziwych komunikatach protokołu SOAP. Inne funkcje zabezpieczeń obejmują przydziały czytnika, które należy skonfigurować, które zostały opisane w poniższej sekcji.

Podczas pracy bezpośrednio z czytnikami XML (na przykład podczas pisania własnego kodera niestandardowego lub podczas pracy bezpośrednio z <xref:System.ServiceModel.Channels.Message> klasą), zawsze używaj zabezpieczonych czytników WCF, gdy istnieje prawdopodobieństwo pracy z niezaufanymi danymi. Utwórz zabezpieczonych czytników, wywołując jedną z przeciążeń metody fabryki statycznej <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> , <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> <xref:System.Xml.XmlDictionaryReader> klasy. Podczas tworzenia czytnika należy przekazać bezpieczne wartości przydziału. Nie wywołuj `Create` przeciążeń metody. Nie tworzą one czytnika WCF. Zamiast tego tworzony jest czytnik, który nie jest chroniony przez funkcje zabezpieczeń opisane w tej sekcji.

### <a name="reader-quotas"></a>Przydziały czytnika

Bezpieczne czytelnicy XML mają pięć konfigurowalnych limitów przydziału. Są one zwykle konfigurowane przy użyciu `ReaderQuotas` właściwości elementów powiązania kodowania lub standardowych powiązań lub przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas> obiektu przesłanego podczas tworzenia czytnika.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Ten limit przydziału ogranicza liczbę bajtów odczytywanych w ramach jednej `Read` operacji podczas odczytywania znacznika początkowego elementu i jego atrybutów. (W przypadku niestrumieniowych przypadków sama sama nazwa elementu nie jest naliczana względem limitu przydziału). <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>jest ważne z następujących powodów:

- Nazwa elementu i jego atrybuty są zawsze buforowane w pamięci, gdy są odczytywane. W związku z tym ważne jest, aby poprawnie ustawić ten limit przydziału w trybie przesyłania strumieniowego, aby zapobiec nadmiernemu buforowaniu, gdy jest oczekiwany strumień strumieniowy. Zapoznaj się z `MaxDepth` sekcją limit przydziału, aby uzyskać informacje na temat rzeczywistej ilości buforowania.

- Zbyt wiele atrybutów XML może korzystać z nieproporcjonalnego czasu przetwarzania, ponieważ nazwy atrybutów muszą być sprawdzane pod kątem unikatowości. `MaxBytesPerRead`ograniczenie tego zagrożenia.

#### <a name="maxdepth"></a>MaxDepth

Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML. Na przykład dokument " \<A> \<B> \<C/> \</B> \</A> " ma głębokość zagnieżdżenia trzech. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>jest ważne z następujących powodów:

- `MaxDepth`Interakcja z `MaxBytesPerRead` : czytnik zawsze przechowuje dane w pamięci dla bieżącego elementu i wszystkich jego elementów nadrzędnych, więc maksymalne użycie pamięci przez czytnik jest proporcjonalne do iloczynu tych dwóch ustawień.

- Podczas deserializacji wykresu obiektów głęboko zagnieżdżonych, Deserializator jest zmuszony do uzyskania dostępu do całego stosu i wyrzuca nieodwracalne działania <xref:System.StackOverflowException> . Istnieje bezpośrednia korelacja między zagnieżdżeniem XML a zagnieżdżeniem obiektów dla <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> . Służy `MaxDepth` do ograniczania tego zagrożenia.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Ten limit przydziału ogranicza rozmiar *NameTable*czytnika. NameTable zawiera pewne ciągi (takie jak przestrzenie nazw i prefiksy), które są napotkane podczas przetwarzania dokumentu XML. Ponieważ te ciągi są buforowane w pamięci, należy ustawić ten limit przydziału, aby zapobiec nadmiernemu buforowaniu, gdy jest oczekiwany strumień.

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Ten limit przydziału ogranicza maksymalny rozmiar ciągu zwracanego przez czytnik XML. Ten limit przydziału nie ogranicza zużycia pamięci w samym czytniku XML, ale w składniku, który korzysta z czytnika. Na przykład gdy program <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczonego przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> , nie wykonuje deserializacji ciągów większych niż ten przydział. Korzystając z <xref:System.Xml.XmlDictionaryReader> klasy bezpośrednio, nie wszystkie metody respektują ten przydział, ale tylko metody, które są przeznaczone specjalnie do odczytu ciągów, takich jak <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> Metoda. <xref:System.Xml.XmlReader.Value%2A>Ten limit przydziału nie ma wpływ na Właściwość czytnika, dlatego nie należy jej używać, gdy wymagana jest Ochrona tego przydziału.

#### <a name="maxarraylength"></a>MaxArrayLength

Ten limit przydziału ogranicza maksymalny rozmiar tablicy elementów podstawowych, które zwraca czytnik XML, w tym tablic bajtowych. Ten limit przydziału nie ogranicza zużycia pamięci w samym czytniku XML, ale w dowolnym składniku, który korzysta z czytnika. Na przykład gdy program <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczonego przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> , nie deserializacji tablic bajtowych większych niż ten przydział. Ważne jest, aby ustawić ten przydział przy próbie miksowania strumieniowych i buforowanych modeli programowania w ramach jednego kontraktu. Należy pamiętać, że w przypadku używania <xref:System.Xml.XmlDictionaryReader> klasy bezpośrednio, tylko metody, które są specjalnie przeznaczone do odczytywania tablic o dowolnym rozmiarze niektórych typów pierwotnych, na przykład <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A> , przestrzeganie tego limitu przydziału.

## <a name="threats-specific-to-the-binary-encoding"></a>Zagrożenia specyficzne dla kodowania binarnego

Binarne kodowanie XML obsługiwane przez WCF zawiera funkcję *ciągów słownika* . Duży ciąg może być zakodowany przy użyciu tylko kilku bajtów. Zapewnia to znaczący wzrost wydajności, ale wprowadza nowe zagrożenia typu "odmowa usługi", które należy wyeliminować.

Istnieją dwa rodzaje słowników: *static* i *Dynamic*. Statyczny słownik jest wbudowaną listą długich ciągów, które mogą być reprezentowane przy użyciu krótkiego kodu w kodowaniu binarnym. Ta lista ciągów jest ustalana podczas tworzenia czytnika i nie można jej modyfikować. Żaden z ciągów w słowniku statycznym, który domyślnie nie używa WCF, jest wystarczająco duży, aby postanowić poważne zagrożenie odmowy usługi, chociaż mogą one być nadal używane w ataku do rozbudowy słownika. W zaawansowanych scenariuszach, w których dostarczasz własny słownik statyczny, należy zachować ostrożność podczas wprowadzania dużych ciągów słownika.

Funkcja słowniki dynamiczne umożliwia aplikacjom Definiowanie własnych ciągów i kojarzenie ich z krótkimi kodami. Te mapowania ciągów do kodu są przechowywane w pamięci podczas całej sesji komunikacji, w taki sposób, że kolejne komunikaty nie muszą ponownie wysyłać ciągów i mogą korzystać z kodów, które są już zdefiniowane. Te ciągi mogą mieć dowolną długość i w ten sposób stanowić bardziej poważne zagrożenie niż te w słowniku statycznym.

Pierwszym zagrożeniem, które musi zostać skorygowane, jest możliwość, że słownik dynamiczny (Tabela mapowania ciągu do kodu) staje się zbyt duży. Ten słownik może być rozwinięty w ciągu kilku komunikatów i dlatego `MaxReceivedMessageSize` limit przydziału nie zapewnia ochrony, ponieważ ma zastosowanie tylko do poszczególnych komunikatów. W związku z tym istnieje oddzielna <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> Właściwość, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> która ogranicza rozmiar słownika.

W przeciwieństwie do większości innych przydziałów, ten limit przydziału stosuje się również podczas pisania komunikatów. Jeśli zostanie przekroczony podczas odczytywania komunikatu, `QuotaExceededException` jest on generowany w zwykły sposób. Jeśli zostanie przekroczony podczas zapisywania komunikatu, wszelkie ciągi, które powodują przekroczenie limitu przydziału, są zapisywane w postaci, w jakiej są, bez używania funkcji słowniki dynamiczne.

### <a name="dictionary-expansion-threats"></a>Zagrożenia rozszerzenia słownika

Znaczna Klasa ataków specyficznych dla plików binarnych wynika z rozszerzenia słownika. Niewielki komunikat w postaci binarnej może przełączać się do bardzo dużego komunikatu w w pełni rozwiniętej postaci tekstowej, jeśli jest to szerokie użycie funkcji słowników ciągów. Współczynnik rozwinięcia dla ciągów słownika dynamicznego jest ograniczony przez <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> limit przydziału, ponieważ żaden ciąg słownika dynamicznego nie przekracza maksymalnego rozmiaru całego słownika.

<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>Właściwości, `MaxStringContentLength` i `MaxArrayLength` ograniczają tylko użycie pamięci. Zwykle nie są one wymagane do ograniczania zagrożeń w przypadku użycia niestrumieniowego, ponieważ użycie pamięci jest już ograniczone przez program `MaxReceivedMessageSize` . Zlicza natomiast `MaxReceivedMessageSize` bajty sprzed rozbudowy. Gdy kodowanie binarne jest w użyciu, użycie pamięci może potencjalnie przekroczyć `MaxReceivedMessageSize` , ograniczenie tylko przez współczynnik <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> . Z tego powodu ważne jest, aby zawsze ustawiać wszystkie przydziały czytnika (zwłaszcza w <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> przypadku używania kodowania binarnego).

W przypadku używania kodowania binarnego razem z <xref:System.Runtime.Serialization.DataContractSerializer> , `IExtensibleDataObject` interfejs może być nieużywany do instalowania ataku do rozszerzenia słownika. Ten interfejs zasadniczo zapewnia nieograniczony magazyn dla dowolnych danych, które nie są częścią kontraktu. Jeśli nie można ustawić przydziałów z niską ilością, która została `MaxSessionSize` pomnożona przez nie powoduje `MaxReceivedMessageSize` problemu, należy wyłączyć tę `IExtensibleDataObject` funkcję w przypadku używania kodowania binarnego. Ustaw `IgnoreExtensionDataObject` Właściwość na wartość `true` `ServiceBehaviorAttribute` atrybutu. Alternatywnie nie należy implementować `IExtensibleDataObject` interfejsu. Aby uzyskać więcej informacji, zobacz [Kontrakty danych zgodne z przekazywaniem dalej](forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Podsumowanie przydziałów

Poniższa tabela zawiera podsumowanie wskazówek dotyczących przydziałów.

|Warunek|Ważne przydziały do ustawienia|
|---------------|-----------------------------|
|Brak przesyłania strumieniowego lub przesyłania strumieniowego małych komunikatów, tekstu lub kodowania MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead` i`MaxDepth`|
|Brak przesyłania strumieniowego i przesyłania strumieniowego małych komunikatów, kodowanie binarne|`MaxReceivedMessageSize`, `MaxSessionSize` i wszystkie`ReaderQuotas`|
|Przesyłanie strumieniowe dużych komunikatów, tekstu lub kodowania MTOM|`MaxBufferSize`i wszystkie`ReaderQuotas`|
|Przesyłanie strumieniowe dużych komunikatów, kodowanie binarne|`MaxBufferSize`, `MaxSessionSize` i wszystkie`ReaderQuotas`|

- Limity czasu na poziomie transportu muszą zawsze być ustawione i nigdy nie używać synchronicznych operacji odczytu/zapisu, gdy przesyłanie strumieniowe jest w użyciu, niezależnie od tego, czy przesyłasz strumieniowo duże lub małe wiadomości.

- W razie wątpliwości dotyczących limitu przydziału Ustaw dla niego wartość bezpieczną, zamiast pozostawić ją otwartą.

## <a name="preventing-malicious-code-execution"></a>Zapobieganie wykonywaniu złośliwego kodu

Następujące ogólne klasy zagrożeń mogą wykonywać kod i mieć niezamierzone efekty:

- Deserializator ładuje złośliwy, niebezpieczny lub wrażliwy na zabezpieczenia typ.

- Komunikat przychodzący powoduje, że Deserializator Konstruuje wystąpienie zwykle bezpiecznego typu w taki sposób, że ma niezamierzone konsekwencje.

W poniższych sekcjach szczegółowo omówiono te klasy zagrożeń.

## <a name="datacontractserializer"></a>DataContractSerializer

(Aby uzyskać informacje o zabezpieczeniach w programie <xref:System.Xml.Serialization.XmlSerializer> , zobacz odpowiednią dokumentację). Model zabezpieczeń dla programu <xref:System.Xml.Serialization.XmlSerializer> jest podobny do tego dla programu <xref:System.Runtime.Serialization.DataContractSerializer> i różni się głównie szczegółowo. Na przykład <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybut jest używany do dołączania typu zamiast <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu. Jednak niektóre zagrożenia specyficzne dla programu <xref:System.Xml.Serialization.XmlSerializer> zostały omówione w dalszej części tego tematu.

### <a name="preventing-unintended-types-from-being-loaded"></a>Uniemożliwianie ładowania nieplanowanych typów

Ładowanie niezamierzonych typów może mieć znaczące konsekwencje, bez względu na to, czy typ jest złośliwy, czy tylko ma efekty uboczne z uwzględnieniem zabezpieczeń. Typ może zawierać luki w zabezpieczeniach, które mogą być używane w konstruktorze lub konstruktorze klasy, mają duże rozmiary pamięci, które ułatwiają ataki typu "odmowa usługi" lub mogą generować nieodzyskiwalne wyjątki. Typy mogą mieć konstruktory klas, które są uruchamiane natychmiast po załadowaniu typu i przed utworzeniem jakichkolwiek wystąpień. Z tego powodu ważne jest, aby kontrolować zestaw typów, które może ładować Deserializator.

<xref:System.Runtime.Serialization.DataContractSerializer>Deserializacji w luźno połączony sposób. Nigdy nie odczytuje typu środowiska uruchomieniowego języka wspólnego (CLR) ani nazw zestawów z danych przychodzących. Jest to podobne do zachowania <xref:System.Xml.Serialization.XmlSerializer> , ale różni się od zachowania <xref:System.Runtime.Serialization.NetDataContractSerializer> , <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Luźny sprzężenie wprowadza stopień bezpieczeństwa, ponieważ zdalna osoba atakująca nie może wskazywać dowolnego typu do załadowania tylko przez nadanie tego typu w wiadomości.

<xref:System.Runtime.Serialization.DataContractSerializer>Zawsze można załadować typ, który jest aktualnie oczekiwany zgodnie z umową. Na przykład jeśli kontrakt danych ma składową danych typu `Customer` , <xref:System.Runtime.Serialization.DataContractSerializer> można załadować `Customer` Typ podczas deserializacji tego elementu członkowskiego danych.

Ponadto <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje polimorfizm. Element członkowski danych może być zadeklarowany jako <xref:System.Object> , ale dane przychodzące mogą zawierać `Customer` wystąpienie. Jest to możliwe tylko wtedy, gdy `Customer` Typ został "znany" do deserializacji za pomocą jednego z następujących mechanizmów:

- <xref:System.Runtime.Serialization.KnownTypeAttribute>atrybut zastosowany do typu.

- `KnownTypeAttribute`atrybut określający metodę, która zwraca listę typów.

- `ServiceKnownTypeAttribute`przypisane.

- `KnownTypes`Sekcja konfiguracji.

- Lista znanych typów jawnie przenoszona do <xref:System.Runtime.Serialization.DataContractSerializer> podczas konstruowania, jeśli używasz serializatora bezpośrednio.

Każdy z tych mechanizmów zwiększa powierzchnię obszaru, wprowadzając więcej typów, które Deserializator może załadować. Kontroluj każdy z tych mechanizmów, aby upewnić się, że żadne złośliwe lub niezamierzone typy nie są dodawane do listy znanych typów.

Gdy znany typ znajduje się w zakresie, można go załadować w dowolnym momencie, a wystąpienia typu można utworzyć, nawet jeśli kontrakt zakazuje rzeczywiste użycie. Na przykład załóżmy, że typ "unniebezpiecznychtype" zostanie dodany do listy znanych typów przy użyciu jednego z powyższych mechanizmów. Oznacza to, że:

- `MyDangerousType`jest ładowany, a jego Konstruktor klas działa.

- Nawet w przypadku deserializacji kontraktu danych za pomocą elementu członkowskiego danych w postaci ciągu złośliwy komunikat może nadal spowodować wystąpienie `MyDangerousType` do utworzenia. Kod w `MyDangerousType` , taki jak metody ustawiające właściwości, może być uruchamiany. Po wykonaniu tej czynności Deserializator próbuje przypisać to wystąpienie do elementu członkowskiego danych String i niepowodzeniem z wyjątkiem.

Podczas pisania metody zwracającej listę znanych typów lub przekazywania listy bezpośrednio do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora upewnij się, że kod, który przygotowuje listę, jest bezpieczny i działa tylko na zaufanych danych.

Jeśli określono znane typy w konfiguracji, upewnij się, że plik konfiguracji jest bezpieczny. Zawsze Używaj silnych nazw w konfiguracji (poprzez określenie klucza publicznego podpisanego zestawu, w którym znajduje się typ), ale nie określaj wersji typu do załadowania. Moduł ładujący typ automatycznie wybiera najnowszą wersję, jeśli jest to możliwe. W przypadku określenia konkretnej wersji w konfiguracji, należy uruchomić następujące zagrożenie: typ może mieć lukę w zabezpieczeniach, która może zostać rozwiązana w przyszłej wersji, ale nadal jest ona załadowana, ponieważ jest ona jawnie określona w konfiguracji.

Zbyt wiele znanych typów ma inną sekwencję: <xref:System.Runtime.Serialization.DataContractSerializer> tworzy pamięć podręczną kodu serializacji/deserializacji w domenie aplikacji, z wpisem dla każdego typu, który musi serializować i zdeserializować. Ta pamięć podręczna nigdy nie jest czyszczona, o ile domena aplikacji jest uruchomiona. W związku z tym osoba atakująca, która wie, że aplikacja używa wielu znanych typów, może spowodować deserializacja wszystkich tych typów, powodując, że pamięć podręczna zużywa nieproporcjonalnie dużą ilość pamięci.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Zapobieganie, że typy nie są w stanie niezamierzonym

Typ może mieć wewnętrzne ograniczenia spójności, które muszą zostać wymuszone. Należy zachować ostrożność, aby uniknąć przerywania tych ograniczeń podczas deserializacji.

Poniższy przykład typu reprezentuje stan blokady na statku kosmicznym i wymusza ograniczenie, że zarówno drzwi wewnętrzne, jak i zewnętrzne nie mogą być otwarte w tym samym czasie.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Osoba atakująca może wysłać złośliwy komunikat w taki sposób, aby obejść ograniczenia i pobrać obiekt w nieprawidłowym stanie, który może mieć niezamierzone i nieprzewidywalne konsekwencje.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Tę sytuację można uniknąć, wiedząc o następujących kwestiach:

- Gdy <xref:System.Runtime.Serialization.DataContractSerializer> deserializacji większość klas, konstruktory nie są uruchamiane. W związku z tym nie należy polegać na zarządzaniu stanami w konstruktorze.

- Użyj wywołania zwrotnego, aby upewnić się, że obiekt jest w prawidłowym stanie. Wywołanie zwrotne oznaczone <xref:System.Runtime.Serialization.OnDeserializedAttribute> atrybutem jest szczególnie przydatne, ponieważ jest uruchamiane po ukończeniu deserializacji i ma szansę na sprawdzenie i poprawienie ogólnego stanu. Aby uzyskać więcej informacji, zobacz [wywołania zwrotne serializacji odporne na wersje](version-tolerant-serialization-callbacks.md).

- Nie należy projektować typów kontraktu danych, aby polegać na każdej określonej kolejności, w której należy wywołać metody ustawiające właściwości.

- Należy zachować ostrożność przy użyciu starszych typów oznaczonych <xref:System.SerializableAttribute> atrybutem. Wiele z nich zostało zaprojektowanych do pracy z .NET Framework usługami zdalnymi do użytku tylko z zaufanymi danymi. Istniejące typy oznaczone za pomocą tego atrybutu mogą nie zostać zaprojektowane z myślą o bezpieczeństwie stanu.

- Nie należy polegać na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwościach <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu w celu zagwarantowania obecności danych, o ile dotyczy to bezpieczeństwa stanu. Dane mogą mieć zawsze `null` , `zero` lub `invalid` .

- Nie należy nigdy ufać grafowi obiektu odszeregowanym od niezaufanego źródła danych bez weryfikowania go jako pierwszego. Każdy pojedynczy obiekt może być w spójnym stanie, ale wykres obiektów jako całość może nie być. Ponadto nawet jeśli tryb zachowywania grafu obiektów jest wyłączony, deserializowany Wykres może mieć wiele odwołań do tego samego obiektu lub mieć odwołania cykliczne. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>Bezpieczne używanie NetDataContractSerializer

<xref:System.Runtime.Serialization.NetDataContractSerializer>Jest to aparat serializacji, który używa ścisłego sprzężenia do typów. Jest to podobne do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Oznacza to, że określa typ do wystąpienia, odczytując zestaw .NET Framework i nazwę typu z danych przychodzących. Chociaż jest częścią usługi WCF, nie ma żadnego podanego sposobu podłączania w tym aparacie serializacji; należy napisać kod niestandardowy. Usługa `NetDataContractSerializer` jest świadczona głównie w celu ułatwienia migracji .NET Framework komunikacji zdalnej do usługi WCF. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [serializacji i deserializacji](serialization-and-deserialization.md).

Ponieważ sam komunikat może wskazywać, że każdy typ może być ładowany, <xref:System.Runtime.Serialization.NetDataContractSerializer> mechanizm jest z natury niezabezpieczony i powinien być używany tylko z zaufanymi danymi. Istnieje możliwość zapewnienia bezpieczeństwa przez zapisanie bezpiecznego, nieograniczonego typu, który umożliwia ładowanie tylko bezpiecznych typów (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> Właściwości).

Nawet w przypadku użycia z zaufanymi danymi dane przychodzące mogą niewystarczająco określić typ do załadowania, zwłaszcza jeśli <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> Właściwość jest ustawiona na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> . Każda osoba mająca dostęp do katalogu aplikacji lub globalnej pamięci podręcznej zestawów może zastąpić złośliwy typ zamiast tego, który powinien zostać załadowany. Zawsze upewnij się, że zabezpieczenia katalogu aplikacji i globalnej pamięci podręcznej zestawów zostały prawidłowo ustawione.

Ogólnie rzecz biorąc, Jeśli zezwolisz na dostęp częściowo zaufanego kodu do Twojego `NetDataContractSerializer` wystąpienia lub w inny sposób kontroluje selektor zastępczy ( <xref:System.Runtime.Serialization.ISurrogateSelector> ) lub spinacz serializacji ( <xref:System.Runtime.Serialization.SerializationBinder> ), kod może nawiązać dużą kontrolę nad procesem serializacji/deserializacji. Na przykład może wstrzyknąć dowolnego typu, prowadzić do ujawnienia informacji, naruszać wynikowy wykres obiektu lub dane serializowane lub przepełnić wynikowy strumień serializowany.

Innym problemem z bezpieczeństwem `NetDataContractSerializer` jest odmowa usługi, a nie złośliwe zagrożenie wykonania kodu. W przypadku korzystania z programu `NetDataContractSerializer` należy zawsze ustawić <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> bezpieczną wartość przydziału. Można łatwo utworzyć małą złośliwą wiadomość, która alokuje tablicę obiektów, których rozmiar jest ograniczony tylko do tego przydziału.

### <a name="xmlserializer-specific-threats"></a>XmlSerializer — zagrożenia specyficzne dla określonych

<xref:System.Xml.Serialization.XmlSerializer>Model zabezpieczeń jest podobny do tego <xref:System.Runtime.Serialization.DataContractSerializer> . Niektóre zagrożenia są jednak unikatowe dla programu <xref:System.Xml.Serialization.XmlSerializer> .

<xref:System.Xml.Serialization.XmlSerializer>Generuje *zestawy serializacji* w czasie wykonywania, które zawierają kod, który faktycznie serializować i deserializacji; te zestawy są tworzone w katalogu plików tymczasowych. Jeśli jakiś inny proces lub użytkownik ma prawa dostępu do tego katalogu, mogą zastąpić kod serializacji/deserializacji z dowolnym kodem. <xref:System.Xml.Serialization.XmlSerializer>Następnie uruchamia ten kod przy użyciu jego kontekstu zabezpieczeń, zamiast kodu serializacji/deserializacji. Upewnij się, że uprawnienia są poprawnie ustawione w katalogu plików tymczasowych, aby zapobiec temu.

<xref:System.Xml.Serialization.XmlSerializer>Ma również tryb, w którym używa wstępnie wygenerowanych zestawów serializacji zamiast generować je w czasie wykonywania. Ten tryb jest wyzwalany za każdym razem, gdy <xref:System.Xml.Serialization.XmlSerializer> może znaleźć odpowiedni zestaw serializacji. <xref:System.Xml.Serialization.XmlSerializer>Sprawdza, czy zestaw serializacji został podpisany przez ten sam klucz, który został użyty do podpisania zestawu, który zawiera typy, które są serializowane. Zapewnia to ochronę przed złośliwymi zestawami, które są ukrywane jako zestawy serializacji. Jeśli jednak zestaw, który zawiera typy, które można serializować, nie jest podpisany, <xref:System.Xml.Serialization.XmlSerializer> nie może wykonać tego sprawdzenia i używa dowolnego zestawu o poprawnej nazwie. Dzięki temu możliwe jest uruchomienie złośliwego kodu. Należy zawsze podpisywać zestawy, które zawierają typy możliwe do serializacji, lub ściśle kontrolować dostęp do katalogu aplikacji i globalnej pamięci podręcznej zestawów, aby zapobiec wprowadzaniu złośliwych zestawów.

<xref:System.Xml.Serialization.XmlSerializer>Może być przedmiotem ataku typu "odmowa usługi". Nie <xref:System.Xml.Serialization.XmlSerializer> ma `MaxItemsInObjectGraph` limitu przydziału (jest on dostępny w przypadku <xref:System.Runtime.Serialization.DataContractSerializer> ). W ten sposób deserializacji arbitralnej ilości obiektów, który jest ograniczony tylko do rozmiaru wiadomości.

### <a name="partial-trust-threats"></a>Częściowe zagrożenia zaufania

Należy zwrócić uwagę na następujące kwestie dotyczące zagrożeń związanych z kodem uruchomionym z częściowym zaufaniem. Te zagrożenia obejmują złośliwy, częściowo zaufany kod, a także złośliwy, częściowo zaufany kod w połączeniu z innymi scenariuszami ataków (na przykład częściowo zaufany kod, który konstruuje określony ciąg, a następnie deserializacji go).

- W przypadku korzystania z dowolnych składników serializacji nigdy nie podawaj żadnych uprawnień przed takim użyciem, nawet jeśli cały scenariusz serializacji znajduje się w zakresie potwierdzenia i nie ma żadnych niezaufanych danych lub obiektów. Takie użycie może prowadzić do luk w zabezpieczeniach.

- W przypadkach, gdy częściowo zaufany kod ma kontrolę nad procesem serializacji, za pośrednictwem punktów rozszerzalności (surogatów), typów, które są serializowane lub w inny sposób, kod częściowo zaufany może spowodować, że serializator wyprowadza dużą ilość danych do strumienia serializowanego, co może spowodować odmowę usługi (DoS) do odbiorcy tego strumienia. W przypadku serializowania danych przeznaczonych dla obiektu docelowego, które są poufne dla zagrożeń systemu DoS, nie należy serializować częściowo zaufanych typów lub w inny sposób umożliwić serializacji z częściowo zaufanymi formantami kodu.

- Jeśli zezwolisz na dostęp do wystąpienia częściowo zaufanego kodu <xref:System.Runtime.Serialization.DataContractSerializer> lub w inny sposób kontrolujesz [surogaty kontraktu danych](../extending/data-contract-surrogates.md), może być możliwe uzyskanie doskonałej kontroli nad procesem serializacji/deserializacji. Na przykład może wstrzyknąć dowolnego typu, prowadzić do ujawnienia informacji, naruszać wynikowy wykres obiektu lub dane serializowane lub przepełnić wynikowy strumień serializowany. Równoważne <xref:System.Runtime.Serialization.NetDataContractSerializer> zagrożenie zostało opisane w sekcji "Korzystanie z bezpiecznego NetDataContractSerializer".

- Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do typu (lub typu oznaczonego jako <xref:System.SerializableAttribute> , ale nie <xref:System.Runtime.Serialization.ISerializable> ), Deserializator może utworzyć wystąpienie takiego typu, nawet jeśli wszystkie konstruktory są niepubliczne lub chronione przez żądania.

- Nigdy nie ufaj wynikowi deserializacji, chyba że dane, które mają zostać deserializowane, są zaufane, a ty masz pewność, że wszystkie znane typy są zaufaniem. Należy pamiętać, że znane typy nie są ładowane z pliku konfiguracji aplikacji (ale są ładowane z pliku konfiguracji komputera) podczas uruchamiania w częściowej relacji zaufania.

- W przypadku przekazania <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia z surogatem dodanym do częściowo zaufanego kodu, kod może zmienić wszystkie modyfikowalne ustawienia dla tego surogatu.

- W przypadku obiektu deserializowanego, jeśli czytnik XML (lub dane w tym miejscu) pochodzi z częściowo zaufanego kodu, należy traktować ten obiekt jako niezaufany.

- Fakt, że <xref:System.Runtime.Serialization.ExtensionDataObject> Typ nie ma publicznych składowych, nie oznacza, że dane w niej są bezpieczne. Na przykład w przypadku deserializacji z uprzywilejowanego źródła danych do obiektu, w którym znajdują się pewne dane, następnie należy odczytywać ten obiekt do częściowo zaufanego kodu, częściowo zaufany kod może odczytać dane `ExtensionDataObject` przez Serializowanie obiektu. Rozważ ustawienie <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> do `true` momentu deserializacji z uprzywilejowanego źródła danych do obiektu, który jest później przekazywać do kodu częściowo zaufanego.

- <xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługują serializację prywatnych, chronionych, wewnętrznych i publicznych składowych w trybie pełnego zaufania. Jednak w częściowej relacji zaufania tylko publiczne składowe mogą być serializowane. <xref:System.Security.SecurityException>Występuje, gdy aplikacja próbuje serializować niepublicznego elementu członkowskiego.

    Aby zezwolić na Serializowanie wewnętrznych lub chronionych wewnętrznych elementów członkowskich w częściowej relacji zaufania, użyj <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu Assembly. Ten atrybut umożliwia zestawowi zadeklarować, że jego wewnętrzne elementy członkowskie są widoczne dla innego zestawu. W tym przypadku zestaw, który chce mieć zaszeregowaną wewnętrzną składową, deklaruje, że jego wewnętrzne elementy członkowskie są widoczne dla System. Runtime. Serialization. dll.

    Zaletą tego podejścia jest to, że nie wymaga ścieżki generowania kodu z podwyższonym poziomem uprawnień.

    W tym samym czasie istnieją dwie istotne wady.

    Pierwsza wada polega na tym, że właściwość opt <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu jest dla całego zestawu. Oznacza to, że nie można określić, że tylko niektóre klasy mogą mieć serializowane wewnętrzne składowe. Oczywiście nadal możesz zrezygnować z serializacji określonego wewnętrznego elementu członkowskiego, nie dodając <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do tego elementu członkowskiego. Podobnie deweloper może również wybrać, aby element członkowski był wewnętrzny, a nie prywatny lub chroniony, z niewielkimi problemami z widocznością.

    Druga wada polega na tym, że nadal nie obsługuje prywatnych ani chronionych elementów członkowskich.

    Aby zilustrować użycie <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu w częściowej relacji zaufania, należy wziąć pod uwagę następujący program:

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    W powyższym przykładzie `PermissionsHelper.InternetZone` odpowiada <xref:System.Security.PermissionSet> za częściowe zaufanie. Teraz, bez <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aplikacja zakończy się niepowodzeniem, <xref:System.Security.SecurityException> zwracając wskazującą, że niepubliczne składowe nie mogą być serializowane w częściowej relacji zaufania.

    Jeśli jednak dodamy następujący wiersz do pliku źródłowego, program zostanie uruchomiony pomyślnie.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Inne problemy związane z zarządzaniem stanem

Należy zauważyć kilka innych problemów dotyczących zarządzania stanem obiektów:

- W przypadku korzystania z modelu programowania opartego na strumieniach z transportem przesyłania strumieniowego, przetwarzanie komunikatu odbywa się po nadejściu wiadomości. Nadawca wiadomości może przerwać operację wysyłania w środku strumienia, pozostawiając kod w stanie nieprzewidywalnym, jeśli Oczekiwano większej ilości zawartości. Ogólnie rzecz biorąc nie należy polegać na zakończeniu przesyłania strumieniowego ani wykonywać żadnych zadań w operacji opartych na strumieniach, których nie można przywrócić w przypadku przerwania strumienia. Dotyczy to również sytuacji, w której komunikat może być nieprawidłowo sformułowany po treści przesyłania strumieniowego (na przykład może brakować tagu końcowego dla koperty protokołu SOAP lub mieć drugą treść wiadomości).

- Korzystanie z `IExtensibleDataObject` funkcji może spowodować emisję poufnych danych. W przypadku przyjmowania danych z niezaufanego źródła do kontraktów danych z `IExtensibleObjectData` i późniejszymi ponownymi emisjami w bezpiecznym kanale, w którym są podpisane komunikaty, możesz zagwarantowanie, że dane nie są już potrzebne. Ponadto cały wysyłany stan może być nieprawidłowy, jeśli masz znane i nieznane fragmenty danych. Unikaj tej sytuacji przez selektywne ustawienie właściwości dane rozszerzenia na `null` lub przez selektywne wyłączenie `IExtensibleObjectData` funkcji.

## <a name="schema-import"></a>Importowanie schematu

Zwykle proces importowania schematu do generowania typów odbywa się tylko w czasie projektowania, na przykład w przypadku korzystania z narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) w usłudze sieci Web w celu wygenerowania klasy klienta. Jednak w bardziej zaawansowanych scenariuszach możesz przetwarzać schemat w czasie wykonywania. Należy pamiętać, że takie działanie może ujawnić ryzyko wystąpienia zagrożeń typu "odmowa usługi". Importowanie niektórych schematów może zająć dużo czasu. Nie należy używać <xref:System.Xml.Serialization.XmlSerializer> składnika importowania schematu w takich scenariuszach, jeśli schematy są prawdopodobnie pochodzące z niezaufanego źródła.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>Zagrożenia związane z integracją ASP.NET AJAX

Gdy użytkownik implementuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> lub <xref:System.ServiceModel.Description.WebHttpBehavior> , program WCF uwidacznia punkt końcowy, który może akceptować zarówno wiadomości XML, jak i JSON. Istnieje jednak tylko jeden zestaw przydziałów czytnika, używany zarówno przez czytnik XML, jak i czytnik JSON. Niektóre ustawienia przydziału mogą być odpowiednie dla jednego czytnika, ale zbyt duże.

Podczas wdrażania `WebScriptEnablingBehavior` użytkownik ma możliwość uwidocznienia serwera proxy JavaScript w punkcie końcowym. Należy wziąć pod uwagę następujące zagadnienia dotyczące zabezpieczeń:

- Informacje o usłudze (nazwy operacji, nazwach parametrów itd.) można uzyskać, badając serwer proxy JavaScript.

- W przypadku korzystania z punktu końcowego języka JavaScript informacje poufne i prywatne mogą być przechowywane w pamięci podręcznej przeglądarki sieci Web klienta.

## <a name="a-note-on-components"></a>Uwaga dotycząca składników

WCF to elastyczny i dostosowywalny system. Większość zawartości tego tematu koncentruje się na typowych scenariuszach użycia programu WCF. Można jednak tworzyć składniki WCF na wiele różnych sposobów. Ważne jest, aby zrozumieć implikacje zabezpieczeń związane z używaniem każdego składnika. W szczególności:

- Jeśli musisz użyć czytników XML, użyj czytników, a w <xref:System.Xml.XmlDictionaryReader> przeciwieństwie do innych czytelników. Bezpieczne czytelnicy są tworzone przy <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> użyciu <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> metod, lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> . Nie należy używać <xref:System.Xml.XmlReader.Create%2A> metody. Zawsze należy konfigurować czytniki z bezpiecznymi limitami. Aparaty serializacji w programie WCF są bezpieczne tylko wtedy, gdy są używane z bezpiecznymi czytnikami XML z programu WCF.

- W przypadku korzystania z programu <xref:System.Runtime.Serialization.DataContractSerializer> do deserializacji potencjalnie niezaufanych danych zawsze ustawiaj <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> Właściwość.

- Podczas tworzenia komunikatu ustaw `maxSizeOfHeaders` parametr, jeśli nie `MaxReceivedMessageSize` oferuje wystarczającej ochrony.

- Podczas tworzenia kodera należy zawsze konfigurować odpowiednie przydziały, takie jak `MaxSessionSize` i `MaxBufferSize` .

- W przypadku korzystania z filtru komunikatów XPath ustaw, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> Aby ograniczyć liczbę węzłów XML, które są filtrowane. Nie należy używać wyrażeń XPath, które mogą potrwać dłuższy czas do obliczenia bez odwiedzania wielu węzłów.

- Ogólnie rzecz biorąc, w przypadku użycia dowolnego składnika, który akceptuje limit przydziału, należy zapoznać się z jego wpływem na zabezpieczenia i ustawić bezpieczną wartość.

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Znane typy kontraktów danych](data-contract-known-types.md)

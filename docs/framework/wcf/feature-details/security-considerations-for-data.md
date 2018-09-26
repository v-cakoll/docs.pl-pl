---
title: Zagadnienia związane z zabezpieczeniami danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
author: BrucePerlerMS
ms.openlocfilehash: bf3276353473f07f58740a5819226994123efdcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47201156"
---
# <a name="security-considerations-for-data"></a>Zagadnienia związane z zabezpieczeniami danych
Podczas pracy z danymi w Windows Communication Foundation (WCF), należy wziąć pod uwagę liczbę kategorie zagrożeń. W poniższej tabeli wymieniono najważniejsze klasy zagrożeń, które odnoszą się do przetwarzania danych. Usługi WCF udostępnia narzędzia, aby ograniczyć te zagrożenia.  
  
 Odmowa usługi  
 Podczas odbierania niezaufanych danych, danych może spowodować po stronie odbierającej dostępu nieproporcjonalnie różnych zasobów, takich jak pamięć, wątki, dostępnych połączeń lub cykli procesora, powodując długich obliczeń do. Atak typu "odmowa usługi" na serwerze może spowodować awarię i można będzie przetwarzać komunikaty z innych, uzasadnione klientów.  
  
 Wykonywanie złośliwego kodu  
 Przychodzące niezaufanych danych powoduje, że po stronie odbierającej tak uruchomić kod, który go nie zamierza.  
  
 Ujawnienie informacji  
 Zdalnej osobie atakującej wymusza otrzymującej do odpowiadania na żądania, jej w taki sposób, aby ujawnić więcej informacji, niż zamierza.  
  
## <a name="user-provided-code-and-code-access-security"></a>Dostarczony przez użytkownika kod i zabezpieczenia dostępu kodu  
 Liczba miejsc, w ramach infrastruktury usług Windows Communication Foundation (WCF), uruchomić kod, który jest udostępniany przez użytkownika. Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> mechanizm serializacji może wywołać dostarczone przez użytkownika właściwości `set` metody dostępu i `get` metod dostępu. Infrastruktura kanału WCF może również wywoływać dostarczone przez użytkownika klas pochodnych <xref:System.ServiceModel.Channels.Message> klasy.  
  
 Jest odpowiedzialny za autora kodu, aby upewnić się, że istnieje nie luk w zabezpieczeniach. Na przykład, jeśli tworzysz kontraktu danych typu z właściwością elementu członkowskiego danych typu integer, a w polu `set` implementacji metody dostępu przydzielić tablicy, na podstawie wartości właściwości, należy udostępnić możliwości ataku typu "odmowa usługi", jeśli złośliwe komunikat zawiera bardzo dużą wartość dla tego elementu członkowskiego danych. Ogólnie rzecz biorąc Unikaj alokacje na podstawie danych przychodzących lub długie, przetwarzanie w kodzie użytkownika (zwłaszcza, jeśli długie przetwarzanie może być spowodowane małą ilością danych przychodzących). Podczas przeprowadzania analizy zabezpieczeń kodu podanego przez użytkownika, należy również wziąć pod uwagę wszystkie przypadki awarii (czyli wszystkich Programowanie gałęzi gdy wyjątki zostaną zgłoszone).  
  
 Ultimate przykładem kodu podanego przez użytkownika jest kod wewnątrz implementacji usługi dla każdej operacji. Zabezpieczenia implementacji usługi jest odpowiedzialny za. To ułatwia utworzenie przypadkowo implementacji niezabezpieczone operacji, które może spowodować luki w zabezpieczeniach typu "odmowa usługi". Na przykład operacja, która przyjmuje ciąg i zwraca listę wszystkich klientów z bazy danych, których nazwa rozpoczyna się od tego ciągu. Jeśli pracujesz z dużych baz danych i ciąg przekazywany jest pojedynczą literą, Twój kod może podejmować prób utworzenia komunikatu w większe niż dostępna pamięć, co powoduje awarię całej usługi. ( <xref:System.OutOfMemoryException> Nie jest możliwe do odzyskania w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] i zawsze powoduje zablokowanie dostępu do aplikacji.)  
  
 Należy upewnić się, że nie złośliwy kod jest podłączony do różnych punktów rozszerzeń. Jest to szczególnie istotne w przypadku, gdy uruchamianie w częściowej relacji zaufania, pracy z typami z częściowo zaufane zestawy lub tworząc składników można używać przez częściowo zaufany kod. Aby uzyskać więcej informacji zobacz "Częściowego zaufania zagrożenia" w dalszej części tego tematu.  
  
 Podczas uruchamiania w częściowej relacji zaufania, infrastruktura serializacji kontrakt danych obsługuje tylko ograniczony podzestaw kontraktu programowania modelu danych — na przykład, elementy członkowskie danych prywatnych lub typów przy użyciu <xref:System.SerializableAttribute> atrybutów nie są obsługiwane. Aby uzyskać więcej informacji, zobacz [częściowego zaufania](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Unikanie ujawnienie niezamierzonych informacji  
 Podczas projektowania typów możliwych do serializacji z myślą o bezpieczeństwie, ujawnienie informacji jest możliwe istotna.  
  
 Należy wziąć pod uwagę następujące kwestie:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Model programowania umożliwia narażenia prywatne i wewnętrzne dane poza usługą typu lub zestawu podczas serializacji. Ponadto kształt typu mogą być narażone podczas eksportowania schematu. Pamiętaj zrozumieć danego typu serializacji projekcji. Jeśli nie mają żadnych widoczne, należy wyłączyć, szeregując go (na przykład, stosując nie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów w przypadku kontraktu danych).  
  
-   Należy pamiętać, że ten sam typ może mieć wiele projekcji serializacji, w zależności od serializator używany. Ten sam typ może narazić jeden zestaw danych, gdy jest używane z <xref:System.Runtime.Serialization.DataContractSerializer> i inny zestaw danych, gdy jest używane z <xref:System.Xml.Serialization.XmlSerializer>. On przypadkowemu użyciu niewłaściwego serializator może prowadzić do ujawnienia informacji.  
  
-   Za pomocą <xref:System.Xml.Serialization.XmlSerializer> w starszej wersji procedury zdalnej wywołań (procedur RPC) / tryb zakodowany przypadkowo może narazić kształtu wykresu obiektu po stronie wysyłającej się po stronie odbierającej.  
  
## <a name="preventing-denial-of-service-attacks"></a>Zapobieganie atakom typu "odmowa usługi"  
  
### <a name="quotas"></a>Limity przydziału  
 Powoduje po stronie odbierającej można przydzielić znacznej ilości pamięci jest potencjalny atak typu "odmowa usługi". Gdy ta sekcja koncentruje się na problemy z użyciem pamięci wynikające z dużych komunikatów, mogą wystąpić inne ataki. Na przykład wiadomości mogą użyć nieproporcjonalnie duża ilość czasu przetwarzania.  
  
 Ataki typu "odmowa usługi" zazwyczaj zostały skorygowane przy użyciu przydziałów. Po przekroczeniu przydziału <xref:System.ServiceModel.QuotaExceededException> jest zazwyczaj zgłaszany wyjątek. Bez limitu przydziału, niebezpiecznej wiadomości może spowodować, że całą dostępną pamięć, można uzyskać dostęp, co <xref:System.OutOfMemoryException> wyjątku lub wszystkie stosy dostępne były dostępne, dając w efekcie w <xref:System.StackOverflowException>.  
  
 Scenariusz Przekroczono limit przydziału jest możliwe do odzyskania; Jeśli w działającej usłudze, aktualnie przetwarzanego komunikatu jest odrzucana i jest uruchomiony i przetwarza dalsze komunikaty. Scenariusze przepełnienie braku pamięci i stos, jednak nie są możliwe do odzyskania w dowolnym miejscu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; usługa kończy działanie, jeśli wykryje nieważną takie wyjątki.  
  
 Przydziały w programie WCF nie obejmują żadnych wstępnej alokacji. Na przykład jeśli <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> limitu przydziału (znajdujący się w różnych zajęciach) jest ustawiona na 128 KB, nie oznacza to, że 128 KB jest przydzielany automatycznie dla każdego komunikatu. Rzeczywista ilość przydzielonej zależy od rzeczywisty rozmiar wiadomości przychodzącej.  
  
 Wiele przydziały są dostępne w warstwie transportowej. Są to limity przydziału, wymuszane przez kanał transportu określonych w użyciu (HTTP, TCP i tak dalej). Chociaż w tym temacie omówiono niektóre z tych limitów przydziału, te przydziały są szczegółowo opisane w [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>Tablica skrótów luk w zabezpieczeniach  
 Usterka gdy kontraktów danych zawiera tabele lub kolekcji. Problem występuje w przypadku dużej liczby wartości są wstawiane do tablicy skrótów, których dużą liczbę tych wartości generują tę samą wartość skrótu. Może to służyć jako atak DOS.  Ustawiając limit przydziału powiązania MaxRecievedMessageSize można wyeliminować tę lukę w zabezpieczeniach. Należy zachować ostrożność podczas ustawiania ten limit przydziału, aby uniknąć takich ataków. Ten limit przydziału umieszcza górny limit rozmiaru wiadomości WCF. Ponadto należy unikać tabele lub kolekcji w kontraktach usługi danych.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Ograniczanie zużycia pamięci bez przesyłania strumieniowego  
 Model zabezpieczeń w całym dużych komunikatów zależy od tego, czy przesyłania strumieniowego jest używana. W przypadku podstawowych, strumieniowo komunikaty są buforowane do pamięci. W takim przypadku należy użyć <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> limit przydziału dla <xref:System.ServiceModel.Channels.TransportBindingElement> lub powiązania dostarczane przez system, aby zapewnić ochronę przed dużych komunikatów, ograniczając maksymalny rozmiar wiadomości w celu uzyskania dostępu. Należy pamiętać, że usługa może przetwarzanie wielu komunikatów w tym samym czasie, w tym przypadku są one wszystkie w pamięci. Funkcja ograniczania przepustowości celu uniknięcie tego zagrożenia.  
  
 Należy również zauważyć, że `MaxReceivedMessageSize` nie umieścić górną granicę na zmniejszenie zużycia pamięci określonych wiadomości, ale ogranicza ją do w obrębie współczynnika stałej. Na przykład jeśli `MaxReceivedMessageSize` wynosi 1 MB i 1 MB wiadomość zostaje odebrana, a następnie po deserializacji, dodatkowe pamięci jest muszą zawierać wykres obiektu po deserializacji, co spowoduje również zużycia całkowitej ilości pamięci ponad 1 MB. Z tego powodu należy unikać tworzenia typów możliwych do serializacji, które może spowodować zmniejszenie zużycia pamięci znaczących bez dużej ilości danych przychodzących. Na przykład kontraktu danych "MyContract" za pomocą pola członka 50 opcjonalnymi danymi i dodatkowe 100 pól prywatnych mogła zostać utworzona za pomocą konstrukcji XML "\<MyContract / >". Powoduje to XML w pamięci, do którego uzyskiwany jest dostęp dla pól 150. Należy pamiętać, że elementy członkowskie danych są opcjonalne, domyślnie. Problem jest rozliczana w przypadku takiego typu części tablicy.  
  
 `MaxReceivedMessageSize` samodzielnie jest niewystarczająca do wszystkich atakami typu "odmowa usługi". Na przykład Deserializator może być zmuszona do deserializacji wykresu obiektu głęboko zagnieżdżone (obiekt, który zawiera inny obiekt, który zawiera jeden kolejny i tak dalej), przez wiadomości przychodzącej. Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> wywoływać metody w sposób zagnieżdżony do deserializacji takich wykresów. Głębokie zagnieżdżanie wywołań metody może spowodować nieodwracalny <xref:System.StackOverflowException>. To zagrożenie jest zmniejszany przez ustawienie <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> limitu przydziału, aby ograniczyć poziom zagnieżdżenia XML, zgodnie z opisem w sekcji "Przy użyciu bezpiecznego XML" w dalszej części tematu.  
  
 Ustawienie dodatkowych przydziałach `MaxReceivedMessageSize` jest szczególnie ważne w przypadku korzystania z kodowania binarnego XML. Przy użyciu kodowania binarnego jest nieco odpowiednikiem kompresji: dla niewielkiej liczby bajtów w przychodzącej wiadomości może reprezentować dużej ilości danych. Dlatego nawet komunikat dopasowane do `MaxReceivedMessageSize` limit może potrwać znacznie większej ilości pamięci w postaci w pełni rozwinięte. Aby uniknąć takich XML specyficzne zagrożenia, wszystkie przydziały czytnika XML muszą być ustawione poprawnie, zgodnie z opisem w sekcji "Przy użyciu bezpiecznego XML" w dalszej części tego tematu.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Ograniczanie zużycia pamięci za pomocą przesyłania strumieniowego  
 Podczas przesyłania strumieniowego, mogą używać małych `MaxReceivedMessageSize` ustawienia ochrony przed atakami typu "odmowa usługi". Jednak bardziej skomplikowane sytuacje, jest możliwe za pomocą przesyłania strumieniowego. Na przykład usługi przekazywania pliku, akceptuje pliki większe niż całą dostępną pamięć. W takim przypadku ustawić `MaxReceivedMessageSize` na bardzo dużą wartość, oczekiwano, że prawie żadne dane są buforowane w pamięci i komunikat przesyła strumieniowo bezpośrednio na dysku. Jeśli komunikat złośliwego jakiś sposób wymusić WCF do buforowania danych, a nie w tym przypadku przesyłania strumieniowego `MaxReceivedMessageSize` już nie chroni przed wiadomości, uzyskiwanie dostępu do wszystkich dostępnej pamięci.  
  
 Aby osłabić to zagrożenie, ustawienia przydziałów istnieją na różnych składników przetwarzania danych WCF tej buforowanie limit. Najważniejsze z nich jest `MaxBufferSize` właściwość różne elementy powiązania transportu i standardowe powiązania. Podczas przesyłania strumieniowego, należy ustawić ten limit przydziału, biorąc pod uwagę maksymalną ilość pamięci, którą chcesz przydzielić komunikatu. Podobnie jak w przypadku `MaxReceivedMessageSize`, ustawienie nie umieszczać bezwzględny maksymalny zużycie pamięci, ale tylko ogranicza ją do w obrębie współczynnika stałej. Również, jak za pomocą `MaxReceivedMessageSize`, należy pamiętać o możliwości wielu komunikatów przetwarzanych jednocześnie.  
  
### <a name="maxbuffersize-details"></a>Szczegóły MaxBufferSize  
 `MaxBufferSize` Właściwość ogranicza wszelkie zbiorcze buforowania WCF jest. Na przykład WCF zawsze buforuje nagłówków protokołu SOAP i błędach SOAP, a także żadnych części MIME, nie jest w kolejności czytania fizyczną w komunikacie komunikat transmisji optymalizacji mechanizm (MTOM). To ustawienie ogranicza buforowania w tych przypadkach.  
  
 Usługi WCF rozwiązanie to przekazanie `MaxBufferSize` wartość, aby różne składniki, które mogą buforować. Na przykład, niektóre <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> przeciążenia <xref:System.ServiceModel.Channels.Message> take klasy `maxSizeOfHeaders` parametru. Przekazuje WCF `MaxBufferSize` wartość tego parametru, aby ograniczyć ilość buforowania nagłówek SOAP. Jest ważne, aby ustawić ten parametr, korzystając z <xref:System.ServiceModel.Channels.Message> klasy bezpośrednio. Ogólnie rzecz biorąc gdy składnik programu WCF, która przyjmuje parametry przydziału, jest ważne, aby umożliwić poznanie skutków zabezpieczeń tych parametrów i ich poprawnie.  
  
 Koder MTOM wiadomości również ma `MaxBufferSize` ustawienie. Podczas korzystania z powiązań standardowych, jest ono ustawione automatycznie na poziomie transportu `MaxBufferSize` wartość. Jednak podczas tworzenia niestandardowego powiązania za pomocą element powiązania koder MTOM wiadomości, jest ważne, aby ustawić `MaxBufferSize` wartość bezpieczne podczas przesyłania strumieniowego jest używana.  
  
## <a name="xml-based-streaming-attacks"></a>Oparte na języku XML ataków przesyłania strumieniowego  
 `MaxBufferSize` samodzielnie nie jest wystarczająco, aby upewnić się, że WCF nie można wymusić na buforowanie podczas przesyłania strumieniowego jest oczekiwany. Na przykład czytelnicy WCF XML zawsze buforu całego tagu początkowym elementu XML, podczas uruchamiania do odczytywania nowego elementu. Można to zrobić, aby poprawnie przetwarzane przestrzenie nazw i atrybutów. Jeśli `MaxReceivedMessageSize` jest skonfigurowana za duży (na przykład, aby włączyć dużych plików bezpośrednio na dysku przesyłania strumieniowego scenariuszu), złośliwy wiadomości musi być zbudowany w treści cały komunikat w przypadku dużych tagu początkowym elementu XML. Wynikiem próby odczytania jego <xref:System.OutOfMemoryException>. Jest to jedna z wielu możliwych opartych na języku XML typu "odmowa usługi" ataków, które można wszystkie zminimalizować przy użyciu przydziałów czytnika XML, opisanych w sekcji "Przy użyciu bezpiecznego XML" w dalszej części tego tematu. Przesyłanie strumieniowe, jest szczególnie ważne, aby ustawić wszystkie z tych limitów przydziału.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Mieszanie przesyłania strumieniowego i buforowanie modele programowania  
 Wiele możliwych ataków wynikają z mieszanie przesyłanych strumieniowo i obsługiwane strumieniowo modeli programowania, w ramach tej samej usługi. Załóżmy, że istnieje kontrakt usługi o dwie operacje: jeden zajmuje <xref:System.IO.Stream> i innym przyjmuje tablicę pewnego typu niestandardowego. Załóżmy również, że `MaxReceivedMessageSize` jest ustawiona na dużą wartość umożliwiające pierwszej operacji przetwarzania dużych strumieni. Niestety oznacza to, że dużych komunikatów teraz można wysłać również drugą operację i Deserializator buforów danych przechowywanych w pamięci jako tablica przed wywołaniem operacji. Jest to potencjalny atak typu "odmowa usługi": `MaxBufferSize` limitu przydziału nie ogranicza rozmiar treści wiadomości, czyli Deserializator współpracuje z.  
  
 Z tego powodu należy unikać mieszania na podstawie strumienia i innych strumieniowo operacje w tej samej umowy. Oczywiście należy łączyć dwóch modelach programowania, należy użyć następujących kroków:  
  
-   Wyłącz <xref:System.Runtime.Serialization.IExtensibleDataObject> funkcji, ustawiając <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> do `true`. Daje to gwarancję, że tylko elementy członkowskie, które są częścią kontraktu są deserializacji.  
  
-   Ustaw <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> właściwość <xref:System.Runtime.Serialization.DataContractSerializer> bezpieczne wartości. Ten limit przydziału jest dostępna również na <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu lub przy użyciu konfiguracji. Ten limit przydziału ogranicza liczbę obiektów, które są deserializacji w jeden odcinek deserializacji. Normalnie każda operacja parametr lub komunikat część treści w kontraktu komunikatu jest przeprowadzona w jeden odcinek. Podczas deserializacji tablic, każdy wpis tablicy jest traktowana jako oddzielny obiekt.  
  
-   Ustaw wszystkie przydziały czytnika XML bezpieczne wartości. Należy zwrócić uwagę na <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, i <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> i uniknąć ciągów w operacjach-streaming.  
  
-   Przejrzyj listę znanych typów, pamiętając o tym, że jeden z nich mogą być utworzone w dowolnym momencie (zobacz sekcję "Zapobiegania niezamierzonym typów z ładowany" w dalszej części tego tematu).  
  
-   Nie używaj żadnych typów, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który buforu dużej ilości danych. Nie należy dodawać tych typów do listy znanych typów.  
  
-   Nie używaj <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> tablic, <xref:System.Byte> tablic lub typów, które implementują <xref:System.Runtime.Serialization.ISerializable> w umowie.  
  
-   Nie używaj <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> tablic, <xref:System.Byte> tablic lub typów, które implementują <xref:System.Runtime.Serialization.ISerializable> na liście znanych typów.  
  
 Poprzedni środki ostrożności są stosowane, gdy operacja strumieniowo używa <xref:System.Runtime.Serialization.DataContractSerializer>. Nigdy nie Mieszaj przesyłania strumieniowego i programowania — przesyłanie strumieniowe modeli w tej samej usługi, jeśli używasz <xref:System.Xml.Serialization.XmlSerializer>, ponieważ nie ma ochrony <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> limitu przydziału.  
  
### <a name="slow-stream-attacks"></a>Ataki Stream powolne  
 Klasa ataków typu "odmowa usługi" przesyłania strumieniowego nie wiąże się zużycie pamięci. Zamiast tego ataku obejmuje powolne nadawcy i adresata danych. Podczas oczekiwania na dane do wysłania lub odebrania, wyczerpania zasobów, takich jak wątki i dostępnych połączeń. Taka sytuacja może powstać wyniku ataków złośliwych lub z wiarygodnego nadawcy/odbiorcy, w z wolnym połączeniem sieciowym.  
  
 Aby rozwiązać te ataki, prawidłowo transportu przekroczeń limitu czasu. Aby uzyskać więcej informacji, zobacz [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Po drugie, nigdy nie używaj synchronicznej `Read` lub `Write` operacje podczas pracy ze strumieniami w programie WCF.  
  
## <a name="using-xml-safely"></a>Bezpiecznie za pomocą języka XML  
  
> [!NOTE]
>  Mimo że w tej sekcji o XML, informacje dotyczą również dokumenty JavaScript Object Notation (JSON). Przydziały działają podobnie, za pomocą [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>Zabezpieczanie czytelnicy XML  
 Zestaw informacji XML stanowi podstawę przetwarzania wszystkich komunikatów w usłudze WCF. Gdy istnieje może odbierać dane XML z niezaufanego źródła, kilka możliwości ataku typu "odmowa usługi", należy zminimalizować. Usługi WCF zapewnia specjalny, bezpieczna czytelnicy XML. Czytelnicy te są tworzone automatycznie, gdy używany jest jeden standard kodowania w programie WCF (tekst, binary lub MTOM).  
  
 Niektóre z funkcji zabezpieczeń na tych czytelnicy zawsze są aktywne. Na przykład czytników nigdy nie Przetwarzaj definicji typu dokumentu (pliki DTD), które są potencjalnym źródłem ataków typu "odmowa usługi" i nigdy nie powinny być wyświetlane w uzasadnionych komunikaty protokołu SOAP. Inne funkcje zabezpieczeń obejmują czytnika limity przydziału, które muszą zostać skonfigurowane, które są opisane w poniższej sekcji.  
  
 Podczas pracy bezpośrednio z czytnikami XML (takie jak podczas pisania własnego niestandardowego kodera, lub podczas pracy bezpośrednio z <xref:System.ServiceModel.Channels.Message> klasy), zawsze używali czytelnicy bezpiecznego WCF, gdy istnieje ryzyko, pracy z niezaufanych danych. Utwórz bezpieczne czytelnicy przez wywołującego fabryki statyczne przeciążenia metody <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> na <xref:System.Xml.XmlDictionaryReader> klasy. Podczas tworzenia czytnika, są przekazywane w wartości bezpiecznych zasobów. Nie wywołuj `Create` przeciążenia metody. Te nie należy tworzyć czytnik WCF. Zamiast tego czytnik jest tworzony, który nie jest chroniony przy użyciu funkcji zabezpieczeń opisane w tej sekcji.  
  
### <a name="reader-quotas"></a>Przydziały czytnika  
 Bezpieczne czytelnicy XML ma pięć konfigurowalnych limitów przydziału. Te są zwykle konfigurowane za pomocą `ReaderQuotas` właściwości na elementy powiązania kodowania lub powiązań standardowych lub za pomocą <xref:System.Xml.XmlDictionaryReaderQuotas> przekazano obiekt podczas tworzenia czytnika.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Ten limit przydziału ogranicza liczbę bajtów, które są odczytywane w jednym `Read` operacji podczas odczytywania elementu start tag i jego atrybuty. (W przypadkach,-strumieniowo, sama nazwa elementu jest nie przeliczane względem limitu przydziału.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> ważne jest, z następujących powodów:  
  
-   Nazwy elementu i jego atrybuty zawsze są buforowane w pamięci, gdy jest odczytywany. Dlatego ważne jest poprawne ustawienie tego przydziału w transmisji strumieniowej trybu, aby uniknąć nadmiernego buforowanie podczas przesyłania strumieniowego jest oczekiwany. Zobacz `MaxDepth` przydziału zamieszczono informacje dotyczące rzeczywistą ilość buforowania, ma miejsce.  
  
-   Masz zbyt wiele atrybutów XML może używać nieproporcjonalne czas przetwarzania, ponieważ nazwy atrybutu muszą być sprawdzane pod kątem unikatowości. `MaxBytesPerRead` zmniejsza zagrożenie tego typu.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML. Na przykład dokument "\<A >\<B >\<C / >\</B >\</A >" głębokość zagnieżdżenia trzech. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> ważne jest, z następujących powodów:  
  
-   `MaxDepth` wchodzi w interakcję z `MaxBytesPerRead`: czytnik zawsze zachowuje dane w pamięci dla bieżącego elementu i wszystkie jego elementy nadrzędne, zmniejszenie zużycia pamięci maksymalnej czytnika jest proporcjonalna do produktu te dwa ustawienia.  
  
-   Podczas deserializacji grafu obiektów głęboko zagnieżdżone, dostęp do całego stosu i zgłosić nieodwracalny wymuszono Deserializator <xref:System.StackOverflowException>. Między zagnieżdżanie XML i zagnieżdżanie obiektu dla obu istnieje bezpośrednia korelacja <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>. Użyj `MaxDepth` Aby osłabić to zagrożenie.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Ten limit przydziału ogranicza rozmiar czytelnika *niepowtarzającymi*. Tabela nazw zawiera niektóre ciągi (na przykład obszary nazw i prefiksy), napotkanych podczas przetwarzania dokumentu XML. Jak te ciągi są buforowane w pamięci, należy ustawić ten limit przydziału, aby uniknąć nadmiernego buforowanie podczas przesyłania strumieniowego jest oczekiwany.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Ten limit przydziału ogranicza rozmiar maksymalny ciągu, która zwraca odczytującego XML. Ten limit przydziału nie ogranicza użycie pamięci przez czytnik XML, sam, ale w składniku korzystający z czytnika. Na przykład, gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnik zabezpieczony za pomocą <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, nie wykonać deserializacji ciągi przekracza ten limit przydziału. Korzystając z <xref:System.Xml.XmlDictionaryReader> klasy bezpośrednio, nie wszystkie metody względem tego limitu przydziału, ale tylko metody, które zostały zaprojektowane specjalnie umożliwiające odczyt ciągów, takich jak <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> metody. <xref:System.Xml.XmlReader.Value%2A> Właściwość czytnik nie dotyczy tego przydziału i dlatego nie powinny być używane podczas ochrony zawiera ten limit przydziału jest konieczne.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Ten limit przydziału ogranicza maksymalny rozmiar tablicy elementów podstawowych, które zwraca odczytującego XML, w tym tablice typu byte. Ten limit przydziału nie ogranicza użycie pamięci przez czytnik XML, sam, ale w składniku niezależnie od korzystający z czytnika. Na przykład, gdy <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnik zabezpieczony za pomocą <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, nie wykonać deserializacji tablice bajtów przekracza ten limit przydziału. Należy ustawić ten limit przydziału podczas próby mieszać modeli programowania przesyłanych strumieniowo i buforowanej w jednej umowy. Należy pamiętać, że podczas korzystania <xref:System.Xml.XmlDictionaryReader> klasy bezpośrednio, tylko metody, które zostały zaprojektowane specjalnie do odczytania tablic dowolnego rozmiaru niektórych typów pierwotnych, takich jak <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, przestrzegać tego limitu przydziału.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>Kodowanie binarne specyficzne zagrożenia  
 Binarny kod XML, kodowania obsługuje WCF zawiera *ciągi słownika* funkcji. Duże ciągi mogą być zakodowane za pomocą tylko kilku bajtów. Włącza znaczący wzrost wydajności, ale wprowadza nowe zagrożenia typu "odmowa usługi", które muszą zostać skorygowane.  
  
 Istnieją dwa rodzaje słowników: *statyczne* i *dynamiczne*. Słownika statycznego jest lista wbudowanej długich ciągów, które mogą być reprezentowane za pomocą krótki kod w kodowanie binarne. Ta lista ciągów jest stała, gdy proces czytający zostanie utworzona i nie może być modyfikowany. Żaden ciągów w słowniku statycznym, która domyślnie używa usługi WCF nie jest wystarczająco duży, aby stwarzać poważne zagrożenie typu "odmowa usługi", mimo że są nadal mogą być stosowane w atak słownikowy rozszerzenia. W zaawansowanych scenariuszach, w których dostarczasz słownika statycznego należy zachować ostrożność, wprowadzając słownika dużych ciągów.  
  
 Funkcja dynamiczne słowników pozwala zdefiniować własne ciągi i skojarz je z krótkich kodów. Te mapowania kod ciągu są przechowywane w pamięci podczas sesji całej komunikacji tak, aby kolejne komunikaty nie jest konieczne ponowne wysyłanie ciągów i mogą korzystać z kodów, które są już zdefiniowane. Te ciągi mogą być o dowolnej długości i dlatego stanowią zagrożenie poważniejsze niż w słowniku statycznym.  
  
 Należy zminimalizować zagrożenia pierwszy jest możliwość dynamiczny słownik (tabeli mapowania kod ciągu), które stają się zbyt duży. Tego słownika można rozwinąć w ciągu kilku wiadomości, a więc `MaxReceivedMessageSize` przydziału oferuje nie ochrony, ponieważ dotyczy on tylko każdy komunikat oddzielnie. W związku z tym, oddzielny <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> istnieje właściwość na <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , która ogranicza rozmiar słownika.  
  
 W przeciwieństwie do większości innych przydziałów ten limit przydziału ma zastosowanie również podczas zapisywania komunikatów. Jeśli zostanie on przekroczony przy odczycie komunikatu `QuotaExceededException` jest zgłaszany w zwykły sposób. Jeśli zostanie on przekroczony, podczas zapisywania wiadomości, wszelkie ciągi, które powodują przydziału przekroczenie są zapisywane w postaci-jest bez korzystania z funkcji dynamicznego słowników.  
  
### <a name="dictionary-expansion-threats"></a>Słownik rozszerzenia zagrożenia  
 Znaczące klasy specyficzne dla danych binarnych ataków wynikającej z rozszerzenia słownika. Małe komunikat w formacie binarnym może przekształcić w bardzo dużych komunikatów w pełni rozwinięte postaci tekstowej Jeśli to sprawia, że zwiększone użycie funkcji słowników ciągów. Współczynnik rozszerzania dla ciągów dynamiczny słownik jest ograniczona przez <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> limit przydziału, ponieważ nie ciągu dynamiczny słownik przekracza maksymalny rozmiar całego słownika.  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, I `MaxArrayLength` właściwości tylko ograniczyć zużycie pamięci. Zwykle nie są zobowiązani do eliminowanie jakiekolwiek zagrożenia, użycie innego niż przesyłane strumieniowo, ponieważ użycie pamięci jest już ograniczona przez `MaxReceivedMessageSize`. Jednak `MaxReceivedMessageSize` liczby bajtów wstępne rozszerzenia. Podczas kodowania binarnego jest używany, wykorzystanie pamięci może potencjalnie wykracza poza `MaxReceivedMessageSize`, jest ograniczona tylko przez współczynnik <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Z tego powodu jest ważne, aby zawsze ustawić wszystkie przydziały reader (szczególnie <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) podczas korzystania z kodowania binarnego.  
  
 Podczas korzystania z kodowania binarnego wraz z <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` precyzyjnym interfejsu do zainstalowania atak słownikowy rozszerzenia. Ten interfejs zasadniczo zapewnia nieograniczony magazyn dla dowolnych danych, które nie jest częścią kontraktu. Jeśli limity przydziału nie można ustawić na tyle niskie, tak, aby `MaxSessionSize` pomnożona przez `MaxReceivedMessageSize` nie jest to stanowić problem, wyłącz `IExtensibleDataObject` są wyposażone w przypadku korzystania z kodowania binarnego. Ustaw `IgnoreExtensionDataObject` właściwości `true` na `ServiceBehaviorAttribute` atrybutu. Alternatywnie, nie należy implementować `IExtensibleDataObject` interfejsu. Aby uzyskać więcej informacji, zobacz [kontrakty danych zgodne](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Podsumowanie przydziałów  
 W poniższej tabeli przedstawiono wskazówki dotyczące limitów przydziału.  
  
|Warunek|Ważne przydziały, aby ustawić|  
|---------------|-----------------------------|  
|Bez przesyłania strumieniowego i przesyłania strumieniowego małych komunikatów, tekst lub kodowanie MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead`, i `MaxDepth`|  
|Bez przesyłania strumieniowego i przesyłania strumieniowego małych komunikatów binarnych kodowania|`MaxReceivedMessageSize`, `MaxSessionSize`, a wszystkie `ReaderQuotas`|  
|Przesyłanie strumieniowe dużych komunikatów, tekst lub kodowanie MTOM|`MaxBufferSize` i wszystkie `ReaderQuotas`|  
|Kodowanie przesyłania strumieniowego dużych komunikatów binarnych|`MaxBufferSize`, `MaxSessionSize`, a wszystkie `ReaderQuotas`|  
  
-   Limity czasu poziomu transportu musi zawsze mieć ustawioną i nigdy nie używaj synchronicznej operacji odczytu/zapisu podczas przesyłania strumieniowego jest używany, niezależnie od tego, czy są przesyłanie strumieniowe dużych lub małych komunikatów.  
  
-   W razie wątpliwości dotyczące przydziału, ustaw ją na wartość bezpieczne, a nie pozostawiając je otwarte.  
  
## <a name="preventing-malicious-code-execution"></a>Zapobieganie wykonywaniu złośliwego kodu  
 Następujących klas ogólnych zagrożeń można wykonać kod i mieć niezamierzone efekty:  
  
-   Deserializator ładuje typ złośliwy, niebezpieczny lub istotnymi dla zabezpieczeń.  
  
-   Wiadomości przychodzące powoduje, że Deserializator do utworzenia wystąpienia typu zwykle bezpieczne w taki sposób, który posiada niezamierzone konsekwencje.  
  
 W poniższych sekcjach omówiono te klasy dalsze zagrożenia.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Aby uzyskać informacje o zabezpieczeniach <xref:System.Xml.Serialization.XmlSerializer>, zobacz odpowiednią dokumentację.) Model zabezpieczeń <xref:System.Xml.Serialization.XmlSerializer> jest podobny do <xref:System.Runtime.Serialization.DataContractSerializer>i różni się przede wszystkim w szczegółach. Na przykład <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybut jest używany do włączenia typu zamiast <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu. Jednak niektóre zagrożeń unikatowe dla <xref:System.Xml.Serialization.XmlSerializer> zostały omówione w dalszej części tego tematu.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>Uniemożliwienie ładowany niezamierzone typów  
 Trwa ładowanie typów niezamierzone może mieć poważne konsekwencje, czy typ jest złośliwe lub po prostu ma efekty uboczne istotnymi dla zabezpieczeń. Typ może zawierać luki w zabezpieczeniach możliwe do wykorzystania, akcje istotnymi dla zabezpieczeń w jego konstruktorze lub konstruktora klasy, mają zużycia dużej ilości pamięci, który ułatwia ataków typu "odmowa usługi" lub może zgłaszać wyjątki nieodwracalny. Typy mogą mieć konstruktorów klas, systemami operacyjnymi zaraz po jego typ jest ładowany, oraz przed utworzeniem żadnych wystąpień. Z tego względu należy kontrolować zestaw typów, które może spowodować załadowanie deserializacji.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Deserializuje w swobodną. Nigdy nie odczytuje wspólnego języka wspólnego (CLR), typ i zestaw nazw z danych przychodzących. Jest to podobne do zachowania <xref:System.Xml.Serialization.XmlSerializer>, ale różni się od zachowania <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Luźne powiązanie wprowadza poziom bezpieczeństwa, ponieważ zdalnej osobie atakującej nie może wskazywać dowolnego typu, można załadować tylko za pomocą nazw tego typu w komunikacie.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Będzie można załadować typu, który aktualnie jest oczekiwany zgodnie z umową. Na przykład, jeśli kontraktu danych ma składową danych typu `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> mogą ładować `Customer` wpisz po jego deserializuje ten element członkowski danych.  
  
 Ponadto <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje polimorfizm. Element członkowski danych może być zadeklarowana jako <xref:System.Object>, ale może zawierać dane przychodzące `Customer` wystąpienia. Jest to możliwe tylko wtedy, gdy `Customer` typu złożonego "znanych" do deserializacji za pomocą jednego z tych mechanizmów:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute> zastosowany do typu.  
  
-   `KnownTypeAttribute` atrybut określający metodę, która zwraca listę typów.  
  
-   `ServiceKnownTypeAttribute` atrybut.  
  
-   `KnownTypes` Sekcji konfiguracji.  
  
-   Listę znanych typów jawnie przekazany do <xref:System.Runtime.Serialization.DataContractSerializer> podczas konstruowania, jeśli bezpośrednio za pomocą serializatora.  
  
 Każdy z tych mechanizmów zwiększa obszar powierzchni, wprowadzenie do większej liczby typów, które można załadować deserializacji. Każdy z tych mechanizmów, aby upewnić się, że żadne typy złośliwego bądź niepożądanego są dodawane do listy znanych typów kontroli.  
  
 Gdy znany typ znajduje się w zakresie, mogą być ładowane w dowolnym momencie i można było utworzyć wystąpienia typu, nawet wtedy, gdy kontrakt zabrania jest używana. Na przykład załóżmy, że typ, który "MyDangerousType" zostanie dodany do listy znanych typów, przy użyciu jednej z powyższych mechanizmów. Oznacza to, że:  
  
-   `MyDangerousType` jest ładowany i jego uruchomieniem konstruktora klasy.  
  
-   Nawet wtedy, gdy podczas deserializacji kontraktu danych za pomocą element członkowski danych ciągu, złośliwy wiadomości mogą spowodować wystąpienie `MyDangerousType` do utworzenia. Możesz pisać kod w `MyDangerousType`, takie jak w przypadku metod ustawiających właściwości mogą być uruchamiane. Po zakończeniu tej operacji Deserializator próbuje przypisać tego wystąpienia ciągu element członkowski danych i zakończyć się niepowodzeniem z powodu wyjątku.  
  
 Podczas zapisywania metodę, która zwraca listę znanych typów, lub gdy przekazywanie bezpośrednio do listy <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, upewnij się, że kod, który przygotowuje listy jest bezpieczna działa tylko z zaufanych danych.  
  
 Jeśli Określanie znanych typów w konfiguracji, upewnij się, że plik konfiguracyjny jest bezpieczne. Zawsze używaj silnych nazw w konfiguracji (przez określenie klucza publicznego zestawu podpisem, w której znajduje się typ), ale nie określono wersji typu do załadowania. Moduł ładujący typu automatycznie wybiera najnowszej wersji, jeśli jest to możliwe. Jeśli określisz określonej wersji w konfiguracji, istnieje ryzyko następujących: typ może mieć luki w zabezpieczeniach, które mogą zostać rozwiązane w przyszłej wersji, ale wersja nadal ładuje, ponieważ jest on jawnie określony w konfiguracji.  
  
 Zbyt wiele znanych typów ma inną konsekwencją: <xref:System.Runtime.Serialization.DataContractSerializer> tworzy pamięć podręczną kodu serializacji/deserializacji w domenie aplikacji, za pomocą wpis dla każdego typu musi serializacji i deserializacji. Ta pamięć podręczna nigdy nie zostanie wyczyszczona tak długo, jak działa domeny aplikacji. W związku z tym osoba atakująca, która rozpoznaje, że aplikacja korzysta z wielu znanych typów może spowodować deserializacji obiektu danych tych typów, powodując pamięci podręcznej, aby zużywać nieproporcjonalnie duża ilość pamięci.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>Uniemożliwienie typów w niezamierzonym stanie  
 Typ może mieć ograniczenia wewnętrznego sprawdzania spójności, które muszą zostać wymuszone. Należy uważać, aby uniknąć przerwanie tych ograniczeń podczas deserializacji.  
  
 Poniższy przykład typu reprezentuje stan wstawionym na statki kosmiczne i wymusza ograniczenie, że zarówno wewnętrzne i zewnętrzne drzwi nie można otworzyć w tym samym czasie.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Osoba atakująca może wysłać złośliwy komunikat podobny do poniższego, poruszanie się po ograniczenia i uzyskanie obiektu w nieprawidłowym stanie, który może mieć niezamierzone i nieprzewidywalne skutki.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Można uniknąć tej sytuacji jest pamiętać o następujących kwestiach:  
  
-   Gdy <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje większości klas konstruktory nie uruchamiaj. W związku z tym nie należy polegać na zarządzanie stanem, wszystkie wykonane w konstruktorze.  
  
-   Korzystać z wywołań zwrotnych, aby upewnić się, że obiekt jest w nieprawidłowym stanie. Wywołania zwrotnego oznaczone <xref:System.Runtime.Serialization.OnDeserializedAttribute> atrybut jest szczególnie przydatne, ponieważ jest uruchamiana po zakończeniu deserializacji i ma szansę, aby zbadać i rozwiązać ogólny stan. Aby uzyskać więcej informacji, zobacz [wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Nie należy projektować typy kontraktu danych opierać się na określonej kolejności, w którym właściwość musi być wywołana metod ustawiających.  
  
-   Powinien zachować ostrożność przy użyciu starszych typach oznaczone elementem <xref:System.SerializableAttribute> atrybutu. Wiele z nich zostały zaprojektowane do pracy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting do użytku z tylko zaufane dane. Istniejące typy oznaczone przy użyciu tego atrybutu może nie jest przeznaczony stanu bezpieczeństwa na uwadze.  
  
-   Nie należy polegać na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość `DataMemberAttribute` atrybutu, aby zagwarantować obecności danych w zakresie dotyczącym bezpieczeństwa stanu jest. Dane można zawsze być `null`, `zero`, lub `invalid`.  
  
-   Nigdy nie zaufanie wykresu obiektu deserializacji ze źródła danych w niezaufanych bez najpierw sprawdzania poprawności. Poszczególnych obiektów może być w stanie spójności, ale wykresu obiektu jako całości może nie być. Ponadto nawet po wyłączeniu trybu konserwacji wykresu obiektu wykresu po deserializacji może mieć wiele odwołań do tego samego obiektu lub masz odwołania cykliczne. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>Bezpiecznie przy użyciu NetDataContractSerializer  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> Jest mechanizm serializacji, który używa ścisłego sprzężenia do typów. Jest to podobne do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Oznacza to, określa, którego typu wystąpienia, czytając [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Nazwa zestawu i typu danych przychodzących. Wchodzi w skład WCF, ale nie istnieje sposób podany o podłączenie ten mechanizm serializacji; musi być napisany kod niestandardowy. `NetDataContractSerializer` Znajduje się przede wszystkim do jej obsługi ułatwiają migrację z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting do programu WCF. Aby uzyskać więcej informacji, zobacz sekcję istotne w [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Ponieważ samej wiadomości może wskazywać na dowolny typ może być załadowany, <xref:System.Runtime.Serialization.NetDataContractSerializer> mechanizm jest z założenia niezabezpieczone i powinien być używany tylko z zaufanych danych. Istnieje możliwość zwiększyć bezpieczeństwo, pisząc integratora typ bezpieczny i ograniczenie typu, który umożliwia tylko bezpiecznych typy załadować (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> właściwości).  
  
 Nawet wtedy, gdy jest używany z zaufanych danych, dane przychodzące niewystarczająco mogą określać typ obciążenia, zwłaszcza wtedy, gdy <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwość jest ustawiona na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Każda osoba mająca dostęp do katalogu aplikacji lub do globalnej pamięci podręcznej można zastąpić typu złośliwych zamiast ten, który powinien załadować. Zapewnij zabezpieczeń katalogu aplikacji i global assembly cache poprawnie, ustawiając uprawnienia.  
  
 Ogólnie rzecz biorąc, jeśli zezwolisz na dostęp częściowo zaufany kod, aby Twoje `NetDataContractSerializer` wystąpienia lub w inny sposób kontroluje selektora znaków (<xref:System.Runtime.Serialization.ISurrogateSelector>) lub dla integratora serializacji (<xref:System.Runtime.Serialization.SerializationBinder>), kod może wykonywać znaczną kontrolę nad proces serializacji/deserializacji. Na przykład go mogą wprowadzać dowolne typy, doprowadzić do ujawnienia informacji, manipulowanie wynikowy wykres obiektu lub serializowane dane lub przepełnienie wynikowe serializowanym strumieniu.  
  
 Inny problem z zabezpieczeniami `NetDataContractSerializer` jest typu "odmowa usługi, nie zagrożenie wykonywania złośliwego kodu". Korzystając z `NetDataContractSerializer`zawsze ustaw <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> przydziału bezpieczne wartości. Jest łatwy do konstruowania małych komunikat złośliwy, który przydziela tablicę obiektów, których rozmiar jest ograniczony tylko ilością tego przydziału.  
  
### <a name="xmlserializer-specific-threats"></a>Zagrożenia specyficzne dla elementu XmlSerializer  
 <xref:System.Xml.Serialization.XmlSerializer> Model zabezpieczeń jest podobny do <xref:System.Runtime.Serialization.DataContractSerializer>. Jednak kilka zagrożeń są unikatowe dla <xref:System.Xml.Serialization.XmlSerializer>.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Generuje *zestawy serializacji* w czasie wykonywania, który zawiera kod, który faktycznie serializuje i deserializuje; te zestawy są tworzone w katalogu plików tymczasowych. Jeśli inny proces lub użytkownik nie ma praw dostępu do tego katalogu, może zastąpić kod serializacji/deserializacji, za pomocą dowolnego kodu. <xref:System.Xml.Serialization.XmlSerializer> Następnie uruchamia ten kod zamiast kodu serializacji/deserializacji za pomocą jego kontekstu zabezpieczeń. Upewnij się, że uprawnienia zostały ustawione prawidłowo dla katalogu plików tymczasowych Aby temu zapobiec.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Ma również tryb, w którym używa zestawów serializacji wstępnie wygenerowanego zamiast generować je w czasie wykonywania. Ten tryb jest wyzwalana po każdym <xref:System.Xml.Serialization.XmlSerializer> można znaleźć zestawu serializacji odpowiednie. <xref:System.Xml.Serialization.XmlSerializer> Sprawdza, czy zestaw serializacji została podpisana przez ten sam klucz, który został użyty do podpisania zestawu, który zawiera typy serializowanego. To zapewnia ochronę z zestawów złośliwego trwa mogą przybierać zestawy serializacji. Jednakże, jeśli zestaw, który zawiera Twoje typów możliwych do serializacji nie jest podpisany, <xref:System.Xml.Serialization.XmlSerializer> nie można wykonać ten test i korzysta z żadnych zestawów z właściwą nazwą. Umożliwia uruchamianie złośliwego kodu. Zawsze podpisywać zestawy, które zawierają typy z możliwością serializowania lub ściśle kontrolować dostęp do katalogu aplikacji i globalnej pamięci podręcznej, aby uniknąć wprowadzenia złośliwego zestawów.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Mogą podlegać "odmowa usługi". <xref:System.Xml.Serialization.XmlSerializer> Nie ma `MaxItemsInObjectGraph` limitu przydziału (w jakim są dostępne na <xref:System.Runtime.Serialization.DataContractSerializer>). W efekcie deserializuje dowolnej liczby obiektów, ograniczony tylko ilością rozmiar komunikatu.  
  
### <a name="partial-trust-threats"></a>Zagrożenia częściowej relacji zaufania  
 Należy zwrócić uwagę następujące kwestie dotyczące zagrożeń związanych z kodu działającego z częściowej relacji zaufania. Te zagrożenia obejmują złośliwy kod częściowo zaufany, a także złośliwego częściowo zaufany kod w połączeniu z inne scenariusze ataków (na przykład, częściowo zaufany kod, który tworzy określony ciąg znaków, a następnie podczas deserializacji).  
  
-   Podczas korzystania z żadnych składników serializacji, nigdy nie assert wszelkich uprawnień, zanim tych danych użycia, nawet jeśli scenariusz całego serializacji znajduje się w zakresie usługi potwierdzenia, a nie mamy do czynienia z niezaufanych danych lub obiektów. Takie użycie może prowadzić do luk w zabezpieczeniach.  
  
-   W przypadkach, gdy ma kontrolę nad procesem serializacji, za pomocą punkty rozszerzeń (surogatów), typów, które jest serializowana, lub w inny sposób przez częściowo zaufany kod częściowo zaufany kod może powodować serializator służący do wypełniania wyjściowego dużą ilość dane do strumienia serializacji, co może spowodować przeprowadzenie ataku typu "odmowa usługi" (DoS) do odbiorcy tego strumienia. Przypadku serializowania danych przeznaczonych dla obiektu docelowego, który jest wrażliwa na zagrożenia DoS serializacji typów częściowo zaufany lub nie inny sposób umożliwić częściowo zaufany kod sterowania serializacji.  
  
-   Jeśli zezwolisz na dostęp częściowo zaufany kod, aby Twoje <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia lub w inny sposób kontroluje [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), może on wykonywać dużą kontrolę nad procesem serializacji/deserializacji. Na przykład go mogą wprowadzać dowolne typy, doprowadzić do ujawnienia informacji, manipulowanie wynikowy wykres obiektu lub serializowane dane lub przepełnienie wynikowe serializowanym strumieniu. Odpowiednik <xref:System.Runtime.Serialization.NetDataContractSerializer> zagrożeń zostało opisane w sekcji "Przy użyciu NetDataContractSerializer Securely".  
  
-   Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do typu (lub typ jest oznaczony jako `[Serializable]` , ale nie jest `ISerializable`), Deserializator można utworzyć wystąpienie takiego typu, nawet jeśli wszystkie konstruktory niepubliczne lub chronione przez żądania.  
  
-   Nigdy nie należy zakładać wynik deserializacji, chyba że danych ma zostać przeprowadzona jest zaufany, a masz pewność, że wszystkie znane typy są typami, które można zaufać. Należy zauważyć, że znanych typów nie są ładowane z pliku konfiguracji aplikacji, (a zostaną załadowane z pliku konfiguracji komputera) podczas uruchamiania w trybie częściowego zaufania.  
  
-   W przypadku przekazania `DataContractSerializer` wystąpienie z surogatu dodane do częściowo zaufany kod, kod może zmienić ustawienia można modyfikować w tym zastępczy.  
  
-   Dla obiektu po deserializacji Jeśli odczytującego XML (lub je tam) pochodzi z częściowo zaufany kod zaliczenie wynikowego obiektu po deserializacji niezaufanych danych.  
  
-   Fakt, <xref:System.Runtime.Serialization.ExtensionDataObject> typ nie ma publicznych elementów członkowskich oznacza, że w nim dane nie jest bezpieczne. Na przykład, jeśli zdeserializować źródła danych uprzywilejowanego na obiekt, w której niektóre znajdują się dane, następnie ręcznie, który obiekt częściowo zaufany kod częściowo zaufany kod może odczytywać dane w `ExtensionDataObject` przez serializacji obiektu. Rozważ ustawienie <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> do `true` podczas deserializacji źródła danych uprzywilejowanych do obiektu, który jest późniejsza przekazany do częściowo zaufany kod.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje serializacji prywatnych, chronionych, wewnętrzne i publiczne elementy członkowskie w trybie pełnego zaufania. Jednak w częściowej relacji zaufania, może być Zserializowany tylko publiczne elementy członkowskie. Element `SecurityException` jest generowany, jeśli aplikacja próbuje serializacji niepublicznego elementu członkowskiego.  
  
     Aby zezwolić na wewnętrzny lub chronionych wewnętrznych składowych być serializowana w częściowej relacji zaufania, użyj `System.Runtime.CompilerServices.InternalsVisibleTo` atrybutu zestawu. Ten atrybut umożliwia zestawu, aby zadeklarować, że jej składowe wewnętrzne są widoczne dla niektórych innych zestawów. W tym przypadku zestaw, który chce mieć jego wewnętrznych składowych serializacji oświadcza, że jej składowe wewnętrzne są widoczne dla System.Runtime.Serialization.dll.  
  
     Zaletą tego podejścia jest to, że nie wymaga ścieżką generowanie kodu z podwyższonym poziomem uprawnień.  
  
     W tym samym czasie istnieją dwie główne wady.  
  
     Pierwszy wadą jest to, że opcjonalna właściwość `InternalsVisibleTo` atrybutu jest całego zestawu. Oznacza to nie można określić, że tylko niektórych klasa może mieć jego wewnętrznych składowych serializacji. Oczywiście nadal możesz nie serializacji określonego elementu członkowskiego wewnętrznego, po prostu dodając nie `DataMember` atrybutu tego elementu członkowskiego. Podobnie Deweloper można też dołączyć do wewnętrznego zamiast prywatnych lub chronionych, za pomocą widoczność nieznaczne problemy.  
  
     Drugi Wadą jest to, że nadal nie obsługuje prywatnych ani chronionych elementów członkowskich.  
  
     Aby zilustrować użytkowania `InternalsVisibleTo` atrybutu w częściowej relacji zaufania, należy wziąć pod uwagę następujący program:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     W powyższym przykładzie `PermissionsHelper.InternetZone` odpowiada `PermissionSet` częściowego zaufania. Teraz, bez `InternalsVisibleToAttribute`, aplikacja zakończy się niepowodzeniem, zostanie zgłoszony `SecurityException` wskazujący, że niepubliczne składowe nie może być serializowana w częściowej relacji zaufania.  
  
     Jednak jeśli dodamy następujący wiersz do pliku źródłowego, program zostanie uruchomiony pomyślnie.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Inne problemy Zarządzanie stanem  
 Warto wspomnieć o kilku uwagi dotyczące zarządzania stanem obiektu:  
  
-   Korzystając z modelu programowania opartego na strumień za pomocą transportu przesyłania strumieniowego, przetwarzanie wiadomości wypada nadejściu wiadomości. Nadawca wiadomości może przerwać operację wysyłania w środku strumienia, pozostawiając Twój kod w nieprzewidywalnym stanie, jeśli Oczekiwano większej ilości zawartości. Ogólnie rzecz biorąc, nie należy polegać na strumień jest pełna, a nie wykonuj żadnych działań w ramach operacji na podstawie strumienia, którego nie można obniżyć ponownie w przypadku, gdy strumień jest przerywana. Dotyczy to również sytuacji, gdy komunikat może być źle sformułowane z treści strumieniowych (na przykład, jego może brakować tagu końcowego koperty protokołu SOAP lub mogą mieć drugi treść komunikatu).  
  
-   Za pomocą `IExtensibleDataObject` funkcji może spowodować, że poufnych danych maszynowych. Jeśli użytkownik akceptuje dane z niezaufanego źródła w kontraktach danych za pomocą `IExtensibleObjectData` i później ponownie emitując je na bezpiecznego kanału, w której wiadomości są podpisane, możesz są potencjalnie zagwarantowanie nic wiedzieć o danych. Ponadto ogólny stan, który jest wysyłany może być nieprawidłowy, jeśli znanych i nieznanych fragmentów danych należy wziąć pod uwagę. Uniknąć tej sytuacji, ustawiając albo selektywnie właściwość danych rozszerzenia `null` lub przez wyłączenie selektywnie `IExtensibleObjectData` funkcji.  
  
## <a name="schema-import"></a>Importuj schemat  
 Normalnie, proces importowania schematu w celu generowania typów występuje tylko w czasie projektowania, na przykład, korzystając z [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) usługi sieci Web, aby wygenerować klasę klienta. Jednak w bardziej zaawansowanych scenariuszy może przetwarzać schematem w czasie wykonywania. Należy pamiętać, że ten sposób może narazić możesz o zagrożeniu typu "odmowa usługi". Niektóre schematu może zająć dużo czasu do zaimportowania. Nigdy nie używaj <xref:System.Xml.Serialization.XmlSerializer> składnik Importowanie schematu w takich scenariuszach, jeśli schematy są prawdopodobnie pochodzące z niezaufanego źródła.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Specyficzne zagrożenia integracji AJAX programu ASP.NET  
 Gdy użytkownik implementuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> lub <xref:System.ServiceModel.Description.WebHttpBehavior>, WCF uwidacznia punkt końcowy, który może akceptować wiadomości XML i JSON. Jednak jest tylko jeden zestaw przydziały czytnika używane zarówno przez czytnik XML i czytnika JSON. Niektóre ustawienia limitu przydziału może być odpowiednie dla jeden czytnik, ale zbyt duży dla siebie.  
  
 Podczas implementowania `WebScriptEnablingBehavior`, użytkownik ma możliwość udostępnienia JavaScript serwera proxy w punkcie końcowym. Należy rozważyć następujące zagadnienia dotyczące zabezpieczeń:  
  
-   Informacje o usłudze (nazwy operacji, nazwy parametru itd.) można uzyskać, sprawdzając serwera proxy JavaScript.  
  
-   Korzystając z punktu końcowego języka JavaScript, informacje poufne i prywatne mogą być zachowane w obiekcie klienta pamięci podręcznej przeglądarki sieci Web.  
  
## <a name="a-note-on-components"></a>Uwaga dotycząca składników  
 Usługi WCF jest elastyczne i możliwe do dostosowania systemu. Większość zawartości w tym temacie skoncentrować się na najbardziej typowe scenariusze użycia usługi WCF. Jednak jest możliwe do tworzenia składników, które WCF zapewnia wiele różnych sposobów. Jest to ważne, aby umożliwić poznanie skutków zabezpieczeń za pomocą każdego składnika. W szczególności:  
  
-   Podczas czytelnicy XML musi być używany, należy użyć czytników <xref:System.Xml.XmlDictionaryReader> zawiera klasy, w przeciwieństwie do innych czytników. Bezpieczne czytelnicy są tworzone przy użyciu <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> metody. Nie używaj <xref:System.Xml.XmlReader.Create%2A> metody. Zawsze należy skonfigurować czytników przy użyciu bezpiecznych przydziały. Aparaty serializacji w usłudze WCF są bezpieczne, tylko wtedy, gdy jest używane z bezpiecznego czytelnicy XML z usługi WCF.  
  
-   Korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> deserializować potencjalnie niezaufane dane, zawsze wartość <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> właściwości.  
  
-   Podczas tworzenia komunikatu, ustaw `maxSizeOfHeaders` parametru Jeśli `MaxReceivedMessageSize` nie daje wystarczającą ilość ochrony.  
  
-   Podczas tworzenia kodera, zawsze skonfigurować odpowiednie limity przydziału, takiego jak `MaxSessionSize` i `MaxBufferSize`.  
  
-   Korzystając z XPath filtr komunikatów, ustaw <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> Aby ograniczyć ilość węzłów XML, które odwiedza filtru. Nie używaj wyrażenia XPath, które może zająć dużo czasu do obliczeń bez konieczności przechodzenia z wieloma węzłami.  
  
-   Ogólnie rzecz biorąc korzystając z dowolnego składnika, który akceptuje limit przydziału, zrozumieć jego skutki dla bezpieczeństwa i ustaw ją na wartość bezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)

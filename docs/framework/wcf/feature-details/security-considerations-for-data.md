---
title: "Zagadnienia związane z zabezpieczeniami danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bb7a40bc38a3fdf3f7be2b31e30e768e26be2d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-data"></a>Zagadnienia związane z zabezpieczeniami danych
Podczas pracy z danymi w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], należy wziąć pod uwagę liczbę kategorii zagrożeń. W poniższej tabeli wymieniono najważniejsze klasy zagrożenia, które odnoszą się do przetwarzania danych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]udostępnia narzędzia, aby ograniczyć te zagrożenia.  
  
 Odmowa usługi  
 Podczas odbierania danych niezaufanych, danych może spowodować po stronie odbierającej dostęp do różnych zasobów, takich jak pamięci, wątki, dostępne połączenia lub cyklów procesora nieproporcjonalnie dużego przy powodują długie obliczenia. Atak typu "odmowa usługi" na serwerze może spowodować jej awarii i nie można przetworzyć wiadomości od innych, oryginalnych klientów.  
  
 Wykonanie złośliwego kodu  
 Przychodzące niezaufanych danych powoduje, że po stronie odbierającej do uruchomienia kodu, który go nie chcesz.  
  
 Ujawnienie informacji  
 Zdalnej osobie atakującej wymusza otrzymującej odpowiadać na żądania jej w taki sposób, aby ujawnić informacji więcej niż zamierza.  
  
## <a name="user-provided-code-and-code-access-security"></a>Kod użytkownika i zabezpieczenia dostępu kodu  
 Liczba miejsc w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastruktury, uruchamiać kod dostarczonego przez użytkownika. Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> mechanizm serializacji może wywołać dostarczane przez użytkownika właściwości `set` metody dostępu i `get` metody dostępu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktury kanału może również wywołują dostarczane przez użytkownika klas pochodnych <xref:System.ServiceModel.Channels.Message> klasy.  
  
 Jest odpowiedzialny za autora kod, aby upewnić się, że luk w zabezpieczeniach nie istnieje. Na przykład w przypadku utworzenia typu kontraktu danych z właściwością elementu członkowskiego danych typu integer, a w `set` implementacja metody dostępu przydzielić tablicy na podstawie wartości właściwości, udostępnianie możliwości ataku typu "odmowa usługi", jeśli złośliwe komunikat zawiera bardzo dużą wartość dla tego elementu członkowskiego danych. Ogólnie rzecz biorąc należy unikać alokacje na podstawie danych przychodzących lub długie przetwarzanie w kodzie użytkownika (zwłaszcza, jeśli długich przetwarzania może być spowodowany niewielką ilość przychodzących danych). Podczas przeprowadzania analizy zabezpieczeń kodu użytkownika, upewnij się, że należy również rozważyć wszystkich przypadkach niepowodzenia (oznacza to, że wszystkie kodu gałęzie gdzie są zgłaszane wyjątki).  
  
 Ultimate przykładem kodu dostarczonego przez użytkownika jest kodu wewnątrz implementacji usługi dla każdej operacji. Zabezpieczenia implementacji usługi odpowiada użytkownik. Jest łatwo tworzyć przypadkowo implementacji niezabezpieczonych operacji, które mogą skutkować luk w zabezpieczeniach typu "odmowa usługi". Na przykład operację, która przyjmuje ciągiem i zwraca listę klientów z bazy danych, których nazwa rozpoczyna się od tego ciągu. Jeśli pracujesz z dużej bazy danych, a ciąg przekazywany jest tylko pojedyncze litery, kodu mogą próbować utworzyć wiadomości większych niż dostępnej pamięci, co powoduje awarię całej usługi. ( <xref:System.OutOfMemoryException> Nie jest możliwe do odzyskania w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] i zawsze powoduje zablokowanie dostępu do aplikacji.)  
  
 Należy upewnić się, że nie złośliwy kod jest podłączony do różnych punktów rozszerzalności. Jest to szczególnie istotne w przypadku, gdy jest używany w częściowej relacji zaufania, dotyczących typów z częściowo zaufanych zestawów lub tworzenie składników można używać przez kod częściowo zaufany. Aby uzyskać więcej informacji zobacz "Częściowego zaufania zagrożeń" w dalszej części artykułu.  
  
 Może uruchomionej w częściowej relacji zaufania, infrastruktury serializacji kontraktu danych obsługuje tylko ograniczone podzbiór danych kontraktu modelu programowania — na przykład dane prywatne elementy Członkowskie lub typów przy użyciu <xref:System.SerializableAttribute> atrybutów nie są obsługiwane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Częściowej relacji zaufania](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Unikanie przypadkowe ujawnienie.  
 Podczas projektowania typów możliwych do serializacji z myślą o bezpieczeństwie, ujawnienie informacji jest możliwy problem.  
  
 Należy rozważyć następujące kwestie:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Model programowania umożliwia narażenia prywatne i wewnętrzne danych poza typu lub zestawu podczas serializacji. Ponadto kształtu typu mogą być narażone podczas eksportowania schematu. Pamiętaj zrozumieć danego typu serializacji projekcji. Jeśli nie mają żadnych widoczne, wyłącz, szeregując go (na przykład stosując nie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu w przypadku kontraktu danych).  
  
-   Należy pamiętać, że ten sam typ może mieć wielu serializacji projekcji, w zależności od elementu serializującego w użyciu. Ten sam typ może narazić jeden zestaw danych, gdy jest używany z <xref:System.Runtime.Serialization.DataContractSerializer> i inny zestaw danych, gdy jest używany z <xref:System.Xml.Serialization.XmlSerializer>. Przypadkowemu użyciu niewłaściwy serializator może spowodować ujawnienie informacji.  
  
-   Przy użyciu <xref:System.Xml.Serialization.XmlSerializer> w starszej wersji procedur zdalnych wywołań (procedur RPC) / zakodowanego tryb przypadkowo może narazić kształtu Wykres obiektu po stronie wysyłającej do po stronie odbierającej.  
  
## <a name="preventing-denial-of-service-attacks"></a>Zapobieganie atakom typu "odmowa usługi"  
  
### <a name="quotas"></a>Przydziały  
 Powoduje po stronie odbierającej można przydzielić znaczną ilość pamięci jest potencjalny atak typu "odmowa usługi". Gdy w tej sekcji koncentruje się na problemy z użyciem pamięci wynikających z dużych wiadomości, może wystąpić inne ataki. Na przykład wiadomości posłużyć nieproporcjonalnie dużego czas przetwarzania.  
  
 Ataki typu "odmowa usługi" są zazwyczaj skorygowane przy użyciu przydziałów. Po przekroczeniu przydziału <xref:System.ServiceModel.QuotaExceededException> jest zazwyczaj zgłaszany wyjątek. Bez przydziału, niebezpieczną wiadomość może spowodować całą dostępną pamięć można było uzyskać dostęp, co powoduje <xref:System.OutOfMemoryException> wyjątku lub wszystkie dostępne stosy można uzyskać dostęp, wynikowe w <xref:System.StackOverflowException>.  
  
 Przekroczono przydział scenariusza są możliwe do odzyskania; Jeśli w działającej usłudze, aktualnie przetwarzanego komunikatu jest odrzucany i kontynuowanie działania i przetwarza dalsze komunikaty. Scenariusze przepełnienie braku pamięci i stosu, jednak nie są możliwe do odzyskania w dowolnym miejscu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; zakończenie usługi, jeśli wykryje takie wyjątki.  
  
 Przydziały w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymagają żadnych wstępnej alokacji. Na przykład jeśli <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> przydziału (znajdujący się na różnych klas) jest ustawiona na 128 KB, nie oznacza to, że 128 KB automatycznie przypisany do każdego komunikatu. Wartość rzeczywistego przydzielone zależy od rzeczywisty rozmiar wiadomości przychodzącej.  
  
 Wiele przydziały są dostępne w warstwie transportowej. Są to limitami przez kanał transportu określonych w użyciu (HTTP, TCP i tak dalej). Gdy w tym temacie omówiono niektóre z tych przydziałów, te przydziały opisano szczegółowo w [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>HashTable luki w zabezpieczeniach  
 Usterka gdy kontraktów danych zawierają obiektach HashTable lub kolekcji. Problem występuje, jeśli wiele wartości są wstawiane do obiektu hashtable gdzie dużą liczbę tych wartości Generowanie taką samą wartość skrótu. Może być używany jako atak DOS.  Ta luka w zabezpieczeniach można zminimalizować przez ustawienie limitu przydziału powiązania MaxRecievedMessageSize. Należy zachować ostrożność podczas ustawiania ten limit przydziału, aby zapobiec takim atakom. Ten limit przydziału umieszcza górny limit rozmiaru wiadomości WCF. Ponadto należy unikać obiektach HashTable lub kolekcji w kontraktach sieci danych.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Ograniczanie zużycia pamięci bez przesyłania strumieniowego  
 Model zabezpieczeń wokół dużych wiadomości zależy od tego, czy przesyłanie strumieniowe jest używana. W przypadku podstawowych, z systemem innym niż strumieniowo komunikaty są buforowane do pamięci. W takim przypadku należy użyć <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> przydziału na <xref:System.ServiceModel.Channels.TransportBindingElement> lub na wiązania dostarczane przez system, aby zapewnić ochronę przed dużych wiadomości przez ograniczenie maksymalny rozmiar wiadomości dostępu do. Należy pamiętać, że usługi może przetwarzać wiele komunikatów w tym samym czasie, w którym to przypadku są w pamięci. Funkcja ograniczania przepustowości umożliwia uniknięcie tego zagrożenia.  
  
 Należy również zauważyć, że `MaxReceivedMessageSize` nie umieścić górna granica na wiadomości zużycie pamięci, ale ogranicza ją do wewnątrz stały wskaźnik. Na przykład jeśli `MaxReceivedMessageSize` to 1 MB i 1 MB wiadomość zostanie odebrana, a następnie zdeserializowany, dodatkowe pamięci jest muszą zawierać wykres obiektu po deserializacji, co spowoduje także zużycie całkowitej ilości pamięci ponad 1 MB. Z tego powodu Unikaj tworzenia typów możliwych do serializacji, które może spowodować zmniejszenie zużycia pamięci znaczących bez dużą ilość przychodzących danych. Na przykład kontraktu danych "MyContract" z polami elementu członkowskiego 50 opcjonalnymi danymi i dodatkowe 100 pól prywatnych mogła zostać utworzona z konstrukcji XML "\<MyContract / >". Powoduje to XML w pamięci, do której uzyskuje dostęp do pola 150. Należy pamiętać, że elementy członkowskie danych są opcjonalne domyślnie. Problem jest rozliczana, jeśli taki typ jest częścią tablicy.  
  
 `MaxReceivedMessageSize`samodzielnie nie jest wystarczająco przed atakami typu "odmowa usługi" wszystkie. Na przykład Deserializator może wymusić rozszeregować wykresu obiektu głęboko zagnieżdżone (obiekt, który zawiera inny obiekt, który zawiera jeszcze inną i tak dalej) komunikatu przychodzącego. Zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> wywoływać metod w sposób zagnieżdżony do deserializacji takie wykresy. Głębokiego zagnieżdżenia wywołań metody mogą spowodować nieodwracalny <xref:System.StackOverflowException>. To zagrożenie jest skorygowane przez ustawienie <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> przydziału, aby ograniczyć poziom zagnieżdżenia XML, zgodnie z opisem w sekcji "Przy użyciu bezpiecznie XML" w dalszej części tematu.  
  
 Ustawianie przydziałów dodatkowe `MaxReceivedMessageSize` jest szczególnie ważne w przypadku przy użyciu kodowania binarnego XML. Przy użyciu kodowania binarnego odpowiada nieco kompresji: dla niewielkiej liczby bajtów w komunikacie przychodzącym może reprezentować dużą ilość danych. W związku z tym nawet komunikat dopasowane do `MaxReceivedMessageSize` limit może trwać znacznie większej ilości pamięci w postaci rozwinięty. Ograniczających zagrożenia takie specyficzne dla XML, wszystkie przydziały czytnika XML muszą być ustawione poprawnie, zgodnie z opisem w sekcji "Przy użyciu bezpiecznie XML" w dalszej części tego tematu.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Ograniczanie zużycia pamięci z przesyłania strumieniowego  
 Podczas przesyłania strumieniowego, mogą używać małych `MaxReceivedMessageSize` ustawienie, aby zapewnić ochronę przed atakami typu "odmowa usługi". Jednak bardziej złożonych zadań są możliwe w przypadku przesyłania strumieniowego. Na przykład usługi przekazywania plików akceptuje pliki o rozmiarze większym niż całą dostępną pamięć. W takim przypadku należy ustawić `MaxReceivedMessageSize` bardzo dużą wartość oczekiwano, że prawie żadne dane są buforowane w pamięci i komunikat strumieni bezpośrednio na dysku. Jeśli jakiś sposób wymusić niebezpieczną wiadomość [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do buforu danych zamiast przesyłania strumieniowego w takim przypadku `MaxReceivedMessageSize` nie chroni przed komunikat podczas uzyskiwania dostępu do całej dostępnej pamięci.  
  
 Aby osłabić to zagrożenie, istnieją ustawienia określonego limitu przydziału o różnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składników przetwarzania danych, które ograniczyć buforowania. Najważniejsze z nich jest `MaxBufferSize` właściwości na różne elementy powiązania transportu i standardowe powiązania. Podczas przesyłania strumieniowego, należy ustawić ten limit przydziału, biorąc pod uwagę maksymalną ilość pamięci, którą można przydzielić na jeden komunikat. Jak `MaxReceivedMessageSize`, ustawienie wstawiają absolutny zużycie pamięci, ale tylko ogranicza ją do wewnątrz stały wskaźnik. Ponadto jako z `MaxReceivedMessageSize`, należy pamiętać o możliwości wiele komunikatów przetwarzanych jednocześnie.  
  
### <a name="maxbuffersize-details"></a>Szczegóły MaxBufferSize  
 `MaxBufferSize` Właściwość ogranicza buforowanie dowolnego zbiorczego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze buforuje nagłówki SOAP i błędach SOAP, a także żadnych części MIME się nie być w kolejności odczytywania fizycznych w komunikat mechanizmu optymalizacji transmisji wiadomości (MTOM). To ustawienie pozwala ograniczyć ilość buforowanie we wszystkich tych przypadkach.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Rozwiązanie to przekazywanie `MaxBufferSize` wartość różne składniki, które mogą buforować. Na przykład niektóre <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> overloads z <xref:System.ServiceModel.Channels.Message> podjęcia klasy `maxSizeOfHeaders` parametru. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]przekazuje `MaxBufferSize` wartość tego parametru, aby ograniczyć ilość buforowanie nagłówka SOAP. Ważne jest, aby ustawić wartość tego parametru, gdy usługi <xref:System.ServiceModel.Channels.Message> bezpośrednio klasa. Ogólnie, gdy składnik w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pobierającej parametry przydziału, ważne jest, aby zrozumieć ryzyko związane z tych parametrów i poprawnie ustawiona.  
  
 Koder komunikatu MTOM ma również `MaxBufferSize` ustawienie. Podczas korzystania z wiązania standardowa, to ma wartość automatycznie na poziomie transportu `MaxBufferSize` wartość. Jednak podczas tworzenia niestandardowego powiązania za pomocą elementu powiązania koder komunikatu MTOM, ważne jest, aby ustawić `MaxBufferSize` jest używana właściwość na wartość bezpieczne podczas przesyłania strumieniowego.  
  
## <a name="xml-based-streaming-attacks"></a>Oparte na języku XML ataków przesyłania strumieniowego  
 `MaxBufferSize`samodzielnie nie wystarcza do zapewnienia, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie można wymusić do buforowania, gdy przesyłania strumieniowego. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] czytników XML zawsze buforu całego tagu początkowym elementu XML podczas uruchamiania odczytać nowego elementu. Można to zrobić, aby poprawnie przetworzyć obszary nazw i atrybuty. Jeśli `MaxReceivedMessageSize` jest skonfigurowana za duży (na przykład, aby włączyć dużego pliku bezpośrednio do dysku przesyłania strumieniowego scenariusz), niebezpiecznej wiadomości mogą być zbudowane z treści cały komunikat w przypadku dużych tagu początkowym elementu XML. Próba odczytu go powoduje <xref:System.OutOfMemoryException>. Jest to jedna z wielu opartych na języku XML typu "odmowa usługi" ataki których wszystkie można zminimalizować przy użyciu przydziały czytnika XML, omówionych w sekcji "Przy użyciu bezpiecznie XML" w dalszej części tego tematu. Podczas przesyłania strumieniowego, jest szczególnie ważne wszystkie te przydziały.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Mieszanie przesyłania strumieniowego i buforowanie modele programowania  
 Wiele możliwych ataków wynikają z mieszanie przesyłania strumieniowego i strumieniowo modele programowania, w tej samej usługi. Załóżmy, że istnieje kontraktu usługi z dwóch operacji: wyższy <xref:System.IO.Stream> i inny pobiera tablicę pewnego typu niestandardowego. Załóżmy również, że `MaxReceivedMessageSize` jest ustawiona na dużą wartość umożliwiające pierwszej operacji przetwarzania dużych strumieni. Niestety oznacza to, że dużych wiadomości mogą teraz być wysyłane do druga operacja również i Deserializator danych buforów w pamięci jako tablica przed wywołaniem operacji. Jest to potencjalny atak typu "odmowa usługi": `MaxBufferSize` limitu przydziału nie istnieje limit rozmiaru treści wiadomości, czyli Deserializator współpracuje z.  
  
 Z tego powodu należy unikać mieszanie operacje na podstawie strumienia i strumieniowo w tym samym kontrakcie. Należy bezwzględnie mieszać dwa modele programowania, należy użyć następujących kroków:  
  
-   Wyłącz <xref:System.Runtime.Serialization.IExtensibleDataObject> funkcji przez ustawienie <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> właściwość <xref:System.ServiceModel.ServiceBehaviorAttribute> do `true`. Dzięki temu, że rozszeregować są tylko elementy członkowskie, które są częścią kontraktu.  
  
-   Ustaw <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> właściwość <xref:System.Runtime.Serialization.DataContractSerializer> bezpieczne wartości. Ten przydział jest również dostępna w <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu lub przy użyciu konfiguracji. Ten limit przydziału ogranicza liczbę obiektów, które są rozszeregować w jednym epizodu deserializacji. Zwykle każda operacja parametru lub wiadomości część treści kontraktu komunikatu jest rozszeregować w jeden odcinek. Podczas deserializacji tablic, każdego wpisu tablicy jest traktowany jako oddzielny obiekt.  
  
-   Ustaw wszystkie przydziały czytnika XML bezpieczne wartości. Należy zwrócić uwagę na <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, i <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> i uniknąć ciągów w operacjach strumieniowo.  
  
-   Przejrzyj listę znanych typów, z uwzględnieniem, że jeden z nich można wdrożyć w dowolnym momencie (zobacz sekcję "Uniemożliwia niezamierzone typy z ładowany" w dalszej części tego tematu).  
  
-   Nie używaj żadnych typów, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który buforu dużą ilość danych. Nie dodawaj takich typów do listy znanych typów.  
  
-   Nie używaj <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> tablic, <xref:System.Byte> stałych lub typy, które implementują <xref:System.Runtime.Serialization.ISerializable> w umowie.  
  
-   Nie używaj <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> tablic, <xref:System.Byte> stałych lub typy, które implementują <xref:System.Runtime.Serialization.ISerializable> listy znanych typów.  
  
 Zastosuj poprzednich kroków, gdy operacja strumieniowo używa <xref:System.Runtime.Serialization.DataContractSerializer>. Nigdy nie łączyć przesyłania strumieniowego i programowania strumieniowo modeli na tej samej usługi, jeśli używasz <xref:System.Xml.Serialization.XmlSerializer>, ponieważ nie ma ochrony <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> przydziału.  
  
### <a name="slow-stream-attacks"></a>Ataki wolne strumienia  
 Klasa przesyłania strumieniowego ataków typu "odmowa usługi" nie jest związana zużycie pamięci. Zamiast tego ataku obejmuje powolne nadawcy lub odbiornika danych. Podczas oczekiwania na dane do wysłania lub odebrania, wyczerpania zasobów, takich jak dostępnych połączeń i wątków. Taka sytuacja może powstać wyniku złośliwymi atakami lub z wiarygodnego nadawcy/odbiorcy w powolne połączenie sieciowe.  
  
 Aby uniknąć tego rodzaju ataki, prawidłowo limity czasu transportu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Transportu przydziały](../../../../docs/framework/wcf/feature-details/transport-quotas.md). Po drugie, nigdy nie używaj synchroniczne `Read` lub `Write` operacji podczas pracy ze strumieni w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-xml-safely"></a>Bezpiecznie za pomocą XML  
  
> [!NOTE]
>  Mimo że ta sekcja opisuje XML informacje mają zastosowanie również do dokumentów JavaScript Object Notation (JSON). Przydziały działają podobnie, za pomocą [mapowanie między formatami JSON i XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>Zabezpieczanie czytników XML  
 XML typu infoset sprawdzonych podstawą przetwarzania komunikatu w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Gdy istnieje odbierać dane XML z niezaufanego źródła, kilka możliwości ataku typu "odmowa usługi" który musi skorygowane. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zawiera specjalne, bezpieczne czytników XML. Czytniki te są tworzone automatycznie podczas przy użyciu jednej z standardowe kodowania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (tekst, binary lub MTOM).  
  
 Niektóre z funkcji zabezpieczeń na tych czytników zawsze są aktywne. Na przykład czytników nigdy nie przetworzył definicji typu dokumentu (pliki DTD), które są źródłem potencjalnych ataków typu "odmowa usługi" i nigdy nie powinna być widoczna w uzasadnionych wiadomości SOAP. Inne funkcje zabezpieczeń obejmują przydziały czytnika, które muszą być skonfigurowane, które zostały opisane w poniższej sekcji.  
  
 Podczas pracy bezpośrednio z czytników XML (takich jak podczas pisania niestandardowego kodera lub podczas pracy bezpośrednio z <xref:System.ServiceModel.Channels.Message> klasy), należy zawsze używać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczania czytników, gdy istnieje ryzyko, pracy z niezaufanych danych. Tworzenie bezpiecznej czytników przez wywoływania statycznych fabryki przeciążenia metody <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> na <xref:System.Xml.XmlDictionaryReader> klasy. Podczas tworzenia modułu odczytującego, podaj wartości bezpiecznych zasobów. Nie wywołuj `Create` przeciążenia metody. Nie twórz te [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] czytnika. Zamiast tego czytnika jest tworzony, który nie jest chroniony przez funkcje zabezpieczeń opisanych w tej sekcji.  
  
### <a name="reader-quotas"></a>Przydziały czytnika  
 Bezpieczne czytników XML ma pięć można konfigurować przydziały. Te są zwykle konfigurowane za pomocą `ReaderQuotas` właściwości na elementy powiązania kodowania lub standardowe powiązania lub przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas> podczas tworzenia modułu odczytującego został przekazany pusty obiekt.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Ten limit przydziału ogranicza liczbę bajtów, które są odczytywane w jednej `Read` operacji podczas odczytywania elementu start tagu i jego atrybuty. (W przypadku strumieniowo, nazwa elementu jest pomijany względem limitu przydziału.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> jest istotne z następujących powodów:  
  
-   Nazwy elementu i jego atrybuty zawsze są buforowane w pamięci, gdy są odczytywane. Dlatego jest ważne, aby ustawić ten limit przydziału prawidłowo w trybie, aby uniknąć nadmiernego buforowania, gdy przesyłania strumieniowego strumieniowym. Zobacz `MaxDepth` przydziału sekcji informacji o rzeczywista ilość buforowanie ma miejsce.  
  
-   O zbyt wiele atrybutów XML posłużyć nieproporcjonalnie czasu przetwarzania ponieważ nazwy atrybutów muszą być sprawdzane pod kątem unikatowości. `MaxBytesPerRead`zmniejsza zagrożenie tego typu.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Ten limit przydziału ogranicza maksymalną głębokość zagnieżdżenia elementów XML. Na przykład dokument "\<A >\<B >\<C / >\</B >\</A >" głębokość zagnieżdżenia trzech. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>ważne jest, z następujących powodów:  
  
-   `MaxDepth`współdziała z `MaxBytesPerRead`: czytnik zawsze przechowuje dane w pamięci dla bieżącego elementu i wszystkich jego obiektów nadrzędnych, więc zużycie pamięci maksymalnej czytnika danych jest proporcjonalny do wyniku te dwa ustawienia.  
  
-   Podczas deserializacji wykresu obiektu głęboko zagnieżdżone, Deserializator wymusza na dostęp do całego stosu i zgłosić nieodwracalny <xref:System.StackOverflowException>. Bezpośrednie korelacji istnieje między zagnieżdżenia XML i zagnieżdżenia obiektu dla obu <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>. Użyj `MaxDepth` Aby osłabić to zagrożenie.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Ten limit przydziału ogranicza rozmiar czytelnika *niepowtarzającymi*. Niepowtarzającymi zawiera niektóre ciągi (takie jak obszary nazw i prefiksy) napotkanych podczas przetwarzania dokumentu XML. Jak te ciągi są buforowane w pamięci, należy ustawić ten limit przydziału, aby uniknąć nadmiernego buforowania, gdy przesyłania strumieniowego.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Ten limit przydziału ogranicza maksymalny rozmiar ciągu zwracające modułu odczytującego XML. Ten limit przydziału nie ogranicza zużycie pamięci w samej modułu odczytującego XML, ale w składniku korzystający z czytnika. Na przykład, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczone przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, nie wykonać deserializacji ciągów przekracza ten limit przydziału. Korzystając z <xref:System.Xml.XmlDictionaryReader> bezpośrednio, klasa nie wszystkie metody względem ten limit przydziału, ale tylko metody, które są specjalnie zaprojektowane do odczytu ciągów, takich jak <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> metody. <xref:System.Xml.XmlReader.Value%2A> Właściwość czytnik nie ma wpływu na ten limit przydziału i w związku z tym nie należy używać podczas ochrony zawiera ten przydział jest konieczne.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Ten limit przydziału ogranicza maksymalny rozmiar to tablica wartości pierwotnych, które zwraca modułu odczytującego XML, łącznie z tablic bajtowych. Ten limit przydziału nie ogranicza zużycie pamięci w samej modułu odczytującego XML, ale niezależnie od składnika korzystający z czytnika. Na przykład, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> używa czytnika zabezpieczone przy użyciu <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, nie wykonać deserializacji tablice typu byte przekracza ten limit przydziału. Należy ustawić ten limit przydziału, podczas próby mieszać modele programowania przesyłania strumieniowego i buforowane w jednej umowy. Należy pamiętać, że przy użyciu <xref:System.Xml.XmlDictionaryReader> klas, metod, które są specjalnie zaprojektowane do odczytu tablice dowolnego rozmiar niektórych typów pierwotnych, takich jak <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, przestrzegać tego limitu przydziału.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>Zagrożenia specyficzne dla kodowania binarnego  
 Kodowanie binarne XML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje obejmuje *słownika ciągów* funkcji. Ciąg dużych może zostać zakodowany przy użyciu tylko kilka bajtów. Włącza znaczący wzrost wydajności, ale wprowadza nowych zagrożeń typu "odmowa usługi", które muszą zostać skorygowane.  
  
 Istnieją dwa rodzaje słowniki: *statycznych* i *dynamiczne*. Słowniku statycznym przedstawiono listę wbudowanych długich ciągów, które mogą być reprezentowane przy użyciu krótkich kodu przy użyciu kodowania binarnego. Ta lista ciągów zostanie rozwiązany, gdy czytnik jest tworzony i nie może być modyfikowany. Brak ciągów w słowniku statycznym który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa domyślnie są wystarczająco duże stwarzać poważne zagrożenie typu "odmowa usługi", mimo że nadal mogą ich używać w atak słownikowy rozszerzenia. W zaawansowanych scenariuszach, w którym podać własne słowniku statycznym należy zachować ostrożność, wprowadzając Duży słownik ciągów.  
  
 Funkcja dynamicznej słowniki pozwala definiować własne ciągów i skojarzyć je z krótkich kodów. Te mapowania kod ciągu są przechowywane w pamięci podczas sesji całej komunikacji kolejne komunikaty nie trzeba ponownie wysłać ciągi i może korzystać z kodów, które zostały już zdefiniowane. Te parametry mogą być o dowolnej długości i w związku z tym stanowiących zagrożenie poważniejsze niż w słowniku statycznym.  
  
 Pierwszy zagrożenie, które muszą zostać skorygowane, jest możliwość dynamiczny słownik (tabeli mapowania kod ciągu) za duży. W ciągu kilku wiadomości, można rozwinąć ten słownik i dlatego element `MaxReceivedMessageSize` przydziału oferuje nie ochrony, ponieważ jest stosowany tylko do każdej wiadomości osobno. W związku z tym oddzielnej <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> właściwość istnieje na <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , która ogranicza rozmiar słownika.  
  
 W przeciwieństwie do większości innych przydziały ten przydział ma również zastosowanie podczas zapisywania wiadomości. Jeśli zostanie przekroczony limit podczas czytania wiadomości, `QuotaExceededException` jest zgłaszany w zwykły sposób. Jeśli zostanie przekroczony limit podczas pisania wiadomości, wszelkie ciągi, które spowodować przekroczenie limitu przydziału są zapisywane jako — jest bez korzystania z funkcji dynamicznego słownika.  
  
### <a name="dictionary-expansion-threats"></a>Słownik rozszerzenia zagrożeń  
 Znaczące klasy specyficzne dla danych binarnych ataków wynika z rozszerzenia słownika. Mała wiadomości w formacie binarnym może przekształcić w bardzo dużych komunikatów w postaci tekstowej rozwinięty Jeśli zwiększone użycie funkcji słowniki ciągu. Współczynnik rozszerzania dla ciągów dynamiczny słownik jest ograniczona przez <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> przydziału, ponieważ ciąg dynamiczny słownik nie przekracza maksymalny rozmiar całego słownika.  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, I `MaxArrayLength` właściwości jedynie ograniczyć zużycie pamięci. Zwykle nie są wymagane ograniczających wszelkie zagrożenia wykorzystania strumieniowo, ponieważ użycie pamięci jest już ograniczone przez `MaxReceivedMessageSize`. Jednak `MaxReceivedMessageSize` liczby bajtów wstępne rozszerzenia. Podczas kodowania binarnego jest używany, użycie pamięci może potencjalnie wykracza poza `MaxReceivedMessageSize`, jest ograniczona tylko przez współczynnik <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Dlatego jest ważne, aby zawsze ustawić wszystkie przydziały czytnika (szczególnie <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) przy użyciu kodowania binarnego.  
  
 Korzystając z kodowanie binarne razem z <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` precyzyjnym interfejsu do zainstalowania na ataki słownikowe rozszerzenia. Ten interfejs zasadniczo zapewnia nieograniczony magazyn dla dowolne dane, które nie jest częścią kontraktu. Jeśli przydziały nie można ustawić na tyle niskie, tak, aby `MaxSessionSize` pomnożona przez `MaxReceivedMessageSize` nie stanowić problem, wyłącz `IExtensibleDataObject` funkcji przy użyciu kodowania binarnego. Ustaw `IgnoreExtensionDataObject` właściwości `true` na `ServiceBehaviorAttribute` atrybutu. Możesz też implementuje `IExtensibleDataObject` interfejsu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Podsumowanie przydziałów  
 W poniższej tabeli przedstawiono wskazówki dotyczące przydziałów.  
  
|Warunek|Przydziały ważne, aby ustawić|  
|---------------|-----------------------------|  
|Brak przesyłania strumieniowego lub przesyłania strumieniowego małych komunikatów, tekst lub kodowanie MTOM|`MaxReceivedMessageSize`, `MaxBytesPerRead`, i`MaxDepth`|  
|Kodowanie nie przesyłania strumieniowego lub przesyłania strumieniowego małych komunikatów binarnych|`MaxReceivedMessageSize`, `MaxSessionSize`, a wszystkie`ReaderQuotas`|  
|Przesyłanie strumieniowe dużych wiadomości, tekst lub kodowanie MTOM|`MaxBufferSize`i wszystkie`ReaderQuotas`|  
|Kodowanie transmisji strumieniowej dużych wiadomości, binarne|`MaxBufferSize`, `MaxSessionSize`, a wszystkie`ReaderQuotas`|  
  
-   Limity czasu poziomu transportu zawsze musi być ustawiona i nigdy nie używaj synchroniczne odczyt/zapis podczas przesyłania strumieniowego jest w użyciu, niezależnie od tego, czy strumieniowo duże lub małe wiadomości.  
  
-   W razie wątpliwości dotyczące limit przydziału, należy ustawić na wartość bezpieczne, a nie pozostawić go otwórz.  
  
## <a name="preventing-malicious-code-execution"></a>Uniemożliwia wykonanie złośliwego kodu  
 Następujące klasy ogólne zagrożeń można wykonać kod i niezamierzone skutki:  
  
-   Deserializator ładuje typ złośliwego, niebezpieczne lub istotnych dla zabezpieczeń.  
  
-   Komunikat przychodzący powoduje deserializacji do utworzenia wystąpienia typu zwykle bezpieczne w taki sposób, który ma niezamierzone skutki.  
  
 W poniższych sekcjach omówiono te klasy dalsze zagrożeń.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Aby uzyskać informacje o zabezpieczeniach <xref:System.Xml.Serialization.XmlSerializer>, zobacz stosowną dokumentację.) Model zabezpieczeń <xref:System.Xml.Serialization.XmlSerializer> jest podobny do <xref:System.Runtime.Serialization.DataContractSerializer>i różni się głównie w szczegółach. Na przykład <xref:System.Xml.Serialization.XmlIncludeAttribute> atrybut służy do włączenia typu zamiast <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu. Jednak niektóre zagrożenia unikatowe dla <xref:System.Xml.Serialization.XmlSerializer> zostały omówione w dalszej części tego tematu.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>Uniemożliwia niezamierzone typów ładowany  
 Podczas ładowania typów niezamierzone może mieć znaczący wpływ, czy typ jest złośliwe lub po prostu ma efekty uboczne istotnych dla zabezpieczeń. Typem może zawierać luki w zabezpieczeniach kończona, akcje dotyczące zabezpieczeń w jego konstruktora lub konstruktora klasy, ma wpływ dużej ilości pamięci, który ułatwia ataków typu "odmowa usługi" lub może zgłaszać wyjątki nieodwracalny. Typy mogą mieć konstruktorów klas, uruchamiane natychmiast po załadowaniu typ i przed utworzeniem wystąpienia. Z tego względu należy kontrolować zestaw typów, które mogą ładować deserializacji.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Deserializuje w sposób luźno powiązanych. Nigdy nie odczytuje wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR), typ i zestaw nazwy z przychodzących danych. Jest to podobne do zachowania <xref:System.Xml.Serialization.XmlSerializer>, ale różni się od zachowania <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Luźne powiązanie wprowadza bezpieczeństwo, ponieważ zdalnej osobie atakującej nie może wskazywać dowolnego typu do ładowania tylko za pomocą nazw tego typu w komunikacie.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Będzie można załadować typu, który obecnie jest oczekiwany zgodnie z umową. Na przykład, jeśli element członkowski danych typu kontraktu danych `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> mogą ładować `Customer` typu po jego deserializuje ten element członkowski danych.  
  
 Ponadto <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje polimorfizm. Element członkowski danych może być zadeklarowana jako <xref:System.Object>, ale może zawierać danych przychodzących `Customer` wystąpienia. Jest to możliwe tylko wtedy, gdy `Customer` typu złożonego "znane" do deserializacji za pomocą jednego z tych mechanizmów:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute>Atrybut zastosowany do typu.  
  
-   `KnownTypeAttribute`atrybut określający metodę, która zwraca listę typów.  
  
-   `ServiceKnownTypeAttribute`atrybut.  
  
-   `KnownTypes` Sekcji konfiguracji.  
  
-   Lista znanych typów jawnie przekazany do <xref:System.Runtime.Serialization.DataContractSerializer> podczas konstruowania, jeśli bezpośrednio przy użyciu serializatora.  
  
 Każdy z tych mechanizmów zwiększa prawdopodobieństwo dzięki zastosowaniu więcej typów, które można załadować deserializacji. Kontrolować każdy z tych mechanizmów, aby upewnić się, że żadne typy złośliwego bądź niepożądanego zostaną dodane do listy znanych typów.  
  
 Po znanego typu w zakresie mogą być ładowane w dowolnym momencie i można było utworzyć wystąpienia typu, nawet wtedy, gdy kontrakt jest zabronione jest używana. Załóżmy na przykład, "MyDangerousType" zostanie dodany do listy znanych typów, za pomocą jednego z powyższych mechanizmów typu. Oznacza to, że:  
  
-   `MyDangerousType`jest załadowany i jego uruchomieniem konstruktora klasy.  
  
-   Nawet w przypadku deserializacji kontraktu danych z elementem członkowskim danych ciąg, niebezpiecznej wiadomości mogą spowodować wystąpienie `MyDangerousType` do utworzenia. Kod w `MyDangerousType`, takich jak metody ustawiające właściwości, może uruchomić. Po zakończeniu Deserializator spróbuje przypisać do elementu członkowskiego danych ciągu tego wystąpienia i zakończyć się niepowodzeniem z powodu wyjątku.  
  
 Podczas zapisywania metodę, która zwraca listy znanych typów lub podczas przekazywania bezpośrednio do listy <xref:System.Runtime.Serialization.DataContractSerializer> konstruktora, upewnij się, że kod, który przygotowuje listy jest bezpieczna i działa tylko z zaufanych danych.  
  
 Określanie typów znane w konfiguracji, upewnij się, że plik konfiguracji jest bezpieczne. Zawsze używać silnych nazw w konfiguracji (przez określenie podpisem zestawu, w którym znajduje się typ klucza publicznego), ale nie określono wersji typu do załadowania. Moduł ładujący typ wybiera automatycznie najnowszą wersję, jeśli to możliwe. Jeśli określisz określonej wersji w konfiguracji, uruchom następujące ryzyka: typ może mieć luki w zabezpieczeniach mogą rozwiązany w przyszłej wersji, ale wersja nadal ładuje, ponieważ został on jawnie określony w konfiguracji.  
  
 O zbyt wiele znanych typów ma inny konsekwencji: <xref:System.Runtime.Serialization.DataContractSerializer> tworzy pamięć podręczną kodu serializacji/deserializacji w domenie aplikacji, wpis dla każdego typu musi serializacji i deserializacji. Ta pamięć podręczna nie jest wyczyszczone, tak długo, jak działa domeny aplikacji. W związku z tym osoba atakująca, która rozpoznaje, że aplikacja używa wielu znanych typów może spowodować deserializacji te typy, co powoduje pamięci podręcznej, aby wymagać nieproporcjonalnie dużej ilości pamięci.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>Uniemożliwia typy są w stanie niezamierzone  
 Typ może mieć ograniczenia wewnętrznego sprawdzania spójności, które muszą zostać wymuszone. Należy uważać, aby uniknąć dzielenia tych warunków ograniczających podczas deserializacji.  
  
 Poniższy przykład typu reprezentuje stan śluzę na kosmicznego i wymusza ograniczenia, że zarówno wewnętrzne i zewnętrzne drzwi nie może zostać otwarty w tym samym czasie.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Osoba atakująca może wysłać złośliwy komunikat podobny do tego, poruszania się ograniczenia i uzyskanie obiektu w nieprawidłowym stanie, który może mieć konsekwencje niepożądanych i nieprzewidywalnych.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Można uniknąć tej sytuacji jest uwagę na następujące kwestie:  
  
-   Gdy <xref:System.Runtime.Serialization.DataContractSerializer> deserializuje większość klas, konstruktory nie uruchamiaj. W związku z tym nie należy polegać na wszelkie zarządzanie stanem wykonane w konstruktorze.  
  
-   Wywołania zwrotne umożliwia upewnij się, że obiekt jest w nieprawidłowym stanie. Wywołanie zwrotne oznaczonych <xref:System.Runtime.Serialization.OnDeserializedAttribute> atrybut jest szczególnie przydatne, ponieważ jest uruchamiana po deserializacji została zakończona i możliwością Sprawdź i popraw ogólny stan. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Typy kontraktu danych zależą od określonej kolejności, w którym właściwość można wywołać metody ustawiające nie projektów.  
  
-   Zajmie się przy użyciu starsze typy oznaczone <xref:System.SerializableAttribute> atrybutu. Wiele z nich zostały zaprojektowane do pracy z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] usług zdalnych dla tylko zaufane danych. Istniejące typy z tym atrybutem może nie zostały zaprojektowane bezpieczeństwa stanu pamiętać.  
  
-   Nie należy polegać na <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość `DataMemberAttribute` atrybutu, aby zagwarantować obecności danych w zakresie, w jakim stanie bezpieczeństwa. Dane można zawsze być `null`, `zero`, lub `invalid`.  
  
-   Nigdy nie zaufania wykres obiektu rozszeregować ze źródła danych niezaufanych bez najpierw sprawdzania poprawności. Poszczególnych obiektów może być w stanie spójności, ale wykres obiektu jako całość może nie być. Ponadto nawet po wyłączeniu trybu konserwacji obiektu wykresu zdeserializowany wykresu może mieć wiele odwołań do tego samego obiektu lub zawierać odwołań cyklicznych. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>Bezpieczny sposób za pomocą NetDataContractSerializer  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> Jest aparatem serializacji, który używa ścisłej sprzężenia do typów. Jest to podobne do <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Oznacza to, określa typ do utworzenia wystąpienia odczytując [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Nazwa zestawu i typu danych przychodzących. Chociaż jest częścią [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nie istnieje sposób podany o podłączenie aparatu tej serializacji; musi być napisana kodu niestandardowego. `NetDataContractSerializer` Podano przede wszystkim do jej obsługi ułatwiają migrację z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w odpowiedniej sekcji [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Ponieważ komunikatu może wskazywać, mogą być ładowane dowolnego typu, <xref:System.Runtime.Serialization.NetDataContractSerializer> mechanizm jest z założenia niezabezpieczone i powinien być używany tylko z zaufanych danych. Można zabezpieczyć pisząc integratora typu bezpiecznego, ograniczenie typu umożliwiający tylko bezpiecznych typy załadować (przy użyciu <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> właściwości).  
  
 Nawet wtedy, gdy jest używany z zaufanych danych, danych przychodzących niewystarczająco może określać typ obciążenia, zwłaszcza, jeśli <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> właściwość jest ustawiona na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Każda osoba mająca dostęp do katalogu aplikacji lub do globalnej pamięci podręcznej zestawów można zastąpić typu złośliwego zamiast ten, który powinien załadować. Zawsze zapewnienia bezpieczeństwa katalogu aplikacji i Globalna pamięć podręczna zestawów poprawnie ustawiając uprawnienia.  
  
 Ogólnie, jeśli zezwolisz na dostęp częściowo zaufany kod do Twojej `NetDataContractSerializer` wystąpienia lub inny sposób kontroluje selektora dwuskładnikowego (<xref:System.Runtime.Serialization.ISurrogateSelector>) lub wiążącego serializacji (<xref:System.Runtime.Serialization.SerializationBinder>), kod może wykonywać wiele kontroli nad proces serializacji/deserializacji. Na przykład go może wstrzyknąć arbitralnie wybrane typy, spowodować ujawnienie informacji, manipulowanie wynikowy wykres obiektu lub dane serializowane lub przepełnienie wynikowe strumieniu serializowanym.  
  
 Inny problem z zabezpieczeniami `NetDataContractSerializer` jest odmowę usługi, nie zagrożenie wykonanie złośliwego kodu. Korzystając z `NetDataContractSerializer`zawsze ustaw <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> przydziału do bezpiecznego wartość. Jest łatwy do skonstruowania wiadomość złośliwego małych przydziela tablicę obiektów, którego rozmiar jest ograniczona tylko przez ten limit przydziału.  
  
### <a name="xmlserializer-specific-threats"></a>Zagrożenia specyficzne dla elementu XmlSerializer  
 <xref:System.Xml.Serialization.XmlSerializer> Model zabezpieczeń jest podobny do <xref:System.Runtime.Serialization.DataContractSerializer>. Jednak kilka zagrożenia są unikatowe dla <xref:System.Xml.Serialization.XmlSerializer>.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Generuje *zestawów serializacji* w czasie wykonywania, która zawiera kod, który faktycznie serializuje i deserializuje; te zestawy są tworzone w katalogu plików tymczasowych. Jeśli inny proces lub użytkownik nie ma praw dostępu do tego katalogu, ich może zastąpić kod serializacji/deserializacji dowolnego kodu. <xref:System.Xml.Serialization.XmlSerializer> Następnie uruchamia ten kod przy użyciu jego kontekstu zabezpieczeń, zamiast kodu serializacji/deserializacji. Upewnij się, że uprawnienia zostały poprawnie skonfigurowane w katalogu plików tymczasowych do temu zapobiec.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Ma również tryb, w którym używa zestawów serializacji wstępnie wygenerowane zamiast generować je w czasie wykonywania. Ten tryb jest wyzwalane, gdy <xref:System.Xml.Serialization.XmlSerializer> można znaleźć zestawu serializacji odpowiedni. <xref:System.Xml.Serialization.XmlSerializer> Sprawdza, czy zestaw serializacji został podpisany przez tego samego klucza, który został użyty do podpisania zestawu, który zawiera typy serializowana. To zapewnia ochronę z zestawów złośliwego są ukryte jako zestawy serializacji. Jednak jeśli zestaw, który zawiera typy z możliwością serializowania nie jest podpisany, <xref:System.Xml.Serialization.XmlSerializer> nie sprawdzaj i korzysta z żadnych zestawów z poprawną nazwę. Umożliwia uruchamianie złośliwego kodu. Zawsze podpisują zestawy, które zawierają typy z możliwością serializowania lub ściśle kontroli dostępu do katalogu aplikacji i Globalna pamięć podręczna zestawów do zapobiegania wprowadzeniu złośliwego zestawów.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Mogą podlegać typu "odmowa usługi". <xref:System.Xml.Serialization.XmlSerializer> Nie ma `MaxItemsInObjectGraph` przydziału (co jest dostępne na <xref:System.Runtime.Serialization.DataContractSerializer>). W związku z tym go deserializuje dowolnej liczby obiektów ograniczona tylko rozmiar komunikatu.  
  
### <a name="partial-trust-threats"></a>Zagrożenia częściowej relacji zaufania  
 Należy zwrócić uwagę następujące kwestie dotyczące zagrożenia związane z kodem uruchomiony z częściowa relacja zaufania. Zagrożenia te obejmują złośliwy kod częściowo zaufany, a także złośliwy kod częściowo zaufany w połączeniu z innymi ataki (na przykład częściowo zaufany kod, który tworzy określony ciąg znaków, a następnie podczas deserializacji).  
  
-   Podczas korzystania z żadnych składników serializacji, nigdy nie assert żadnych uprawnień przed takie użycia, nawet jeśli scenariusz całego serializacji jest w zakresie sieci assert i nie mamy do czynienia z niezaufanych danych lub obiektów. Takie użycie może prowadzić do luk w zabezpieczeniach.  
  
-   W przypadkach, gdy częściowo zaufany kod ma kontroli nad procesem serializacji, za pomocą punktów rozszerzalności (surogatów), typy serializowana, lub w inny sposób częściowo zaufany kod może spowodować serializatora do wyjściowego dużą ilość dane w serializowanym strumieniu, co może spowodować przeprowadzenie ataku typu "odmowa usługi" (DoS) do odbiornika tego strumienia. Jeśli są serializacji danych przeznaczonych dla obiektu docelowego, który jest wielkość liter na zagrożenia systemu DoS, nie serializował typów, częściowo zaufanych lub w przeciwnym razie powiadomienie częściowo zaufany kod sterowania serializacji.  
  
-   Jeśli zezwolisz na dostęp częściowo zaufany kod do Twojej <xref:System.Runtime.Serialization.DataContractSerializer> wystąpienia lub w inny sposób kontroluje [surogaty kontraktu danych](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), może wykonywać wiele kontroli nad procesem serializacji/deserializacji. Na przykład go może wstrzyknąć arbitralnie wybrane typy, spowodować ujawnienie informacji, manipulowanie wynikowy wykres obiektu lub dane serializowane lub przepełnienie wynikowe strumieniu serializowanym. Odpowiednik <xref:System.Runtime.Serialization.NetDataContractSerializer> zagrożenie jest opisany w sekcji "Przy użyciu NetDataContractSerializer bezpiecznie".  
  
-   Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do typu (lub typ jest oznaczony jako `[Serializable]` , ale nie jest `ISerializable`), Deserializator można utworzyć wystąpienia takiego typu, nawet jeśli wszystkie konstruktorów niepublicznego lub chronione przez żądania.  
  
-   Nigdy nie ufać wyniku deserializacji, chyba że dane do zdeserializowania jest zaufany, a masz pewność, że wszystkie znane typy są typy, którym ufasz. Należy pamiętać, że znanych typów nie są ładowane z pliku konfiguracji aplikacji, (a zostaną załadowane z pliku konfiguracji komputera) podczas uruchamiania w częściowej relacji zaufania.  
  
-   W przypadku przekazania `DataContractSerializer` wystąpienia z surogatu dodane do częściowo zaufany kod kod można zmienić ustawienia można modyfikować w tym dwuskładnikowego.  
  
-   Dla obiektu po deserializacji Jeśli modułu odczytującego XML (lub dane tam) jest dostarczany z częściowo zaufanego kodu zdeserializowany obiekt wynikowy należy traktować jako niezaufanych danych.  
  
-   Fakt który <xref:System.Runtime.Serialization.ExtensionDataObject> typ nie ma publicznych członków oznacza, że dane znajdujące się w nim jest bezpieczne. Na przykład, jeśli zdeserializować źródła danych uprzywilejowanych do obiektu, w której niektóre znajdują się dane, następnie ręcznie, obiektu częściowo zaufany kod częściowo zaufany kod może odczytywać dane w `ExtensionDataObject` przez szeregowania obiektu. Rozważ ustawienie <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> do `true` podczas deserializacji źródła danych uprzywilejowanych do obiektu, który jest nowsza przekazany do częściowo zaufany kod.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obsługuje serializacji prywatnych, chronionych wewnętrzne i publiczne elementy członkowskie w trybie pełnego zaufania. Jednak w częściowej relacji zaufania, można serializować tylko publiczne elementy członkowskie. A `SecurityException` jest generowany, jeśli aplikacja próbuje szeregować niepublicznego elementu członkowskiego.  
  
     Aby umożliwić wewnętrzny lub chronionych wewnętrznych elementów członkowskich do serializacji w częściowej relacji zaufania, użyj `System.Runtime.CompilerServices.InternalsVisibleTo` atrybutu zestawu. Ten atrybut umożliwia zestawu zadeklarować, że jego wewnętrzne elementy członkowskie są widoczne dla niektórych innych zestawów. W takim przypadku zestawu, który chce mieć jego wewnętrzne elementy członkowskie serializacji deklaruje, że jego wewnętrzne elementy członkowskie są widoczne dla System.Runtime.Serialization.dll.  
  
     Zaletą tej metody jest, że nie wymaga ścieżka generowania kodu z podwyższonym poziomem uprawnień.  
  
     W tym samym czasie istnieją dwa główne wady.  
  
     Pierwszy wadą jest opcjonalnych właściwość `InternalsVisibleTo` atrybut jest całego zestawu. Oznacza to, że nie można określić, czy tylko niektóre klasa może mieć wewnętrznego członków serializacji. Oczywiście, nadal możesz nie serializacji określonego elementu członkowskiego wewnętrznego, po prostu dodając nie `DataMember` atrybutu do tego elementu członkowskiego. Podobnie Deweloper można również dołączyć do wewnętrznego zamiast prywatne lub chronione z widoczność niewielkie problemy.  
  
     Drugi Wadą jest to, że nadal nie obsługuje prywatnych lub chronionych elementów członkowskich.  
  
     Aby zilustrować stosowania `InternalsVisibleTo` atrybutu w częściowej relacji zaufania, należy rozważyć następujący program:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     W powyższym przykładzie `PermissionsHelper.InternetZone` odpowiada `PermissionSet` dla częściowej relacji zaufania. Teraz, bez `InternalsVisibleToAttribute`, aplikacja zakończy się niepowodzeniem, wyrzucanie `SecurityException` wskazujący, że nie można zserializować niepublicznych elementów członkowskich w częściowej relacji zaufania.  
  
     Jednak jeśli mamy Dodaj następujący wiersz do pliku źródłowego, program zostanie uruchomiony pomyślnie.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Inne problemy zarządzania stanem  
 Kilka problemy dotyczące zarządzania stanem obiektu są warto zauważyć:  
  
-   Używając modelu programowania strumienia z transportem przesyłania strumieniowego, przetwarzanie wiadomości wypada dociera do wiadomości. Nadawcy wiadomości może przerwać operację wysyłania środku strumienia, pozostawiając kodu w nieprzewidywalnym stanie, jeśli oczekiwany więcej zawartości. Ogólnie rzecz biorąc, nie należy polegać na strumienia są kompletne i nie wykonuj pracę w operacji na podstawie strumienia, którego nie można obniżyć ponownie w przypadku, gdy strumień jest przerywana. To samo dotyczy sytuacji, gdy komunikat może być źle sformułowane po jednostkę przesyłania strumieniowego (na przykład go może brakować tagu końcowego dla koperty protokołu SOAP lub mieć drugi treści komunikatu).  
  
-   Przy użyciu `IExtensibleDataObject` funkcji może spowodować emitować poufnych danych. Jeśli użytkownik akceptuje dane z niezaufanego źródła w kontraktach danych z `IExtensibleObjectData` i później ponownie emitowanie go na bezpiecznego kanału, gdy są podpisane wiadomości, można są potencjalnie zagwarantowanie nic nie wiadomo o danych. Ponadto może być nieprawidłowy, jeśli znane i nieznane fragmentów danych należy wziąć pod uwagę ogólny stan wysyłania. Tego uniknąć, ustawiając albo selektywnie właściwość danych rozszerzenia `null` lub selektywnie wyłączając `IExtensibleObjectData` funkcji.  
  
## <a name="schema-import"></a>Importowanie schematu  
 Normalnie, proces importowania schematu do generowania typów występuje tylko w czasie projektowania, na przykład, korzystając z [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) na usługi sieci Web do generowania klasy klienta. Jednak w bardziej zaawansowanych scenariuszy może przetwarzać schematu w czasie wykonywania. Należy pamiętać, że w ten sposób może doprowadzić do ryzyka typu "odmowa usługi". Niektóre schematu może zająć dużo czasu do zaimportowania. Nigdy nie używaj <xref:System.Xml.Serialization.XmlSerializer> składnik Importowanie schematu w scenariuszach, jeśli schematy prawdopodobnie pochodzą z niezaufanego źródła.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Zagrożenia specyficzne dla integracji AJAX ASP.NET  
 Gdy użytkownik wykonuje <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> lub <xref:System.ServiceModel.Description.WebHttpBehavior>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przedstawia punktu końcowego, który może zaakceptować wiadomości XML i JSON. Istnieje jednak tylko jeden zestaw przydziały czytnika używane zarówno przez modułu odczytującego XML i czytnika JSON. Niektóre ustawienia limitu przydziału może być odpowiednie dla jeden czytnik lecz za duża dla siebie.  
  
 Podczas implementowania `WebScriptEnablingBehavior`, użytkownik ma możliwość ujawnia pośredniczącą JavaScript w punkcie końcowym. Należy rozważyć następujące zagadnienia dotyczące zabezpieczeń:  
  
-   Informacje o usłudze (nazwy operacji, nazwy parametrów itd.) można uzyskać, sprawdzając serwera proxy JavaScript.  
  
-   Podczas korzystania z punktu końcowego JavaScript, informacje poufne i prywatne mogą być zachowane w pamięci podręcznej przeglądarki sieci Web klienta.  
  
## <a name="a-note-on-components"></a>Uwaga na temat składników  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]to elastyczny i dostosowywanych system. Większość zawartości tego tematu skupić się na najbardziej typowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] scenariusze użycia. Jednak jest możliwe utworzenie składniki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udostępnia wiele różnych sposobów. Należy zrozumieć implikacje zabezpieczeń przy użyciu każdego składnika. W szczególności:  
  
-   Gdy czytniki XML musi być używany, użyj czytników <xref:System.Xml.XmlDictionaryReader> klasa udostępnia w przeciwieństwie do innych czytników. Bezpieczne czytników są tworzone przy użyciu <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, lub <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> metody. Nie używaj <xref:System.Xml.XmlReader.Create%2A> metody. Zawsze skonfigurować bezpieczne Przydziały czytników. Serializacja silników w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są bezpieczne, tylko wtedy, gdy jest używany z bezpiecznego czytników XML z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Korzystając z <xref:System.Runtime.Serialization.DataContractSerializer> można deserializować danych potencjalnie niezaufanych, należy zawsze wartość <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> właściwości.  
  
-   Podczas tworzenia komunikat, ustaw `maxSizeOfHeaders` parametru Jeśli `MaxReceivedMessageSize` nie zapewniają wystarczająco dużo ochronę.  
  
-   Podczas tworzenia kodera, zawsze skonfiguruj odpowiednie przydziały, takich jak `MaxSessionSize` i `MaxBufferSize`.  
  
-   Korzystając z języka XPath filtr komunikatu, należy ustawić <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> Aby ograniczyć liczbę węzłów XML odwiedza filtru. Nie należy używać wyrażenia XPath, które może zająć dużo czasu obliczeniowe bez konieczności przechodzenia wiele węzłów.  
  
-   Ogólnie rzecz biorąc korzystając z każdego składnika, który akceptuje limit przydziału, zrozumieć jego wpływ na bezpieczeństwo i ustawioną wartość bezpieczne.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)

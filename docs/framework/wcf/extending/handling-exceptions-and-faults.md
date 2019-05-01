---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c29b3900a36d8d5c41fee49c408a2e3fdf67680b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991422"
---
# <a name="handling-exceptions-and-faults"></a>Obsługa wyjątków i błędów
Wyjątki są używane do komunikowania się błędy lokalnie w implementacji klienta lub usługi. Błędy, z drugiej strony, są używane do komunikacji błędów przez granice usługi, takie jak z serwera do klienta lub na odwrót. Oprócz błędów kanały transportu często używają mechanizmów specyficznych dla transportu do komunikowania się błędy na poziomie transportu. Na przykład transportu HTTP używa kodów stanu, takie jak 404 do komunikowania się nieistniejące adresu URL punktu końcowego (jest nie punktu końcowego do odesłania błędów). Ten dokument zawiera trzy sekcje, które zapewniają wskazówki autorom w niestandardowym kanale. Pierwsza sekcja zawiera wskazówki dotyczące kiedy i jak zdefiniować i zgłaszać wyjątki. Druga sekcja zawiera wskazówki dotyczące generowania i korzystanie z błędów. Trzecia sekcja wyjaśnia, jak Podaj informacje o śledzeniu ułatwiające użytkownika niestandardowego kanału Rozwiązywanie problemów z uruchomionych aplikacji.  
  
## <a name="exceptions"></a>Wyjątki  
 Istnieją dwie rzeczy, o których należy pamiętać, gdy zostanie zgłoszony wyjątek: Najpierw musi być typu, który pozwala użytkownikom na zapis poprawny kod, który pozwala reagować odpowiednio do wyjątku. Po drugie ma dostarczać wystarczających informacji dla użytkownika, aby zrozumieć, co poszło źle, wpływ awarii i sposobie jego rozwiązania. W poniższych sekcjach znajdują się wskazówki dotyczące typów wyjątków i wiadomości w kanałach usługi Windows Communication Foundation (WCF). Istnieje również ogólne wskazówki dotyczące wyjątków na platformie .NET w wytycznych projektowych dla dokumentu wyjątków.  
  
### <a name="exception-types"></a>Typy wyjątków  
 Wszystkie wyjątki generowane przez kanały musi być albo <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, lub typ pochodzący od <xref:System.ServiceModel.CommunicationException>. (Wyjątki, takie jak <xref:System.ObjectDisposedException> może również zostać wygenerowany, ale tylko do wskazania, że kod wywołujący ma niewłaściwego użycia kanału. Jeśli kanał jest prawidłowo używana, jego musi tylko wyrzucić danego.) Usługi WCF zawiera siedem typy wyjątków, które wynikają z <xref:System.ServiceModel.CommunicationException> i są przeznaczone do użycia przez kanały. Istnieją inne <xref:System.ServiceModel.CommunicationException>-pochodnych wyjątki, które są przeznaczone do użytku przez inne części systemu. Te typy wyjątków to:  
  
|Typ wyjątku|Znaczenie|Wyjątek wewnętrzny zawartości|Strategia odzyskiwania|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Adres punktu końcowego, określony w celu nasłuchiwania jest już używana.|Jeśli jest obecny, zawiera więcej szczegółów na temat błędów transportu, który spowodował wyjątek. Na przykład. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, lub <xref:System.Net.Sockets.SocketException>.|Spróbuj użyć innego adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces nie ma mieć dostęp do adresu punktu końcowego określonego w celu nasłuchiwania.|Jeśli jest obecny, zawiera więcej szczegółów na temat błędów transportu, który spowodował wyjątek. Na przykład <xref:System.IO.PipeException>, lub <xref:System.Net.HttpListenerException>.|Spróbuj przy użyciu różnych poświadczeń.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Używane jest w stanie Faulted (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Należy zwrócić uwagę, czy, gdy obiekt z wieloma oczekujących połączeń, przechodzi do stanu Faulted tylko jedno wywołanie zgłasza wyjątek, który jest powiązany z awarii i pozostałe throw wywołania <xref:System.ServiceModel.CommunicationObjectFaultedException>. To zwykle wyjątek, ponieważ aplikacja overlooks wyjątek i próbuje użyć obiektu już uszkodzoną, prawdopodobnie w wątku innego niż ten, który Przechwycono wyjątek oryginalny.|Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> błędów w pierwszej kolejności, może istnieć inne prace wymagane do odzyskania.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Używany zostało przerwane (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Podobnie jak <xref:System.ServiceModel.CommunicationObjectFaultedException>, jego wyjątku wskazuje Aplikacja wywołała <xref:System.ServiceModel.ICommunicationObject.Abort%2A> dla obiektu, prawdopodobnie z innego wątku, i obiekt nie jest już możliwe z tego powodu.|Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> przerwania w pierwszej kolejności, może być inne prace wymagane do odzyskania.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Zdalny punkt końcowy docelowy nie nasłuchuje. Może to wynikać z dowolnej części adresu punktu końcowego jest niepoprawny, nierozwiązywalny lub punktu końcowego są w dół. Przykłady obejmują błąd DNS, Menedżer kolejki nie są dostępne, a usługa nie działa.|Wyjątek wewnętrzny zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.|Spróbuj użyć innego adresu. Alternatywnie nadawca może Poczekaj chwilę i spróbuj ponownie w przypadku, gdy usługa nie działa|  
|<xref:System.ServiceModel.ProtocolException>|Protokoły komunikacyjne zgodnie z opisem w zasadach punktu końcowego niezgodność między punktami końcowymi. Na przykład ramek niezgodność typu zawartości lub Przekroczono rozmiar maksymalny komunikatu.|Jeśli jest obecny zawiera więcej informacji o błędzie określony protokół. Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wewnętrzny wyjątek, gdy przekracza MaxReceivedMessageSize przyczynę błędu.|Odzyskiwanie: Upewnij się, nadawca i odebranych protokół, które ustawienia są zgodne. Jednym ze sposobów, w tym celu jest ponownie zaimportować metadane punktu końcowego usługi (zasady) i umożliwia powiązanie wygenerowany ponownie utworzyć kanał.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Zdalny punkt końcowy nasłuchuje, ale nie jest gotowa do przetwarzania komunikatów.|Jeśli jest obecny, wyjątek wewnętrzny zawiera błąd protokołu SOAP lub szczegóły błędu na poziomie transportu.|Odzyskiwanie: Zaczekaj i spróbuj ponownie wykonać operację później.|  
|<xref:System.TimeoutException>|Operacja nie powiodła się przed upływem limitu czasu.|Może dostarczyć szczegóły limitu czasu.|Zaczekaj i spróbuj ponownie wykonać operację później.|  
  
 Zdefiniuj nowy typ wyjątku, tylko wtedy, gdy tego typu odnosi się do strategii odzyskiwania różni się od wszystkich istniejących typów wyjątków. Jeśli zdefiniujesz nowy typ wyjątku, musi pochodzić od <xref:System.ServiceModel.CommunicationException> lub jedna z jej klas pochodnych.  
  
### <a name="exception-messages"></a>Komunikaty o wyjątkach  
 Komunikaty o wyjątkach są przeznaczone dla użytkownika nie program tak powinien zapewniają wystarczające informacje, aby pomóc użytkownikowi zrozumieć i rozwiązać problem. Są trzy podstawowe części komunikatu wyjątku dobrej:  
  
 Co się stało. Wyczyść opisz problem przy użyciu terminów, które odnoszą się do komputera przez użytkownika. Na przykład komunikat o wyjątku zły będzie "Nieprawidłowa konfiguracja sekcji". Spowoduje to pozostawienie użytkownika zastanawiasz się, które sekcji konfiguracji jest nieprawidłowy i dlaczego jest on nieprawidłowy. Ulepszony komunikat będzie "Nieprawidłowa konfiguracja sekcji \<customBinding >". Komunikat o jeszcze lepiej byłoby "nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie ma już o nazwie myTransport transportu". Jest to bardzo szczegółowy komunikat o błędzie, przy użyciu nazwy użytkownika można łatwo zidentyfikować i warunki, w pliku konfiguracyjnym aplikacji. Istnieją jednak jeszcze kilka kluczowych składników. ich brak.  
  
 Znaczenia tego błędu. O ile nie jest wyświetlony komunikat z informacją wyraźnie oznacza błąd, użytkownik prawdopodobnie zastanawiasz się, czy jest to błąd krytyczny lub jeśli można go zignorować. Ogólnie rzecz biorąc komunikaty powinny prowadzić z znaczenia lub znaczenia tego błędu. Aby poprawić w poprzednim przykładzie, może być komunikat "ServiceHost nie udało się otwarty z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie jest już o nazwie myTransport transportu ".  
  
 Jak użytkownika powinno rozwiązać ten problem. Najważniejsza część komunikatu pomaga rozwiązać problem użytkownika. Komunikat powinien zawierać wskazówek lub wskazówek na temat, co należy sprawdzić lub usunąć w celu rozwiązania problemu. Na przykład "ServiceHost nie udało się otwarty z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie jest już o nazwie myTransport transportu. Upewnij się, że istnieje tylko jeden transportu w powiązaniu".  
  
## <a name="communicating-faults"></a>Błędy przekazywania  
 Protokołu SOAP 1.1 i SOAP 1.2 należy zdefiniować strukturę określonych błędów. Istnieją pewne różnice między dwoma specyfikacje, ale ogólnie rzecz biorąc, wiadomości i MessageFault typy są używane do tworzenia i wykorzystywania błędów.  
  
 ![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1.2 błędów (po lewej) i protokołu SOAP 1.1 (po prawej) błędów. Należy pamiętać, że w SOAP 1.1 element błędów kwalifikowanych przestrzeni nazw.  
  
 Protokołu SOAP definiuje komunikatu o błędzie jako komunikat, który zawiera element błędów (element, którego nazwa jest `<env:Fault>`) jako element podrzędny elementu `<env:Body>`. Zawartość elementu błędów się nieznacznie różnić między SOAP 1.1 i SOAP 1.2, jak pokazano na rysunku 1. Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasy normalizuje te różnice w jeden obiekt modelu:  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 `Code` Właściwość odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ błędu. Protokołu SOAP 1.2 definiuje pięć dopuszczalnych wartości dla `faultCode` (na przykład nadawcy i odbiorcy) i definiuje `Subcode` element, który może zawierać żadnej wartości podrzędnego. (Zobacz [specyfikacji protokołu SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) listę kodów błędów dopuszczalny rozmiar oraz ich znaczenie.) Protokołu SOAP 1.1 ma nieco inny mechanizm: Definiuje cztery `faultCode` wartości (na przykład klient i serwer), które można rozszerzyć, definiując całkowicie nowe lub przy użyciu notacji z kropką w celu utworzenia bardziej szczegółowe `faultCodes`, na przykład Client.Authentication.  
  
 Używanie MessageFault na błędy programu, FaultCode.Name i FaultCode.Namespace mapuje nazwę i przestrzeń nazw protokołu SOAP 1.2 `env:Code` lub SOAP 1.1 `faultCode`. Mapuje FaultCode.SubCode `env:Subcode` dla SOAP 1.2 i ma wartość null dla protokołu SOAP 1.1.  
  
 Należy utworzyć nowych odporności kody podrzędne (lub nowe kody błędów, jeśli przy użyciu protokołu SOAP 1.1) Jeśli interesujące programowo rozróżnienie błędów. Jest to analogiczne do tworzenia nowego typu wyjątku. Należy unikać, używając zapisu kropkowego z kodami błędów SOAP 1.1. ( [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) również zachęca do używania notacji z kropką kodu błędu.)  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 `Reason` Właściwość odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) zrozumiałą dla użytkownika opis warunku błędu odpowiednikiem komunikat o wyjątku. `FaultReason` Klasy (i protokołu SOAP `env:Reason/faultString`) ma wbudowaną obsługę posiadanie wielu tłumaczeń w celu globalizacji.  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 Zawartość szczegółów błędów są dostępne w MessageFault przy użyciu różnych metod, w tym `GetDetail` \<T > i `GetReaderAtDetailContents`(). Szczegóły błędów jest elementem nieprzezroczyste przenoszenia dodatkowe szczegóły dotyczące błędu. Jest to przydatne w przypadku niektórych dowolnego szczegółów ze strukturą, które należy wykonać przy użyciu błędu.  
  
### <a name="generating-faults"></a>Generowanie błędów  
 W tej sekcji opisano proces generowania błąd w odpowiedzi na wykryte w kanale lub we właściwości wiadomości, utworzone przez kanał jest w stanie błędu. Typowym przykładem jest wysyłanie ponownie błąd w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.  
  
 Podczas generowania usterki, niestandardowy kanał nie ma wysyłać usterki bezpośrednio, zamiast powinien zgłosić wyjątek i pozwól warstwy nad zdecydować, czy można przekonwertować tego wyjątku do awarii i jak wysłać go. Do pomocy w tej konwersji, powinien udostępniać kanał `FaultConverter` wdrożenia, który można przekonwertować wyjątek w niestandardowym kanale odpowiednią odporność. `FaultConverter` definiuje się następująco:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 Poszczególnych kanałów, które generuje błędy niestandardowe musi implementować `FaultConverter` i przywrócić go po wywołaniu `GetProperty<FaultConverter>`. Niestandardowy `OnTryCreateFaultMessage` implementacji należy przekonwertować wyjątek usterki lub delegować do kanału wewnętrzny `FaultConverter`. Jeśli kanał jest transport go należy przekonwertować wyjątek lub przekazać do kodera `FaultConverter` lub wartość domyślną `FaultConverter` dostarczane w programie WCF. Wartość domyślna `FaultConverter` konwertuje błędy komunikaty o błędach określone przez WS-Addressing i protokołu SOAP. Oto przykład `OnTryCreateFaultMessage` implementacji.  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Domniemanie tego wzorca jest, że wyjątki zgłaszane między warstwami dla warunków błędu, które wymagają błędów musi zawierać wystarczających informacji dla odpowiednich generatora błędów do utworzenia poprawne błędów. Jako autor niestandardowym kanale może zdefiniować typy wyjątków, które odpowiadają warunki w różnych domenach błędów, jeśli takie wyjątki jeszcze nie istnieje. Należy zauważyć, że wyjątki przechodzenie warstwach kanału skontaktować się warunek błędu, a nie dane nieprzezroczyste błędów.  
  
### <a name="fault-categories"></a>Kategorie błędów  
 Zazwyczaj istnieją trzy kategorie błędów:  
  
1. Błędy, które są rozpowszechniona w całym stosie. Te błędy można napotkał w dowolnej warstwie stosu kanału, na przykład InvalidCardinalityAddressingException.  
  
2. Błędy, które mogą być napotkał dowolne miejsce powyżej wybranej warstwie w stosie na przykład niektóre błędy, które odnoszą się do transakcji lub do ról zabezpieczeń.  
  
3. Błędy, które są kierowane w pojedynczej warstwie w stosie, na przykład błędy, takie jak błędy numer sekwencji WS-RM.  
  
 Kategoria 1. Błędy są zazwyczaj WS-Addressing i błędach SOAP. Podstawa `FaultConverter` klasy dostarczone przez architekturę WCF błędy konwertuje komunikaty o błędach określić WS-Addressing i protokołu SOAP, dzięki czemu nie trzeba obsługiwać konwersji tych wyjątków samodzielnie.  
  
 Kategoria 2. Błędy występują, gdy warstwa dodaje właściwość do komunikat, który nie używa całkowicie informacji wiadomości, które odnoszą się do tej warstwy. Błędy mogą zostać wykryte później, gdy wyższej warstwie prosi właściwości wiadomości do przetwarzania wiadomości dalszych informacji. Takie kanałów powinny implementować `GetProperty` określonej wcześniej, aby umożliwić wyższej warstwie do odesłania poprawne błędów. Na przykład jest TransactionMessageProperty. Ta właściwość jest dodawany do wiadomości bez w pełni sprawdzania poprawności wszystkie dane w nagłówku (w ten sposób może obejmować, kontaktując się z koordynatorem transakcji rozproszonych (DTC).  
  
 Kategoria 3. Błędy tylko są generowane i wysyłane przez warstwę w procesorze. W związku z tym wszystkie wyjątki są zawarte w obrębie warstwy. Aby poprawić spójność kanałów i łatwość konserwacji, niestandardowy kanał należy używać ze wzorcem określonym wcześniej do wygenerowania komunikaty o błędach nawet w przypadku błędów wewnętrznych.  
  
### <a name="interpreting-received-faults"></a>Interpretowanie błędy odebrane  
 Ta sekcja zawiera wskazówki dotyczące generowania odpowiedni wyjątek podczas odbierania komunikatu o błędzie. Drzewo decyzyjne dla przetwarzania komunikatu w każdej warstwie stosu jest następująca:  
  
1. Jeśli warstwa uwzględnia komunikatu jest nieprawidłowy, warstwy należy wykonać przetwarzanie "nieprawidłowy komunikat". Takie przetwarzanie zależy od warstwy mogą jednak zawierać porzucenie wiadomości, śledzenia, lub zostanie zgłoszony wyjątek są konwertowane na błąd. Przykłady obejmują zabezpieczeń odbiera komunikat, który nie jest właściwie zabezpieczona lub odebranie komunikatu z liczbą sekwencji zły Menedżera zasobów.  
  
2. W przeciwnym razie jeśli komunikat jest komunikat o błędzie, który odnosi się do warstwy, a komunikat nie ma sensu poza interakcji warstwy, warstwy powinna obsługiwać warunku błędu. Na przykład jest błąd odmowa sekwencji Menedżera zasobów jest całkowicie nieprzydatna warstwy powyżej kanału Menedżera zasobów i oznacza to spowodowaniem błędu kanału Menedżera zasobów i zgłaszanie z oczekujących operacji.  
  
3. W przeciwnym razie komunikat powinien być zwracane z Request() lub Receive(). Obejmuje to przypadki, w której warstwie rozpoznaje usterki, ale błędu tylko wskazuje, że żądanie nie powiodło się, a nie oznacza spowodowaniem błędu kanału i zgłaszanie z oczekujących operacji. Aby zwiększyć użyteczność w takiej sytuacji, należy zaimplementować warstwy `GetProperty<FaultConverter>` i zwracają `FaultConverter` klasy, który można przekonwertować błąd wyjątku przez zastąpienie `OnTryCreateException`.  
  
 Poniższy model obiektów obsługuje konwertowania komunikaty wyjątków:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 Warstwy kanału można zaimplementować `GetProperty<FaultConverter>` do obsługi konwersji komunikaty o błędach do wyjątków. Aby to zrobić, należy zastąpić `OnTryCreateException` i sprawdź komunikat o błędzie. Jeśli rozpoznany, przeprowadzić konwersję, w przeciwnym razie poproś kanału wewnętrzny, aby przekonwertować go. Kanały transportu powinny delegować metody do `FaultConverter.GetDefaultFaultConverter` by otrzymać domyślny FaultConverter protokołu SOAP/WS-Addressing.  
  
 Typowa implementacja wygląda następująco:  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Dla warunków określonych błędów, które mają scenariuszy odzyskiwania distinct, należy wziąć pod uwagę definiujący klasę pochodną z `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Przetwarzanie MustUnderstand  
 Protokołu SOAP definiuje ogólnych błędów do sygnalizowania, że wymagany nagłówek nie został zrozumiany przez odbiorcę. Ten błąd jest znany jako `mustUnderstand` błędów. W programie WCF, nigdy nie Generuj niestandardowe kanały `mustUnderstand` błędów. Zamiast tego dyspozytora WCF, która znajduje się w górnej części stos komunikacji WCF, sprawdza, że wszystkie nagłówki, które zostały oznaczone jako MustUndestand = true były zrozumiałe stosu podstawowego. Jeśli dowolny nie były zrozumiałe `mustUnderstand` błąd jest zgłaszany w tym momencie. (Użytkownik może wybrać wyłączyć to `mustUnderstand` przetwarzania i wdróż aplikację otrzymywać wszystkie nagłówki wiadomości. In that Case aplikacja jest odpowiedzialny za wykonanie `mustUnderstand` przetwarzania.) Wygenerowany błędów zawiera nagłówek NotUnderstood zawierającą nazwy wszystkich nagłówków z MustUnderstand = true, która była niezrozumiała.  
  
 Jeśli kanał protokołu wysyła niestandardowy nagłówek o MustUnderstand = true i odbiera `mustUnderstand` błędów, jego musi ustalić czy jest nagłówek wysłanie go z powodu tego błędu. Istnieją dwa elementy członkowskie na `MessageFault` klasy, które są przydatne w tym:  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault` Zwraca `true` Jeśli błąd jest `mustUnderstand` błędów. `WasHeaderNotUnderstood` Zwraca `true` nagłówka o podanej nazwie i przestrzeni nazw jest uwzględniane w błędów jako nagłówek NotUnderstood.  W przeciwnym razie zwraca `false`.  
  
 Jeśli kanał emituje nagłówek, który jest oznaczony MustUnderstand = true, a warstwa ta powinny również implementować wzorzec interfejsu API generowania wyjątków należy przekonwertować `mustUnderstand` błędy spowodowane nagłówka do bardziej użyteczne wyjątku, zgodnie z wcześniejszym opisem.  
  
## <a name="tracing"></a>Śledzenie  
 Program .NET Framework dostarcza mechanizm śledzenia wykonywania programu, jako sposób, aby ułatwić diagnozowanie aplikacji produkcyjnych lub sporadycznych problemów, w którym nie jest możliwe tylko dołączanie debugera i Przechodź przez kod. Podstawowe składniki ten mechanizm znajdują się w <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw i składają się:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia do zapisania, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, który jest abstrakcyjna klasa bazowa dla konkretnych obiektów nasłuchujących otrzymywać informacje, które mają być śledzone od <xref:System.Diagnostics.TraceSource> i wyprowadzić dane do miejsca docelowego określonego odbiornika. Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML. Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który umożliwia użytkownikowi aplikacji, Kontroluj ich szczegółowość śledzenia i zwykle jest określona w konfiguracji.  
  
- Oprócz podstawowych składników można używać [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) wyszukiwania usługi WCF i wyświetlić ślady. To narzędzie jest przeznaczony specjalnie dla plików śledzenia generowane przez program WCF i napisanych przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener>. Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenia.  
  
 ![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Śledzenie za pomocą kanału niestandardowe  
 Niestandardowe kanały należy zapisać komunikaty śledzenia, aby pomóc w diagnozowaniu problemów, gdy nie jest możliwe dołączyć debuger do uruchomionej aplikacji. Obejmuje to dwa zadania wysokiego poziomu: Utworzenie wystąpienia <xref:System.Diagnostics.TraceSource> i wywoływania jego metody można zapisywać dane śledzenia.  
  
 Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, string, należy określić staje się nazwę tego źródła. Ta nazwa jest używana do konfigurowania źródła śledzenia (poziom śledzenia Włącz/Wyłącz/set). Jest także wyświetlany w śledzeniu danych wyjściowych sam. Niestandardowe kanały powinien umożliwia ułatwiają danych wyjściowych śledzenia zrozumienie skąd pochodzą informacje o śledzeniu unikatową nazwę. Częstą praktyką jest, przy użyciu nazwy zestawu, który zapisuje informacje jako nazwy źródła śledzenia. Na przykład WCF używa System.ServiceModel jako źródła śledzenia dla informacje zapisane z zestawu System.ServiceModel.  
  
 Po utworzeniu źródła śledzenia, należy wywołać jej <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, lub <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metod na zapisywanie wpisów śledzenia do odbiorników śledzenia. Dla każdego wpisu śledzenia pisania, należy do klasyfikowania typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w <xref:System.Diagnostics.TraceEventType>. Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji należy określić, czy wpis śledzenia przekazywane są do odbiornika. Na przykład ustawienie poziomie śledzenia w konfiguracji, aby `Warning` umożliwia `Warning`, `Error` i `Critical` śledzenia wpisy, które ma zostać zapisany, ale bloki informacji i pełne wpisy. Oto przykład tworzenia wystąpienia źródła śledzenia i wypisywanie wpis na poziomie informacji:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  Zdecydowanie zaleca się, że podajesz nazwę źródła śledzenia, który jest unikatowy w niestandardowym kanale w celu śledzenia danych wyjściowych użytkownikom zorientować się, skąd pochodzą dane wyjściowe.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integracja z usługą w podglądzie śledzenia  
 Dane śledzenia generowane przez kanał może być danych wyjściowych w formacie czytelnym przez [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako odbiornik śledzenia. Nie jest to coś, deweloper kanału, należy wykonać. Jest to raczej użytkownik aplikacji (lub osobę, rozwiązywanie problemów z aplikacji), które należy skonfigurować ten odbiornik śledzenia w pliku konfiguracji aplikacji. Na przykład następująca konfiguracja generuje informacje ze śledzenia z obu <xref:System.ServiceModel?displayProperty=nameWithType> i `Microsoft.Samples.Udp` pliku o nazwie `TraceEventsFile.e2e`:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a>Śledzenie danych strukturalnych  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metodę przyjmującą jeden lub więcej obiektów, które mają być uwzględniane we wpisie śledzenia. Ogólnie rzecz biorąc <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda jest wywoływana dla każdego obiektu, a wynikowy ciąg jest zapisywany jako część wpis śledzenia. Korzystając z <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> w danych wyjściowych danych śledzenia, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>. Wynikowy wpis śledzenia zawiera kod XML podany przez <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Poniżej przedstawiono przykładowy wpis z danymi aplikacji XML:  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 Przeglądarka śledzenia WCF rozumie schemat `TraceRecord` element przedstawionego wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla go w formacie tabelarycznym. Kanał powinna używać tego schematu śledzenia danych ze strukturą aplikacji aby ułatwić użytkownikom Svctraceviewer.exe odczytywać dane.

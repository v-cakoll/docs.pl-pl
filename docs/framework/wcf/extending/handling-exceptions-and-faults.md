---
title: "Obsługa wyjątków i błędów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a69acb9b640c17e6641efc6c30798e3856ef6e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="handling-exceptions-and-faults"></a>Obsługa wyjątków i błędów
Wyjątki są używane do komunikacji błędy lokalnie w obrębie implementacji klienta lub usługi. Błędy, z drugiej strony, są używane do komunikacji błędy w granicach usługi, takie jak z serwera do klienta lub na odwrót. Oprócz błędów kanały transportu często używają mechanizmów specyficznych dla transportu do komunikowania się błędy na poziomie transportu. Na przykład transportu HTTP używa kodów stanu, takie jak 404 do komunikowania się nieistniejącego punktu końcowego adresu URL (Brak żaden punkt końcowy do odesłania błędów). Ten dokument zawiera trzy sekcje, które zawierają wskazówki autorom niestandardowym kanale. Pierwsza sekcja zawiera wskazówki dotyczące czasu i sposób definiowania i zgłaszanie wyjątków. Druga sekcja zawiera wskazówki dotyczące generowania i korzystanie z błędów. Trzeci sekcji opisano sposób Podaj informacje o śledzeniu, aby ułatwić rozwiązywanie problemów uruchamianie aplikacji użytkownika niestandardowego kanału.  
  
## <a name="exceptions"></a>Wyjątki  
 Istnieją dwie czynności należy wziąć pod uwagę podczas generowania wyjątku: najpierw musi być typu, który pozwala użytkownikom na zapis prawidłowego kodu, który można reagować odpowiednio wyjątek. Po drugie musi on zawierać informacje wystarczające do użytkownika, aby zrozumieć, co poszło źle, wpływ awarii i jak to naprawić. W poniższych sekcjach znajdują się wskazówki dotyczące typów wyjątków i wiadomości dla [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanałów. Istnieje również ogólne wskazówki dotyczące wyjątków w .NET w wytycznych projektowych wyjątki dokumentu.  
  
### <a name="exception-types"></a>Typy wyjątków  
 Wszystkie wyjątki zgłaszane przez kanały musi być równa albo <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, lub typ pochodzący od <xref:System.ServiceModel.CommunicationException>. (Wyjątki, takie jak <xref:System.ObjectDisposedException> może również zostać wygenerowany, ale tylko do wskazują, że kod wywołujący ma niewłaściwego użycia kanału. Jeśli kanał jest prawidłowo używana, jego musi tylko zgłosić danego wyjątki.) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia siedmiu typów wyjątków, które pochodzą z <xref:System.ServiceModel.CommunicationException> i mają być używane przez kanały. Istnieją inne <xref:System.ServiceModel.CommunicationException>-pochodnych wyjątki, które są przeznaczone do użytku przez inne części systemu. Te typy wyjątek to:  
  
|Typ wyjątku|Znaczenie|Wyjątek wewnętrzny zawartości|Strategia odzyskiwania|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Podany adres punktu końcowego w celu nasłuchiwania jest już używana.|Jeśli jest obecny, zawiera więcej informacji o błędzie transport, który spowodował wyjątek. Na przykład. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, lub <xref:System.Net.Sockets.SocketException>.|Spróbuj inny adres.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces nie ma mieć dostęp do podany adres punktu końcowego w celu nasłuchiwania.|Jeśli jest obecny, zawiera więcej informacji o błędzie transport, który spowodował wyjątek. Na przykład <xref:System.IO.PipeException>, lub <xref:System.Net.HttpListenerException>.|Spróbuj i ma inne poświadczenia.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Używany jest w stanie Faulted (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Należy pamiętać, że gdy obiekt z wieloma do czasu wywołania przejścia w stan końcowy: Faulted, tylko jedno wywołanie zgłasza wyjątek dotyczące awarii i pozostałe throw wywołania <xref:System.ServiceModel.CommunicationObjectFaultedException>. Zwykle zgłoszenia tego wyjątku, ponieważ aplikacja overlooks wyjątek i próbuje użyć obiektu już błędnej, prawdopodobnie w wątku innego niż ten, który Przechwycono wyjątek oryginalnego.|Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> do usterki w pierwszej kolejności, mogą być inne zadania wymagane do odzyskania.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Używany została przerwana (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Podobnie jak <xref:System.ServiceModel.CommunicationObjectFaultedException>, jego wyjątek wskazuje aplikacji została wywołana <xref:System.ServiceModel.ICommunicationObject.Abort%2A> dla obiektu, prawdopodobnie z innego wątku, i obiekt nie jest już możliwe z tego powodu.|Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> przerwania w pierwszym rzędzie, może być inne zadania wymagane do odzyskania.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Zdalny punkt końcowy docelowych nie nasłuchuje. Może to wynikać z częścią adres punktu końcowego jest nieprawidłowy, nierozwiązywalne lub punkt końcowy jest wciśnięty. Przykładami błędów DNS, menedżera kolejek nie są dostępne, a usługa nie działa.|Wyjątek wewnętrzny zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.|Spróbuj inny adres. Alternatywnie nadawca może Zaczekaj chwilę i spróbuj ponownie w przypadku, gdy usługa nie działa|  
|<xref:System.ServiceModel.ProtocolException>|Protokoły komunikacji w sposób opisany w zasadach punktu końcowego są niezgodne między punktami końcowymi. Na przykład framing niezgodność typu zawartości lub przekracza rozmiar maksymalny komunikatu.|Jeśli jest obecny zawiera więcej informacji o błędzie określony protokół. Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wyjątek wewnętrzny, gdy przekracza MaxReceivedMessageSize przyczynę błędu.|Odzyskiwanie: Upewnij się, nadawcy i protokół odebrane przez ustawienia są zgodne. Jednym ze sposobów jest ponownie zaimportować metadane punktu końcowego usługi (zasady) i umożliwia powiązanie wygenerowany ponownie utworzyć kanał.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Zdalny punkt końcowy nasłuchuje, ale nie jest przygotowany do przetwarzania komunikatów.|Jeśli jest obecny, wyjątek wewnętrzny zapewnia błędu protokołu SOAP lub szczegółów błąd poziomu transportu.|Odzyskiwanie: Zaczekaj i spróbuj ponownie wykonać operację później.|  
|<xref:System.TimeoutException>|Nie można zakończyć przed upływem limitu czasu operacji.|Może zawierają szczegółowe informacje o limicie czasu.|Zaczekaj i spróbuj ponownie wykonać operację później.|  
  
 Zdefiniuj nowy typ wyjątku, tylko w przypadku tego typu odnosi się do strategii odzyskiwania określonych różnych ze wszystkich istniejących typów wyjątków. W przypadku definiowania nowy typ wyjątku, musi pochodzić od <xref:System.ServiceModel.CommunicationException> lub jednej z jej klas pochodnych.  
  
### <a name="exception-messages"></a>Komunikaty o wyjątkach  
 Komunikaty o wyjątkach są przeznaczone dla użytkownika nie program, należy zapewniają wystarczających informacji pomóc użytkownikowi zrozumieć i rozwiązać problem. Dostępne są następujące trzy podstawowe części komunikatu dobrej wyjątek:  
  
 Co się stało. Podaj czytelny opis problemu, przy użyciu terminów, które odnoszą się do komputera przez użytkownika. Na przykład komunikat wyjątek złego byłoby "Nieprawidłowa konfiguracja sekcji". Spowoduje to pozostawienie użytkownika zastanawiasz się w sekcji konfiguracji, które są niepoprawne i dlaczego jest niepoprawny. Ulepszone komunikat będzie "Nieprawidłowa konfiguracja sekcji \<customBinding >". Będą jeszcze bardziej poprawić jakość komunikat "nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie jest już transportu o nazwie myTransport". Jest to bardzo określonego komunikatu korzystania z warunków i nazw, które użytkownik może łatwo zidentyfikować w pliku konfiguracyjnym aplikacji. Istnieją jednak nadal kilka kluczowych składników Brak.  
  
 Znaczenia tego błędu. O ile w komunikacie wyraźnie oznacza błąd, użytkownik prawdopodobnie zastanawiasz się, czy jest to błąd krytyczny lub jeśli można go zignorować. Ogólnie rzecz biorąc wiadomości powinny prowadzić znaczenie lub znaczenia tego błędu. Aby zwiększyć w poprzednim przykładzie, komunikat może być "ServiceHost nie powiodło się z powodu błędu konfiguracji Otwórz: nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transportu o nazwie myTransport".  
  
 Jak użytkownik powinien rozwiązać problem. Najważniejsze część komunikatu pomaga użytkownika Napraw ten problem. Komunikat powinna zawierać wskazówek lub wskazówki dotyczące Sprawdź i napraw, aby rozwiązać problem. Na przykład "ServiceHost nie powiodło się z powodu błędu konfiguracji Otwórz: nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie jest już transportu o nazwie myTransport. Upewnij się, że istnieje transportu tylko jedno powiązanie".  
  
## <a name="communicating-faults"></a>Przekazywania błędów  
 SOAP 1.1 i SOAP 1.2 zdefiniować szczególne strukturę błędów. Istnieją pewne różnice między dwoma specyfikacje, ale ogólnie rzecz biorąc, typy komunikatu i MessageFault są używane do tworzenia i korzystania z błędów.  
  
 ![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
SOAP 1.2 usterek (po lewej) i (po prawej) błędu protokołu SOAP 1.1. Należy pamiętać, że w SOAP 1.1 tylko element błędów kwalifikowane w obszarze nazw.  
  
 SOAP definiuje komunikat o błędzie komunikat, który zawiera element usterek (element o nazwie `<env:Fault>`) jako element podrzędny `<env:Body>`. Zawartość elementu błędów się nieco różnić między SOAP 1.1 i SOAP 1.2, jak pokazano na rysunku 1. Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasy normalizuje te różnice w jeden obiekt modelu:  
  
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
  
 `Code` Właściwość odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ błędu. SOAP 1.2 definiuje pięć dopuszczalnych wartości dla `faultCode` (na przykład nadawcy i odbiorcy) i definiuje `Subcode` element, który może zawierać żadnej wartości podrzędny. (Zobacz [Specyfikacja protokołu SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=95176) listę kodów dopuszczalny usterek i ich znaczenie.) SOAP 1.1 ma mechanizm nieco inne: definiuje cztery `faultCode` wartości (na przykład klient i serwer), które mogą być rozszerzane przez zdefiniowanie całkowicie nowe lub przy użyciu notacji kropka można utworzyć bardziej szczegółowe `faultCodes`, na przykład Client.Authentication.  
  
 Używanie MessageFault do błędów programów, FaultCode.Name i FaultCode.Namespace mapuje nazwę i przestrzeń nazw protokołu SOAP 1.2 `env:Code` lub protokołu SOAP 1.1 `faultCode`. Mapuje FaultCode.SubCode `env:Subcode` dla SOAP 1.2 i ma wartość null dla SOAP 1.1.  
  
 Należy utworzyć nowe kody podrzędne usterek (lub nowe kody błędów, jeśli przy użyciu protokołu SOAP 1.1) Jeśli interesujące programowo odróżnienie błąd. To jest analogiczne do utworzenia nowego typu wyjątku. Należy unikać używania kropkowego kody błędów SOAP 1.1. ( [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) również zachęca do używania kodu błędu kropkowego.)  
  
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
  
 `Reason` Właściwość odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) zrozumiałą dla użytkownika opis warunku błędu odpowiednikiem komunikat o wyjątku. `FaultReason` Klasy (i SOAP `env:Reason/faultString`) ma wbudowaną obsługę o wielu tłumaczenia dla globalizacji.  
  
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
  
 Zawartość szczegółów błędów są dostępne w MessageFault przy użyciu różnych metod, w tym `GetDetail` \<T > i `GetReaderAtDetailContents`(). Szczegół błędu jest elementem nieprzezroczyste przeprowadzania dodatkowe szczegóły dotyczące błędu. Jest to przydatne w przypadku niektórych dowolnego szczegółów strukturalnych, które należy wykonać z usterki.  
  
### <a name="generating-faults"></a>Generowanie błędów  
 W tej sekcji opisano proces generowania błąd w odpowiedzi na błąd wykryto w kanale lub we właściwości wiadomości utworzone przez kanał. Typowym przykładem odsyła błąd w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.  
  
 Podczas generowania usterki, niestandardowym kanale najlepiej nie przesyłać usterki bezpośrednio, zamiast powinien zgłosić wyjątek i pozwól warstwy powyżej zdecydować, czy można przekonwertować tego wyjątku do usterki oraz jak wysłać go. W celu ułatwienia tej konwersji, należy podać kanału `FaultConverter` wdrożenia, który można przekonwertować wyjątek w niestandardowym kanale właściwe usterki. `FaultConverter`nie zdefiniowano jako:  
  
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
  
 Każdy kanału, który generuje błędy niestandardowe musi implementować `FaultConverter` i zwracać ją w wywołaniu `GetProperty<FaultConverter>`. Niestandardowa `OnTryCreateFaultMessage` implementacji musi przekonwertuj wyjątek błąd lub delegowania w wewnętrznym kanale `FaultConverter`. Jeśli kanał jest transport musi przekonwertować wyjątek lub przekazać do kodera `FaultConverter` lub wartość domyślną `FaultConverter` w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] . Wartość domyślna `FaultConverter` konwertuje błędy komunikatów "fault" określony przez WS-Addressing i protokołu SOAP. Oto przykład `OnTryCreateFaultMessage` implementacji.  
  
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
  
 Możliwa tego wzorca jest, że wyjątki zgłaszane między warstwami dla warunków błędu, które wymagają błędów muszą zawierać informacje dla odpowiedniego generatora błędów, aby utworzyć poprawne błędów. Jako autor niestandardowym kanale mogą określić typy wyjątków, które odpowiadają różnych awarii, jeśli takie wyjątki jeszcze nie istnieje. Należy pamiętać, że wyjątków przechodzi przez kanał warstwy skontaktować się warunku błędu, a nie dane nieprzezroczyste błędów.  
  
### <a name="fault-categories"></a>Kategorie błędów  
 Zazwyczaj są trzy kategorie błędów:  
  
1.  Błędy, które są rozpowszechniona w całym cały stos. Te błędy można napotkał na wszystkie warstwy stosu kanału, na przykład InvalidCardinalityAddressingException.  
  
2.  Błędy, które mogą być napotkał dowolne miejsce powyżej wybranej warstwie w stosie na przykład niektóre błędy, które odnoszą się do przesłanej transakcji lub do ról zabezpieczeń.  
  
3.  Błędy, które są kierowane na warstwę stosu, na przykład błędów, takich jak błędy numer sekwencji WS-RM.  
  
 Kategoria 1. Błędy są zwykle WS-Addressing i błędach SOAP. Podstawowym `FaultConverter` klasy przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] błędy konwertuje komunikatów "fault" określony przez WS-Addressing i SOAP dzięki czemu nie trzeba obsłużyć konwersji tych wyjątków samodzielnie.  
  
 Kategoria 2. Błędów wtedy, gdy warstwy dodaje właściwość do komunikat, który nie zużywa całkowicie komunikat informacji dotyczących tej warstwy. Błędy mogą być wykrywane później, gdy właściwość wiadomości przetworzyć komunikatu dalszych informacji o prosi o wyższej warstwie. Takie kanałów powinien implementować `GetProperty` określony wcześniej, aby włączyć wyższej warstwie do odesłania poprawne błędów. Na przykład jest TransactionMessageProperty. Ta właściwość jest dodany komunikat bez pełni sprawdzanie poprawności wszystkich danych w nagłówku (zrobić, może obejmować kontaktowania się z koordynatorem transakcji rozproszonych (DTC).  
  
 Kategoria 3. Błędy są tylko i wysyłane przez warstwę pojedynczy procesor. W związku z tym wszystkie wyjątki są zawarte w warstwie. Aby zwiększyć zgodność między kanałów i łatwości konserwacji, niestandardowe kanału należy używać wzorzec wcześniej określony do generowania komunikatów "fault" nawet w przypadku błędów wewnętrznych.  
  
### <a name="interpreting-received-faults"></a>Interpretowanie odebranych błędów  
 Ta sekcja zawiera wskazówki dotyczące generowania odpowiedni wyjątek, gdy odbiera komunikat o błędzie. Drzewo decyzyjne dotyczące przetwarzania komunikatu w każdej warstwie w stosie wygląda następująco:  
  
1.  Jeśli warstwa uwzględnia komunikatu jest nieprawidłowy, warstwy należy wykonać jego przetwarzanie "nieprawidłowy komunikat". Takie przetwarzanie specyficzne dla warstwy, ale może obejmować usunięcie wiadomości, śledzenie, lub zgłoszeniu wyjątku, który zostaje przekształcona na błąd. Przykładami zabezpieczeń odbieranie wiadomości, który nie jest prawidłowo zabezpieczony lub odbieranie wiadomości z liczbą sekwencji zły Menedżera zasobów.  
  
2.  W przeciwnym razie jeśli komunikat jest komunikat o błędzie, który dotyczy w szczególności do warstwy, a komunikat nie ma sensu poza interakcji przesuwaniu, warstwy powinna obsługiwać warunku błędu. Na przykład jest błąd odmowy sekwencji RM znaczenia do warstwy powyżej kanału RM i oznacza to spowodowaniem błędu kanału RM i zgłaszanie z oczekujących operacji.  
  
3.  W przeciwnym razie wiadomości powinny być zwracane z Request() lub Receive(). Dotyczy to przypadków, w których warstwy rozpoznaje błędu, ale usterki tylko wskazuje, że żądanie nie powiodło się i nie oznacza spowodowaniem błędu kanału i zgłaszanie z oczekujących operacji. Aby poprawić użyteczność w takim przypadku, powinien implementować warstwy `GetProperty<FaultConverter>` i zwracać `FaultConverter` klasy, który można przekonwertować usterki wyjątek przez zastąpienie `OnTryCreateException`.  
  
 Następujące model obiektów obsługuje konwertowania komunikaty wyjątków:  
  
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
  
 Można zaimplementować w warstwie kanału `GetProperty<FaultConverter>` do obsługi konwertowania komunikatów "fault" wyjątków. Aby to zrobić, należy zastąpić `OnTryCreateException` i przejrzyj komunikat o błędzie. Rozpoznany, wykonać konwersji, w przeciwnym razie poproś wewnętrzny kanału do konwertowania. Kanały transportu powinny być delegowane do `FaultConverter.GetDefaultFaultConverter` by otrzymać domyślny FaultConverter SOAP/WS-Addressing.  
  
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
  
 Warunki określonych błędów, które mają scenariuszy odzyskiwania distinct, rozważ zdefiniowanie klasy pochodnej z `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Atrybut MustUnderstand przetwarzania  
 SOAP definiuje ogólne usterki do sygnalizacji wymagany nagłówek nie został zrozumiany przez odbiorcę. Ten błąd jest nazywany `mustUnderstand` błędów. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nigdy nie Generuj kanałów niestandardowych `mustUnderstand` błędów. Zamiast tego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Dyspozytorze, który znajduje się w górnej części [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu komunikacji, sprawdza, czy wszystkie nagłówki, które zostały oznaczone jako MustUndestand = true zostały zrozumiane przez stos podstawowej. Jeśli dowolne są niezrozumiałe, `mustUnderstand` błąd jest zgłaszany w tym momencie. (Użytkownik może wyłączyć to `mustUnderstand` przetwarzania i mają otrzymywać wszystkie nagłówki komunikatów aplikacji. In that Case aplikacji jest odpowiedzialny za wykonywanie `mustUnderstand` przetwarzania.) Wygenerowany błąd zawiera nagłówek NotUnderstood, zawierającą nazwy wszystkich nagłówków z MustUnderstand = true, które są niezrozumiałe.  
  
 Jeśli kanał protokołu wysyła niestandardowy nagłówek o MustUnderstand = true i odbiera `mustUnderstand` usterka, go musi ustalić czy jest nagłówka ona wysłana z powodu tego błędu. Istnieją dwa elementy członkowskie na `MessageFault` klasy, które są przydatne w przypadku to:  
  
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
  
 `IsMustUnderstandFault`Zwraca `true` w przypadku błędu `mustUnderstand` błędów. `WasHeaderNotUnderstood`Zwraca `true` nagłówek o określonej nazwie i przestrzeni nazw jest uwzględniane w usterek jako nagłówek NotUnderstood.  W przeciwnym razie zwraca `false`.  
  
 Jeśli kanał emituje nagłówek, który jest oznaczony jako atrybut MustUnderstand = true, a następnie tej warstwy powinny również implementować wzorzec interfejsu API generowania wyjątków i należy przekonwertować `mustUnderstand` błędy spowodowane nagłówka do bardziej użyteczne wyjątków opisanych powyżej.  
  
## <a name="tracing"></a>Śledzenie  
 .NET Framework zapewnia mechanizm do śledzenia realizacji program sposób ułatwiających diagnozowanie aplikacji produkcyjnych i przejściowych problemów, gdy nie jest możliwe tylko dołączenie debugera i kroków kod. Podstawowe składniki ten mechanizm znajdują się w <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw i obejmować:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia do zapisania, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, która jest abstrakcyjna klasa podstawowa dla konkretnych obiektów nasłuchujących odbierać informacje, które mają być śledzone z <xref:System.Diagnostics.TraceSource> i wyjścia go do lokalizacji docelowej, specyficzne dla odbiornika. Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML. Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który umożliwia użytkownikowi aplikacji kontrolować poziom szczegółowości śledzenia i zwykle jest określona w konfiguracji.  
  
-   Oprócz podstawowych składników, możesz użyć [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) umożliwiają wyświetlenie i wyszukiwania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] śladów. Zaprojektowany specjalnie z myślą pliki śledzenia wygenerowany przez narzędzie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i zapisany przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener>. Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenia.  
  
 ![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Śledzenie za pomocą kanału niestandardowe  
 Wiadomości śledzenia ułatwiających diagnozowanie problemów, gdy nie jest możliwe dołączanie debugera do uruchomionej aplikacji należy zapisać jego kanałów niestandardowych. Ten proces obejmuje dwa zadania wysokiego poziomu: Tworzenie wystąpień <xref:System.Diagnostics.TraceSource> i wywołanie jego metody można zapisywać dane śledzenia.  
  
 Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, należy określić ciąg staje się nazwa tego źródła. Ta nazwa jest używana do konfigurowania (set Włącz/Wyłącz śledzenie poziom) źródła śledzenia. Jest także wyświetlany w wyniku sam śledzenia. Kanałów niestandardowych należy używać unikatową nazwę w celu czytników zrozumieć, z której pochodzi informacji o śledzeniu danych wyjściowych śledzenia. Standardową praktyką jest użycie nazwy zestawu, który zapisuje informacje jak nazwa źródła śledzenia. Na przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa System.ServiceModel jako źródła śledzenia informacji z zestawu System.ServiceModel.  
  
 Po utworzeniu źródła śledzenia, należy wywołać jej <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, lub <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metod na zapisywanie wpisów śledzenia do obiektów nasłuchujących śledzenia. Dla każdego wpisu śledzenia pisania należy sklasyfikować typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w <xref:System.Diagnostics.TraceEventType>. Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji należy ustalić, czy wpis śledzenia jest dane wyjściowe do odbiornika. Na przykład ustawienie poziomu śledzenia w konfiguracji, aby `Warning` umożliwia `Warning`, `Error` i `Critical` śledzenia wpisy są zapisywane, ale bloki wpisy informacji i pełne. Poniżej przedstawiono przykład tworzenia wystąpienia źródła śledzenia i zapisywania wpisu na poziomie informacji:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  Zdecydowanie zaleca się, że podajesz nazwę źródła śledzenia, która jest unikatowa dla niestandardowego kanału pomagające zrozumieć, skąd pochodzą dane wyjściowe czytniki danych wyjściowych śledzenia.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrowanie z przeglądarki śledzenia  
 Ślady generowane przez kanał może być danych wyjściowych w formacie, który może zostać odczytany przez [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako obiektu nasłuchującego śledzenia. Nie jest to coś, deweloper kanału, należy wykonać. Jest to raczej użytkownik aplikacji (lub osoby, rozwiązywanie problemów z aplikacji) który musi skonfigurować tym odbiorniku śledzenia w pliku konfiguracyjnym aplikacji. Na przykład następująca konfiguracja generuje informacje o śledzeniu na obu <xref:System.ServiceModel?displayProperty=nameWithType> i `Microsoft.Samples.Udp` pliku o nazwie `TraceEventsFile.e2e`:  
  
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
  
#### <a name="tracing-structured-data"></a>Śledzenia danych strukturalnych  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metody pobierającej jednego lub większej liczby obiektów, które mają być uwzględniane we wpisie śledzenia. Ogólnie rzecz biorąc <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda jest wywoływana dla każdego obiektu i wynikowy ciąg jest zapisywany jako część wpis śledzenia. Korzystając z <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> do danych wyjściowych danych śledzenia, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>. Wynikowy wpis śledzenia zawiera XML podał <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Oto przykładowy wpis z danych XML aplikacji:  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Podglądu śledzenia rozumie schemat `TraceRecord` element przedstawione wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla go w formacie tabelarycznym. Kanał należy używać tego schematu podczas śledzenia danych strukturalnych aplikacji aby ułatwić użytkownikom Svctraceviewer.exe odczytać danych.

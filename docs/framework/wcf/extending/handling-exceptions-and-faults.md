---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 7fa045dc6fd6e31eccf29e22ae2e212f59dfaec0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111871"
---
# <a name="handling-exceptions-and-faults"></a>Obsługa wyjątków i błędów
Wyjątki są używane do komunikowania błędów lokalnie w ramach usługi lub implementacji klienta. Błędy, z drugiej strony, są używane do komunikowania błędów w granicach usługi, takich jak z serwera do klienta lub odwrotnie. Oprócz usterek kanały transportowe często używają mechanizmów specyficznych dla transportu do przekazywania błędów na poziomie transportu. Na przykład transport HTTP używa kodów stanu, takich jak 404 do komunikowania nieistniejącego adresu URL punktu końcowego (nie ma punktu końcowego, aby wysłać z powrotem błąd). Ten dokument składa się z trzech sekcji, które zawierają wskazówki dla niestandardowych autorów kanałów. Pierwsza sekcja zawiera wskazówki dotyczące tego, kiedy i jak zdefiniować i zgłosić wyjątki. Druga sekcja zawiera wskazówki dotyczące generowania i zużywania usterek. W trzeciej sekcji wyjaśniono, jak dostarczyć informacje śledzenia, aby pomóc użytkownikowi kanału niestandardowego w rozwiązywaniu problemów z uruchomionymi aplikacjami.  
  
## <a name="exceptions"></a>Wyjątki  
 Istnieją dwie rzeczy, o których należy pamiętać podczas zgłaszania wyjątku: Najpierw musi być typu, który pozwala użytkownikom napisać poprawny kod, który może odpowiednio reagować na wyjątek. Po drugie musi dostarczyć wystarczających informacji dla użytkownika, aby zrozumieć, co poszło nie tak, wpływ awarii i jak go naprawić. W poniższych sekcjach przedstawiono wskazówki dotyczące typów wyjątków i komunikatów dla kanałów Programu Windows Communication Foundation (WCF). Istnieją również ogólne wskazówki dotyczące wyjątków w .NET w wskazówki dotyczące projektowania wyjątków dokumentu.  
  
### <a name="exception-types"></a>Typy wyjątków  
 Wszystkie wyjątki generowane przez kanały <xref:System.TimeoutException?displayProperty=nameWithType> <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>muszą być albo , <xref:System.ServiceModel.CommunicationException>lub typu pochodnego z . (Wyjątki, <xref:System.ObjectDisposedException> takie jak mogą być również generowane, ale tylko w celu wskazania, że kod wywołujący niewłaściwie kanał. Jeśli kanał jest używany poprawnie, musi zgłaszać tylko podane wyjątki.) WCF zawiera siedem typów wyjątków, które wynikają z <xref:System.ServiceModel.CommunicationException> i są przeznaczone do użycia przez kanały. Istnieją inne <xref:System.ServiceModel.CommunicationException>wyjątki pochodne, które są przeznaczone do użycia przez inne części systemu. Te typy wyjątków są następujące:  
  
|Typ wyjątku|Znaczenie|Zawartość wyjątku wewnętrznego|Strategia odzyskiwania|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Adres punktu końcowego określony do nasłuchiwania jest już używany.|Jeśli jest obecny, zawiera więcej szczegółów na temat błędu transportu, który spowodował ten wyjątek. Na przykład. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, <xref:System.Net.Sockets.SocketException>lub .|Spróbuj użyć innego adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces nie jest dozwolony dostęp do adresu punktu końcowego określonego do nasłuchiwania.|Jeśli jest obecny, zawiera więcej szczegółów na temat błędu transportu, który spowodował ten wyjątek. Na przykład <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>lub .|Spróbuj z różnymi poświadczeniami.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|Używany <xref:System.ServiceModel.ICommunicationObject> jest w stanie Faulted (aby uzyskać więcej informacji, zobacz [Opis zmian stanu).](understanding-state-changes.md) Należy zauważyć, że gdy obiekt z wieloma oczekującymi wywołaniami przechodzi do stanu Faulted, tylko jedno wywołanie <xref:System.ServiceModel.CommunicationObjectFaultedException>zgłasza wyjątek, który jest związany z awarią, a pozostałe wywołania zgłosić . Ten wyjątek jest zazwyczaj zgłaszany, ponieważ aplikacja pomija jakiś wyjątek i próbuje użyć już wadliwego obiektu, prawdopodobnie w wątku innym niż ten, który przechował oryginalny wyjątek.|Jeśli present zawiera szczegółowe informacje na temat wyjątku wewnętrznego.|Utwórz nowy obiekt. Należy pamiętać, że <xref:System.ServiceModel.ICommunicationObject> w zależności od tego, co spowodowało błąd w pierwszej kolejności, może być inne prace wymagane do odzyskania.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|Używany <xref:System.ServiceModel.ICommunicationObject> został przerwany (aby uzyskać więcej informacji, zobacz [Opis zmian stanu).](understanding-state-changes.md) Podobny <xref:System.ServiceModel.CommunicationObjectFaultedException>do , ten wyjątek <xref:System.ServiceModel.ICommunicationObject.Abort%2A> wskazuje, że aplikacja wywoływała obiekt, prawdopodobnie z innego wątku, a obiekt nie jest już użyteczny z tego powodu.|Jeśli present zawiera szczegółowe informacje na temat wyjątku wewnętrznego.|Utwórz nowy obiekt. Należy zauważyć, że <xref:System.ServiceModel.ICommunicationObject> w zależności od tego, co spowodowało przerwanie w pierwszej kolejności, może być inne prace wymagane do odzyskania.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Docelowy zdalny punkt końcowy nie nasłuchuje. Może to wynikać z dowolnej części adresu punktu końcowego jest niepoprawna, nierozwiązywalna lub punkt końcowy jest w dół. Przykłady obejmują błąd DNS, Menedżer kolejek nie jest dostępny i usługa nie jest uruchomiona.|Wewnętrzny wyjątek zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.|Spróbuj użyć innego adresu. Alternatywnie nadawca może chwilę poczekać i spróbować ponownie w przypadku, gdy usługa została wyłączna|  
|<xref:System.ServiceModel.ProtocolException>|Protokoły komunikacyjne, zgodnie z opisem w zasadach punktu końcowego, są niezgodne między punktami końcowymi. Na przykład przekroczenie rozmiaru zawartości ramek lub przekroczono maksymalny rozmiar wiadomości.|Jeśli obecny zawiera więcej informacji na temat określonego błędu protokołu. Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wewnętrzny wyjątek, gdy przyczyną błędu jest przekroczenie MaxReceivedMessageSize.|Odzyskiwanie: Upewnij się, że ustawienia nadawcy i odebranego protokołu są zgodne. Jednym ze sposobów, aby to zrobić, jest ponowne zaimportowanie metadanych punktu końcowego usługi (zasady) i użycie wygenerowanego powiązania do ponownego wygenerowania kanału.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Zdalny punkt końcowy nasłuchuje, ale nie jest przygotowany do przetwarzania wiadomości.|Jeśli jest obecny, wewnętrzny wyjątek zawiera szczegóły błędu PROTOKOŁU SOAP lub na poziomie transportu.|Odzyskiwanie: Poczekaj i ponów próbę wykonania operacji później.|  
|<xref:System.TimeoutException>|Operacja nie została ukończona w okresie limitu czasu.|Może podać szczegółowe informacje na temat limitu czasu.|Poczekaj i ponów próbę wykonania operacji później.|  
  
 Zdefiniuj nowy typ wyjątku tylko wtedy, gdy ten typ odpowiada określonej strategii odzyskiwania różni się od wszystkich istniejących typów wyjątków. Jeśli zdefiniujesz nowy typ wyjątku, <xref:System.ServiceModel.CommunicationException> musi on pochodzić z lub jednej z jego klas pochodnych.  
  
### <a name="exception-messages"></a>Komunikaty o wyjątkach  
 Komunikaty o wyjątkach są skierowane do użytkownika, a nie do programu, więc powinny one dostarczyć wystarczających informacji, aby pomóc użytkownikowi zrozumieć i rozwiązać problem. Trzy istotne części dobrego komunikatu o wyjątku to:  
  
 co miało miejsce. Podaj jasny opis problemu przy użyciu terminów, które odnoszą się do środowiska użytkownika. Na przykład zły komunikat o wyjątku będzie "Nieprawidłowa sekcja konfiguracji". Pozostawia to użytkownika zastanawiasz się, która sekcja konfiguracji jest niepoprawna i dlaczego jest niepoprawna. Ulepszony komunikat będzie "Nieprawidłowa sekcja \<konfiguracji customBinding>". Jeszcze lepszy komunikat będzie "Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport". Jest to bardzo specyficzny komunikat przy użyciu terminów i nazw, które użytkownik może łatwo zidentyfikować w pliku konfiguracyjnym aplikacji. Jednak nadal brakuje kilku kluczowych składników.  
  
 Znaczenie błędu. O ile komunikat wyraźnie nie określa, co oznacza błąd, użytkownik może się zastanawiać, czy jest to błąd krytyczny lub czy można go zignorować. Ogólnie rzecz biorąc komunikaty powinny prowadzić ze znaczeniem lub znaczeniem błędu. Aby poprawić poprzedni przykład, komunikat może być "ServiceHost nie można otworzyć z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport".  
  
 Jak użytkownik powinien rozwiązać problem. Najważniejszą częścią wiadomości jest pomoc użytkownikowi w rozwiązaniu problemu. Komunikat powinien zawierać pewne wskazówki lub wskazówki dotyczące tego, co należy sprawdzić lub naprawić, aby rozwiązać problem. Na przykład "ServiceHost nie można otworzyć z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport. Upewnij się, że w oprawie znajduje się tylko jeden transport".  
  
## <a name="communicating-faults"></a>Informowanie o błędach  
 ZARÓWNO mydło 1.1, jak i MYDŁO 1.2 definiują specyficzną strukturę usterek. Istnieją pewne różnice między tymi dwoma specyfikacjami, ale ogólnie rzecz biorąc, Message i MessageFault typy są używane do tworzenia i zużywają błędy.  
  
 ![Obsługa wyjątków i usterek](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2SaultComparisonc")  
Usterka SOAP 1.2 (po lewej) i BŁĄD SOAP 1.1 (po prawej). Należy zauważyć, że w soap 1.1 tylko fault element jest obszar nazw kwalifikowany.  
  
 Protokół SOAP definiuje komunikat o błędzie jako komunikat zawierający tylko `<env:Fault>`element błędu (element, którego nazwą jest) jako element podrzędny `<env:Body>`. Zawartość elementu usterki różni się nieznacznie między MYDŁEM 1.1 a MYDŁEM 1.2, jak pokazano na rysunku 1. Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasa normalizuje te różnice w jeden model obiektu:  
  
```csharp
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
  
 Właściwość `Code` odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ usterki. PROTOKÓŁ SOAP 1.2 definiuje pięć `faultCode` dopuszczalnych wartości dla (na przykład `Subcode` Nadawca i Odbiorca) i definiuje element, który może zawierać dowolną wartość podkodu. (Lista dopuszczalnych kodów usterek i ich znaczenie znajduje się w [specyfikacji protokołu SOAP 1.2).](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) SOAP 1.1 ma nieco inny mechanizm: `faultCode` definiuje cztery wartości (na przykład klient i serwer), które można rozszerzyć, definiując całkowicie nowe lub `faultCodes`za pomocą notacji kropkowej, aby utworzyć bardziej szczegółowe , na przykład Client.Authentication.  
  
 Podczas korzystania z messagefault do programowania błędów, FaultCode.Name i FaultCode.Namespace mapuje do nazwy i `env:Code` obszaru nazw protokołu SOAP `faultCode`1.2 lub SOAP 1.1 . FaultCode.SubCode mapuje `env:Subcode` do protokołu SOAP 1.2 i jest zerowy dla protokołu SOAP 1.1.  
  
 Należy utworzyć nowe podkody błędów (lub nowe kody usterek, jeśli używasz protokołu SOAP 1.1), jeśli programowo rozróżnia się usterkę. Jest to analogiczne do tworzenia nowego typu wyjątku. Należy unikać używania notacji kropkowej z kodami usterek SOAP 1.1. (Profil [podstawowy WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) również zniechęca do używania notacji dot kodu błędu).  
  
```csharp
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
  
 Właściwość `Reason` odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) czytelny dla człowieka opis stanu błędu analogiczne do komunikatu wyjątku. Klasa `FaultReason` (i `env:Reason/faultString`SOAP) ma wbudowaną obsługę wielu tłumaczeń w interesie globalizacji.  
  
```csharp
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
  
 Zawartość szczegółów usterki są widoczne na MessageFault `GetDetail` \<przy użyciu różnych `GetReaderAtDetailContents`metod, w tym T> i (). Szczegóły usterki jest nieprzezroczysty element do przenoszenia dodatkowych szczegółów na temat usterki. Jest to przydatne, jeśli istnieje kilka dowolnych szczegółów strukturalnych, które chcesz przeprowadzić z błędem.  
  
### <a name="generating-faults"></a>Generowanie błędów  
 W tej sekcji opisano proces generowania błędu w odpowiedzi na warunek błędu wykryty w kanale lub we właściwości wiadomości utworzonej przez kanał. Typowym przykładem jest wysłanie z powrotem błędu w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.  
  
 Podczas generowania błędu kanał niestandardowy nie powinien wysyłać usterki bezpośrednio, a raczej powinien zgłosić wyjątek i pozwolić warstwie powyżej zdecydować, czy przekonwertować ten wyjątek na błąd i jak go wysłać. Aby pomóc w tej konwersji, `FaultConverter` kanał powinien zapewnić implementację, która może konwertować wyjątek zgłaszany przez kanał niestandardowy na odpowiedni błąd. `FaultConverter`jest zdefiniowany jako:  
  
```csharp
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
  
 Każdy kanał, który generuje niestandardowe błędy, musi `FaultConverter` `GetProperty<FaultConverter>`zaimplementować i zwrócić go z wywołania do . Implementacja `OnTryCreateFaultMessage` niestandardowa musi przekonwertować wyjątek na błąd `FaultConverter`lub delegować do kanału wewnętrznego . Jeśli kanał jest transportem, musi przekonwertować wyjątek lub `FaultConverter` delegować `FaultConverter` do kodera lub domyślnie podany w WCF . Domyślnie `FaultConverter` konwertuje błędy odpowiadające komunikatom o błędach określonym przez WS-Addressing i SOAP. Oto przykład `OnTryCreateFaultMessage` implementacji.  
  
```csharp
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
  
 Implikacją tego wzorca jest to, że wyjątki generowane między warstwami dla warunków błędów, które wymagają błędów, muszą zawierać wystarczającą ilość informacji dla odpowiedniego generatora usterek, aby utworzyć poprawny błąd. Jako autor kanału niestandardowego można zdefiniować typy wyjątków, które odpowiadają różnym warunkom błędów, jeśli takie wyjątki jeszcze nie istnieją. Należy zauważyć, że wyjątki przechodzące przez warstwy kanału powinny komunikować się warunek błędu, a nie nieprzezroczyste dane błędów.  
  
### <a name="fault-categories"></a>Kategorie usterek  
 Zasadniczo istnieją trzy kategorie usterek:  
  
1. Błędy, które są wszechobecne w całym stosie. Te błędy mogą wystąpić w dowolnej warstwie w stosie kanału, na przykład InvalidCardinalityAddressingException.  
  
2. Błędy, które można napotkać w dowolnym miejscu powyżej określonej warstwy w stosie, na przykład niektóre błędy, które odnoszą się do transakcji przepływanych lub ról zabezpieczeń.  
  
3. Błędy, które są skierowane do pojedynczej warstwy w stosie, na przykład błędy, takie jak błędy numerów sekwencyjnych WS-RM.  
  
 Kategorii 1. Usterki są zazwyczaj WS-Adresowanie i błędy PROTOKOŁU SOAP. Klasa `FaultConverter` podstawowa dostarczana przez WCF konwertuje błędy odpowiadające komunikatom o błędach określonym przez WS-Addressing i SOAP, dzięki czemu nie trzeba samodzielnie obsługiwać konwersji tych wyjątków.  
  
 Kategorii 2. Błędy występują, gdy warstwa dodaje właściwość do wiadomości, która nie zużywa całkowicie informacji o wiadomości, które odnoszą się do tej warstwy. Błędy mogą być wykryte później, gdy wyższa warstwa prosi właściwość message do przetwarzania informacji o wiadomościach dalej. Takie kanały `GetProperty` powinny implementować określony wcześniej, aby umożliwić wyższej warstwie odesłanie prawidłowego błędu. Przykładem tego jest TransactionMessageProperty. Ta właściwość jest dodawana do wiadomości bez pełnej weryfikacji wszystkich danych w nagłówku (może to obejmować skontaktowanie się z koordynatorem transakcji rozproszonych (DTC).  
  
 Kategorii 3. Usterki są generowane i wysyłane tylko przez jedną warstwę w procesorze. W związku z tym wszystkie wyjątki są zawarte w warstwie. Aby poprawić spójność między kanałami i ułatwić konserwację, kanał niestandardowy powinien używać wzorca określonego wcześniej do generowania komunikatów o błędach nawet w przypadku błędów wewnętrznych.  
  
### <a name="interpreting-received-faults"></a>Interpretowanie odebranych błędów  
 Ta sekcja zawiera wskazówki dotyczące generowania odpowiedniego wyjątku podczas odbierania komunikatu o błędzie. Drzewo decyzyjne do przetwarzania wiadomości w każdej warstwie stosu jest w następujący sposób:  
  
1. Jeśli warstwa uzna wiadomość za nieprawidłową, warstwa powinna wykonać przetwarzanie "nieprawidłowej wiadomości". Takie przetwarzanie jest specyficzne dla warstwy, ale może obejmować upuszczenie wiadomości, śledzenie lub zgłaszanie wyjątku, który zostanie przekonwertowany na błąd. Przykłady obejmują zabezpieczenia odbieranie wiadomości, która nie jest poprawnie zabezpieczona, lub RM odbieranie wiadomości ze złym numerem sekwencyjnym.  
  
2. W przeciwnym razie jeśli komunikat jest komunikatem o błędzie, który ma zastosowanie w szczególności do warstwy, a wiadomość nie ma znaczenia poza interakcją warstwy, warstwa powinna obsługiwać warunek błędu. Przykładem tego jest błąd odmowy sekwencji RM, który jest bez znaczenia dla warstw powyżej kanału RM i który implikuje błąd kanału RM i wyrzucanie z oczekujących operacji.  
  
3. W przeciwnym razie wiadomość powinna zostać zwrócona z request() lub receive(). Obejmuje to przypadki, w których warstwa rozpoznaje błąd, ale błąd tylko wskazuje, że żądanie nie powiodło się i nie oznacza błąd kanału i wyrzucanie z oczekujących operacji. Aby poprawić użyteczność w takim przypadku, `GetProperty<FaultConverter>` warstwa `FaultConverter` powinna zaimplementować i zwrócić klasę `OnTryCreateException`pochodną, która może przekonwertować błąd na wyjątek przez zastąpienie .  
  
 Następujący model obiektu obsługuje konwertowanie komunikatów na wyjątki:  
  
```csharp
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
  
 Warstwa kanału `GetProperty<FaultConverter>` można zaimplementować do obsługi konwersji komunikatów o błędach do wyjątków. Aby to zrobić, `OnTryCreateException` należy zastąpić i sprawdzić komunikat o błędzie. Jeśli zostanie rozpoznana, wykonaj konwersję, poproś kanał wewnętrzny o jej przekonwertowanie. Kanały transportu `FaultConverter.GetDefaultFaultConverter` należy delegować do uzyskania domyślnego soap/WS-Addressing FaultConverter.  
  
 Typowa implementacja wygląda następująco:  
  
```csharp
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
  
 W przypadku określonych warunków błędów, które mają różne scenariusze odzyskiwania, należy rozważyć zdefiniowanie klasy pochodnej `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Przetwarzanie MustUnderstand  
 PROTOKÓŁ SOAP definiuje ogólną usterkę sygnalizacji, że wymagany nagłówek nie został zrozumiany przez odbiornik. Ten błąd jest `mustUnderstand` znany jako usterka. W WCF kanały `mustUnderstand` niestandardowe nigdy nie generują błędów. Zamiast tego WCF Dispatcher, który znajduje się w górnej części stosu komunikacji WCF, sprawdza, czy wszystkie nagłówki, które zostały oznaczone jako MustUnderstand= true zostały zrozumiane przez podstawowy stos. Jeśli którekolwiek nie zostały `mustUnderstand` zrozumiane, błąd jest generowany w tym momencie. (Użytkownik może wyłączyć to `mustUnderstand` przetwarzanie i aplikacja odbierać wszystkie nagłówki wiadomości. W takim przypadku aplikacja jest `mustUnderstand` odpowiedzialna za przetwarzanie.) Wygenerowany błąd zawiera nierozdumiony nagłówek, który zawiera nazwy wszystkich nagłówków z MustUnderstand = true, które nie zostały zrozumiane.  
  
 Jeśli kanał protokołu wysyła niestandardowy nagłówek z MustUnderstand = true i odbiera `mustUnderstand` błąd, należy dowiedzieć się, czy ten błąd jest z powodu nagłówka, który wysłał. Istnieją dwa elementy `MessageFault` członkowskie w klasie, które są przydatne do tego:  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault`zwraca, `true` jeśli usterka jest wadą. `mustUnderstand` `WasHeaderNotUnderstood`zwraca, `true` jeśli nagłówek o określonej nazwie i obszarze nazw jest uwzględniony w usterce jako nagłówek NotUnderstood.  W przeciwnym `false`razie zwraca .  
  
 Jeśli kanał emituje nagłówek, który jest oznaczony MustUnderstand = true, a następnie tej `mustUnderstand` warstwy należy również zaimplementować wzorzec interfejsu API generowania wyjątków i należy przekonwertować błędy spowodowane przez ten nagłówek do bardziej użyteczny wyjątek, jak opisano wcześniej.  
  
## <a name="tracing"></a>Śledzenie  
 .NET Framework zapewnia mechanizm śledzenia wykonywania programu jako sposób na pomoc w diagnozowaniu aplikacji produkcyjnych lub sporadyczne problemy, gdzie nie jest możliwe po prostu dołączyć debugera i krok po kroku przez kod. Podstawowe składniki tego mechanizmu <xref:System.Diagnostics?displayProperty=nameWithType> znajdują się w przestrzeni nazw i składają się z:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>które mają być napisane, który jest abstrakcyjną klasą podstawową dla konkretnych słuchaczy, które otrzymują informacje, które mają być śledzone z <xref:System.Diagnostics.TraceSource> i wyjście go do miejsca docelowego specyficzne dla odbiornika. Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML. Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który pozwala użytkownikowi aplikacji kontrolować szczegółowość śledzenia i jest zazwyczaj określony w konfiguracji.  
  
- Oprócz podstawowych składników można użyć [narzędzia Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania i wyszukiwania śladów WCF. Narzędzie zostało zaprojektowane specjalnie dla plików śledzenia generowanych przez <xref:System.Diagnostics.XmlWriterTraceListener>WCF i wypisywane za pomocą . Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenie.  
  
 ![Obsługa wyjątków i usterek](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Śledzenie z kanału niestandardowego  
 Kanały niestandardowe powinny zapisywać komunikaty śledzenia, aby pomóc w diagnozowaniu problemów, gdy nie jest możliwe dołączenie debugera do uruchomionej aplikacji. Obejmuje to dwa zadania wysokiego poziomu: tworzenie wystąpienia <xref:System.Diagnostics.TraceSource> i wywoływanie jego metod do zapisu śladów.  
  
 Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, określony ciąg staje się nazwą tego źródła. Ta nazwa jest używana do konfigurowania (włącz/wyłącz/ustaw poziom śledzenia) źródła śledzenia. Pojawia się również w danych wyjściowych śledzenia. Kanały niestandardowe powinny używać unikatowej nazwy źródła, aby pomóc czytelnikom danych wyjściowych śledzenia zrozumieć, skąd pochodzą informacje śledzenia. Przy użyciu nazwy zestawu, który zapisuje informacje jako nazwę źródła śledzenia jest powszechną praktyką. Na przykład WCF używa System.ServiceModel jako źródła śledzenia informacji zapisanych z System.ServiceModel zestawu.  
  
 Gdy masz źródło śledzenia, można <xref:System.Diagnostics.TraceSource.TraceData%2A> <xref:System.Diagnostics.TraceSource.TraceEvent%2A>wywołać <xref:System.Diagnostics.TraceSource.TraceInformation%2A> jego , lub metody zapisu śledzenia wpisów do odbiorników śledzenia. Dla każdego wpisu śledzenia, który piszesz, należy sklasyfikować <xref:System.Diagnostics.TraceEventType>typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w . Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji określają, czy wpis śledzenia jest wyprowadzany do odbiornika. Na przykład ustawienie poziomu śledzenia `Warning` w `Warning` `Error` konfiguracji, aby umożliwiać zapisanie wpisów śledzenia i `Critical` śledzenia, ale blokuje wpisy informacje i pełne. Oto przykład tworzenia wystąpienia źródła śledzenia i wypisywanie wpisu na poziomie informacji:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> Zdecydowanie zaleca się określenie nazwy źródła śledzenia, która jest unikatowa dla kanału niestandardowego, aby ułatwić czytnikom danych wyjściowych zrozumienie, skąd pochodzi dane wyjściowe.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integracja z przeglądarką śledzenia  
 Ślady generowane przez kanał mogą być dane wyjściowe w formacie czytelnym dla [narzędzia Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako odbiornik śledzenia. To nie jest coś, co ty, jako deweloper kanału, musisz zrobić. Jest to raczej użytkownik aplikacji (lub osoba, która rozwiązuje problemy z aplikacją), która musi skonfigurować ten odbiornik śledzenia w pliku konfiguracyjnym aplikacji. Na przykład następujące wyjścia konfiguracyjne <xref:System.ServiceModel?displayProperty=nameWithType> śledzą `Microsoft.Samples.Udp` informacje zarówno `TraceEventsFile.e2e`z i do pliku o nazwie:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metodę, która przyjmuje jeden lub więcej obiektów, które mają być uwzględnione we wpisie śledzenia. Ogólnie rzecz <xref:System.Object.ToString%2A?displayProperty=nameWithType> biorąc metoda jest wywoływana na każdy obiekt i wynikowy ciąg jest zapisywany jako część wpisu śledzenia. Podczas <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> korzystania z śledzenia danych wyjściowych, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>. Wynikowy wpis śledzenia zawiera kod XML dostarczony przez plik <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Oto przykładowy wpis z danymi aplikacji XML:  
  
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
  
 Przeglądarka śledzenia WCF rozumie schemat `TraceRecord` elementu pokazano wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla je w formacie tabelarycznym. Kanał powinien używać tego schematu podczas śledzenia danych aplikacji strukturalnych, aby pomóc użytkownikom Svctraceviewer.exe odczytać dane.

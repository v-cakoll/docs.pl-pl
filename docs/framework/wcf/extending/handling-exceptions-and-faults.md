---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 676ebe999c72ed678b7432ec154b1ec104b4d6cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795701"
---
# <a name="handling-exceptions-and-faults"></a>Obsługa wyjątków i błędów
Wyjątki są używane do komunikacji błędów lokalnie w ramach usługi lub implementacji klienta. Z drugiej strony są używane do przekazywania błędów między granicami usług, na przykład z serwera do klienta lub na odwrót. Oprócz błędów, kanały transportu często używają mechanizmów specyficznych dla transportu do przekazywania błędów na poziomie transportu. Na przykład transport HTTP używa kodów stanu, takich jak 404 do przekazywania nieistniejącego adresu URL punktu końcowego (nie istnieje punkt końcowy do wysłania błędu). Ten dokument składa się z trzech sekcji, które zawierają wskazówki dotyczące niestandardowych autorów kanałów. W pierwszej sekcji znajdują się wskazówki dotyczące tego, kiedy i jak definiować i generować wyjątki. Druga sekcja zawiera wskazówki dotyczące generowania i zużywania błędów. Trzecia sekcja wyjaśnia, jak podać informacje o śledzeniu, aby ułatwić użytkownikowi niestandardowego kanału Rozwiązywanie problemów z uruchamianiem aplikacji.  
  
## <a name="exceptions"></a>Wyjątki  
 Podczas zgłaszania wyjątku należy pamiętać o dwóch kwestiach: Najpierw musi być typu, który umożliwia użytkownikom pisanie poprawnego kodu, który może reagować odpowiednio do wyjątku. Po drugie należy zapewnić użytkownikowi wystarczającą ilość informacji, aby zrozumieć, co poszło źle, wpływ na awarie oraz sposób jego rozwiązania. Poniższe sekcje zawierają wskazówki dotyczące typów wyjątków i komunikatów dla kanałów Windows Communication Foundation (WCF). Istnieją także ogólne wskazówki dotyczące wyjątków w programie .NET w temacie Wskazówki dotyczące projektowania dla dokumentu wyjątków.  
  
### <a name="exception-types"></a>Typy wyjątków  
 Wszystkie wyjątki zgłoszone przez kanały muszą być albo <xref:System.TimeoutException?displayProperty=nameWithType>albo <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>albo typem pochodnym <xref:System.ServiceModel.CommunicationException>. (Takie <xref:System.ObjectDisposedException> wyjątki mogą również być zgłaszane, ale tylko wtedy, gdy kod wywołujący nie użył kanału. Jeśli kanał jest używany prawidłowo, musi zgłosić tylko określone wyjątki. Funkcja WCF udostępnia siedem typów wyjątków, które <xref:System.ServiceModel.CommunicationException> pochodzą z i są przeznaczone do użycia przez kanały. Istnieją inne <xref:System.ServiceModel.CommunicationException>wyjątki pochodne, które są przeznaczone do użycia przez inne części systemu. Te typy wyjątków są następujące:  
  
|Typ wyjątku|Znaczenie|Wewnętrzna zawartość wyjątku|Strategia odzyskiwania|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Adres punktu końcowego określony do nasłuchiwania jest już używany.|Jeśli jest obecny, zawiera więcej szczegółowych informacji o błędzie transportu, który spowodował ten wyjątek. Na przykład. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>lub .<xref:System.Net.Sockets.SocketException>|Spróbuj użyć innego adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces nie ma dostępu do adresu punktu końcowego określonego do nasłuchiwania.|Jeśli jest obecny, zawiera więcej szczegółowych informacji o błędzie transportu, który spowodował ten wyjątek. Na przykład <xref:System.IO.PipeException>, lub <xref:System.Net.HttpListenerException>.|Spróbuj użyć innych poświadczeń.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|Używany jest stan błędu (Aby uzyskać więcej informacji, zobacz temat [Informacje o zmianach stanu](understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject> Należy zauważyć, że gdy obiekt z wieloma oczekującymi wywołaniami przechodzi do stanu błędu, tylko jedno wywołanie zgłasza wyjątek związany z awarią, a pozostałe wywołania generują <xref:System.ServiceModel.CommunicationObjectFaultedException>. Ten wyjątek jest zazwyczaj zgłaszany, ponieważ aplikacja zaobserwuje wyjątek i próbuje użyć już uszkodzonego obiektu, prawdopodobnie w wątku innym niż ten, który przechwycił oryginalny wyjątek.|Jeśli jest obecny, zawiera szczegółowe informacje o wyjątku wewnętrznym.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego <xref:System.ServiceModel.ICommunicationObject> , co spowodowało błąd w pierwszym miejscu, może być konieczne wykonanie innych czynności wymaganych do odzyskania.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|Używany program został przerwany (Aby uzyskać więcej informacji, zobacz temat [Informacje o zmianach stanu](understanding-state-changes.md)). <xref:System.ServiceModel.ICommunicationObject> Podobnie jak <xref:System.ServiceModel.ICommunicationObject.Abort%2A> , jego wyjątek wskazuje, że aplikacja została wywołana dla obiektu, prawdopodobnie z innego wątku, a obiekt nie jest już użyteczny z tego powodu. <xref:System.ServiceModel.CommunicationObjectFaultedException>|Jeśli jest obecny, zawiera szczegółowe informacje o wyjątku wewnętrznym.|Utwórz nowy obiekt. Należy pamiętać, że w zależności od tego <xref:System.ServiceModel.ICommunicationObject> , co spowodowało przerwanie działania w pierwszym miejscu, może być konieczne wykonanie innych czynności.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Docelowy zdalny punkt końcowy nie nasłuchuje. Może to wynikać z nieprawidłowej części adresu punktu końcowego, nierozwiązywalny lub punktu końcowego. Przykłady obejmują błąd DNS, Menedżer kolejki jest niedostępny i usługa nie jest uruchomiona.|Wewnętrzny wyjątek zapewnia szczegóły, zazwyczaj z bazowego transportu.|Spróbuj użyć innego adresu. Alternatywnie nadawca może poczekać chwilę i spróbować ponownie w przypadku, gdy usługa nie działa|  
|<xref:System.ServiceModel.ProtocolException>|Protokoły komunikacyjne, zgodnie z opisem w zasadach punktu końcowego, są niezgodne między punktami końcowymi. Na przykład niezgodność typu ramki lub maksymalny rozmiar komunikatu został przekroczony.|Jeśli jest obecny, zawiera więcej informacji o konkretnym błędzie protokołu. Na przykład jest <xref:System.ServiceModel.QuotaExceededException> wewnętrzny wyjątek, gdy przyczyną błędu jest przekraczanie MaxReceivedMessageSize.|Przywrócenia Upewnij się, że ustawienia nadawcy i odebrane protokoły są zgodne. Aby to zrobić, należy ponownie zaimportować metadane punktu końcowego usługi i użyć wygenerowanego powiązania do ponownego utworzenia kanału.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Zdalny punkt końcowy nasłuchuje, ale nie jest przygotowany do przetwarzania komunikatów.|Jeśli jest obecny, wyjątek wewnętrzny zawiera szczegóły błędu protokołu SOAP lub poziomu transportu.|Przywrócenia Poczekaj, a następnie spróbuj ponownie wykonać operację później.|  
|<xref:System.TimeoutException>|Nie można ukończyć operacji przed upływem limitu czasu.|Może podawać szczegółowe informacje o limicie czasu.|Poczekaj, a następnie spróbuj ponownie wykonać operację później.|  
  
 Zdefiniuj nowy typ wyjątku tylko wtedy, gdy ten typ odnosi się do konkretnej strategii odzyskiwania innej niż wszystkie istniejące typy wyjątków. Jeśli zdefiniujesz nowy typ wyjątku, musi on pochodzić z <xref:System.ServiceModel.CommunicationException> lub jednej z jej klas pochodnych.  
  
### <a name="exception-messages"></a>Komunikaty o wyjątkach  
 Komunikaty o wyjątkach są wskazywane przez użytkownika, który nie jest programem, dlatego powinny udostępnić wystarczające informacje, aby pomóc użytkownikom zrozumieć i rozwiązać problem. Trzy podstawowe części dobrego komunikatu o wyjątku:  
  
 Co się stało. Podaj jasny opis problemu przy użyciu terminów związanych ze środowiskami użytkownika. Na przykład komunikat o nieprawidłowym wyjątku to "Nieprawidłowa sekcja konfiguracji". Spowoduje to pozostawienie użytkownika, którego sekcja konfiguracji jest nieprawidłowa i dlaczego jest niepoprawna. Ulepszony komunikat to "Nieprawidłowa niestandardowa \<sekcja konfiguracji >". Jeszcze lepszym komunikatem może być "nie można dodać transportu o nazwie" Moje Transporting "do powiązania o nazwie Moje powiązanie, ponieważ powiązanie ma już transport o nazwie" transport ". Jest to bardzo konkretny komunikat z użyciem warunków i nazw, które użytkownik może łatwo zidentyfikować w pliku konfiguracji aplikacji. Jednak nadal brakuje kilku kluczowych składników.  
  
 Istotność błędu. Chyba że komunikat wskazuje, że błąd oznacza, użytkownik może się zastanawiać, czy jest to błąd krytyczny czy można go zignorować. Ogólnie rzecz biorąc komunikaty powinny prowadzić do znaczenia lub znaczenia błędu. Aby ulepszyć poprzedni przykład, komunikat może być następujący: "nie można otworzyć ServiceHost z powodu błędu konfiguracji. Nie można dodać transportu o nazwie "Moje transtransport" do powiązania o nazwie Moje powiązanie, ponieważ powiązanie ma już transport o nazwie "Moje transtransport".  
  
 Jak użytkownik powinien rozwiązać problem. Najważniejszym elementem wiadomości jest pomoc w rozwiązaniu problemu. Komunikat powinien zawierać wskazówki lub wskazówki dotyczące tego, co należy sprawdzić lub naprawić, aby rozwiązać problem. Na przykład: "nie można otworzyć elementu ServiceHost z powodu błędu konfiguracji. Nie można dodać transportu o nazwie "Moje transtransport" do powiązania o nazwie Moje powiązanie, ponieważ powiązanie ma już transport o nazwie "Moje transtransport". Upewnij się, że w powiązaniu istnieje tylko jeden transport.  
  
## <a name="communicating-faults"></a>Komunikacja błędów  
 Protokoły SOAP 1,1 i SOAP 1,2 definiują określoną strukturę błędów. Istnieją pewne różnice między tymi dwiema specyfikacjami, ale ogólnie rzecz biorąc, wiadomości i typy MessageFault są używane do tworzenia i korzystania z błędów.  
  
 ![Obsługa wyjątków i błędów](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")  
Błąd protokołu SOAP 1,2 (z lewej) i błąd protokołu SOAP 1,1 (prawo). Należy pamiętać, że w protokole SOAP 1,1 tylko element Fault ma kwalifikowaną przestrzeń nazw.  
  
 Protokół SOAP definiuje komunikat o błędzie jako komunikat, który zawiera tylko element błędu (element, którego nazwa jest `<env:Fault>`) jako `<env:Body>`element podrzędny. Zawartość elementu Fault różni się nieco od protokołu SOAP 1,1 i protokołu SOAP 1,2, jak pokazano na rysunku 1. <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> Jednak Klasa normalizuje te różnice w jednym modelu obiektów:  
  
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
  
 Właściwość odnosi `env:Code` się do (lub `faultCode` w SOAP 1,1) i identyfikuje typ błędu. `Code` Protokół SOAP 1,2 definiuje pięć wartości dopuszczalnych `faultCode` dla (na przykład nadawcy i odbiorcę) i `Subcode` definiuje element, który może zawierać dowolną wartość kodu. (Patrz [Specyfikacja protokołu SOAP 1,2](https://go.microsoft.com/fwlink/?LinkId=95176) , aby uzyskać listę dozwolonych kodów błędów i ich znaczenie). Protokół SOAP 1,1 ma nieco inny mechanizm: Definiuje cztery `faultCode` wartości (na przykład klienta i serwera), które można rozszerzyć przez zdefiniowanie zupełnie nowych lub przy użyciu notacji kropkowej w celu utworzenia bardziej szczegółowych `faultCodes`informacji, na przykład Client. Authentication.  
  
 W przypadku używania MessageFault z błędami programu FaultCode.Name i FaultCode. Namespace mapuje do nazwy i przestrzeni nazw protokołu SOAP 1,2 `env:Code` lub SOAP 1,1. `faultCode` FaultCode. Subcode mapuje do `env:Subcode` protokołu SOAP 1,2 i ma wartość null dla protokołu SOAP 1,1.  
  
 Należy utworzyć nowe podkody błędów (lub nowe kody błędów w przypadku korzystania z protokołu SOAP 1,1), jeśli jest to interesujące do programistycznego odróżnienia błędu. Jest to analogiczne do tworzenia nowego typu wyjątku. Należy unikać używania notacji kropki z kodami błędów SOAP 1,1. ( [Profil usługi WS-I Basic](https://go.microsoft.com/fwlink/?LinkId=95177) odradza również korzystanie z notacji kropki kodu błędu).  
  
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
  
 Właściwość odnosi `env:Reason` się do (lub `faultString` w protokole SOAP 1,1) opis nieprawidłowego stanu błędu analogicznie do komunikatu o wyjątku. `Reason` Klasa (i SOAP `env:Reason/faultString`) ma wbudowaną obsługę mającą wiele tłumaczeń w interesie globalizacji. `FaultReason`  
  
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
  
 Zawartość szczegółów błędu jest narażona na MessageFault przy użyciu różnych metod, `GetDetail`w \<tym T `GetReaderAtDetailContents`> i (). Szczegóły błędu to nieprzezroczysty element służący do przeprowadzenia dodatkowych szczegółów dotyczących błędu. Jest to przydatne, jeśli istnieje pewne szczegółowe informacje strukturalne, które chcesz przenieść wraz z błędem.  
  
### <a name="generating-faults"></a>Generowanie błędów  
 W tej sekcji opisano proces generowania błędu w odpowiedzi na warunek błędu wykryty w kanale lub we właściwości komunikatu utworzonej przez kanał. Typowy przykład wysyła błąd w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.  
  
 Podczas generowania błędu kanał niestandardowy nie powinien wysyłać błędu bezpośrednio, raczej powinien zgłosić wyjątek i pozwolić warstwie powyżej zdecydować, czy skonwertować ten wyjątek na błąd i jak go wysłać. Aby pomóc w tej konwersji, kanał powinien zapewnić `FaultConverter` implementację, która może przekonwertować wyjątek zgłoszony przez niestandardowy kanał na odpowiedni błąd. `FaultConverter`jest zdefiniowany jako:  
  
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
  
 Każdy kanał generujący błędy niestandardowe musi implementować `FaultConverter` i zwracać z wywołania do. `GetProperty<FaultConverter>` Implementacja niestandardowa `OnTryCreateFaultMessage` musi wykonać konwersję wyjątku na błąd lub delegata do wewnętrznego `FaultConverter`kanału. Jeśli kanał jest transportem, należy przekonwertować wyjątek lub obiekt delegowany do kodera `FaultConverter` lub domyślnego ustawienia `FaultConverter` usługi WCF. Domyślnie `FaultConverter` konwertuje błędy odpowiadające komunikatom o błędach określonych przez WS-Addressing i SOAP. Oto przykładowa `OnTryCreateFaultMessage` implementacja.  
  
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
  
 Implikacje tego wzorca polega na tym, że wyjątki zgłaszane między warstwami dla warunków błędów, które wymagają błędów, muszą zawierać wystarczające informacje dla odpowiedniego generatora błędów w celu utworzenia poprawnego błędu. Jako autor niestandardowego kanału możesz zdefiniować typy wyjątków odpowiadające różnym warunkom błędów, jeśli takie wyjątki jeszcze nie istnieją. Należy zauważyć, że wyjątki, które przechodzą warstwy kanałów, powinny przekazywać warunek błędu, a nie nieprzezroczyste dane błędów.  
  
### <a name="fault-categories"></a>Kategorie błędów  
 Zazwyczaj istnieją trzy kategorie błędów:  
  
1. Błędy, które są rozpowszechnione w całym stosie. Te błędy można napotkać w dowolnej warstwie stosu kanału, na przykład InvalidCardinalityAddressingException.  
  
2. Błędy, które mogą wystąpić w dowolnym miejscu powyżej pewnej warstwy na stosie, na przykład niektóre błędy odnoszące się do transakcji przepływu lub do ról zabezpieczeń.  
  
3. Błędy, które są kierowane do pojedynczej warstwy w stosie, na przykład błędy, takie jak błędne numery sekwencyjne WS-RM.  
  
 Kategoria 1. Błędy to ogólnie rozwiązywanie adresów WS-Addressing i SOAP. Klasa bazowa `FaultConverter` dostarczana przez funkcję WCF konwertuje błędy odpowiadające komunikatom o błędach określone przez WS-Addressing i SOAP, aby nie trzeba było ich samodzielnie obsłużyć konwersji.  
  
 Kategoria 2. Błędy występują, gdy warstwa dodaje właściwość do wiadomości, która nie korzysta całkowicie z informacji o komunikatach odnoszących się do tej warstwy. Błędy mogą zostać wykryte później, gdy wyższa warstwa będzie pytać Właściwość komunikatu o dalsze przetwarzanie informacji o komunikatach. Takie kanały powinny implementować `GetProperty` określony wcześniej, aby umożliwić wyższej warstwie wysłanie poprawnego błędu. Przykładem jest TransactionMessageProperty. Ta właściwość jest dodawana do komunikatu bez pełnej weryfikacji wszystkich danych w nagłówku (może to wiązać się z kontaktem z koordynatorem transakcji rozproszonych (DTC).  
  
 Kategoria 3. Błędy są generowane i wysyłane przez pojedynczą warstwę w procesorze. W związku z tym wszystkie wyjątki są zawarte w warstwie. Aby zwiększyć spójność między kanałami i ułatwić konserwację, kanał niestandardowy powinien używać określonego wcześniej wzorca do generowania komunikatów o błędach nawet w przypadku błędów wewnętrznych.  
  
### <a name="interpreting-received-faults"></a>Interpretowanie odebranych błędów  
 Ta sekcja zawiera wskazówki dotyczące generowania odpowiedniego wyjątku podczas otrzymywania komunikatu o błędzie. Drzewo decyzyjne służące do przetwarzania komunikatów w każdej warstwie stosu jest następujące:  
  
1. Jeśli warstwa traktuje komunikat jako nieprawidłowy, warstwa powinna wykonać przetwarzanie "nieprawidłowy komunikat". Takie przetwarzanie jest specyficzne dla warstwy, ale może obejmować porzucanie komunikatu, śledzenie lub zgłaszanie wyjątku, który jest konwertowany na błąd. Przykłady obejmują zabezpieczenia otrzymujące komunikat, który nie jest prawidłowo zabezpieczony lub Menedżer zasobów otrzymuje komunikat z nieprawidłowym numerem sekwencyjnym.  
  
2. W przeciwnym razie, jeśli komunikat jest komunikatem o błędzie, który jest stosowany w odróżnieniu od warstwy, a komunikat nie ma znaczenia poza interakcją warstwy, warstwa powinna obsłużyć warunek błędu. Przykładem jest to, że sekwencja RM odrzuciła błąd, który jest bez względu na warstwy powyżej kanału RM i który oznacza błąd kanału RM i wyrzucanie z oczekujących operacji.  
  
3. W przeciwnym razie komunikat powinien zostać zwrócony z żądania () lub Receive (). Obejmuje to przypadki, w których warstwa rozpoznaje błąd, ale tylko wskazuje, że żądanie nie powiodło się i nie implikuje błędu kanału i zostanie wyrzucane z oczekujących operacji. Aby poprawić użyteczność w takim przypadku, warstwa powinna zaimplementować `GetProperty<FaultConverter>` i `FaultConverter` zwrócić klasę pochodną, która może skonwertować błąd na wyjątek przez zastąpienie `OnTryCreateException`.  
  
 Poniższy model obiektów obsługuje konwertowanie komunikatów na wyjątki:  
  
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
  
 Warstwę kanału można zaimplementować `GetProperty<FaultConverter>` w celu obsługi konwersji komunikatów o błędach na wyjątki. Aby to zrobić, Zastąp `OnTryCreateException` i Sprawdź komunikat o błędzie. Jeśli jest rozpoznawana, wykonaj konwersję, w przeciwnym razie podawaj wewnętrzny kanał, aby go przekonwertować. Kanały transportowe powinny `FaultConverter.GetDefaultFaultConverter` być delegowane do programu, aby można było korzystać z protokołu SOAP/WS-Addressing FaultConverter.  
  
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
  
 W przypadku określonych warunków błędu, które mają odrębne scenariusze odzyskiwania, należy rozważyć Definiowanie `ProtocolException`klasy pochodnej.  
  
### <a name="mustunderstand-processing"></a>Przetwarzanie MustUnderstand  
 Protokół SOAP definiuje ogólny błąd sygnalizujący, że wymagany nagłówek nie został rozpoznany przez odbiornik. Ten błąd jest znany jako `mustUnderstand` błąd. W programie WCF kanały niestandardowe nigdy nie `mustUnderstand` generują błędów. Zamiast tego, Dyspozytor WCF, który znajduje się w górnej części stosu komunikacji WCF, sprawdza, czy wszystkie nagłówki, które zostały oznaczone jako MustUnderstand = true, zostały zinterpretowane przez bazowego stosu. Jeśli nie zostały one zrozumiane, `mustUnderstand` w tym momencie zostanie wygenerowany błąd. (Użytkownik może zdecydować się na wyłączenie tego `mustUnderstand` przetwarzania i wyświetlenie wszystkich nagłówków komunikatów przez aplikację. W takim przypadku aplikacja jest odpowiedzialna za wykonywanie `mustUnderstand` operacji przetwarzania. Wygenerowany błąd zawiera nagłówek NotUnderstood, który zawiera nazwy wszystkich nagłówków z MustUnderstand = true, które nie zostały zrozumiałe.  
  
 Jeśli kanał protokołu wysyła niestandardowy nagłówek z parametrem MustUnderstand = true i odbiera `mustUnderstand` błąd, musi ustalić, czy ten błąd jest spowodowany przez plik, który został wysłany. Istnieją dwa elementy członkowskie `MessageFault` klasy, które są przydatne dla tego:  
  
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
  
 `IsMustUnderstandFault`zwraca `true` czy błąd `mustUnderstand` jest błędem. `WasHeaderNotUnderstood`zwraca `true` czy nagłówek z określoną nazwą i przestrzenią nazw jest uwzględniony w błędzie jako nagłówek NotUnderstood.  W przeciwnym razie zwraca `false`.  
  
 Jeśli kanał emituje nagłówek, który jest oznaczony jako MustUnderstand = true, wówczas ta warstwa powinna również zaimplementować wzorzec interfejsu API generacji wyjątków i powinna konwertować `mustUnderstand` błędy spowodowane przez ten nagłówek na bardziej przydatny wyjątek, jak opisano wcześniej.  
  
## <a name="tracing"></a>Śledzenie  
 .NET Framework zapewnia mechanizm śledzenia wykonywania programu w celu pomocy w diagnozowaniu aplikacji produkcyjnych lub sporadycznych problemów, gdy nie jest możliwe po prostu dołączenie debugera i przechodzenie przez kod. Podstawowe składniki tego mechanizmu znajdują się w <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw i składają się z:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, czyli źródło informacji śledzenia do zapisania, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>która jest abstrakcyjną klasą bazową dla konkretnych odbiorników, które odbierają informacje do śledzenia <xref:System.Diagnostics.TraceSource> z i wyprowadzają je do lokalizacji docelowej specyficznej dla odbiornika. Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> wyprowadza informacje o śledzeniu do pliku XML. <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>Na koniec, dzięki czemu użytkownik aplikacji kontroluje szczegółowość śledzenia i jest zazwyczaj określany w konfiguracji.  
  
- Oprócz podstawowych składników można użyć [narzędzia Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania i wyszukiwania śladów WCF. Narzędzie jest przeznaczone specjalnie dla plików śledzenia generowanych przez program WCF i pisanych przy <xref:System.Diagnostics.XmlWriterTraceListener>użyciu programu. Na poniższej ilustracji przedstawiono różne składniki, które są objęte śledzeniem.  
  
 ![Obsługa wyjątków i błędów](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Śledzenie z kanału niestandardowego  
 Kanały niestandardowe powinny zapisywać komunikaty śledzenia, aby pomóc w diagnozowaniu problemów, gdy nie jest możliwe dołączenie debugera do uruchomionej aplikacji. Obejmuje to dwa zadania wysokiego poziomu: Tworzenie wystąpienia a i wywoływanie metod w celu pisania śladów. <xref:System.Diagnostics.TraceSource>  
  
 Podczas tworzenia wystąpienia elementu <xref:System.Diagnostics.TraceSource>, określony ciąg otrzymuje nazwę tego źródła. Ta nazwa służy do konfigurowania (Włącz/Wyłącz/Ustaw poziom śledzenia) źródła śledzenia. Pojawia się również w danych wyjściowych śledzenia. Kanały niestandardowe powinny używać unikatowej nazwy źródła, aby ułatwić czytelnikom wyników śledzenia zrozumienie, z których pochodzą dane śledzenia. Typowym zastosowaniem jest nazwa zestawu, który zapisuje informacje jako nazwa źródła śledzenia. Na przykład WCF używa elementu System. ServiceModel jako źródła śledzenia dla informacji pisanych z zestawu System. ServiceModel.  
  
 Po utworzeniu źródła śledzenia należy wywołać <xref:System.Diagnostics.TraceSource.TraceData%2A>metody, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>lub <xref:System.Diagnostics.TraceSource.TraceInformation%2A> , aby pisać wpisy śledzenia do detektorów śledzenia. Dla każdego zapisywanego wpisu śledzenia należy sklasyfikować typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w <xref:System.Diagnostics.TraceEventType>. Ta klasyfikacja i ustawienie poziomu śledzenia w obszarze Konfiguracja określają, czy wpis śledzenia jest wyprowadzany do odbiornika. Na przykład ustawienie poziomu śledzenia w obszarze `Warning` konfiguracja pozwala `Warning`na zapisywanie wpisów `Error` `Critical` śledzenia, ale bloków informacji i zapisów pełnych. Oto przykład tworzenia wystąpienia źródła śledzenia i zapisywania wpisu na poziomie informacji:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> Zdecydowanie zaleca się określenie źródłowej nazwy śledzenia, która jest unikatowa dla niestandardowego kanału, aby ułatwić śledzenie odczytywanych danych wyjściowych.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integracja z podglądem śledzenia  
 Ślady generowane przez kanał mogą być wyprowadzane w formacie możliwym do odczytania przez [narzędzie Podgląd śledzenia usług (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) za pomocą <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> programu jako odbiornika śledzenia. Nie jest to coś, co należy zrobić w przypadku deweloperów kanału. Nie jest to jednak użytkownik aplikacji (lub osoba odpowiedzialna za rozwiązywanie problemów z aplikacją), która musi skonfigurować ten odbiornik śledzenia w pliku konfiguracyjnym aplikacji. Na przykład następująca konfiguracja wyprowadza informacje o śledzeniu z obu <xref:System.ServiceModel?displayProperty=nameWithType> i `Microsoft.Samples.Udp` do pliku o nazwie `TraceEventsFile.e2e`:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType><xref:System.Diagnostics.TraceSource.TraceData%2A> ma metodę, która pobiera jeden lub więcej obiektów, które mają być uwzględnione w wpisie śledzenia. Ogólnie rzecz biorąc <xref:System.Object.ToString%2A?displayProperty=nameWithType> Metoda jest wywoływana dla każdego obiektu, a wynikowy ciąg jest zapisywana jako część wpisu śledzenia. Podczas używania <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> do śledzenia danych wyjściowych można <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> przekazać jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>. Wynikowy wpis śledzenia zawiera kod XML dostarczony przez <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Oto przykład wpisu z danymi aplikacji XML:  
  
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
  
 Przeglądarka śledzenia danych `TraceRecord` programu WCF rozumie schemat elementu pokazanego wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla go w formacie tabelarycznym. Kanał powinien używać tego schematu podczas śledzenia danych aplikacji ze strukturą, aby ułatwić SvcTraceViewer. exe odczytywanie danych.

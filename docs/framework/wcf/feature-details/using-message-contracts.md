---
title: Używanie kontraktów komunikatu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 4c5f1ab0b6fa56e4836a950ca3f2bbad19cfbff2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121982"
---
# <a name="using-message-contracts"></a>Używanie kontraktów komunikatu
Zwykle podczas tworzenia aplikacji Windows Communication Foundation (WCF), deweloperzy zwracać szczególną uwagę na struktur danych oraz problemy z serializacją i nie trzeba zajmować się struktury komunikaty, w których odbywa się dane. Dla tych aplikacji tworząc kontraktów danych dla parametrów lub zwracanych wartości jest bardzo proste. (Aby uzyskać więcej informacji, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Jednak czasami pełną kontrolę nad struktury komunikatu protokołu SOAP jest równie ważne jak kontrolę nad jego zawartość. Jest to szczególnie istotne w przypadku, gdy ważne jest współdziałanie lub specjalnie Sterowanie zabezpieczeniami problemy na poziomie komunikatu lub części komunikatu. W takich przypadkach można utworzyć *kontraktu komunikatu* , pozwala na określenie struktury dokładne wiadomości SOAP wymagane.  
  
 W tym temacie omówiono, jak utworzyć kontrakt szczegółowy komunikat o błędzie dla operacji za pomocą różnych atrybutów kontraktu komunikatu.  
  
## <a name="using-message-contracts-in-operations"></a>Używanie kontraktów komunikatu podczas operacji  
 Usługi WCF obsługuje operacje modelowane w dowolnym *zdalnego wywoływania (procedur RPC) styl* lub *komunikatów styl*. W przypadku operacji stylu RPC mogą mieć dowolny typ możliwy do serializacji i mieć dostęp do funkcji, które są dostępne dla połączeń lokalnych, takich jak wiele parametrów i `ref` i `out` parametrów. W przypadku tego stylu formantu serializacji wybrany struktury danych w podstawowej wiadomości i środowisko wykonawcze programu WCF tworzy wiadomości do obsługi operacji. Dzięki temu deweloperzy, którzy nie jest zaznajomiony z protokołu SOAP i SOAP komunikaty, aby szybko i łatwo tworzyć i korzystać z usługi aplikacji.  
  
 Poniższy przykład kodu pokazuje operacji usługi w modelu w stylu RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Zazwyczaj kontraktu danych jest wystarczająca do zdefiniowania schematu dla wiadomości. Na przykład w poprzednim przykładzie, jest wystarczające dla większości aplikacji Jeśli `BankingTransaction` i `BankingTransactionResponse` mają kontraktów danych do definiowania zawartości źródłowej komunikaty protokołu SOAP. Aby uzyskać więcej informacji na temat kontraktów danych zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Jednak czasami jest niezbędne precyzyjnie kontrolować, jak struktury wiadomości SOAP przesyłane przez sieć. Najbardziej typowym scenariuszem dla tego jest wstawianie niestandardowych nagłówków protokołu SOAP. Inny typowy scenariusz polega do definiowania właściwości zabezpieczeń dla komunikatu nagłówki i treść, oznacza to, aby zdecydować, czy te elementy są cyfrowo podpisane i szyfrowane. Na koniec niektórych stosów protokołu SOAP firm wymagają komunikatów w określonym formacie. Operacje obsługi komunikatów w stylu zapewniają tej kontrolki.  
  
 Operacja stylu komunikatów ma co najwyżej jeden parametr i jedną wartość zwracaną gdzie oba typy są typy komunikatów; oznacza to, że ich serializować bezpośrednio do określonej struktury komunikatu protokołu SOAP. Może to być dowolny typ oznaczone <xref:System.ServiceModel.MessageContractAttribute> lub <xref:System.ServiceModel.Channels.Message> typu. Poniższy przykład kodu pokazuje operacją podobny do poprzedniego RCP stylu, ale, który używa stylu komunikatów.  
  
 Na przykład jeśli `BankingTransaction` i `BankingTransactionResponse` są oba typy, które są kontrakty komunikatów, a następnie kod w następujących operacji jest nieprawidłowy.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Jednakże poniższy kod jest nieprawidłowy.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Wyjątek jest generowany dla każdej operacji, która obejmuje typ kontraktu komunikatu i który nie jest zgodna z jednym z wzorców prawidłowe. Oczywiście operacje, które nie obejmują typy kontraktu komunikatu nie podlegają te ograniczenia.  
  
 Jeśli typ ma kontraktu komunikatu i kontraktu danych, jej kontraktu komunikatu uznaje się, gdy typ jest używany w operacji.  
  
## <a name="defining-message-contracts"></a>Definiowanie kontraktów komunikatu  
 Do zdefiniowania kontraktu komunikatu dla typu (oznacza to, aby zdefiniować mapowania między typem i koperty protokołu SOAP), zastosuj <xref:System.ServiceModel.MessageContractAttribute> do typu. Następnie Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do tych członków typ, który chcesz przekształcić nagłówków protokołu SOAP, a następnie zastosować <xref:System.ServiceModel.MessageBodyMemberAttribute> do tych elementów członkowskich mają być na części treści protokołu SOAP wiadomości.  
  
 Poniższy kod zawiera przykład z użyciem kontraktu komunikatu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Korzystając z tego typu jako parametru operacja, jest generowany w następujących koperty protokołu SOAP:  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 Należy zauważyć, że `operation` i `transactionDate` są wyświetlane jako nagłówków protokołu SOAP i treści protokołu SOAP składa się z element otoki `BankingTransaction` zawierający `sourceAccount`,`targetAccount`, i `amount`.  
  
 Można zastosować <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> do pola, właściwości i zdarzenia, niezależnie od tego, czy są publiczne, prywatne, chroniony lub wewnętrzny.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Pozwala określić atrybuty WrapperName i WrapperNamespace, które kontrolować nazwę element otoki w treści komunikatu protokołu SOAP. Domyślnie nazwa kontraktu komunikatu typ jest używany do otoki i przestrzeni nazw, w którym zdefiniowano kontraktu komunikatu `http://tempuri.org/` jest używany jako domyślny obszar nazw.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybuty są ignorowane w kontrakty komunikatów. Jeśli <xref:System.Runtime.Serialization.KnownTypeAttribute> jest wymagane, umieść go w operacji, który używa kontraktu komunikatu w danym.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Kontrolowanie nagłówka i treści część nazwy i przestrzenie nazw  
 W reprezentacji SOAP kontraktu komunikatu każda część nagłówka i treści mapuje do elementu XML, który ma nazwę i przestrzeni nazw.  
  
 Domyślnie, przestrzeń nazw jest taka sama jak przestrzeń nazw kontraktu usługi, komunikat jest uczestnikiem, która nazwa jest określana przez nazwę elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybuty są stosowane.  
  
 Możesz zmienić te ustawienia domyślne, manipulowanie <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (w klasie nadrzędnej <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów).  
  
 Należy wziąć pod uwagę klasy w poniższym przykładzie kodu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 W tym przykładzie `IsAudited` nagłówka znajduje się w przestrzeni nazw określonej w kodzie, a część treści, która reprezentuje `theData` elementu członkowskiego jest reprezentowany przez element XML o nazwie `transactionData`. Na poniższym obrazie przedstawiono XML generowanych dla tego kontraktu komunikatu.  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Kontrolowanie, czy zostaną opakowane części treści protokołu SOAP  
 Domyślnie części treści protokołu SOAP są serializowane w elemencie opakowana. Na przykład, poniższy kod przedstawia `HelloGreetingMessage` element otoki wygenerowany na podstawie nazwy <xref:System.ServiceModel.MessageContractAttribute> typ kontraktu komunikatu, aby uzyskać `HelloGreetingMessage` wiadomości.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Aby pominąć element otoki, należy ustawić <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> właściwość `false`. Aby kontrolować nazwę i przestrzeń nazw elementu otoki, należy użyć <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> i <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> właściwości.  
  
> [!NOTE]
>  Posiadanie więcej niż jedną część treści wiadomości w wiadomości, które nie zostały zapakowane nie jest zgodne z protokołu WS-I Basic Profile 1.1 i nie jest zalecane podczas projektowania nowych kontrakty komunikatów. Jednak może być konieczne więcej niż jedną część treści komunikatu odkodowany w niektórych scenariuszach współpracy określone. Jeśli ma zostać przesłany więcej niż jednego elementu danych w treści komunikatu, zaleca się do używania trybu domyślnego (zawinięte). Całkowicie dopuszczalne jest posiadanie więcej niż jeden nagłówek wiadomości w nieopakowane komunikaty.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Przy użyciu niestandardowych typów wewnątrz kontrakty komunikatów  
 Każdy nagłówek wiadomości poszczególnych i część treści wiadomości jest serializowana (przekształcane w XML) przy użyciu aparatu wybranym serializacji w dla kontraktu usługi użycia wiadomości. Domyślny mechanizm serializacji, `XmlFormatter`, może obsłużyć dowolny typ, który ma kontraktu danych, albo jawnie (dzięki <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) lub niejawnie (poprzez jest typ pierwotny, posiadające <xref:System.SerializableAttribute?displayProperty=nameWithType>i tak dalej). Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 W powyższym przykładzie `Operation` i `BankingTransactionData` typy muszą mieć kontraktu danych i `transactionDate` jest możliwy do serializacji ponieważ <xref:System.DateTime> jest podstawowy (i dlatego ma umowę niejawne danych).  
  
 Jednak istnieje możliwość przełączyć się na aparat serializacji różnych `XmlSerializer`. W przypadku wprowadzenia takiego przełącznika, należy upewnić się, że wszystkie typy używane do nagłówków wiadomości i części treści są serializacji przy użyciu `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Używanie tablic wewnątrz kontrakty komunikatów  
 Możesz użyć tablic powtarzających się elementów w kontrakty komunikatów na dwa sposoby.  
  
 Pierwsza to użycie <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> bezpośrednio w tablicy. W tym przypadku całej tablicy jest serializowany jako jeden element (czyli jeden nagłówek lub jedną część treści) z wieloma elementami podrzędnymi. Należy wziąć pod uwagę klasy w poniższym przykładzie.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Powoduje to nagłówków protokołu SOAP jest podobny do następującego.  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 Innym sposobem jest użycie <xref:System.ServiceModel.MessageHeaderArrayAttribute>. W takim przypadku każdy element tablicy jest serializowana niezależnie i, że każdy element w tablicy ma jeden nagłówek, podobny do następującego.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Domyślna nazwa dla wpisów tablicy jest nazwą elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderArrayAttribute> zastosować atrybutów.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Dziedziczy atrybut <xref:System.ServiceModel.MessageHeaderAttribute>. Ma ona ten sam zestaw funkcji jako atrybuty inny niż tablica, na przykład możliwość określenia kolejność, nazwę i przestrzeń nazw dla tablicy nagłówków w taki sam sposób, gdy ustawiasz dla pojedynczego nagłówka. Kiedy używasz `Order` właściwość w tablicy, dotyczy ona całej tablicy.  
  
 Można zastosować <xref:System.ServiceModel.MessageHeaderArrayAttribute> tylko do tablic, nie kolekcji.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Korzystanie z tablic bajtowych w kontrakty komunikatów  
 Tablice typu byte, gdy jest używana z atrybutami inny niż tablica (<xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute>), nie są traktowane jako tablic, ale jako specjalny typ pierwotny, reprezentowane jako dane zakodowane w formacie Base64 wynikowy kod XML.  
  
 Kiedy używać tablic bajtowych z atrybutem tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute>, wyniki zależą od serializator używany. Przy użyciu domyślnego elementu serializującego tablica jest przedstawiana jako pojedynczy wpis dla każdego bajtu. Jednak gdy `XmlSerializer` jest zaznaczone, (przy użyciu <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi), tablice bajtowe są traktowane jako dane Base64, niezależnie od tego, czy są używane atrybuty tablicy lub inny niż tablica.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podpisywanie i szyfrowanie części wiadomości  
 Kontrakt komunikatu można wskazać, czy nagłówki i/lub treści komunikatu powinna być cyfrowo podpisane i szyfrowane.  
  
 Jest to realizowane przez ustawienie <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów. Właściwość jest wyliczeniem <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> wpisz i może być równa <xref:System.Net.Security.ProtectionLevel.None> (nie szyfrowania lub podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (podpis cyfrowy tylko), lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (szyfrowanie i podpisu cyfrowego). Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Te funkcje zabezpieczeń do pracy należy poprawnie skonfigurować powiązania i zachowania. Jeśli używasz tych funkcji zabezpieczeń bez odpowiedniej konfiguracji (na przykład, próba zalogowania się wiadomość bez podawania poświadczeń), wyjątek jest generowany w momencie sprawdzania poprawności.  
  
 Nagłówki komunikatów poziom ochrony jest określana osobno dla każdego nagłówka.  
  
 Dla części treści wiadomości poziom ochrony można traktować jako "minimalny poziom ochrony." Treść ma poziom ochrony tylko jeden, niezależnie od liczby części treści. Poziom ochrony treści jest określana przez najwyższy <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> ustawienie właściwości wszystkie części treści. Jednak należy ustawić poziom ochrony każdej części treści do rzeczywistego protection minimalny wymagany poziom.  
  
 Należy wziąć pod uwagę klasy w poniższym przykładzie kodu.  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 W tym przykładzie `recordID` nagłówka nie są chronione, `patientName` jest `signed`, i `SSN` zostaje zaszyfrowany i podpisany. Część treści co najmniej jeden `medicalHistory`, ma <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> zastosowane, i w związku z tym treść cały komunikat zostaje zaszyfrowany i podpisany, mimo że komentarze i diagnozowania części treści Określ niższe poziomy ochrony.  
  
## <a name="soap-action"></a>Akcja SOAP  
 Powiązane standardów usług sieci Web i SOAP zdefiniować właściwość o nazwie `Action` , może być obecny dla każdego komunikatu protokołu SOAP, wysyłane. Operacja <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> właściwości formantu wartość tej właściwości.  
  
## <a name="soap-header-attributes"></a>Atrybuty nagłówek SOAP  
 SOAP standard definiuje następujące atrybuty, które mogą występować w nagłówku:  
  
-   `Actor/Role` (`Actor` w SOAP 1.1, `Role` w SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Lub `Role` atrybut określa identyfikator (URI) węzła, dla których przeznaczony jest dany nagłówek. `MustUnderstand` Atrybut określa, czy węzeł przetwarzania nagłówka musi go zrozumieć. `Relay` Atrybut określa, czy nagłówek do węzłów podrzędnych. Usługi WCF nie wykonuje jakiegokolwiek przetwarzania tych atrybutów na komunikaty przychodzące z wyjątkiem `MustUnderstand` atrybutu, jak to określono w sekcji "Przechowywanie wersji kontraktów komunikatu" w dalszej części tego tematu. Jednakże umożliwia odczytywanie i zapisywanie tych atrybutów zgodnie z potrzebami, tak jak w poniższym opisie.  
  
 Podczas wysyłania komunikatu, te atrybuty nie są generowane domyślnie. Możesz to zmienić na dwa sposoby. Najpierw możesz statycznie ustawić atrybuty do dowolnych wartości, żądane przez zmianę <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> właściwości, jak pokazano w poniższym przykładzie kodu. (Należy pamiętać, że ma nie `Role` właściwości; ustawienie <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> emituje właściwość `Role` atrybutu, jeśli używasz protokołu SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Drugi sposób kontroluje te atrybuty jest dynamicznie, za pomocą kodu. Można to osiągnąć przez opakowywanie typ żądanego nagłówka w <xref:System.ServiceModel.MessageHeader%601> typu (Upewnij się, nie należy mylić tego typu za pomocą wersji nieogólnego) i za pomocą typu wraz z <xref:System.ServiceModel.MessageHeaderAttribute>. Następnie należy użyć właściwości na <xref:System.ServiceModel.MessageHeader%601> można ustawić atrybutów protokołu SOAP, jak pokazano w poniższym przykładzie kodu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 Jeśli używasz mechanizmy kontroli statycznej i dynamicznej statyczne ustawienia są używane jako domyślne, ale później może zostać przesłonięta przez przy użyciu mechanizmu dynamiczne, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Tworzenie powtarzanych nagłówki przy użyciu atrybutu dynamic kontroli jest dozwolone, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Po stronie odbierającej odczytywania tych atrybutów protokołu SOAP jest możliwe tylko jeśli <xref:System.ServiceModel.MessageHeader%601> klasa jest używana dla nagłówka typu. Sprawdź `Actor`, `Relay`, lub `MustUnderstand` właściwości nagłówek <xref:System.ServiceModel.MessageHeader%601> typu, aby odnaleźć ustawień atrybutów na odebranym komunikacie.  
  
 Gdy komunikat jest odbierany i następnie odesłał, ustawień atrybutów protokołu SOAP tylko Przejdź błądzenia dla nagłówków <xref:System.ServiceModel.MessageHeader%601> typu.  
  
## <a name="order-of-soap-body-parts"></a>Zlecenia części treści protokołu SOAP  
 W niektórych sytuacjach może być konieczne kontrolować kolejność części treści. Kolejność elementów treści jest porządek alfabetyczny domyślnie, ale mogą być kontrolowane przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości. Właściwość ta ma tą samą semantyką jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości, z wyjątkiem zachowanie w scenariuszach dziedziczenia (w treści typu podstawowego, elementy członkowskie nie są sortowane przed elementy członkowskie typu pochodnego treści kontrakty komunikatów). Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie `amount` zwykle przybyły, aby najpierw ponieważ ona jest pierwszy w kolejności alfabetycznej. Jednak <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> właściwość umieszcza położenia trzeciego.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktów komunikatu  
 Od czasu do czasu może być konieczna zmiana kontrakty komunikatów. Na przykład nową wersję aplikacji może dodać dodatkowe nagłówka do wiadomości. Następnie podczas wysyłania z nowej wersji do starego, system musi obsłużyć dodatkowe nagłówka, jak również brak nagłówka podczas przechodzenia w drugą stronę.  
  
 Obowiązują następujące reguły dla nagłówków wersji:  
  
-   Usługi WCF nie obiekt do brakujących nagłówków — odpowiednie elementy członkowskie są pozostawiane wartościami domyślnymi.  
  
-   Usługi WCF ignoruje także nieoczekiwane dodatkowe nagłówki. Jedynym wyjątkiem od tej reguły jest, jeśli dodatkowe nagłówek ma `MustUnderstand` ustawioną wartość atrybutu `true` w przychodzącej wiadomości SOAP — w tym przypadku jest zgłaszany wyjątek, ponieważ nie można przetworzyć nagłówek, który musi być rozumiane.  
  
 Komunikat o treści mają podobne zasady przechowywania wersji — Brak i dodatkowe części treści wiadomości są ignorowane.  
  
## <a name="inheritance-considerations"></a>Uwagi dotyczące dziedziczenia  
 Typ kontraktu komunikatu może dziedziczyć z innego typu, tak długo, jak typ podstawowy ma również kontraktu komunikatu.  
  
 Podczas tworzenia lub uzyskiwania dostępu do wiadomości przy użyciu typ kontraktu komunikatu, która dziedziczy inne typy kontraktu komunikatu, obowiązują następujące reguły:  
  
-   Wszystkie nagłówki wiadomości w hierarchii dziedziczenia pochodzą ze sobą w celu utworzenia pełnego zestawu nagłówków wiadomości.  
  
-   Wszystkie części treści wiadomości w hierarchii dziedziczenia pochodzą ze sobą w celu utworzenia pełnego treść. Części treści są uporządkowane zgodnie ze zwykłymi regułami sortowania (przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości i następnie alfabetycznej), niezwiązany z ich miejsca w hierarchii dziedziczenia. Za pomocą Dziedziczenie kontraktów komunikatu, w których części treści wiadomości wystąpić na różnych poziomach drzewa dziedziczenia jest zdecydowanie odradzane. Jeśli klasa bazowa i Klasa pochodna należy zdefiniować nagłówek lub część treści o takiej samej nazwie, elementu członkowskiego z klasy podstawowej większość służy do przechowywania wartości w tej części w nagłówku lub w treści.  
  
 Należy wziąć pod uwagę klas w poniższym przykładzie kodu.  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 `PatientRecord` Klasa opisuje komunikat jeden nagłówek o nazwie `ID`. Nagłówek odnosi się do `personID` i nie `patientID` elementu członkowskiego, ponieważ większość podstawowy element członkowski jest wybierany. W efekcie `patientID` pola w tym przypadku jest bezużyteczny. Treść wiadomości zawiera `diagnosis` następuje `patientName` elementu, ponieważ jest w porządku alfabetycznym. Należy zauważyć, że w przykładzie pokazano wzorzec, który jest zdecydowanie odradzane: zarówno podstawowy, jak i kontrakty komunikatów pochodna ma części treści wiadomości.  
  
## <a name="wsdl-considerations"></a>Zagadnienia dotyczące WSDL  
 Podczas generowania kontraktu usługi sieci Web Services Description Language (WSDL) z usługi, który używa kontrakty komunikatów, to należy pamiętać, że nie wszystkie funkcje kontraktu komunikatu są odzwierciedlane w wynikowej WSDL. Należy wziąć pod uwagę następujące kwestie:  
  
-   WSDL nie można wyrazić koncepcji tablicy nagłówków. Podczas tworzenia wiadomości z tablicą przy użyciu nagłówków <xref:System.ServiceModel.MessageHeaderArrayAttribute>, WSDL wynikowy odzwierciedla tylko jeden nagłówek zamiast tablicy.  
  
-   Dokument WSDL wynikowy może nie odzwierciedlać pewne informacje poziom ochrony.  
  
-   Typ komunikatu wygenerowany w formacie WSDL ma taką samą nazwę jak nazwa klasy typ kontraktu komunikatu.  
  
-   Gdy kontrakt przy użyciu tego samego komunikatu w wielu operacjach, wiele typów wiadomości są generowane w dokumencie WSDL. Nazwy są tworzone unikatowe, przez dodanie liczby "2", "3" i tak dalej do późniejszego wykorzystania. Podczas importowania pliku WSDL Wstecz, wiele typy kontraktu komunikatu są tworzone i są identyczne, z wyjątkiem ich nazwy.  
  
## <a name="soap-encoding-considerations"></a>Uwagi dotyczące kodowania SOAP  
 WCF pozwala na używanie starszej wersji protokołu SOAP stylu XML, kodowania, jego użycie nie jest zalecane. Korzystając z tego stylu (przez ustawienie `Use` właściwości `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> stosowane do umowy serwisowej), mają zastosowanie następujące dodatkowe kwestie:  
  
-   Nagłówki wiadomości są nieobsługiwane. oznacza to, że atrybut <xref:System.ServiceModel.MessageHeaderAttribute> i atrybut tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute> są niezgodne z kodowaniem SOAP.  
  
-   Jeśli kontraktu komunikatu jest nie zawinięty, oznacza to, jeśli właściwość <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ustawiono `false`, kontraktu komunikatu może mieć część treści tylko jeden.  
  
-   Nazwa elementu otoki dla kontraktu komunikatu żądania musi odpowiadać nazwie operacji. Użyj `WrapperName` właściwości kontraktu komunikatu, w tym.  
  
-   Nazwa elementu otoki dla kontraktu komunikatu odpowiedzi musi być taka sama jak nazwa operacji sufiks przez "Response". Użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> właściwości kontraktu komunikatu, w tym.  
  
-   Kodowaniem SOAP zachowuje odwołania do obiektu. Rozważmy na przykład, poniższy kod.  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 Po serializacji wiadomości przy użyciu kodowania SOAP, `changedFrom` i `changedTo` nie zawierają własne kopie `p`, ale zamiast tego wskazać polecenie kopiowania wewnątrz `changedBy` elementu.  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 Każdy nagłówek wiadomości i część treści wiadomości jest serializowana, niezależnie od innych. W związku z tym ten sam przestrzenie nazw mogą być deklarowane ponownie dla każdego nagłówka i część treści. Aby zwiększyć wydajność, zwłaszcza jeśli chodzi o rozmiar wiadomości w sieci, należy skonsolidować wiele nagłówków i części treści w jednoczęściowych nagłówku lub w treści. Na przykład zamiast następujący kod:  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Użyj tego kodu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Oparte na zdarzeniach asynchronicznych i kontrakt komunikatu  
 Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.  
  
 Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu `/messageContract` opcja polecenia. Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)

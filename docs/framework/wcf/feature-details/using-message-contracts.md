---
title: Używanie kontraktów komunikatu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 18d0ea97f1de40044d40fa85c9792c809fb73346
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959880"
---
# <a name="using-message-contracts"></a>Używanie kontraktów komunikatu
Zwykle podczas kompilowania aplikacji Windows Communication Foundation (WCF) deweloperzy mogą zwrócić szczególną uwagę na struktury danych i problemy z serializacji i nie muszą stanowić problemu ze strukturą komunikatów, w których dane są przenoszone. W przypadku tych aplikacji Tworzenie kontraktów danych dla parametrów lub zwracanych wartości jest proste. (Aby uzyskać więcej informacji, zobacz [określanie transfer danych w kontraktach usługi](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)).  
  
 Jednak czasami Pełna kontrola nad strukturą komunikatu protokołu SOAP jest równie ważna jako kontrola nad zawartością. Jest to szczególnie ważne, gdy współpraca jest ważna lub aby w szczególności kontrolować problemy z zabezpieczeniami na poziomie komunikatu lub komunikatu. W takich przypadkach można utworzyć *kontrakt komunikatu* , który pozwala określić strukturę dokładnego komunikatu SOAP.  
  
 W tym temacie omówiono sposób użycia różnych atrybutów kontraktu komunikatów w celu utworzenia konkretnej kontraktu komunikatu dla operacji.  
  
## <a name="using-message-contracts-in-operations"></a>Korzystanie z kontraktów komunikatów w operacjach  
 Funkcja WCF obsługuje operacje modelowane na *stylu zdalnego wywołania procedury (RPC)* lub w *stylu obsługi komunikatów*. W operacji w stylu wywołania procedury (RPC) można używać dowolnego typu możliwego do serializacji i masz dostęp do funkcji, które są dostępne dla wywołań lokalnych, takich jak wiele `ref` parametrów `out` i parametry. W tym stylu forma serializacji wybrana kontroluje strukturę danych w podstawowych komunikatach, a środowisko uruchomieniowe WCF tworzy komunikaty do obsługi tej operacji. Umożliwia to deweloperom, którzy nie znają komunikatów SOAP i SOAP, aby szybko i łatwo tworzyć i używać aplikacji usług.  
  
 Poniższy przykład kodu przedstawia operację usługi modelowaną w stylu wywołania RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Zwykle kontrakt danych jest wystarczający do zdefiniowania schematu dla komunikatów. Na przykład w poprzednim przykładzie jest to wystarczające dla większości aplikacji, jeśli `BankingTransaction` i `BankingTransactionResponse` zawiera Kontrakty danych do definiowania zawartości źródłowych komunikatów protokołu SOAP. Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Jednak czasami konieczne jest precyzyjną kontrolę nad sposobem, w jaki Struktura komunikatu protokołu SOAP przesyłanego przez sieć. Najbardziej typowym scenariuszem jest wstawianie niestandardowych nagłówków protokołu SOAP. Innym typowym scenariuszem jest zdefiniowanie właściwości zabezpieczeń dla nagłówków i treści wiadomości, oznacza to, że w celu określenia, czy te elementy są podpisane cyfrowo i szyfrowane. Na koniec niektóre stosy protokołu SOAP innych firm wymagają komunikatów w określonym formacie. Operacje w stylu obsługi komunikatów zapewniają tę kontrolkę.  
  
 Operacja w stylu obsługi komunikatów ma co najwyżej jeden parametr i jedną wartość zwracaną, gdy oba typy to typy komunikatów. oznacza to, że serializacji bezpośrednio do określonej struktury wiadomości SOAP. Może to być dowolny typ oznaczony przy użyciu <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.Channels.Message> lub. Poniższy przykład kodu pokazuje operację podobną do powyższego typu RCP, ale używa stylu obsługi komunikatów.  
  
 Na przykład jeśli `BankingTransaction` i `BankingTransactionResponse` są oba typy, które są kontraktami komunikatów, kod w następujących operacjach jest prawidłowy.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Jednak następujący kod jest nieprawidłowy.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Wyjątek jest zgłaszany dla każdej operacji, która obejmuje typ kontraktu komunikatu, który nie jest zgodny z jednym z prawidłowych wzorców. Oczywiście operacje, które nie obejmują typów kontraktu komunikatów, nie podlegają tym ograniczeniom.  
  
 Jeśli typ ma zarówno umowę komunikatu, jak i kontrakt danych, tylko jego kontrakt wiadomości jest brany pod uwagę, gdy typ jest używany w operacji.  
  
## <a name="defining-message-contracts"></a>Definiowanie kontraktów komunikatów  
 Aby zdefiniować kontrakt wiadomości dla typu (oznacza to, aby zdefiniować mapowanie między typem i kopertą protokołu SOAP), Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do tego typu. Następnie Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do tych elementów członkowskich typu, który chcesz umieścić w nagłówkach protokołu SOAP, i <xref:System.ServiceModel.MessageBodyMemberAttribute> Zastosuj do tych członków, które chcesz umieścić w częściach treści protokołu SOAP wiadomości.  
  
 Poniższy kod stanowi przykład użycia kontraktu komunikatu.  
  
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
  
 W przypadku używania tego typu jako parametru operacji generowana jest następująca Koperta protokołu SOAP:  
  
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
  
 Zauważ, `operation` że `transactionDate` i są wyświetlane jako nagłówki protokołu SOAP, a treść protokołu SOAP składa `sourceAccount`się`targetAccount`z elementu `amount` `BankingTransaction` otoki zawierającego,, i.  
  
 Można zastosować <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> do wszystkich pól, właściwości i zdarzeń, niezależnie od tego, czy są one publiczne, prywatne, chronione czy wewnętrzne.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Pozwala określić atrybuty otokname i WrapperNamespace, które kontrolują nazwę elementu otoki w treści komunikatu protokołu SOAP. Domyślnie nazwa typu kontraktu wiadomości jest używana dla otoki i przestrzeń nazw, w której jest zdefiniowany `http://tempuri.org/` kontrakt komunikatu, jest używana jako domyślna przestrzeń nazw.  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.KnownTypeAttribute>atrybuty są ignorowane w kontraktach komunikatów. <xref:System.Runtime.Serialization.KnownTypeAttribute> Jeśli jest to wymagane, umieść je w operacji, która używa danego kontraktu komunikatu.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Kontrolowanie nazw nagłówka i części treści i przestrzeni nazw  
 W reprezentacji protokołu SOAP kontraktu komunikatu każdy nagłówek i część treści są mapowane na element XML, który ma nazwę i przestrzeń nazw.  
  
 Domyślnie przestrzeń nazw jest taka sama jak przestrzeń nazw kontraktu usługi, w którym uczestniczy ten komunikat, a nazwa jest określana przez nazwę elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderAttribute> mają zastosowanie <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybuty lub.  
  
 Te ustawienia domyślne można <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> zmienić przez manipulowanie i <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (w klasie <xref:System.ServiceModel.MessageHeaderAttribute> nadrzędnej atrybutów i <xref:System.ServiceModel.MessageBodyMemberAttribute> ).  
  
 Rozważmy klasę w poniższym przykładzie kodu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 W tym przykładzie `IsAudited` nagłówek znajduje się w przestrzeni nazw określonej w kodzie, a część treści `theData` reprezentująca element członkowski jest reprezentowana przez element XML o nazwie `transactionData`. Poniżej przedstawiono listę XML wygenerowaną dla tego kontraktu komunikatu.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Kontrolowanie, czy części treści protokołu SOAP są opakowane  
 Domyślnie części treści protokołu SOAP są serializowane wewnątrz opakowanego elementu. Na przykład poniższy kod pokazuje `HelloGreetingMessage` element otoki wygenerowany na podstawie nazwy <xref:System.ServiceModel.MessageContractAttribute> typu w kontrakcie komunikatu dla `HelloGreetingMessage` wiadomości.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Aby pominąć element otoki, należy ustawić <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> właściwość na `false`. Aby kontrolować nazwę i przestrzeń nazw elementu otoki, użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> właściwości i. <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A>  
  
> [!NOTE]
> Posiadanie więcej niż jednej części treści wiadomości w komunikatach, które nie są opakowane, nie jest zgodne z profilem WS-I Basic 1,1 i nie jest zalecane podczas projektowania nowych kontraktów komunikatów. Może jednak być konieczne posiadanie więcej niż jednej nieopakowanej treści wiadomości w niektórych scenariuszach współdziałania. W przypadku przesyłania więcej niż jednego fragmentu danych w treści wiadomości zaleca się użycie trybu domyślnego (opakowany). Posiadanie więcej niż jednego nagłówka wiadomości w nieopakowanych komunikatach jest całkowicie akceptowalne.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Używanie typów niestandardowych wewnątrz kontraktów komunikatów  
 Każdy pojedynczy nagłówek wiadomości i część treści komunikatu są serializowane (włączone w formacie XML) przy użyciu wybranego aparatu serializacji dla kontraktu usługi, w którym jest używana wiadomość. Domyślny aparat serializacji, `XmlFormatter`,, może obsługiwać dowolny typ, który ma umowę danych, albo jawnie (przez <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>posiadanie) lub niejawnie (przez typ <xref:System.SerializableAttribute?displayProperty=nameWithType>pierwotny, posiadający, i tak dalej). Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 W poprzednim przykładzie `Operation` typy i `BankingTransactionData` muszą mieć kontrakt danych i `transactionDate` można je serializować, ponieważ <xref:System.DateTime> jest elementem pierwotnym (i dlatego ma niejawny kontrakt danych).  
  
 Istnieje jednak możliwość przełączenia się do innego aparatu serializacji, czyli `XmlSerializer`. W przypadku wybrania takiego przełącznika należy upewnić się, że wszystkie typy używane do nagłówków wiadomości i części treści są serializowane przy użyciu `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Używanie tablic wewnątrz kontraktów komunikatów  
 Można używać tablic powtarzających się elementów w kontraktach komunikatów na dwa sposoby.  
  
 Pierwszym z nich jest użycie <xref:System.ServiceModel.MessageHeaderAttribute> lub a <xref:System.ServiceModel.MessageBodyMemberAttribute> bezpośrednio na tablicy. W takim przypadku cała tablica jest serializowana jako jeden element (to jest jeden nagłówek lub jedna część treści) z wieloma elementami podrzędnymi. Rozważmy klasę w poniższym przykładzie.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Wyniki w nagłówkach protokołu SOAP są podobne do następujących.  
  
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
  
 Alternatywą dla tego jest użycie <xref:System.ServiceModel.MessageHeaderArrayAttribute>. W takim przypadku każdy element tablicy jest serializowany niezależnie i dlatego każdy element tablicy ma jeden nagłówek, podobny do poniższego.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Nazwa domyślna dla wpisów tablicy to nazwa elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderArrayAttribute> zastosowano atrybuty.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atrybut dziedziczy <xref:System.ServiceModel.MessageHeaderAttribute>z. Ma ten sam zestaw funkcji co atrybuty nietablicowe, na przykład można ustawić kolejność, nazwę i przestrzeń nazw dla tablicy nagłówków w taki sam sposób, jak w przypadku pojedynczego nagłówka. Użycie `Order` właściwości w tablicy ma zastosowanie do całej tablicy.  
  
 Można zastosować <xref:System.ServiceModel.MessageHeaderArrayAttribute> tylko do tablic, nie kolekcji.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Używanie tablic bajtowych w kontraktach komunikatów  
 Tablice bajtowe, gdy są używane z atrybutami nietablicowymi <xref:System.ServiceModel.MessageHeaderAttribute>(<xref:System.ServiceModel.MessageBodyMemberAttribute> i), nie są traktowane jako tablice, ale jako specjalne typy pierwotne reprezentowane jako dane zakodowane algorytmem Base64 w wyjściowym kodzie XML.  
  
 W przypadku używania tablic bajtowych z atrybutem <xref:System.ServiceModel.MessageHeaderArrayAttribute>Array wyniki zależą od serializatora w użyciu. W przypadku domyślnego serializatora tablica jest reprezentowana jako pojedynczy wpis dla każdego bajtu. Jednak po `XmlSerializer` wybraniu ( <xref:System.ServiceModel.XmlSerializerFormatAttribute> przy użyciu w kontrakcie usługi) tablice bajtowe są traktowane jako dane base64, niezależnie od tego, czy są używane atrybuty tablicowe czy nietablicowe.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podpisywanie i szyfrowanie części wiadomości  
 Umowa o komunikat może wskazywać, czy nagłówki i/lub treść komunikatu powinny być podpisane cyfrowo i szyfrowane.  
  
 Jest to realizowane przez ustawienie <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów. Właściwość jest wyliczeniem <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> typu i może być ustawiona na <xref:System.Net.Security.ProtectionLevel.None> (bez szyfrowania lub podpisu), <xref:System.Net.Security.ProtectionLevel.Sign> (tylko podpis cyfrowy) lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (szyfrowanie i podpis cyfrowy). Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Aby te funkcje zabezpieczeń działały, należy prawidłowo skonfigurować powiązanie i zachowania. W przypadku korzystania z tych funkcji zabezpieczeń bez właściwej konfiguracji (na przykład próba podpisania wiadomości bez podawania poświadczeń) wyjątek jest zgłaszany podczas walidacji.  
  
 Dla nagłówków wiadomości poziom ochrony jest określany osobno dla każdego nagłówka.  
  
 W przypadku części treści wiadomości poziom ochrony może być uważany za "minimalny poziom ochrony". Treść ma tylko jeden poziom ochrony, niezależnie od liczby części treści. Poziom ochrony treści jest określany na podstawie najwyższego <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> ustawienia właściwości wszystkich części treści. Należy jednak ustawić poziom ochrony każdej części treści na rzeczywisty wymagany minimalny poziom ochrony.  
  
 Rozważmy klasę w poniższym przykładzie kodu.  
  
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
  
 W tym przykładzie `recordID` nagłówek nie jest chroniony, `patientName` jest `signed`i `SSN` jest szyfrowany i podpisany. Zastosowano co najmniej jedną część `medicalHistory`treści, i w ten sposób cała treść komunikatu jest zaszyfrowana i podpisana, mimo że komentarze i części treści diagnostyki określają niższe poziomy ochrony. <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>  
  
## <a name="soap-action"></a>Akcja SOAP  
 Standardy SOAP i pokrewne usługi sieci Web definiują Właściwość `Action` o nazwie, która może być obecna dla każdej wysyłanej wiadomości protokołu SOAP. Operacja <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> i<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> właściwości kontrolują wartość tej właściwości.  
  
## <a name="soap-header-attributes"></a>Atrybuty nagłówka SOAP  
 Standard SOAP definiuje następujące atrybuty, które mogą istnieć w nagłówku:  
  
- `Actor/Role`(`Actor` w SOAP 1,1, `Role` w SOAP 1,2)  
  
- `MustUnderstand`  
  
- `Relay`  
  
 Atrybut `Actor` or`Role` określa Uniform Resource Identifier (URI) węzła, dla którego jest przeznaczony podany nagłówek. Ten `MustUnderstand` atrybut określa, czy węzeł przetwarzający nagłówek musi je zrozumieć. Ten `Relay` atrybut określa, czy nagłówek ma być przekazywany do węzłów podrzędnych. Funkcja WCF nie wykonuje żadnego przetwarzania tych atrybutów w komunikatach przychodzących, z wyjątkiem tego `MustUnderstand` , jak określono w sekcji "wersja kontraktu komunikatów" w dalszej części tego tematu. Umożliwia jednak odczytywanie i zapisywanie tych atrybutów w razie potrzeby, jak w poniższym opisie.  
  
 Podczas wysyłania komunikatu te atrybuty nie są emitowane domyślnie. Można to zmienić na dwa sposoby. Najpierw można statycznie ustawić atrybuty dla dowolnych żądanych wartości, zmieniając <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>właściwości, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>i <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> , jak pokazano w poniższym przykładzie kodu. (Należy zauważyć, że nie `Role` ma właściwości; <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> ustawienie właściwości emituje atrybut `Role` , jeśli używasz protokołu SOAP 1,2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Drugi sposób sterowania tymi atrybutami jest dynamiczny, za pomocą kodu. Można to osiągnąć przez zapakowanie żądanego typu nagłówka w <xref:System.ServiceModel.MessageHeader%601> typie (należy pamiętać, aby nie mylić tego typu z wersją nieogólną) i przy użyciu typu razem <xref:System.ServiceModel.MessageHeaderAttribute>z. Następnie można użyć właściwości w <xref:System.ServiceModel.MessageHeader%601> celu ustawienia atrybutów protokołu SOAP, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Jeśli używasz zarówno dynamicznego, jak i statycznego mechanizmu kontroli, ustawienia statyczne są używane jako domyślne, ale można je później zastąpić przy użyciu mechanizmu dynamicznego, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Tworzenie powtórzonych nagłówków z dynamiczną kontrolką atrybutów jest dozwolone, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Na stronie otrzymującej odczytywanie tych atrybutów protokołu SOAP można wykonać tylko wtedy, <xref:System.ServiceModel.MessageHeader%601> gdy Klasa jest używana dla nagłówka w typie. `Relay`Sprawdź, lub`MustUnderstand` właściwości nagłówka<xref:System.ServiceModel.MessageHeader%601> typu, aby odnaleźć ustawienia atrybutu dla odebranego komunikatu. `Actor`  
  
 Gdy wiadomość zostanie odebrana, a następnie wysłana z powrotem, ustawienia atrybutu protokołu SOAP są tylko w przypadku nagłówków <xref:System.ServiceModel.MessageHeader%601> typu.  
  
## <a name="order-of-soap-body-parts"></a>Kolejność części treści protokołu SOAP  
 W pewnych okolicznościach może być konieczne kontrolowanie kolejności części treści. Kolejność elementów treści jest domyślnie alfabetyczna, ale może być kontrolowana przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwość. Ta właściwość ma tę samą semantykę co <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> właściwość, z wyjątkiem zachowania w scenariuszach dziedziczenia (w kontraktach komunikatów, składowe treści typu podstawowego nie są sortowane przed składowanymi elementami typu pochodnego). Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie w pierwszej `amount` kolejności jest to pierwsze, ponieważ jest ono pierwsze w porządku alfabetycznym. <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> Jednak Właściwość umieszcza ją w trzecim położeniu.  
  
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
  
## <a name="message-contract-versioning"></a>Przechowywanie wersji kontraktu komunikatów  
 Czasami może zajść konieczność zmiany kontraktów komunikatów. Na przykład Nowa wersja aplikacji może dodać dodatkowy nagłówek do wiadomości. Następnie podczas wysyłania z nowej wersji do starego system musi zajmować się dodatkowym nagłówkiem, a także brakującym nagłówkiem podczas przechodzenia w inne kierunki.  
  
 W przypadku nagłówków wersji obowiązują następujące reguły:  
  
- WCF nie jest obiektem w brakujących nagłówkach — odpowiadające im elementy członkowskie są pozostawiane w wartościach domyślnych.  
  
- Funkcja WCF ignoruje także nieoczekiwane dodatkowe nagłówki. Jedynym wyjątkiem od tej reguły jest, czy dodatkowy nagłówek ma `MustUnderstand` atrybut ustawiony na `true` w przychodzącym komunikacie protokołu SOAP — w tym przypadku wyjątek jest zgłaszany, ponieważ nie można przetworzyć nagłówka, który musi być zrozumiały.  
  
 Treści komunikatów mają podobne reguły dotyczące wersji — ignorowane są zarówno brakujące, jak i dodatkowe części treści komunikatów.  
  
## <a name="inheritance-considerations"></a>Zagadnienia dotyczące dziedziczenia  
 Typ kontraktu komunikatu może dziedziczyć z innego typu, o ile typ podstawowy ma także kontrakt komunikatu.  
  
 Podczas tworzenia lub uzyskiwania dostępu do wiadomości za pomocą typu kontraktu komunikatu, który dziedziczy z innych typów kontraktu komunikatów, mają zastosowanie następujące reguły:  
  
- Wszystkie nagłówki wiadomości w hierarchii dziedziczenia są zbierane razem w celu utworzenia pełnego zestawu nagłówków wiadomości.  
  
- Wszystkie części treści wiadomości w hierarchii dziedziczenia są zbierane wraz z pełną treścią wiadomości. Części treści są uporządkowane zgodnie ze zwykłymi regułami określania kolejności ( <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> według właściwości, a następnie alfabetyczne) bez znaczenia dla ich miejsca w hierarchii dziedziczenia. Używanie dziedziczenia kontraktu komunikatów, gdzie części treści komunikatu występują na wielu poziomach drzewa dziedziczenia jest zdecydowanie odradzane. Jeśli klasa bazowa i Klasa pochodna definiują nagłówek lub część treści o tej samej nazwie, element członkowski z klasy podstawowej jest używany do przechowywania wartości tego nagłówka lub części treści.  
  
 Rozważmy klasy w poniższym przykładzie kodu.  
  
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
  
 Klasa opisuje komunikat z jednym nagłówkiem o nazwie `ID`. `PatientRecord` Nagłówek odnosi się do `personID` i nie do `patientID` elementu członkowskiego, ponieważ wybierany jest element członkowski najwyższego poziomu. Oznacza to, `patientID` że w tym przypadku pole jest bezużyteczne. Treść wiadomości zawiera `diagnosis` element, po którym następuje `patientName` element, ponieważ jest to porządek alfabetyczny. Należy zauważyć, że w przykładzie przedstawiono wzorzec, który jest silnie odradzany: kontrakt podstawowy i pochodny są częścią wiadomości.  
  
## <a name="wsdl-considerations"></a>Zagadnienia dotyczące języka WSDL  
 Podczas generowania kontraktu Web Services Description Language (WSDL) z usługi używającej kontraktów komunikatów należy pamiętać, że nie wszystkie funkcje kontraktu wiadomości są odzwierciedlone w wyniku WSDL. Rozważ następujące kwestie:  
  
- Język WSDL nie może wyrazić koncepcji tablicy nagłówków. W przypadku tworzenia komunikatów z tablicą nagłówków przy użyciu <xref:System.ServiceModel.MessageHeaderArrayAttribute>, wynikiem WSDL odzwierciedla tylko jeden nagłówek zamiast tablicy.  
  
- Otrzymany dokument WSDL może nie odzwierciedlać niektórych informacji na poziomie ochrony.  
  
- Typ komunikatu wygenerowany w języku WSDL ma taką samą nazwę jak nazwa klasy typu kontraktu komunikatu.  
  
- W przypadku korzystania z tego samego kontraktu komunikatu w wielu operacjach w dokumencie WSDL generowane są wiele typów komunikatów. Nazwy są unikatowe przez dodanie cyfr "2", "3" itd., do kolejnych celów. Podczas importowania z powrotem do języka WSDL tworzone są wiele typów kontraktu komunikatów i są one identyczne z wyjątkiem nazw.  
  
## <a name="soap-encoding-considerations"></a>Zagadnienia dotyczące kodowania SOAP  
 Funkcja WCF umożliwia użycie starszego stylu kodowania SOAP w kodzie XML, ale nie jest to zalecane. W przypadku korzystania z tego stylu (przez `Use` ustawienie `Encoded` właściwości na na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> podstawie zastosowania do kontraktu usługi) obowiązują następujące dodatkowe zagadnienia:  
  
- Nagłówki komunikatów nie są obsługiwane; oznacza to, że atrybut <xref:System.ServiceModel.MessageHeaderAttribute> i atrybut <xref:System.ServiceModel.MessageHeaderArrayAttribute> Array są niezgodne z kodowaniem protokołu SOAP.  
  
- Jeśli kontrakt wiadomości nie jest opakowany, oznacza to, że jeśli właściwość <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> jest ustawiona na `false`, kontrakt komunikatu może mieć tylko jedną część treści.  
  
- Nazwa elementu otoki dla kontraktu komunikatu żądania musi być zgodna z nazwą operacji. `WrapperName` Użyj właściwości kontraktu wiadomości dla tego elementu.  
  
- Nazwa elementu otoki dla kontraktu komunikatu odpowiedzi musi być taka sama jak nazwa operacji sufiksu "odpowiedź". <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> Użyj właściwości kontraktu wiadomości dla tego elementu.  
  
- Kodowanie protokołu SOAP zachowuje odwołania do obiektu. Rozważmy na przykład poniższy kod.  
  
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
  
 Po serializacji `changedFrom` komunikatu przy użyciu kodowania protokołu SOAP i `changedTo` nie `p`zawierają własnych kopii, `changedBy` ale zamiast tego należy wskazać kopię wewnątrz elementu.  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 Każdy nagłówek wiadomości i część treści komunikatu są serializowane niezależnie od innych. W związku z tym te same przestrzenie nazw można ponownie zadeklarować dla każdego nagłówka i części ciała. Aby zwiększyć wydajność, szczególnie w zakresie rozmiaru wiadomości w sieci, Konsoliduj wiele nagłówków i części treści w jeden nagłówek lub część treści. Na przykład zamiast następującego kodu:  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Kontrakty asynchronicznych i komunikatów opartych na zdarzeniach  
 Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana `Result` jako właściwość, a pozostałe są zwracane jako właściwości <xref:System.EventArgs> w obiekcie. W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość `Result` jako właściwość, a reszta jest <xref:System.EventArgs> właściwości obiektu.  
  
 Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, `/messageContract` Użyj opcji polecenia. Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)

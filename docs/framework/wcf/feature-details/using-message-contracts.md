---
title: Używanie kontraktów komunikatu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9f6d0e9d64c510b47b0697d02178f1c0a95f61b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-message-contracts"></a>Używanie kontraktów komunikatu
Zwykle podczas kompilowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, deweloperzy zwracać szczególną uwagę na struktur danych oraz problemy serializacji i nie trzeba zajmować się struktury wiadomości, w których odbywa się dane. W przypadku tych aplikacji prostego jest utworzenie kontraktów danych do parametrów lub zwracanych wartości. (Aby uzyskać więcej informacji, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Jednak czasami pełną kontrolę nad struktury wiadomości SOAP jest równie ważne co kontrolę nad jego zawartość. Dotyczy to szczególnie ważne jest współdziałanie, lub aby specjalnie kontroli zabezpieczeń problemy na poziomie komunikatu lub części komunikatu. W takich przypadkach można utworzyć *kontraktu komunikatu* , umożliwia określenie struktury dokładne komunikatu protokołu SOAP wymagane.  
  
 W tym temacie omówiono tworzenie kontraktu określonego komunikatu dla operacji przy użyciu różnych atrybutów kontraktu komunikatu.  
  
## <a name="using-message-contracts-in-operations"></a>Używanie kontraktów komunikatu w operacji  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje operacje uformowany albo *zdalnego wywoływania (procedur RPC) styl* lub *wiadomości styl*. W przypadku operacji stylu wywołania RPC, można użyć dowolnego typu do serializacji i masz dostęp do funkcji, które są dostępne dla połączeń lokalnych, takich jak wiele parametrów i `ref` i `out` parametrów. W tym stylu formę serializacji wybrane formanty struktury danych w podstawowej komunikaty i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego tworzy komunikaty do obsługi operacji. Dzięki temu deweloperzy, którzy nie są jeszcze znane z protokołu SOAP i SOAP komunikatów szybkie i łatwe tworzenie i korzystanie z usługi aplikacji.  
  
 Poniższy przykład kodu pokazuje operacji usługi zgodnie z modelem w stylu wywołania RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Zwykle kontrakt danych jest wystarczająca do definiowania schematu dla wiadomości. Na przykład w poprzednim przykładzie jest wystarczające dla większości aplikacji Jeśli `BankingTransaction` i `BankingTransactionResponse` ma kontraktów danych do definiowania zawartości źródłowej wiadomości protokołu SOAP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] kontrakty danych, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Jednak czasami zachodzi konieczność precyzyjne sterowanie jak struktury wiadomości SOAP są przesyłane przez sieć. Najbardziej typowym scenariuszem dla tego wstawia niestandardowe nagłówki SOAP. Inny typowy scenariusz polega do definiowania właściwości zabezpieczeń w nagłówkach wiadomości i treści, oznacza to, aby zdecydować, czy te elementy są cyfrowo podpisane i zaszyfrowane. Ponadto niektóre stosy SOAP innych firm wymagają wiadomości w określonym formacie. Styl wiadomości operacji Podaj tego formantu.  
  
 Operacja styl wiadomości ma co najwyżej jeden parametr i jednej wartości zwracanej gdzie oba typy są typy komunikatu; oznacza to, że ich serializować bezpośrednio do określonej struktury komunikatu SOAP. Może to być dowolnego typu oznaczone <xref:System.ServiceModel.MessageContractAttribute> lub <xref:System.ServiceModel.Channels.Message> typu. Poniższy przykład kodu pokazuje operacji podobne do poprzedniego stylu RCP, ale styl obsługi komunikatów, który używa.  
  
 Na przykład jeśli `BankingTransaction` i `BankingTransactionResponse` są oba typy, które są kontrakty komunikatów, a następnie kod w następujących operacji jest nieprawidłowy.  
  
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
  
 Wyjątek do żadnej operacji, która obejmuje typ kontraktu komunikatu i który nie jest zgodna z jednym z prawidłową. Oczywiście operacje, które nie obejmują typy kontraktu komunikatu nie podlegają te ograniczenia.  
  
 Jeśli typ ma kontraktu komunikatu i kontraktu danych, jej kontraktu komunikatu gdy jest traktowany jako typ jest używany w operacji.  
  
## <a name="defining-message-contracts"></a>Definiowanie kontraktów komunikatu  
 Aby zdefiniować kontraktu komunikatu dla typu (oznacza to, aby zdefiniować mapowania między typem i koperty protokołu SOAP), zastosuj <xref:System.ServiceModel.MessageContractAttribute> do typu. Następnie Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do tych elementów członkowskich tego typu, aby przekształcić nagłówki SOAP i zastosować <xref:System.ServiceModel.MessageBodyMemberAttribute> do tych elementów członkowskich mają być na części treści protokołu SOAP wiadomości.  
  
 Poniższy kod stanowi przykład z użyciem kontraktu komunikatu.  
  
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
  
 Korzystając z tego typu jako parametr operacji, jest generowany koperty protokołu SOAP następujące:  
  
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
  
 Zwróć uwagę, że `operation` i `transactionDate` widoczne jako nagłówki SOAP i treści protokołu SOAP składa się z elementu otoki `BankingTransaction` zawierający `sourceAccount`,`targetAccount`, i `amount`.  
  
 Możesz zastosować <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> wszystkie pola, właściwości i zdarzenia, niezależnie od tego, czy są one publiczne, prywatne, chronionych lub wewnętrzny.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Pozwala określić atrybuty WrapperName i WrapperNamespace, które kontrolują nazwa elementu otoki w treści komunikatu protokołu SOAP. Domyślnie nazwa kontraktu komunikatu typu służy do otoka i przestrzeni nazw, w którym jest zdefiniowany kontraktu komunikatu `HYPERLINK "http://tempuri.org/" http://tempuri.org/` jest używana jako domyślna przestrzeń nazw.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybuty są ignorowane w kontraktach wiadomości. Jeśli <xref:System.Runtime.Serialization.KnownTypeAttribute> jest wymagane, umieść ją na operację, której używa kontraktu komunikatu zagrożona.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Kontrolowanie nagłówek i treść części nazwy i przestrzenie nazw  
 Każda część nagłówek i treść mapowanie w SOAP reprezentację kontraktu komunikatu do elementu XML, który zawiera nazwę i przestrzeń nazw.  
  
 Domyślnie przestrzeń nazw jest taka sama jak przestrzeń nazw kontraktu usługi, komunikat uczestniczy w, która nazwa jest określona przez nazwę elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybuty są stosowane.  
  
 Te ustawienia domyślne można zmienić, manipulowanie <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (w klasie nadrzędnej <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów).  
  
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
  
 W tym przykładzie `IsAudited` nagłówka znajduje się w przestrzeni nazw określonej w kodzie i część treści, która reprezentuje `theData` członek jest reprezentowany przez element XML o nazwie `transactionData`. Poniżej przedstawiono XML wygenerowany dla tego kontraktu komunikatu.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Kontrolowanie, czy są opakowywane części treści protokołu SOAP  
 Domyślnie części treści protokołu SOAP są serializowane w elemencie opakowana. Na przykład poniższy kod przedstawia `HelloGreetingMessage` element otoki wygenerowane z nazwy <xref:System.ServiceModel.MessageContractAttribute> typ kontraktu komunikatu dla `HelloGreetingMessage` wiadomości.  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Aby pominąć element otoki, ustaw <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> właściwości `false`. Aby kontrolować nazwę i przestrzeń nazw elementu otoki, użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> i <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> właściwości.  
  
> [!NOTE]
>  Mając więcej niż jedną część treści wiadomości w wiadomości, które nie zostały opakowane nie jest zgodne z WS-I Basic Profile 1.1 i nie jest zalecane podczas projektowania nowego kontraktów komunikatu. Jednak może być konieczne więcej niż jedną część treści wiadomości bez otoki w niektórych scenariuszach określonych współdziałania. Ma przesyłać więcej niż jednego elementu danych w treści wiadomości, zalecane jest w trybie domyślne (opakowana). Mając więcej niż jeden nagłówek komunikatu w komunikaty bez otoki jest całkowicie dopuszczalne.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Używanie niestandardowych typów wewnątrz kontraktów komunikatu  
 Każdy nagłówek poszczególnych komunikatów i część treści wiadomości jest serializowany (zamieniło XML) używany aparat wybrany serializacji dla kontraktu usługi których komunikat jest używany. Domyślny aparat serializacji `XmlFormatter`, może obsługiwać dowolnego typu, który ma kontraktu danych, albo jawnie (dzięki użyciu <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) albo niejawnie (poprzez jest typem pierwotnym, o <xref:System.SerializableAttribute?displayProperty=nameWithType>i tak dalej). Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 W powyższym przykładzie `Operation` i `BankingTransactionData` typy muszą mieć kontrakt danych i `transactionDate` można serializować ponieważ <xref:System.DateTime> jest właściwością pierwotną (i dlatego ma niejawnych danych kontraktu).  
  
 Jednak istnieje możliwość przełączyć się do silnika różnych serializacji, `XmlSerializer`. Jeśli takie przełącznika, użytkownik powinien zapewnić wszystkich typów, używany w nagłówkach wiadomości i części treści serializacji przy użyciu `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Używanie tablic wewnątrz kontraktów komunikatu  
 Możesz użyć tablice powtarzających się elementów w kontraktach wiadomości na dwa sposoby.  
  
 Pierwsza to użycie <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> bezpośrednio w tablicy. W takim przypadku całą macierz jest szeregowana jako jeden element (czyli jeden nagłówek lub jedną część treści) z wieloma elementami podrzędnymi. Należy wziąć pod uwagę klasy w poniższym przykładzie.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Powoduje to nagłówki SOAP jest podobny do następującego.  
  
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
  
 Innym sposobem jest użycie <xref:System.ServiceModel.MessageHeaderArrayAttribute>. W takim przypadku każdy element tablicy jest serializowany niezależnie, a więc tablicy każdy element ma jeden nagłówek, podobny do następującego.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Domyślna nazwa wpisy tablicy jest nazwą elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderArrayAttribute> zastosować atrybutów.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Dziedziczy atrybut <xref:System.ServiceModel.MessageHeaderAttribute>. Ma ten sam zestaw funkcji jako atrybuty tablicy, na przykład można ustawić kolejność, nazwę i przestrzeń nazw dla tablicy nagłówków w taki sam sposób, należy ustawić dla pojedynczego nagłówka. Jeśli używasz `Order` właściwości w macierzy, dotyczy całego tablicy.  
  
 Możesz zastosować <xref:System.ServiceModel.MessageHeaderArrayAttribute> tylko dla tablic, nie kolekcji.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Korzystanie z tablic bajtowych w kontraktów komunikatu  
 Tablice typu byte, gdy jest używany z atrybutami nietablicowego (<xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute>), nie są traktowane jako tablic, ale jako specjalny typ pierwotny reprezentowane jako algorytmem Base64 danych w wynikowym pliku XML.  
  
 Jeśli używasz tablice typu byte atrybutem tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute>, wyniki są zależne od elementu serializującego w użyciu. Z domyślnego elementu serializującego tablicy jest reprezentowany jako poszczególnych wpis dla każdego bajtu. Jednakże, gdy `XmlSerializer` jest zaznaczone, (przy użyciu <xref:System.ServiceModel.XmlSerializerFormatAttribute> na kontrakt usługi), tablice typu byte są traktowane jako dane Base64, niezależnie od tego, czy są używane atrybuty tablicy lub tablica nie.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podpisywanie i szyfrowanie części wiadomości  
 Kontrakt komunikatu można wskazać, czy nagłówki i/lub treści wiadomości powinna być cyfrowo podpisane i zaszyfrowane.  
  
 Odbywa się przez ustawienie <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów. Ta właściwość jest wyliczeniem <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> typu i może być ustawiony na <xref:System.Net.Security.ProtectionLevel.None> (nie szyfrowania lub podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (podpisu cyfrowego tylko), lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (szyfrowanie i podpis cyfrowy). Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Te funkcje zabezpieczeń do pracy należy poprawnie skonfigurować powiązania i zachowania. Jeśli używasz funkcji zabezpieczeń bez odpowiedniej konfiguracji (np. Próba zalogowania się wiadomość bez podawania poświadczeń), jest zwracany wyjątek podczas sprawdzania poprawności.  
  
 Nagłówki komunikatów poziom ochrony jest określany osobno dla każdego nagłówka.  
  
 Dla części treści wiadomości poziom ochrony można traktować jako "poziom ochrony minimalnej." Treść ma ochrony tylko jeden poziom, niezależnie od liczby części treści. Poziom ochrony treści jest określany przez najwyższą <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> ustawienie właściwości wszystkie części treści. Jednak rzeczywista ochrony minimalny wymagany poziom należy ustawić poziom ochrony każdej części treści.  
  
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
  
 W tym przykładzie `recordID` nagłówka nie jest chroniony, `patientName` jest `signed`, i `SSN` jest zaszyfrowana i podpisana. Co najmniej jednej części, `medicalHistory`, ma <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> zastosowano, i w związku z tym cała treść jest zaszyfrowana i podpisana, mimo że komentarze i diagnozowania części treści Określ niższe poziomy ochrony.  
  
## <a name="soap-action"></a>Akcja SOAP  
 Powiązane standardów usług sieci Web i SOAP Zdefiniuj właściwość o nazwie `Action` które może być stosowany w przypadku każdej wysyłane wiadomości protokołu SOAP. Operacja <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> właściwości formantu wartości tej właściwości.  
  
## <a name="soap-header-attributes"></a>Atrybuty nagłówka SOAP  
 SOAP standard definiuje następujące atrybuty, które mogą wystąpić w nagłówku:  
  
-   `Actor/Role` (`Actor` w SOAP 1.1, `Role` w SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Lub `Role` atrybut określa jednolity identyfikator zasobów (URI) węzła, dla którego ma określony nagłówek. `MustUnderstand` Atrybut określa, czy węzeł przetwarzania nagłówka musi go zrozumieć. `Relay` Atrybut określa, czy nagłówek jest przekazywanie węzły podrzędne. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wykonuje żadnych przetwarzania tych atrybutów w komunikatach przychodzących, z wyjątkiem `MustUnderstand` atrybutu, jak określono w sekcji "Przechowywanie wersji kontraktów komunikatu" w dalszej części tego tematu. Jednak umożliwia odczytywanie i zapisywanie tych atrybutów, w razie potrzeby, tak jak następujący opis.  
  
 Podczas wysyłania wiadomości, te atrybuty nie są emitowane domyślnie. Można to zmienić na dwa sposoby. Najpierw, użytkownik może statycznie Ustaw atrybuty wszystkie odpowiednie wartości, zmieniając <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> właściwości, jak pokazano w poniższym przykładzie kodu. (Należy pamiętać, że ma nie `Role` właściwości; ustawienie <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> emituje właściwości `Role` atrybut, jeśli używasz protokołu SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Drugi sposób kontrolowania tych atrybutów jest dynamicznie, za pomocą kodu. Można to osiągnąć, opakowując typu żądanego nagłówka w <xref:System.ServiceModel.MessageHeader%601> typu (nie należy mylić tego typu z wersją nieogólnego być) i przy użyciu typu razem z <xref:System.ServiceModel.MessageHeaderAttribute>. Następnie należy użyć właściwości na <xref:System.ServiceModel.MessageHeader%601> można ustawić atrybutów protokołu SOAP, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Jeśli używasz zarówno dynamiczny, jak i mechanizmy kontroli statycznych, statyczne ustawienia są używane jako domyślny, ale później może zostać przesłonięta przez przy użyciu mechanizmu dynamicznej, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Tworzenie powtarzane nagłówki za pomocą formantu atrybutu dynamic jest dozwolone, jak pokazano w poniższym kodzie.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Po stronie odbiorczej odczytywania tych atrybutów SOAP jest możliwe tylko jeśli <xref:System.ServiceModel.MessageHeader%601> klasy jest używany do nagłówka w typie. Sprawdź `Actor`, `Relay`, lub `MustUnderstand` właściwości nagłówka o <xref:System.ServiceModel.MessageHeader%601> typ, aby wykryć ustawienia atrybutu dla odebranego komunikatu.  
  
 Gdy komunikat jest odbierany i następnie odesłał, ustawienia atrybutu SOAP postępować tylko obustronne dla nagłówków <xref:System.ServiceModel.MessageHeader%601> typu.  
  
## <a name="order-of-soap-body-parts"></a>Kolejność części treści protokołu SOAP  
 W niektórych sytuacjach może być konieczne sterować kolejnością części treści. Kolejność elementów treści jest alfabetycznej domyślnie, ale mogą być kontrolowane na podstawie <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości. Ta właściwość nie ma tej samej semantyki jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości, z wyjątkiem zachowanie w scenariuszach dziedziczenia (w kontraktów komunikatu, elementy członkowskie nie są sortowane przed członków treści typu pochodnego treści typu podstawowego). Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 W poniższym przykładzie `amount` zwykle przybyły, najpierw ponieważ pierwszy jest alfabetycznie. Jednak <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> właściwości umieszcza je w trzecim pozycji.  
  
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
 Czasami może być konieczna zmiana kontraktów komunikatu. Na przykład nowa wersja aplikacji może dodać dodatkowe nagłówka do wiadomości. Następnie podczas wysyłania z nowej wersji do starego, system musi uwzględniać dodatkowe nagłówka, jak również brak nagłówka podczas przechodzenia w innym kierunku.  
  
 Przechowywanie wersji nagłówków mają zastosowanie następujące reguły:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie object Brak nagłówków — odpowiednie elementy członkowskie są pozostawiane w wartości domyślnych.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje także nieoczekiwany dodatkowych nagłówków. Jedynym wyjątkiem od tej reguły jest dodatkowy nagłówek zawiera `MustUnderstand` ustawić atrybutu `true` przychodzących wiadomości SOAP — w tym przypadku jest zwracany wyjątek, ponieważ nie można przetworzyć nagłówek, który musi być rozpatrywana.  
  
 Komunikat treści mają podobne reguły kontroli wersji — zarówno brak i dodatkowe części treści wiadomości są ignorowane.  
  
## <a name="inheritance-considerations"></a>Uwagi dotyczące dziedziczenia  
 Typ kontraktu komunikatu może dziedziczyć z innego typu, jak typ podstawowy ma również kontraktu komunikatu.  
  
 Podczas tworzenia lub uzyskiwania dostępu do wiadomości przy użyciu typ kontraktu komunikatu, która dziedziczy inne typy kontraktu komunikatu, obowiązują następujące reguły:  
  
-   Wszystkie nagłówki komunikatów w hierarchii dziedziczenia zebrane do pełnego zestawu nagłówków wiadomości.  
  
-   Wszystkie części treści wiadomości w hierarchii dziedziczenia zebrane do utworzenia treści cały komunikat. Części treści są uporządkowane zgodnie z regułami porządkowania zwykle (przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości, a następnie alfabetycznym), niezwiązany z miejsca w hierarchii dziedziczenia. Przy użyciu dziedziczenia kontraktu komunikatu, której części treści wiadomości są na różnych poziomach drzewa dziedziczenia jest zalecane. Jeśli klasa podstawowa i Klasa pochodna definiuje nagłówka lub część treści o takiej samej nazwie, element członkowski z klasy podstawowej większość służy do przechowywania wartości tej części nagłówka lub treści.  
  
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
  
 `PatientRecord` Klasa opisuje komunikat o jeden nagłówek o nazwie `ID`. Nagłówek odpowiada `personID` i nie `patientID` elementu członkowskiego, ponieważ większość podstawowy element członkowski jest wybrany. W związku z tym `patientID` pola w tym przypadku jest bezużyteczny. Treść wiadomości zawiera `diagnosis` następuje element `patientName` elementu, ponieważ jest ona w kolejności alfabetycznej. Zwróć uwagę, przykładzie wzorzec, który jest zdecydowanie niezalecane: zarówno dla typu podstawowego, jak i kontrakty pochodne wiadomości ma części treści wiadomości.  
  
## <a name="wsdl-considerations"></a>Zagadnienia dotyczące WSDL  
 Podczas generowania kontrakt usługi sieci Web Services Description Language (WSDL) z usługą, która używa kontrakty komunikatów, jest pamiętać, że nie wszystkie funkcje kontraktu komunikatu są uwzględniane w wynikowej WSDL. Należy rozważyć następujące kwestie:  
  
-   WSDL nie można wyrazić pojęcie tablicy nagłówków. Podczas tworzenia wiadomości przy użyciu tablicy nagłówków przy użyciu <xref:System.ServiceModel.MessageHeaderArrayAttribute>, wynikowy WSDL odzwierciedla tylko jeden nagłówek zamiast tablicy.  
  
-   Dokument WSDL wynikowy może nie odzwierciedlać niektóre informacje poziomu ochrony.  
  
-   Typ komunikatu wygenerowany w formacie WSDL ma taką samą nazwę jak nazwa klasy typ kontraktu komunikatu.  
  
-   Gdy za pomocą tego samego komunikatu kontraktu w wielu operacjach, wiele typów wiadomości są generowane w dokumencie WSDL. Przez dodanie liczby "2", "3" i tak dalej do celów kolejnych składają unikatowe nazwy. Podczas importowania ponownie WSDL, wiele typów kontraktu komunikatu są tworzone i są identyczne z wyjątkiem ich nazw.  
  
## <a name="soap-encoding-considerations"></a>Uwagi dotyczące kodowania protokołu SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Umożliwia przy użyciu starszej wersji styl XML, kodowania SOAP, jego użycie nie jest zalecane. Korzystając z tym stylem (przez ustawienie `Use` właściwości `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> stosowane do kontraktu usługi), zastosuj następujące dodatkowe zagadnienia:  
  
-   Nagłówki komunikatów są nieobsługiwane. oznacza to, że atrybut <xref:System.ServiceModel.MessageHeaderAttribute> i atrybut tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute> są niezgodne z kodowaniem protokołu SOAP.  
  
-   Jeśli kontraktu komunikatu jest nie opakowane, oznacza to, że właściwość <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ma ustawioną wartość `false`, kontraktu komunikatu może mieć tylko jeden części.  
  
-   Nazwa elementu otoki dla kontraktu komunikatu żądania musi odpowiadać nazwie operacji. Użyj `WrapperName` kontraktu komunikatu dla tej właściwości.  
  
-   Nazwa elementu otoki dla kontraktu komunikatu odpowiedzi musi być taka sama jak nazwa operacji sufiks przez "Odpowiedzi". Użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> kontraktu komunikatu dla tej właściwości.  
  
-   Kodowania SOAP zachowuje odwołania do obiektów. Rozważmy na przykład następujący kod.  
  
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
  
 Po serializacji komunikatów przy użyciu kodowania protokołu SOAP, `changedFrom` i `changedTo` nie zawierają własne kopie `p`, ale zamiast tego punktu do kopiowania wewnątrz `changedBy` elementu.  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 Każdy nagłówek komunikatu i część treści wiadomości jest serializowany niezależnie od innych. W związku z tym samym przestrzeni nazw mogą być deklarowane ponownie dla każdego nagłówka i część treści. Aby poprawić wydajność, szczególnie pod względem rozmiar wiadomości w sieci, należy skonsolidować wiele nagłówków i części treści w Jednoczęściowa nagłówka lub treści. Na przykład zamiast następujący kod:  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Oparty na zdarzeniach asynchronicznych i kontrakty komunikatów  
 Wskazówek dotyczących modelu asynchroniczny oparty na zdarzeniach stanu, że jeśli zostanie zwrócony więcej niż jedną wartość, jedna wartość jest zwracana jako `Result` właściwości, a inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu. Jeden wynik tego jest to, że jeśli klient importuje metadanych za pomocą opcji polecenia asynchroniczny oparty na zdarzeniach i operacji zwraca więcej niż jedną wartość, domyślna <xref:System.EventArgs> obiektu zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.  
  
 Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mieć zwracanych wartości jako właściwości tego obiektu, użyj `/messageContract` — opcja polecenia. Spowoduje to wygenerowanie podpisie, który zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu. Wszystkie wewnętrzny zwracanych wartości są następnie właściwości obiektu komunikatu odpowiedzi.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Projektowanie i implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md)

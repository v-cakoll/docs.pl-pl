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
# <a name="using-message-contracts"></a><span data-ttu-id="a44e1-102">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="a44e1-102">Using Message Contracts</span></span>
<span data-ttu-id="a44e1-103">Zwykle podczas tworzenia aplikacji Windows Communication Foundation (WCF), deweloperzy zwracać szczególną uwagę na struktur danych oraz problemy z serializacją i nie trzeba zajmować się struktury komunikaty, w których odbywa się dane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="a44e1-104">Dla tych aplikacji tworząc kontraktów danych dla parametrów lub zwracanych wartości jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="a44e1-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="a44e1-105">(Aby uzyskać więcej informacji, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="a44e1-105">(For more information, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="a44e1-106">Jednak czasami pełną kontrolę nad struktury komunikatu protokołu SOAP jest równie ważne jak kontrolę nad jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="a44e1-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="a44e1-107">Jest to szczególnie istotne w przypadku, gdy ważne jest współdziałanie lub specjalnie Sterowanie zabezpieczeniami problemy na poziomie komunikatu lub części komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="a44e1-108">W takich przypadkach można utworzyć *kontraktu komunikatu* , pozwala na określenie struktury dokładne wiadomości SOAP wymagane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="a44e1-109">W tym temacie omówiono, jak utworzyć kontrakt szczegółowy komunikat o błędzie dla operacji za pomocą różnych atrybutów kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="a44e1-110">Używanie kontraktów komunikatu podczas operacji</span><span class="sxs-lookup"><span data-stu-id="a44e1-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="a44e1-111">Usługi WCF obsługuje operacje modelowane w dowolnym *zdalnego wywoływania (procedur RPC) styl* lub *komunikatów styl*.</span><span class="sxs-lookup"><span data-stu-id="a44e1-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="a44e1-112">W przypadku operacji stylu RPC mogą mieć dowolny typ możliwy do serializacji i mieć dostęp do funkcji, które są dostępne dla połączeń lokalnych, takich jak wiele parametrów i `ref` i `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="a44e1-113">W przypadku tego stylu formantu serializacji wybrany struktury danych w podstawowej wiadomości i środowisko wykonawcze programu WCF tworzy wiadomości do obsługi operacji.</span><span class="sxs-lookup"><span data-stu-id="a44e1-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="a44e1-114">Dzięki temu deweloperzy, którzy nie jest zaznajomiony z protokołu SOAP i SOAP komunikaty, aby szybko i łatwo tworzyć i korzystać z usługi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a44e1-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="a44e1-115">Poniższy przykład kodu pokazuje operacji usługi w modelu w stylu RPC.</span><span class="sxs-lookup"><span data-stu-id="a44e1-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="a44e1-116">Zazwyczaj kontraktu danych jest wystarczająca do zdefiniowania schematu dla wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="a44e1-117">Na przykład w poprzednim przykładzie, jest wystarczające dla większości aplikacji Jeśli `BankingTransaction` i `BankingTransactionResponse` mają kontraktów danych do definiowania zawartości źródłowej komunikaty protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a44e1-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="a44e1-118">Aby uzyskać więcej informacji na temat kontraktów danych zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a44e1-118">For more information about data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="a44e1-119">Jednak czasami jest niezbędne precyzyjnie kontrolować, jak struktury wiadomości SOAP przesyłane przez sieć.</span><span class="sxs-lookup"><span data-stu-id="a44e1-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="a44e1-120">Najbardziej typowym scenariuszem dla tego jest wstawianie niestandardowych nagłówków protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a44e1-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="a44e1-121">Inny typowy scenariusz polega do definiowania właściwości zabezpieczeń dla komunikatu nagłówki i treść, oznacza to, aby zdecydować, czy te elementy są cyfrowo podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="a44e1-122">Na koniec niektórych stosów protokołu SOAP firm wymagają komunikatów w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="a44e1-123">Operacje obsługi komunikatów w stylu zapewniają tej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="a44e1-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="a44e1-124">Operacja stylu komunikatów ma co najwyżej jeden parametr i jedną wartość zwracaną gdzie oba typy są typy komunikatów; oznacza to, że ich serializować bezpośrednio do określonej struktury komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a44e1-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="a44e1-125">Może to być dowolny typ oznaczone <xref:System.ServiceModel.MessageContractAttribute> lub <xref:System.ServiceModel.Channels.Message> typu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="a44e1-126">Poniższy przykład kodu pokazuje operacją podobny do poprzedniego RCP stylu, ale, który używa stylu komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="a44e1-127">Na przykład jeśli `BankingTransaction` i `BankingTransactionResponse` są oba typy, które są kontrakty komunikatów, a następnie kod w następujących operacji jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="a44e1-128">Jednakże poniższy kod jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="a44e1-129">Wyjątek jest generowany dla każdej operacji, która obejmuje typ kontraktu komunikatu i który nie jest zgodna z jednym z wzorców prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="a44e1-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="a44e1-130">Oczywiście operacje, które nie obejmują typy kontraktu komunikatu nie podlegają te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="a44e1-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="a44e1-131">Jeśli typ ma kontraktu komunikatu i kontraktu danych, jej kontraktu komunikatu uznaje się, gdy typ jest używany w operacji.</span><span class="sxs-lookup"><span data-stu-id="a44e1-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="a44e1-132">Definiowanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="a44e1-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="a44e1-133">Do zdefiniowania kontraktu komunikatu dla typu (oznacza to, aby zdefiniować mapowania między typem i koperty protokołu SOAP), zastosuj <xref:System.ServiceModel.MessageContractAttribute> do typu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="a44e1-134">Następnie Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do tych członków typ, który chcesz przekształcić nagłówków protokołu SOAP, a następnie zastosować <xref:System.ServiceModel.MessageBodyMemberAttribute> do tych elementów członkowskich mają być na części treści protokołu SOAP wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="a44e1-135">Poniższy kod zawiera przykład z użyciem kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-136">Korzystając z tego typu jako parametru operacja, jest generowany w następujących koperty protokołu SOAP:</span><span class="sxs-lookup"><span data-stu-id="a44e1-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="a44e1-137">Należy zauważyć, że `operation` i `transactionDate` są wyświetlane jako nagłówków protokołu SOAP i treści protokołu SOAP składa się z element otoki `BankingTransaction` zawierający `sourceAccount`,`targetAccount`, i `amount`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="a44e1-138">Można zastosować <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> do pola, właściwości i zdarzenia, niezależnie od tego, czy są publiczne, prywatne, chroniony lub wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="a44e1-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="a44e1-139"><xref:System.ServiceModel.MessageContractAttribute> Pozwala określić atrybuty WrapperName i WrapperNamespace, które kontrolować nazwę element otoki w treści komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a44e1-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="a44e1-140">Domyślnie nazwa kontraktu komunikatu typ jest używany do otoki i przestrzeni nazw, w którym zdefiniowano kontraktu komunikatu `http://tempuri.org/` jest używany jako domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="a44e1-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> <span data-ttu-id="a44e1-141">atrybuty są ignorowane w kontrakty komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-141">attributes are ignored in message contracts.</span></span> <span data-ttu-id="a44e1-142">Jeśli <xref:System.Runtime.Serialization.KnownTypeAttribute> jest wymagane, umieść go w operacji, który używa kontraktu komunikatu w danym.</span><span class="sxs-lookup"><span data-stu-id="a44e1-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="a44e1-143">Kontrolowanie nagłówka i treści część nazwy i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="a44e1-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="a44e1-144">W reprezentacji SOAP kontraktu komunikatu każda część nagłówka i treści mapuje do elementu XML, który ma nazwę i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a44e1-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="a44e1-145">Domyślnie, przestrzeń nazw jest taka sama jak przestrzeń nazw kontraktu usługi, komunikat jest uczestnikiem, która nazwa jest określana przez nazwę elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybuty są stosowane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="a44e1-146">Możesz zmienić te ustawienia domyślne, manipulowanie <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (w klasie nadrzędnej <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów).</span><span class="sxs-lookup"><span data-stu-id="a44e1-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="a44e1-147">Należy wziąć pod uwagę klasy w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="a44e1-148">W tym przykładzie `IsAudited` nagłówka znajduje się w przestrzeni nazw określonej w kodzie, a część treści, która reprezentuje `theData` elementu członkowskiego jest reprezentowany przez element XML o nazwie `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="a44e1-149">Na poniższym obrazie przedstawiono XML generowanych dla tego kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="a44e1-150">Kontrolowanie, czy zostaną opakowane części treści protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="a44e1-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="a44e1-151">Domyślnie części treści protokołu SOAP są serializowane w elemencie opakowana.</span><span class="sxs-lookup"><span data-stu-id="a44e1-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="a44e1-152">Na przykład, poniższy kod przedstawia `HelloGreetingMessage` element otoki wygenerowany na podstawie nazwy <xref:System.ServiceModel.MessageContractAttribute> typ kontraktu komunikatu, aby uzyskać `HelloGreetingMessage` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="a44e1-153">Aby pominąć element otoki, należy ustawić <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="a44e1-154">Aby kontrolować nazwę i przestrzeń nazw elementu otoki, należy użyć <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> i <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a44e1-155">Posiadanie więcej niż jedną część treści wiadomości w wiadomości, które nie zostały zapakowane nie jest zgodne z protokołu WS-I Basic Profile 1.1 i nie jest zalecane podczas projektowania nowych kontrakty komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="a44e1-156">Jednak może być konieczne więcej niż jedną część treści komunikatu odkodowany w niektórych scenariuszach współpracy określone.</span><span class="sxs-lookup"><span data-stu-id="a44e1-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="a44e1-157">Jeśli ma zostać przesłany więcej niż jednego elementu danych w treści komunikatu, zaleca się do używania trybu domyślnego (zawinięte).</span><span class="sxs-lookup"><span data-stu-id="a44e1-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="a44e1-158">Całkowicie dopuszczalne jest posiadanie więcej niż jeden nagłówek wiadomości w nieopakowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="a44e1-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="a44e1-159">Przy użyciu niestandardowych typów wewnątrz kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="a44e1-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="a44e1-160">Każdy nagłówek wiadomości poszczególnych i część treści wiadomości jest serializowana (przekształcane w XML) przy użyciu aparatu wybranym serializacji w dla kontraktu usługi użycia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="a44e1-161">Domyślny mechanizm serializacji, `XmlFormatter`, może obsłużyć dowolny typ, który ma kontraktu danych, albo jawnie (dzięki <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) lub niejawnie (poprzez jest typ pierwotny, posiadające <xref:System.SerializableAttribute?displayProperty=nameWithType>i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="a44e1-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="a44e1-162">Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="a44e1-162">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="a44e1-163">W powyższym przykładzie `Operation` i `BankingTransactionData` typy muszą mieć kontraktu danych i `transactionDate` jest możliwy do serializacji ponieważ <xref:System.DateTime> jest podstawowy (i dlatego ma umowę niejawne danych).</span><span class="sxs-lookup"><span data-stu-id="a44e1-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="a44e1-164">Jednak istnieje możliwość przełączyć się na aparat serializacji różnych `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="a44e1-165">W przypadku wprowadzenia takiego przełącznika, należy upewnić się, że wszystkie typy używane do nagłówków wiadomości i części treści są serializacji przy użyciu `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="a44e1-166">Używanie tablic wewnątrz kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="a44e1-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="a44e1-167">Możesz użyć tablic powtarzających się elementów w kontrakty komunikatów na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="a44e1-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="a44e1-168">Pierwsza to użycie <xref:System.ServiceModel.MessageHeaderAttribute> lub <xref:System.ServiceModel.MessageBodyMemberAttribute> bezpośrednio w tablicy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="a44e1-169">W tym przypadku całej tablicy jest serializowany jako jeden element (czyli jeden nagłówek lub jedną część treści) z wieloma elementami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="a44e1-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="a44e1-170">Należy wziąć pod uwagę klasy w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="a44e1-171">Powoduje to nagłówków protokołu SOAP jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="a44e1-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-172">Innym sposobem jest użycie <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a44e1-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="a44e1-173">W takim przypadku każdy element tablicy jest serializowana niezależnie i, że każdy element w tablicy ma jeden nagłówek, podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="a44e1-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="a44e1-174">Domyślna nazwa dla wpisów tablicy jest nazwą elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderArrayAttribute> zastosować atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="a44e1-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> Dziedziczy atrybut <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a44e1-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="a44e1-176">Ma ona ten sam zestaw funkcji jako atrybuty inny niż tablica, na przykład możliwość określenia kolejność, nazwę i przestrzeń nazw dla tablicy nagłówków w taki sam sposób, gdy ustawiasz dla pojedynczego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a44e1-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="a44e1-177">Kiedy używasz `Order` właściwość w tablicy, dotyczy ona całej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="a44e1-178">Można zastosować <xref:System.ServiceModel.MessageHeaderArrayAttribute> tylko do tablic, nie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a44e1-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="a44e1-179">Korzystanie z tablic bajtowych w kontrakty komunikatów</span><span class="sxs-lookup"><span data-stu-id="a44e1-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="a44e1-180">Tablice typu byte, gdy jest używana z atrybutami inny niż tablica (<xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute>), nie są traktowane jako tablic, ale jako specjalny typ pierwotny, reprezentowane jako dane zakodowane w formacie Base64 wynikowy kod XML.</span><span class="sxs-lookup"><span data-stu-id="a44e1-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="a44e1-181">Kiedy używać tablic bajtowych z atrybutem tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute>, wyniki zależą od serializator używany.</span><span class="sxs-lookup"><span data-stu-id="a44e1-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="a44e1-182">Przy użyciu domyślnego elementu serializującego tablica jest przedstawiana jako pojedynczy wpis dla każdego bajtu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="a44e1-183">Jednak gdy `XmlSerializer` jest zaznaczone, (przy użyciu <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi), tablice bajtowe są traktowane jako dane Base64, niezależnie od tego, czy są używane atrybuty tablicy lub inny niż tablica.</span><span class="sxs-lookup"><span data-stu-id="a44e1-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="a44e1-184">Podpisywanie i szyfrowanie części wiadomości</span><span class="sxs-lookup"><span data-stu-id="a44e1-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="a44e1-185">Kontrakt komunikatu można wskazać, czy nagłówki i/lub treści komunikatu powinna być cyfrowo podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="a44e1-186">Jest to realizowane przez ustawienie <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="a44e1-187">Właściwość jest wyliczeniem <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> wpisz i może być równa <xref:System.Net.Security.ProtectionLevel.None> (nie szyfrowania lub podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (podpis cyfrowy tylko), lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (szyfrowanie i podpisu cyfrowego).</span><span class="sxs-lookup"><span data-stu-id="a44e1-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="a44e1-188">Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="a44e1-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="a44e1-189">Te funkcje zabezpieczeń do pracy należy poprawnie skonfigurować powiązania i zachowania.</span><span class="sxs-lookup"><span data-stu-id="a44e1-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="a44e1-190">Jeśli używasz tych funkcji zabezpieczeń bez odpowiedniej konfiguracji (na przykład, próba zalogowania się wiadomość bez podawania poświadczeń), wyjątek jest generowany w momencie sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="a44e1-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="a44e1-191">Nagłówki komunikatów poziom ochrony jest określana osobno dla każdego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a44e1-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="a44e1-192">Dla części treści wiadomości poziom ochrony można traktować jako "minimalny poziom ochrony."</span><span class="sxs-lookup"><span data-stu-id="a44e1-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="a44e1-193">Treść ma poziom ochrony tylko jeden, niezależnie od liczby części treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="a44e1-194">Poziom ochrony treści jest określana przez najwyższy <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> ustawienie właściwości wszystkie części treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="a44e1-195">Jednak należy ustawić poziom ochrony każdej części treści do rzeczywistego protection minimalny wymagany poziom.</span><span class="sxs-lookup"><span data-stu-id="a44e1-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="a44e1-196">Należy wziąć pod uwagę klasy w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-197">W tym przykładzie `recordID` nagłówka nie są chronione, `patientName` jest `signed`, i `SSN` zostaje zaszyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="a44e1-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="a44e1-198">Część treści co najmniej jeden `medicalHistory`, ma <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> zastosowane, i w związku z tym treść cały komunikat zostaje zaszyfrowany i podpisany, mimo że komentarze i diagnozowania części treści Określ niższe poziomy ochrony.</span><span class="sxs-lookup"><span data-stu-id="a44e1-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="a44e1-199">Akcja SOAP</span><span class="sxs-lookup"><span data-stu-id="a44e1-199">SOAP Action</span></span>  
 <span data-ttu-id="a44e1-200">Powiązane standardów usług sieci Web i SOAP zdefiniować właściwość o nazwie `Action` , może być obecny dla każdego komunikatu protokołu SOAP, wysyłane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="a44e1-201">Operacja <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> właściwości formantu wartość tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="a44e1-202">Atrybuty nagłówek SOAP</span><span class="sxs-lookup"><span data-stu-id="a44e1-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="a44e1-203">SOAP standard definiuje następujące atrybuty, które mogą występować w nagłówku:</span><span class="sxs-lookup"><span data-stu-id="a44e1-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   `Actor/Role` <span data-ttu-id="a44e1-204">(`Actor` w SOAP 1.1, `Role` w SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="a44e1-204">(`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="a44e1-205">`Actor` Lub `Role` atrybut określa identyfikator (URI) węzła, dla których przeznaczony jest dany nagłówek.</span><span class="sxs-lookup"><span data-stu-id="a44e1-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="a44e1-206">`MustUnderstand` Atrybut określa, czy węzeł przetwarzania nagłówka musi go zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="a44e1-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="a44e1-207">`Relay` Atrybut określa, czy nagłówek do węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a44e1-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="a44e1-208">Usługi WCF nie wykonuje jakiegokolwiek przetwarzania tych atrybutów na komunikaty przychodzące z wyjątkiem `MustUnderstand` atrybutu, jak to określono w sekcji "Przechowywanie wersji kontraktów komunikatu" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="a44e1-209">Jednakże umożliwia odczytywanie i zapisywanie tych atrybutów zgodnie z potrzebami, tak jak w poniższym opisie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="a44e1-210">Podczas wysyłania komunikatu, te atrybuty nie są generowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="a44e1-211">Możesz to zmienić na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="a44e1-211">You can change this in two ways.</span></span> <span data-ttu-id="a44e1-212">Najpierw możesz statycznie ustawić atrybuty do dowolnych wartości, żądane przez zmianę <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, i <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> właściwości, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="a44e1-213">(Należy pamiętać, że ma nie `Role` właściwości; ustawienie <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> emituje właściwość `Role` atrybutu, jeśli używasz protokołu SOAP 1.2).</span><span class="sxs-lookup"><span data-stu-id="a44e1-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="a44e1-214">Drugi sposób kontroluje te atrybuty jest dynamicznie, za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="a44e1-215">Można to osiągnąć przez opakowywanie typ żądanego nagłówka w <xref:System.ServiceModel.MessageHeader%601> typu (Upewnij się, nie należy mylić tego typu za pomocą wersji nieogólnego) i za pomocą typu wraz z <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a44e1-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="a44e1-216">Następnie należy użyć właściwości na <xref:System.ServiceModel.MessageHeader%601> można ustawić atrybutów protokołu SOAP, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-217">Jeśli używasz mechanizmy kontroli statycznej i dynamicznej statyczne ustawienia są używane jako domyślne, ale później może zostać przesłonięta przez przy użyciu mechanizmu dynamiczne, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="a44e1-218">Tworzenie powtarzanych nagłówki przy użyciu atrybutu dynamic kontroli jest dozwolone, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="a44e1-219">Po stronie odbierającej odczytywania tych atrybutów protokołu SOAP jest możliwe tylko jeśli <xref:System.ServiceModel.MessageHeader%601> klasa jest używana dla nagłówka typu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="a44e1-220">Sprawdź `Actor`, `Relay`, lub `MustUnderstand` właściwości nagłówek <xref:System.ServiceModel.MessageHeader%601> typu, aby odnaleźć ustawień atrybutów na odebranym komunikacie.</span><span class="sxs-lookup"><span data-stu-id="a44e1-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="a44e1-221">Gdy komunikat jest odbierany i następnie odesłał, ustawień atrybutów protokołu SOAP tylko Przejdź błądzenia dla nagłówków <xref:System.ServiceModel.MessageHeader%601> typu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="a44e1-222">Zlecenia części treści protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="a44e1-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="a44e1-223">W niektórych sytuacjach może być konieczne kontrolować kolejność części treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="a44e1-224">Kolejność elementów treści jest porządek alfabetyczny domyślnie, ale mogą być kontrolowane przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a44e1-225">Właściwość ta ma tą samą semantyką jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości, z wyjątkiem zachowanie w scenariuszach dziedziczenia (w treści typu podstawowego, elementy członkowskie nie są sortowane przed elementy członkowskie typu pochodnego treści kontrakty komunikatów).</span><span class="sxs-lookup"><span data-stu-id="a44e1-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="a44e1-226">Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="a44e1-226">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="a44e1-227">W poniższym przykładzie `amount` zwykle przybyły, aby najpierw ponieważ ona jest pierwszy w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="a44e1-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="a44e1-228">Jednak <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> właściwość umieszcza położenia trzeciego.</span><span class="sxs-lookup"><span data-stu-id="a44e1-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="a44e1-229">Przechowywanie wersji kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="a44e1-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="a44e1-230">Od czasu do czasu może być konieczna zmiana kontrakty komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a44e1-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="a44e1-231">Na przykład nową wersję aplikacji może dodać dodatkowe nagłówka do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="a44e1-232">Następnie podczas wysyłania z nowej wersji do starego, system musi obsłużyć dodatkowe nagłówka, jak również brak nagłówka podczas przechodzenia w drugą stronę.</span><span class="sxs-lookup"><span data-stu-id="a44e1-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="a44e1-233">Obowiązują następujące reguły dla nagłówków wersji:</span><span class="sxs-lookup"><span data-stu-id="a44e1-233">The following rules apply for versioning headers:</span></span>  
  
-   <span data-ttu-id="a44e1-234">Usługi WCF nie obiekt do brakujących nagłówków — odpowiednie elementy członkowskie są pozostawiane wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="a44e1-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   <span data-ttu-id="a44e1-235">Usługi WCF ignoruje także nieoczekiwane dodatkowe nagłówki.</span><span class="sxs-lookup"><span data-stu-id="a44e1-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="a44e1-236">Jedynym wyjątkiem od tej reguły jest, jeśli dodatkowe nagłówek ma `MustUnderstand` ustawioną wartość atrybutu `true` w przychodzącej wiadomości SOAP — w tym przypadku jest zgłaszany wyjątek, ponieważ nie można przetworzyć nagłówek, który musi być rozumiane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="a44e1-237">Komunikat o treści mają podobne zasady przechowywania wersji — Brak i dodatkowe części treści wiadomości są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="a44e1-238">Uwagi dotyczące dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="a44e1-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="a44e1-239">Typ kontraktu komunikatu może dziedziczyć z innego typu, tak długo, jak typ podstawowy ma również kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="a44e1-240">Podczas tworzenia lub uzyskiwania dostępu do wiadomości przy użyciu typ kontraktu komunikatu, która dziedziczy inne typy kontraktu komunikatu, obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="a44e1-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="a44e1-241">Wszystkie nagłówki wiadomości w hierarchii dziedziczenia pochodzą ze sobą w celu utworzenia pełnego zestawu nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="a44e1-242">Wszystkie części treści wiadomości w hierarchii dziedziczenia pochodzą ze sobą w celu utworzenia pełnego treść.</span><span class="sxs-lookup"><span data-stu-id="a44e1-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="a44e1-243">Części treści są uporządkowane zgodnie ze zwykłymi regułami sortowania (przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości i następnie alfabetycznej), niezwiązany z ich miejsca w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="a44e1-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="a44e1-244">Za pomocą Dziedziczenie kontraktów komunikatu, w których części treści wiadomości wystąpić na różnych poziomach drzewa dziedziczenia jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="a44e1-245">Jeśli klasa bazowa i Klasa pochodna należy zdefiniować nagłówek lub część treści o takiej samej nazwie, elementu członkowskiego z klasy podstawowej większość służy do przechowywania wartości w tej części w nagłówku lub w treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="a44e1-246">Należy wziąć pod uwagę klas w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-247">`PatientRecord` Klasa opisuje komunikat jeden nagłówek o nazwie `ID`.</span><span class="sxs-lookup"><span data-stu-id="a44e1-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="a44e1-248">Nagłówek odnosi się do `personID` i nie `patientID` elementu członkowskiego, ponieważ większość podstawowy element członkowski jest wybierany.</span><span class="sxs-lookup"><span data-stu-id="a44e1-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="a44e1-249">W efekcie `patientID` pola w tym przypadku jest bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="a44e1-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="a44e1-250">Treść wiadomości zawiera `diagnosis` następuje `patientName` elementu, ponieważ jest w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="a44e1-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="a44e1-251">Należy zauważyć, że w przykładzie pokazano wzorzec, który jest zdecydowanie odradzane: zarówno podstawowy, jak i kontrakty komunikatów pochodna ma części treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a44e1-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="a44e1-252">Zagadnienia dotyczące WSDL</span><span class="sxs-lookup"><span data-stu-id="a44e1-252">WSDL Considerations</span></span>  
 <span data-ttu-id="a44e1-253">Podczas generowania kontraktu usługi sieci Web Services Description Language (WSDL) z usługi, który używa kontrakty komunikatów, to należy pamiętać, że nie wszystkie funkcje kontraktu komunikatu są odzwierciedlane w wynikowej WSDL.</span><span class="sxs-lookup"><span data-stu-id="a44e1-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="a44e1-254">Należy wziąć pod uwagę następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="a44e1-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="a44e1-255">WSDL nie można wyrazić koncepcji tablicy nagłówków.</span><span class="sxs-lookup"><span data-stu-id="a44e1-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="a44e1-256">Podczas tworzenia wiadomości z tablicą przy użyciu nagłówków <xref:System.ServiceModel.MessageHeaderArrayAttribute>, WSDL wynikowy odzwierciedla tylko jeden nagłówek zamiast tablicy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="a44e1-257">Dokument WSDL wynikowy może nie odzwierciedlać pewne informacje poziom ochrony.</span><span class="sxs-lookup"><span data-stu-id="a44e1-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="a44e1-258">Typ komunikatu wygenerowany w formacie WSDL ma taką samą nazwę jak nazwa klasy typ kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="a44e1-259">Gdy kontrakt przy użyciu tego samego komunikatu w wielu operacjach, wiele typów wiadomości są generowane w dokumencie WSDL.</span><span class="sxs-lookup"><span data-stu-id="a44e1-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="a44e1-260">Nazwy są tworzone unikatowe, przez dodanie liczby "2", "3" i tak dalej do późniejszego wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="a44e1-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="a44e1-261">Podczas importowania pliku WSDL Wstecz, wiele typy kontraktu komunikatu są tworzone i są identyczne, z wyjątkiem ich nazwy.</span><span class="sxs-lookup"><span data-stu-id="a44e1-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="a44e1-262">Uwagi dotyczące kodowania SOAP</span><span class="sxs-lookup"><span data-stu-id="a44e1-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="a44e1-263">WCF pozwala na używanie starszej wersji protokołu SOAP stylu XML, kodowania, jego użycie nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="a44e1-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="a44e1-264">Korzystając z tego stylu (przez ustawienie `Use` właściwości `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> stosowane do umowy serwisowej), mają zastosowanie następujące dodatkowe kwestie:</span><span class="sxs-lookup"><span data-stu-id="a44e1-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="a44e1-265">Nagłówki wiadomości są nieobsługiwane. oznacza to, że atrybut <xref:System.ServiceModel.MessageHeaderAttribute> i atrybut tablicy <xref:System.ServiceModel.MessageHeaderArrayAttribute> są niezgodne z kodowaniem SOAP.</span><span class="sxs-lookup"><span data-stu-id="a44e1-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="a44e1-266">Jeśli kontraktu komunikatu jest nie zawinięty, oznacza to, jeśli właściwość <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ustawiono `false`, kontraktu komunikatu może mieć część treści tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="a44e1-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="a44e1-267">Nazwa elementu otoki dla kontraktu komunikatu żądania musi odpowiadać nazwie operacji.</span><span class="sxs-lookup"><span data-stu-id="a44e1-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="a44e1-268">Użyj `WrapperName` właściwości kontraktu komunikatu, w tym.</span><span class="sxs-lookup"><span data-stu-id="a44e1-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="a44e1-269">Nazwa elementu otoki dla kontraktu komunikatu odpowiedzi musi być taka sama jak nazwa operacji sufiks przez "Response".</span><span class="sxs-lookup"><span data-stu-id="a44e1-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="a44e1-270">Użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> właściwości kontraktu komunikatu, w tym.</span><span class="sxs-lookup"><span data-stu-id="a44e1-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="a44e1-271">Kodowaniem SOAP zachowuje odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="a44e1-272">Rozważmy na przykład, poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="a44e1-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="a44e1-273">Po serializacji wiadomości przy użyciu kodowania SOAP, `changedFrom` i `changedTo` nie zawierają własne kopie `p`, ale zamiast tego wskazać polecenie kopiowania wewnątrz `changedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="a44e1-274">Zagadnienia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="a44e1-274">Performance Considerations</span></span>  
 <span data-ttu-id="a44e1-275">Każdy nagłówek wiadomości i część treści wiadomości jest serializowana, niezależnie od innych.</span><span class="sxs-lookup"><span data-stu-id="a44e1-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="a44e1-276">W związku z tym ten sam przestrzenie nazw mogą być deklarowane ponownie dla każdego nagłówka i część treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="a44e1-277">Aby zwiększyć wydajność, zwłaszcza jeśli chodzi o rozmiar wiadomości w sieci, należy skonsolidować wiele nagłówków i części treści w jednoczęściowych nagłówku lub w treści.</span><span class="sxs-lookup"><span data-stu-id="a44e1-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="a44e1-278">Na przykład zamiast następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a44e1-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="a44e1-279">Użyj tego kodu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="a44e1-280">Oparte na zdarzeniach asynchronicznych i kontrakt komunikatu</span><span class="sxs-lookup"><span data-stu-id="a44e1-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="a44e1-281">Dotyczących projektowania opartego na zdarzeniach modelu asynchronicznego stanu, że jeśli zwracana jest więcej niż jedną wartość, jedną wartość jest zwracana jako `Result` właściwości i inne są zwracane jako właściwości na <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="a44e1-282">Jeden wynik tego jest to, że jeśli klient importuje metadane przy użyciu opcji oparte na zdarzeniach asynchronicznych polecenia, a operacja zwraca więcej niż jedną wartość, wartość domyślna <xref:System.EventArgs> zwraca jedną wartość jako `Result` właściwość i pozostałej właściwości <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="a44e1-283">Jeśli chcesz otrzymywać obiekt komunikatu jako `Result` właściwości i mają zwracanych wartości, jak używać właściwości dla tego obiektu `/messageContract` opcja polecenia.</span><span class="sxs-lookup"><span data-stu-id="a44e1-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="a44e1-284">Spowoduje to wygenerowanie sygnaturę, która zwraca komunikat odpowiedzi jako `Result` właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a44e1-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="a44e1-285">Wszystkie wewnętrzne wartości zwracane są następnie właściwości obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a44e1-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44e1-286">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a44e1-286">See also</span></span>

- [<span data-ttu-id="a44e1-287">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="a44e1-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="a44e1-288">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="a44e1-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)

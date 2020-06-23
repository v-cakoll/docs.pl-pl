---
title: Używanie kontraktów komunikatu
description: Dowiedz się, jak używać atrybutów kontraktu wiadomości do tworzenia kontraktu komunikatu określającego strukturę komunikatu protokołu SOAP w obszarze WFC.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 0a75298b50df74ddf15904af43a0eb62c5ba8496
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244715"
---
# <a name="using-message-contracts"></a><span data-ttu-id="d7bd9-103">Używanie kontraktów komunikatu</span><span class="sxs-lookup"><span data-stu-id="d7bd9-103">Using Message Contracts</span></span>
<span data-ttu-id="d7bd9-104">Zwykle podczas kompilowania aplikacji Windows Communication Foundation (WCF) deweloperzy mogą zwrócić szczególną uwagę na struktury danych i problemy z serializacji i nie muszą stanowić problemu ze strukturą komunikatów, w których dane są przenoszone.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-104">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="d7bd9-105">W przypadku tych aplikacji Tworzenie kontraktów danych dla parametrów lub zwracanych wartości jest proste.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-105">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="d7bd9-106">(Aby uzyskać więcej informacji, zobacz [określanie transfer danych w kontraktach usługi](specifying-data-transfer-in-service-contracts.md)).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-106">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="d7bd9-107">Jednak czasami Pełna kontrola nad strukturą komunikatu protokołu SOAP jest równie ważna jako kontrola nad zawartością.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-107">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="d7bd9-108">Jest to szczególnie ważne, gdy współpraca jest ważna lub aby w szczególności kontrolować problemy z zabezpieczeniami na poziomie komunikatu lub komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-108">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="d7bd9-109">W takich przypadkach można utworzyć *kontrakt komunikatu* , który pozwala określić strukturę dokładnego komunikatu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-109">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="d7bd9-110">W tym temacie omówiono sposób użycia różnych atrybutów kontraktu komunikatów w celu utworzenia konkretnej kontraktu komunikatu dla operacji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-110">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="d7bd9-111">Korzystanie z kontraktów komunikatów w operacjach</span><span class="sxs-lookup"><span data-stu-id="d7bd9-111">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="d7bd9-112">Funkcja WCF obsługuje operacje modelowane na *stylu zdalnego wywołania procedury (RPC)* lub w *stylu obsługi komunikatów*.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-112">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="d7bd9-113">W operacji w stylu wywołania procedury (RPC) można używać dowolnego typu możliwego do serializacji i masz dostęp do funkcji, które są dostępne dla wywołań lokalnych, takich jak wiele parametrów i `ref` `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-113">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="d7bd9-114">W tym stylu forma serializacji wybrana kontroluje strukturę danych w podstawowych komunikatach, a środowisko uruchomieniowe WCF tworzy komunikaty do obsługi tej operacji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-114">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="d7bd9-115">Umożliwia to deweloperom, którzy nie znają komunikatów SOAP i SOAP, aby szybko i łatwo tworzyć i używać aplikacji usług.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-115">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="d7bd9-116">Poniższy przykład kodu przedstawia operację usługi modelowaną w stylu wywołania RPC.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-116">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="d7bd9-117">Zwykle kontrakt danych jest wystarczający do zdefiniowania schematu dla komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-117">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="d7bd9-118">Na przykład w poprzednim przykładzie jest to wystarczające dla większości aplikacji, jeśli `BankingTransaction` i `BankingTransactionResponse` zawiera Kontrakty danych do definiowania zawartości źródłowych komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-118">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="d7bd9-119">Aby uzyskać więcej informacji na temat kontraktów danych, zobacz [Korzystanie z kontraktów danych](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-119">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="d7bd9-120">Jednak czasami konieczne jest precyzyjną kontrolę nad sposobem, w jaki Struktura komunikatu protokołu SOAP przesyłanego przez sieć.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-120">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="d7bd9-121">Najbardziej typowym scenariuszem jest wstawianie niestandardowych nagłówków protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-121">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="d7bd9-122">Innym typowym scenariuszem jest zdefiniowanie właściwości zabezpieczeń dla nagłówków i treści wiadomości, oznacza to, że w celu określenia, czy te elementy są podpisane cyfrowo i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-122">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="d7bd9-123">Na koniec niektóre stosy protokołu SOAP innych firm wymagają komunikatów w określonym formacie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-123">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="d7bd9-124">Operacje w stylu obsługi komunikatów zapewniają tę kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-124">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="d7bd9-125">Operacja w stylu obsługi komunikatów ma co najwyżej jeden parametr i jedną wartość zwracaną, gdy oba typy to typy komunikatów. oznacza to, że serializacji bezpośrednio do określonej struktury wiadomości SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-125">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="d7bd9-126">Może to być dowolny typ oznaczony przy użyciu <xref:System.ServiceModel.MessageContractAttribute> lub <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-126">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="d7bd9-127">Poniższy przykład kodu pokazuje operację podobną do powyższego typu RCP, ale używa stylu obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-127">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="d7bd9-128">Na przykład jeśli `BankingTransaction` i `BankingTransactionResponse` są oba typy, które są kontraktami komunikatów, kod w następujących operacjach jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-128">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="d7bd9-129">Jednak następujący kod jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-129">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="d7bd9-130">Wyjątek jest zgłaszany dla każdej operacji, która obejmuje typ kontraktu komunikatu, który nie jest zgodny z jednym z prawidłowych wzorców.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-130">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="d7bd9-131">Oczywiście operacje, które nie obejmują typów kontraktu komunikatów, nie podlegają tym ograniczeniom.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-131">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="d7bd9-132">Jeśli typ ma zarówno umowę komunikatu, jak i kontrakt danych, tylko jego kontrakt wiadomości jest brany pod uwagę, gdy typ jest używany w operacji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-132">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="d7bd9-133">Definiowanie kontraktów komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7bd9-133">Defining Message Contracts</span></span>  
 <span data-ttu-id="d7bd9-134">Aby zdefiniować kontrakt wiadomości dla typu (oznacza to, aby zdefiniować mapowanie między typem i kopertą protokołu SOAP), Zastosuj <xref:System.ServiceModel.MessageContractAttribute> do tego typu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-134">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="d7bd9-135">Następnie Zastosuj <xref:System.ServiceModel.MessageHeaderAttribute> do tych elementów członkowskich typu, który chcesz umieścić w nagłówkach protokołu SOAP, i Zastosuj <xref:System.ServiceModel.MessageBodyMemberAttribute> do tych członków, które chcesz umieścić w częściach treści protokołu SOAP wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-135">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="d7bd9-136">Poniższy kod stanowi przykład użycia kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-136">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-137">W przypadku używania tego typu jako parametru operacji generowana jest następująca Koperta protokołu SOAP:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-137">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-138">Zauważ, że `operation` i `transactionDate` są wyświetlane jako nagłówki protokołu SOAP, a treść protokołu SOAP składa się z elementu otoki `BankingTransaction` zawierającego `sourceAccount` , `targetAccount` , i `amount` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-138">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="d7bd9-139">Można zastosować <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> do wszystkich pól, właściwości i zdarzeń, niezależnie od tego, czy są one publiczne, prywatne, chronione czy wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-139">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="d7bd9-140"><xref:System.ServiceModel.MessageContractAttribute>Pozwala określić atrybuty otokname i WrapperNamespace, które kontrolują nazwę elementu otoki w treści komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-140">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="d7bd9-141">Domyślnie nazwa typu kontraktu wiadomości jest używana dla otoki i przestrzeń nazw, w której jest zdefiniowany kontrakt komunikatu, `http://tempuri.org/` jest używana jako domyślna przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-141">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7bd9-142"><xref:System.Runtime.Serialization.KnownTypeAttribute>atrybuty są ignorowane w kontraktach komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="d7bd9-143">Jeśli <xref:System.Runtime.Serialization.KnownTypeAttribute> jest to wymagane, umieść je w operacji, która używa danego kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-143">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="d7bd9-144">Kontrolowanie nazw nagłówka i części treści i przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="d7bd9-144">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="d7bd9-145">W reprezentacji protokołu SOAP kontraktu komunikatu każdy nagłówek i część treści są mapowane na element XML, który ma nazwę i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-145">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="d7bd9-146">Domyślnie przestrzeń nazw jest taka sama jak przestrzeń nazw kontraktu usługi, w którym uczestniczy ten komunikat, a nazwa jest określana przez nazwę elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> mają zastosowanie atrybuty lub.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-146">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="d7bd9-147">Te ustawienia domyślne można zmienić przez manipulowanie <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (w klasie nadrzędnej <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów i).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-147">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="d7bd9-148">Rozważmy klasę w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-148">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="d7bd9-149">W tym przykładzie `IsAudited` nagłówek znajduje się w przestrzeni nazw określonej w kodzie, a część treści reprezentująca `theData` element członkowski jest reprezentowana przez element XML o nazwie `transactionData` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-149">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="d7bd9-150">Poniżej przedstawiono listę XML wygenerowaną dla tego kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-150">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="d7bd9-151">Kontrolowanie, czy części treści protokołu SOAP są opakowane</span><span class="sxs-lookup"><span data-stu-id="d7bd9-151">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="d7bd9-152">Domyślnie części treści protokołu SOAP są serializowane wewnątrz opakowanego elementu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-152">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="d7bd9-153">Na przykład poniższy kod pokazuje `HelloGreetingMessage` element otoki wygenerowany na podstawie nazwy <xref:System.ServiceModel.MessageContractAttribute> typu w kontrakcie komunikatu dla `HelloGreetingMessage` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-153">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="d7bd9-154">Aby pominąć element otoki, należy ustawić <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> Właściwość na `false` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-154">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="d7bd9-155">Aby kontrolować nazwę i przestrzeń nazw elementu otoki, użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> właściwości i.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-155">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7bd9-156">Posiadanie więcej niż jednej części treści wiadomości w komunikatach, które nie są opakowane, nie jest zgodne z profilem WS-I Basic 1,1 i nie jest zalecane podczas projektowania nowych kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-156">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="d7bd9-157">Może jednak być konieczne posiadanie więcej niż jednej nieopakowanej treści wiadomości w niektórych scenariuszach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-157">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="d7bd9-158">W przypadku przesyłania więcej niż jednego fragmentu danych w treści wiadomości zaleca się użycie trybu domyślnego (opakowany).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-158">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="d7bd9-159">Posiadanie więcej niż jednego nagłówka wiadomości w nieopakowanych komunikatach jest całkowicie akceptowalne.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-159">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="d7bd9-160">Używanie typów niestandardowych wewnątrz kontraktów komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7bd9-160">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="d7bd9-161">Każdy pojedynczy nagłówek wiadomości i część treści komunikatu są serializowane (włączone w formacie XML) przy użyciu wybranego aparatu serializacji dla kontraktu usługi, w którym jest używana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-161">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="d7bd9-162">Domyślny aparat serializacji, `XmlFormatter` ,, może obsługiwać dowolny typ, który ma umowę danych, albo jawnie (przez posiadanie <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ) lub niejawnie (przez typ pierwotny, posiadający <xref:System.SerializableAttribute?displayProperty=nameWithType> , i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-162">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="d7bd9-163">Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-163">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="d7bd9-164">W poprzednim przykładzie `Operation` `BankingTransactionData` typy i muszą mieć kontrakt danych i można je `transactionDate` serializować, ponieważ <xref:System.DateTime> jest elementem pierwotnym (i dlatego ma niejawny kontrakt danych).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-164">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="d7bd9-165">Istnieje jednak możliwość przełączenia się do innego aparatu serializacji, czyli `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-165">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="d7bd9-166">W przypadku wybrania takiego przełącznika należy upewnić się, że wszystkie typy używane do nagłówków wiadomości i części treści są serializowane przy użyciu `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-166">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="d7bd9-167">Używanie tablic wewnątrz kontraktów komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7bd9-167">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="d7bd9-168">Można używać tablic powtarzających się elementów w kontraktach komunikatów na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-168">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="d7bd9-169">Pierwszym z nich jest użycie <xref:System.ServiceModel.MessageHeaderAttribute> lub a <xref:System.ServiceModel.MessageBodyMemberAttribute> bezpośrednio na tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-169">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="d7bd9-170">W takim przypadku cała tablica jest serializowana jako jeden element (to jest jeden nagłówek lub jedna część treści) z wieloma elementami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-170">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="d7bd9-171">Rozważmy klasę w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-171">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="d7bd9-172">Wyniki w nagłówkach protokołu SOAP są podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-172">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-173">Alternatywą dla tego jest użycie <xref:System.ServiceModel.MessageHeaderArrayAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-173">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="d7bd9-174">W takim przypadku każdy element tablicy jest serializowany niezależnie i dlatego każdy element tablicy ma jeden nagłówek, podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-174">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="d7bd9-175">Nazwa domyślna dla wpisów tablicy to nazwa elementu członkowskiego, do którego <xref:System.ServiceModel.MessageHeaderArrayAttribute> zastosowano atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-175">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="d7bd9-176"><xref:System.ServiceModel.MessageHeaderArrayAttribute>Atrybut dziedziczy z <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-176">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="d7bd9-177">Ma ten sam zestaw funkcji co atrybuty nietablicowe, na przykład można ustawić kolejność, nazwę i przestrzeń nazw dla tablicy nagłówków w taki sam sposób, jak w przypadku pojedynczego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-177">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="d7bd9-178">Użycie `Order` właściwości w tablicy ma zastosowanie do całej tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-178">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="d7bd9-179">Można zastosować <xref:System.ServiceModel.MessageHeaderArrayAttribute> tylko do tablic, nie kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-179">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="d7bd9-180">Używanie tablic bajtowych w kontraktach komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7bd9-180">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="d7bd9-181">Tablice bajtowe, gdy są używane z atrybutami nietablicowymi ( <xref:System.ServiceModel.MessageBodyMemberAttribute> i <xref:System.ServiceModel.MessageHeaderAttribute> ), nie są traktowane jako tablice, ale jako specjalne typy pierwotne reprezentowane jako dane zakodowane algorytmem Base64 w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-181">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="d7bd9-182">W przypadku używania tablic bajtowych z atrybutem Array <xref:System.ServiceModel.MessageHeaderArrayAttribute> wyniki zależą od serializatora w użyciu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-182">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="d7bd9-183">W przypadku domyślnego serializatora tablica jest reprezentowana jako pojedynczy wpis dla każdego bajtu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-183">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="d7bd9-184">Jednak po `XmlSerializer` wybraniu (przy użyciu <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi) tablice bajtowe są traktowane jako dane base64, niezależnie od tego, czy są używane atrybuty tablicowe czy nietablicowe.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-184">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="d7bd9-185">Podpisywanie i szyfrowanie części wiadomości</span><span class="sxs-lookup"><span data-stu-id="d7bd9-185">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="d7bd9-186">Umowa o komunikat może wskazywać, czy nagłówki i/lub treść komunikatu powinny być podpisane cyfrowo i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-186">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="d7bd9-187">Jest to realizowane przez ustawienie <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.MessageHeaderAttribute> i <xref:System.ServiceModel.MessageBodyMemberAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-187">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="d7bd9-188">Właściwość jest wyliczeniem <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> typu i może być ustawiona na <xref:System.Net.Security.ProtectionLevel.None> (bez szyfrowania lub podpisu), <xref:System.Net.Security.ProtectionLevel.Sign> (tylko podpis cyfrowy) lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (szyfrowanie i podpis cyfrowy).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-188">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="d7bd9-189">Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-189">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="d7bd9-190">Aby te funkcje zabezpieczeń działały, należy prawidłowo skonfigurować powiązanie i zachowania.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-190">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="d7bd9-191">W przypadku korzystania z tych funkcji zabezpieczeń bez właściwej konfiguracji (na przykład próba podpisania wiadomości bez podawania poświadczeń) wyjątek jest zgłaszany podczas walidacji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-191">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="d7bd9-192">Dla nagłówków wiadomości poziom ochrony jest określany osobno dla każdego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-192">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="d7bd9-193">W przypadku części treści wiadomości poziom ochrony może być uważany za "minimalny poziom ochrony".</span><span class="sxs-lookup"><span data-stu-id="d7bd9-193">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="d7bd9-194">Treść ma tylko jeden poziom ochrony, niezależnie od liczby części treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-194">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="d7bd9-195">Poziom ochrony treści jest określany na podstawie najwyższego <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> Ustawienia właściwości wszystkich części treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-195">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="d7bd9-196">Należy jednak ustawić poziom ochrony każdej części treści na rzeczywisty wymagany minimalny poziom ochrony.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-196">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="d7bd9-197">Rozważmy klasę w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-197">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-198">W tym przykładzie `recordID` nagłówek nie jest chroniony, `patientName` jest `signed` i `SSN` jest szyfrowany i podpisany.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-198">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="d7bd9-199">Zastosowano co najmniej jedną część treści, `medicalHistory` <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> i w ten sposób cała treść komunikatu jest zaszyfrowana i podpisana, mimo że komentarze i części treści diagnostyki określają niższe poziomy ochrony.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-199">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="d7bd9-200">Akcja SOAP</span><span class="sxs-lookup"><span data-stu-id="d7bd9-200">SOAP Action</span></span>  
 <span data-ttu-id="d7bd9-201">Standardy SOAP i pokrewne usługi sieci Web definiują właściwość o nazwie `Action` , która może być obecna dla każdej wysyłanej wiadomości protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-201">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="d7bd9-202">Operacja <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> Właściwości kontrolują wartość tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-202">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="d7bd9-203">Atrybuty nagłówka SOAP</span><span class="sxs-lookup"><span data-stu-id="d7bd9-203">SOAP Header Attributes</span></span>  
 <span data-ttu-id="d7bd9-204">Standard SOAP definiuje następujące atrybuty, które mogą istnieć w nagłówku:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-204">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="d7bd9-205">`Actor/Role`( `Actor` w soap 1,1, `Role` w SOAP 1,2)</span><span class="sxs-lookup"><span data-stu-id="d7bd9-205">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="d7bd9-206">`Actor`Atrybut or `Role` określa Uniform Resource Identifier (URI) węzła, dla którego jest przeznaczony podany nagłówek.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-206">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="d7bd9-207">Ten `MustUnderstand` atrybut określa, czy węzeł przetwarzający nagłówek musi je zrozumieć.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-207">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="d7bd9-208">Ten `Relay` atrybut określa, czy nagłówek ma być przekazywany do węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-208">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="d7bd9-209">Funkcja WCF nie wykonuje żadnego przetwarzania tych atrybutów w komunikatach przychodzących, z wyjątkiem tego `MustUnderstand` , jak określono w sekcji "wersja kontraktu komunikatów" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-209">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="d7bd9-210">Umożliwia jednak odczytywanie i zapisywanie tych atrybutów w razie potrzeby, jak w poniższym opisie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-210">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="d7bd9-211">Podczas wysyłania komunikatu te atrybuty nie są emitowane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-211">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="d7bd9-212">Można to zmienić na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-212">You can change this in two ways.</span></span> <span data-ttu-id="d7bd9-213">Najpierw można statycznie ustawić atrybuty dla dowolnych żądanych wartości, zmieniając <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType> właściwości, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> , jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-213">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="d7bd9-214">(Należy zauważyć, że nie ma `Role` właściwości; ustawienie <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> Właściwości emituje `Role` atrybut, jeśli używasz protokołu SOAP 1,2).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-214">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="d7bd9-215">Drugi sposób sterowania tymi atrybutami jest dynamiczny, za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-215">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="d7bd9-216">Można to osiągnąć przez zapakowanie żądanego typu nagłówka w <xref:System.ServiceModel.MessageHeader%601> typie (należy pamiętać, aby nie mylić tego typu z wersją nieogólną) i przy użyciu typu razem z <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-216">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="d7bd9-217">Następnie można użyć właściwości w <xref:System.ServiceModel.MessageHeader%601> celu ustawienia atrybutów protokołu SOAP, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-217">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-218">Jeśli używasz zarówno dynamicznego, jak i statycznego mechanizmu kontroli, ustawienia statyczne są używane jako domyślne, ale można je później zastąpić przy użyciu mechanizmu dynamicznego, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-218">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="d7bd9-219">Tworzenie powtórzonych nagłówków z dynamiczną kontrolką atrybutów jest dozwolone, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-219">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="d7bd9-220">Na stronie otrzymującej odczytywanie tych atrybutów protokołu SOAP można wykonać tylko wtedy, gdy <xref:System.ServiceModel.MessageHeader%601> Klasa jest używana dla nagłówka w typie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-220">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="d7bd9-221">Sprawdź `Actor` , `Relay` lub `MustUnderstand` Właściwości nagłówka <xref:System.ServiceModel.MessageHeader%601> typu, aby odnaleźć ustawienia atrybutu dla odebranego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-221">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="d7bd9-222">Gdy wiadomość zostanie odebrana, a następnie wysłana z powrotem, ustawienia atrybutu protokołu SOAP są tylko w przypadku nagłówków <xref:System.ServiceModel.MessageHeader%601> typu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-222">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="d7bd9-223">Kolejność części treści protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="d7bd9-223">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="d7bd9-224">W pewnych okolicznościach może być konieczne kontrolowanie kolejności części treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-224">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="d7bd9-225">Kolejność elementów treści jest domyślnie alfabetyczna, ale może być kontrolowana przez <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-225">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d7bd9-226">Ta właściwość ma tę samą semantykę co <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> Właściwość, z wyjątkiem zachowania w scenariuszach dziedziczenia (w kontraktach komunikatów, składowe treści typu podstawowego nie są sortowane przed składowanymi elementami typu pochodnego).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-226">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="d7bd9-227">Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="d7bd9-227">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="d7bd9-228">W poniższym przykładzie w `amount` pierwszej kolejności jest to pierwsze, ponieważ jest ono pierwsze w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-228">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="d7bd9-229">Jednak <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> Właściwość umieszcza ją w trzecim położeniu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-229">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="d7bd9-230">Przechowywanie wersji kontraktu komunikatów</span><span class="sxs-lookup"><span data-stu-id="d7bd9-230">Message Contract Versioning</span></span>  
 <span data-ttu-id="d7bd9-231">Czasami może zajść konieczność zmiany kontraktów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-231">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="d7bd9-232">Na przykład Nowa wersja aplikacji może dodać dodatkowy nagłówek do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-232">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="d7bd9-233">Następnie podczas wysyłania z nowej wersji do starego system musi zajmować się dodatkowym nagłówkiem, a także brakującym nagłówkiem podczas przechodzenia w inne kierunki.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-233">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="d7bd9-234">W przypadku nagłówków wersji obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-234">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="d7bd9-235">WCF nie jest obiektem w brakujących nagłówkach — odpowiadające im elementy członkowskie są pozostawiane w wartościach domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-235">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="d7bd9-236">Funkcja WCF ignoruje także nieoczekiwane dodatkowe nagłówki.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-236">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="d7bd9-237">Jedynym wyjątkiem od tej reguły jest, czy dodatkowy nagłówek ma `MustUnderstand` atrybut ustawiony na `true` w przychodzącym komunikacie protokołu SOAP — w tym przypadku wyjątek jest zgłaszany, ponieważ nie można przetworzyć nagłówka, który musi być zrozumiały.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-237">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="d7bd9-238">Treści komunikatów mają podobne reguły dotyczące wersji — ignorowane są zarówno brakujące, jak i dodatkowe części treści komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-238">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="d7bd9-239">Zagadnienia dotyczące dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="d7bd9-239">Inheritance Considerations</span></span>  
 <span data-ttu-id="d7bd9-240">Typ kontraktu komunikatu może dziedziczyć z innego typu, o ile typ podstawowy ma także kontrakt komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-240">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="d7bd9-241">Podczas tworzenia lub uzyskiwania dostępu do wiadomości za pomocą typu kontraktu komunikatu, który dziedziczy z innych typów kontraktu komunikatów, mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-241">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="d7bd9-242">Wszystkie nagłówki wiadomości w hierarchii dziedziczenia są zbierane razem w celu utworzenia pełnego zestawu nagłówków wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-242">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="d7bd9-243">Wszystkie części treści wiadomości w hierarchii dziedziczenia są zbierane wraz z pełną treścią wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-243">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="d7bd9-244">Części treści są uporządkowane zgodnie ze zwykłymi regułami określania kolejności (według <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> właściwości, a następnie alfabetyczne) bez znaczenia dla ich miejsca w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-244">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="d7bd9-245">Używanie dziedziczenia kontraktu komunikatów, gdzie części treści komunikatu występują na wielu poziomach drzewa dziedziczenia jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-245">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="d7bd9-246">Jeśli klasa bazowa i Klasa pochodna definiują nagłówek lub część treści o tej samej nazwie, element członkowski z klasy podstawowej jest używany do przechowywania wartości tego nagłówka lub części treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-246">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="d7bd9-247">Rozważmy klasy w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-247">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-248">`PatientRecord`Klasa opisuje komunikat z jednym nagłówkiem o nazwie `ID` .</span><span class="sxs-lookup"><span data-stu-id="d7bd9-248">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="d7bd9-249">Nagłówek odnosi się do `personID` i nie do `patientID` elementu członkowskiego, ponieważ wybierany jest element członkowski najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-249">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="d7bd9-250">Oznacza to, że `patientID` w tym przypadku pole jest bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-250">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="d7bd9-251">Treść wiadomości zawiera `diagnosis` element, po którym następuje `patientName` element, ponieważ jest to porządek alfabetyczny.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-251">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="d7bd9-252">Należy zauważyć, że w przykładzie przedstawiono wzorzec, który jest silnie odradzany: kontrakt podstawowy i pochodny są częścią wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-252">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="d7bd9-253">Zagadnienia dotyczące języka WSDL</span><span class="sxs-lookup"><span data-stu-id="d7bd9-253">WSDL Considerations</span></span>  
 <span data-ttu-id="d7bd9-254">Podczas generowania kontraktu Web Services Description Language (WSDL) z usługi używającej kontraktów komunikatów należy pamiętać, że nie wszystkie funkcje kontraktu wiadomości są odzwierciedlone w wyniku WSDL.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-254">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="d7bd9-255">Rozważ następujące kwestie:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-255">Consider the following points:</span></span>  
  
- <span data-ttu-id="d7bd9-256">Język WSDL nie może wyrazić koncepcji tablicy nagłówków.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-256">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="d7bd9-257">W przypadku tworzenia komunikatów z tablicą nagłówków przy użyciu <xref:System.ServiceModel.MessageHeaderArrayAttribute> , wynikiem WSDL odzwierciedla tylko jeden nagłówek zamiast tablicy.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-257">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="d7bd9-258">Otrzymany dokument WSDL może nie odzwierciedlać niektórych informacji na poziomie ochrony.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-258">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="d7bd9-259">Typ komunikatu wygenerowany w języku WSDL ma taką samą nazwę jak nazwa klasy typu kontraktu komunikatu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-259">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="d7bd9-260">W przypadku korzystania z tego samego kontraktu komunikatu w wielu operacjach w dokumencie WSDL generowane są wiele typów komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-260">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="d7bd9-261">Nazwy są unikatowe przez dodanie cyfr "2", "3" itd., do kolejnych celów.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-261">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="d7bd9-262">Podczas importowania z powrotem do języka WSDL tworzone są wiele typów kontraktu komunikatów i są one identyczne z wyjątkiem nazw.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-262">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="d7bd9-263">Zagadnienia dotyczące kodowania SOAP</span><span class="sxs-lookup"><span data-stu-id="d7bd9-263">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="d7bd9-264">Funkcja WCF umożliwia użycie starszego stylu kodowania SOAP w kodzie XML, ale nie jest to zalecane.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-264">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="d7bd9-265">W przypadku korzystania z tego stylu (przez ustawienie `Use` właściwości na `Encoded` na podstawie <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> zastosowania do kontraktu usługi) obowiązują następujące dodatkowe zagadnienia:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-265">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="d7bd9-266">Nagłówki komunikatów nie są obsługiwane; oznacza to, że atrybut <xref:System.ServiceModel.MessageHeaderAttribute> i atrybut Array <xref:System.ServiceModel.MessageHeaderArrayAttribute> są niezgodne z KODOWANIEM protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-266">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="d7bd9-267">Jeśli kontrakt wiadomości nie jest opakowany, oznacza to, że jeśli właściwość <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> jest ustawiona na `false` , kontrakt komunikatu może mieć tylko jedną część treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-267">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="d7bd9-268">Nazwa elementu otoki dla kontraktu komunikatu żądania musi być zgodna z nazwą operacji.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-268">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="d7bd9-269">Użyj `WrapperName` Właściwości kontraktu wiadomości dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-269">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="d7bd9-270">Nazwa elementu otoki dla kontraktu komunikatu odpowiedzi musi być taka sama jak nazwa operacji sufiksu "odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="d7bd9-270">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="d7bd9-271">Użyj <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> Właściwości kontraktu wiadomości dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-271">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="d7bd9-272">Kodowanie protokołu SOAP zachowuje odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-272">SOAP encoding preserves object references.</span></span> <span data-ttu-id="d7bd9-273">Rozważmy na przykład poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-273">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-274">Po serializacji komunikatu przy użyciu kodowania protokołu SOAP `changedFrom` i `changedTo` nie zawierają własnych kopii `p` , ale zamiast tego należy wskazać kopię wewnątrz `changedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-274">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="d7bd9-275">Zagadnienia dotyczące wydajności</span><span class="sxs-lookup"><span data-stu-id="d7bd9-275">Performance Considerations</span></span>  
 <span data-ttu-id="d7bd9-276">Każdy nagłówek wiadomości i część treści komunikatu są serializowane niezależnie od innych.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-276">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="d7bd9-277">W związku z tym te same przestrzenie nazw można ponownie zadeklarować dla każdego nagłówka i części ciała.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-277">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="d7bd9-278">Aby zwiększyć wydajność, szczególnie w zakresie rozmiaru wiadomości w sieci, Konsoliduj wiele nagłówków i części treści w jeden nagłówek lub część treści.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-278">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="d7bd9-279">Na przykład zamiast następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="d7bd9-279">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="d7bd9-280">Użyj tego kodu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-280">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="d7bd9-281">Kontrakty asynchronicznych i komunikatów opartych na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d7bd9-281">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="d7bd9-282">Wskazówki dotyczące projektowania dla asynchronicznego stanu modelu opartego na zdarzeniach, które w przypadku zwrócenia więcej niż jednej wartości, jedna wartość jest zwracana jako `Result` Właściwość, a pozostałe są zwracane jako właściwości w <xref:System.EventArgs> obiekcie.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-282">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d7bd9-283">W związku z tym, jeśli klient Importuje metadane przy użyciu opcji poleceń asynchronicznych opartych na zdarzeniach, a operacja zwraca więcej niż jedną wartość, <xref:System.EventArgs> obiekt domyślny zwraca jedną wartość jako `Result` Właściwość, a reszta jest właściwościami <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-283">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="d7bd9-284">Jeśli chcesz otrzymać obiekt wiadomości jako `Result` Właściwość i mieć wartości zwracane jako właściwości dla tego obiektu, użyj `/messageContract` opcji polecenia.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-284">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="d7bd9-285">Spowoduje to wygenerowanie sygnatury zwracającej komunikat odpowiedzi jako `Result` Właściwość <xref:System.EventArgs> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-285">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d7bd9-286">Wszystkie wewnętrzne wartości zwracane są następnie właściwościami obiektu komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d7bd9-286">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bd9-287">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7bd9-287">See also</span></span>

- [<span data-ttu-id="d7bd9-288">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d7bd9-288">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="d7bd9-289">Projektowanie i implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="d7bd9-289">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)

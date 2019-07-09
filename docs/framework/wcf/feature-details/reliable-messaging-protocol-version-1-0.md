---
title: Reliable Messaging Protocol w wersji 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 6fceb49d107e4268a4b9fad6197335ff9e2af9ab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662794"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="c50c3-102">Reliable Messaging Protocol w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="c50c3-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="c50c3-103">W tym temacie omówiono szczegóły dotyczące implementacji usług Windows Communication Foundation (WCF) dla protokołu WS-Reliable Messaging protocol February 2005 (w wersji 1.0) niezbędne do współpracy przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="c50c3-104">Usługi WCF następuje specyfikacji WS-Reliable Messaging z ograniczeniami i wyjaśnienia szczegółowo opisane w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c50c3-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="c50c3-105">Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1.0 jest wykonywane począwszy od WinFX.</span><span class="sxs-lookup"><span data-stu-id="c50c3-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="c50c3-106">WS-Reliable Messaging February 2005 protokołu jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c50c3-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="c50c3-107">Dla wygody tematu są używane następujące role:</span><span class="sxs-lookup"><span data-stu-id="c50c3-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="c50c3-108">Inicjator: klienta, który inicjuje WS-Reliable komunikat tworzenia sekwencji</span><span class="sxs-lookup"><span data-stu-id="c50c3-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="c50c3-109">Obiekt odpowiadający w trybie: usługa, która odbiera żądania inicjatora</span><span class="sxs-lookup"><span data-stu-id="c50c3-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="c50c3-110">Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c50c3-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="c50c3-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="c50c3-111">Prefix</span></span>|<span data-ttu-id="c50c3-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c50c3-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="c50c3-113">Menedżer zasobów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c50c3-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|
|<span data-ttu-id="c50c3-114">netrm</span><span class="sxs-lookup"><span data-stu-id="c50c3-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="c50c3-115">s</span><span class="sxs-lookup"><span data-stu-id="c50c3-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="c50c3-116">wsa</span><span class="sxs-lookup"><span data-stu-id="c50c3-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="c50c3-117">wsse</span><span class="sxs-lookup"><span data-stu-id="c50c3-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a><span data-ttu-id="c50c3-118">Obsługa komunikatów</span><span class="sxs-lookup"><span data-stu-id="c50c3-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="c50c3-119">Komunikaty do określania sekwencji</span><span class="sxs-lookup"><span data-stu-id="c50c3-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="c50c3-120">Implementuje WCF `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić sekwencji niezawodnych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="c50c3-121">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="c50c3-121">The following constraints apply:</span></span>

- <span data-ttu-id="c50c3-122">B1101: Inicjator WCF nie generuje opcjonalny element wygasa w `CreateSequence` komunikatu lub w przypadkach podczas `CreateSequence` wiadomość zawiera `Offer` element, opcjonalny `Expires` elementu w `Offer` elementu.</span><span class="sxs-lookup"><span data-stu-id="c50c3-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="c50c3-123">B1102: Podczas uzyskiwania dostępu do `CreateSequence` komunikatów WCF`Responder` wysyła i odbiera zarówno `Expires` elementów, jeśli istnieje, ale nie używa ich wartości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="c50c3-124">WS-Reliable Messaging wprowadza `Offer` mechanizm nawiązać dwa konwersacji skorelowany sekwencji, które tworzą sesji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="c50c3-125">R1103: Jeśli `CreateSequence` zawiera `Offer` elemencie Reliable Messaging obiektu odpowiadającego w trybie musi zaakceptować sekwencji i elastyczniejsze `CreateSequenceResponse` zawierający `wsrm:Accept` elementu tworzących dwa skorelowane konwersacji sekwencji lub odrzucić `CreateSequence`żądania.</span><span class="sxs-lookup"><span data-stu-id="c50c3-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="c50c3-126">R1104: `SequenceAcknowledgement` i komunikatów aplikacji przepływają w odwrotnej kolejności musi zostać wysłany do `ReplyTo` odwołania do endpoint `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="c50c3-127">R1105: `AcksTo` i `ReplyTo` punktu końcowego, który odwołuje się w `CreateSequence` musi mieć wartości adresów, które odpowiadają octet-wise.</span><span class="sxs-lookup"><span data-stu-id="c50c3-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="c50c3-128">Obiekt odpowiadający w trybie WCF — sprawdza, czy identyfikator URI części `AcksTo` i `ReplyTo` określenia opcji są identyczne, przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="c50c3-129">R1106: `AcksTo` i `ReplyTo` odwołania do punktu końcowego w `CreateSequence` powinny mieć ten sam zestaw parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="c50c3-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="c50c3-130">Usługi WCF nie wymusza, ale przyjmuje wartość tego [dokumentacja parametry] `AcksTo` i `ReplyTo` na `CreateSequence` są identyczne i używa [dokumentacja parametry] z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji prawdą.</span><span class="sxs-lookup"><span data-stu-id="c50c3-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="c50c3-131">R1107: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` i komunikatów aplikacji przepływają w przeciwny sekwencji musi zostać wysłany do `ReplyTo` odwołania do endpoint `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="c50c3-132">R1108: Gdy dwie sekwencje prawdą są określane przy użyciu mechanizmu oferty `[address]` właściwość `wsrm:AcksTo` odwołania do punktu końcowego elementu podrzędnego `wsrm:Accept` elementu `CreateSequenceResponse` musi odpowiadać byte-wise miejsca docelowego identyfikatora URI `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="c50c3-133">R1109: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzeń komunikatów przez obiekt odpowiadający w trybie muszą być wysyłane do tego samego odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="c50c3-134">Usługi WCF używa do ustanawiania niezawodnych sesji między inicjatora i Responder WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="c50c3-135">Implementacja WS-Reliable Messaging WCF firmy udostępnia niezawodnej sesji, jednokierunkowe "żądanie-odpowiedź" i pełny dupleks wzorce obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="c50c3-136">WS-Reliable Messaging `Offer` mechanizm na `CreateSequence` / `CreateSequenceResponse` umożliwia ustanawianie dwie sekwencje skorelowany prawdą i zapewnia protokół sesji, która jest odpowiednia dla wszystkich komunikatów z punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="c50c3-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="c50c3-137">Ponieważ WCF daje gwarancję zabezpieczeń dla sesji, w tym ochronę end-to-end spójność sesji, jest praktyczne w celu zapewnienia, że komunikaty przeznaczone do tej samej strony docierają tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="c50c3-138">Dzięki temu również piggy zapasowy potwierdzeń sekwencji na wiadomościach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="c50c3-139">W związku z tym ograniczenia R1104 R1105 i R1108 mają zastosowanie do programu WCF.</span><span class="sxs-lookup"><span data-stu-id="c50c3-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="c50c3-140">Przykładem `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-140">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="c50c3-141">Przykładem `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-141">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="c50c3-142">Sequence</span><span class="sxs-lookup"><span data-stu-id="c50c3-142">Sequence</span></span>

<span data-ttu-id="c50c3-143">Oto lista ograniczeń, które dotyczą sekwencji:</span><span class="sxs-lookup"><span data-stu-id="c50c3-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="c50c3-144">Generuje B1201:WCF i uzyskuje dostęp do sekwencji numerów nie jest wyższa niż `xs:long`firmy maksymalną wartość włącznie 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="c50c3-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="c50c3-145">B1202:WCF zawsze generuje zabudowanych pusta ostatni komunikat z identyfikator URI akcji z `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="c50c3-146">B1203: Usługi WCF odbiera i zapewnia komunikat z nagłówkiem sekwencji, który zawiera `LastMessage` tak długo, jak identyfikator URI akcji nie jest elementem `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="c50c3-147">Przykład nagłówek sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-147">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="c50c3-148">Nagłówek bloku nagłówka AckRequested</span><span class="sxs-lookup"><span data-stu-id="c50c3-148">AckRequested Header</span></span>

<span data-ttu-id="c50c3-149">Korzysta z usługi WCF `AckRequested` nagłówek jako mechanizm utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="c50c3-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="c50c3-150">Usługi WCF nie generuje opcjonalnego `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="c50c3-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="c50c3-151">Po odebraniu komunikatu z `AckRequested` nagłówek, który zawiera `MessageNumber` ignoruje WCF elementu `MessageNumber` wartości elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c50c3-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="c50c3-152">Nagłówek SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="c50c3-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="c50c3-153">Usługi WCF używa mechanizmu nakładka potwierdzeń sekwencji w WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="c50c3-154">R1401: Gdy dwie sekwencje prawdą są określane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` nagłówek może być zawarta w każdy komunikat aplikacji przekazywane do określonego adresata.</span><span class="sxs-lookup"><span data-stu-id="c50c3-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="c50c3-155">B1402: Gdy WCF musi wygenerować potwierdzenia przed odebraniem wiadomości dowolnej sekwencji (na przykład, aby spełnić `AckRequested` wiadomości), generuje WCF `SequenceAcknowledgement` nagłówek, który zawiera zakres 0-0, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c50c3-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="c50c3-156">B1403: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementu, ale obsługuje `Nack` elementów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="c50c3-157">Błędy WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="c50c3-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="c50c3-158">Oto lista ograniczeń, które są stosowane do implementacji WCF WS-Reliable Messaging błędów:</span><span class="sxs-lookup"><span data-stu-id="c50c3-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="c50c3-159">B1501: Usługi WCF nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="c50c3-160">Punkt końcowy B1502:WCF może generować `CreateSequenceRefused` błędów, jak opisano w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="c50c3-161">B1503:when punktu końcowego usługi osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, WCF, generuje dodatkowe `CreateSequenceRefused` błędów podrzędnego, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c50c3-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="c50c3-162">Błędy usługi WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="c50c3-162">WS-Addressing Faults</span></span>

<span data-ttu-id="c50c3-163">Ponieważ WS-Reliable Messaging korzysta z protokołu WS-Addressing, WS-Reliable Messaging WCF implementacji może generować błędy WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="c50c3-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="c50c3-164">W tej sekcji omówiono WS-Addressing błędy, generowane WCF jawnie w warstwie usługi WS-Reliable Messaging:</span><span class="sxs-lookup"><span data-stu-id="c50c3-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="c50c3-165">B1601:WCF generuje odporności komunikat adresowania nagłówka wymagane, gdy jest spełniony jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c50c3-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="c50c3-166">Brak komunikatu `Sequence` nagłówka i `Action` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c50c3-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="c50c3-167">A `CreateSequence` Brak komunikatu `MessageId` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c50c3-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="c50c3-168">A `CreateSequence` Brak komunikatu `ReplyTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c50c3-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="c50c3-169">B1602:WCF generuje błędów nie obsługuje akcji w odpowiedzi na wiadomość, których brakuje `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawaną w specyfikacji WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="c50c3-170">B1603:WCF generuje błąd punktu końcowego niedostępna, aby wskazać, że punkt końcowy nie przetwarza sekwencji na podstawie badania `CreateSequence` nagłówków adresowych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="c50c3-171">Kompozycja protokołu</span><span class="sxs-lookup"><span data-stu-id="c50c3-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="c50c3-172">Kompozycja za pomocą usługi WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="c50c3-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="c50c3-173">Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing zalecenia 1.0 [WS-ADDR-CORE] i [WS-ADDR — SOAP].</span><span class="sxs-lookup"><span data-stu-id="c50c3-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="c50c3-174">Podczas gdy wzmianki specyfikacji WS-Reliable Messaging tylko WS-Addressing 2004/08, nie powoduje to ograniczenia wersji WS-Addressing ma być używany.</span><span class="sxs-lookup"><span data-stu-id="c50c3-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="c50c3-175">Oto lista ograniczeń, które dotyczą usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="c50c3-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="c50c3-176">R2101: obu WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="c50c3-177">R2102:A jedną wersją protokołu WS-Addressing należy użyć w danej sekwencji WS-Reliable Messaging lub parę sekwencji prawdą skorelowane przy użyciu `wsrm:Offer` mechanizm.</span><span class="sxs-lookup"><span data-stu-id="c50c3-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="c50c3-178">Kompozycja przy użyciu protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="c50c3-178">Composition with SOAP</span></span>

<span data-ttu-id="c50c3-179">Usługi WCF obsługuje korzystanie z protokołu SOAP 1.1 i SOAP 1.2 za pomocą usługi WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="c50c3-180">Kompozycja za pomocą usługi WS-Security i usługi WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="c50c3-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="c50c3-181">Usługi WCF zapewnia ochronę sekwencji WS-Reliable Messaging przy użyciu zabezpieczenia WS konwersacji bezpiecznego transportowych (HTTPS), skład za pomocą usługi WS-Security i kompozycji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="c50c3-182">Oto lista ograniczeń, które dotyczą usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="c50c3-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="c50c3-183">R2301: ochrona integralności sekwencji WS-Reliable Messaging oprócz integralności i poufności poszczególnych wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="c50c3-184">R2302:AWS — zabezpieczanie konwersacji sesji należy ustanowić przed ustanawiania sequence(s) WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="c50c3-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="c50c3-185">R2303: Jeśli okres istnienia sekwencji WS-Reliable Messaging przekracza zabezpieczenia WS konwersacji okres istnienia sesji `SecurityContextToken` nawiązane za pomocą, musi być odnawiany zabezpieczenia WS konwersacji za pomocą odpowiedniego powiązania zabezpieczenia WS konwersacji odnowienia.</span><span class="sxs-lookup"><span data-stu-id="c50c3-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="c50c3-186">B2304:ws-sekwencji niezawodna obsługa komunikatów lub parę sekwencji skorelowany prawdą są zawsze powiązane z jednej sesji protokołu WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="c50c3-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="c50c3-187">Źródło WCF generuje `wsse:SecurityTokenReference` element w sekcji rozszerzalności element `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="c50c3-188">R2305:when składającą się z zabezpieczenia WS konwersacji, `CreateSequence` wiadomości musi zawierać `wsse:SecurityTokenReference` elementu.</span><span class="sxs-lookup"><span data-stu-id="c50c3-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="c50c3-189">WS-Reliable komunikatów potwierdzenia WS-Policy</span><span class="sxs-lookup"><span data-stu-id="c50c3-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="c50c3-190">Usługi WCF używa WS-Reliable Messaging potwierdzenie WS-Policy `wsrm:RMAssertion` do opisania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="c50c3-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="c50c3-191">Oto lista ograniczeń, które dotyczą usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="c50c3-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="c50c3-192">B3001: Dołącza WCF `wsrm:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="c50c3-193">Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="c50c3-194">B3002: Program WCF obsługuje następujące opcjonalne właściwości WS-Reliable Messaging potwierdzenia i zapewnia kontrolę nad nimi na WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="c50c3-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="c50c3-195">Oto przykład.</span><span class="sxs-lookup"><span data-stu-id="c50c3-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="c50c3-196">Rozszerzenie WS-Reliable Messaging sterowania przepływem</span><span class="sxs-lookup"><span data-stu-id="c50c3-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="c50c3-197">Usługi WCF używa WS-Reliable Messaging rozszerzalności, aby zapewnić opcjonalne dodatkowe ściślejszą kontrolę przepływ komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="c50c3-198">Sterowanie przepływem jest włączona, ustawiając <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="c50c3-199">Oto lista ograniczeń, które dotyczą usługi WCF:</span><span class="sxs-lookup"><span data-stu-id="c50c3-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="c50c3-200">B4001: Po włączeniu Reliable Messaging sterowanie przepływem programu WCF generuje `netrm:BufferRemaining` elementu w elemencie rozszerzalności `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="c50c3-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="c50c3-201">B4002: Po włączeniu Reliable Messaging sterowanie przepływem programu WCF nie wymaga `netrm:BufferRemaining` element ma być obecne w `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c50c3-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="c50c3-202">B4003: Korzysta z usługi WCF `netrm:BufferRemaining` wskazuje, ile nowe komunikaty niezawodnej obsługi komunikatów docelowy może buforować.</span><span class="sxs-lookup"><span data-stu-id="c50c3-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="c50c3-203">B4004: niezawodnej obsługi komunikatów usługi WCF ogranicza liczbę wiadomości przesyłanych podczas aplikacji docelowej niezawodną obsługę komunikatów nie może odbierać wiadomości szybko.</span><span class="sxs-lookup"><span data-stu-id="c50c3-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="c50c3-204">Komunikaty niezawodnej obsługi komunikatów buforów docelowego i wartości elementu spada na 0.</span><span class="sxs-lookup"><span data-stu-id="c50c3-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="c50c3-205">B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 (włącznie), a następnie odczytuje wartości liczby całkowitej z zakresu od 0 i `xs:int`firmy `maxInclusive` wartość 214748364 (włącznie).</span><span class="sxs-lookup"><span data-stu-id="c50c3-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="c50c3-206">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="c50c3-206">Message Exchange Patterns</span></span>

<span data-ttu-id="c50c3-207">W tej sekcji opisano zachowanie firmy WCF stosowania WS-Reliable Messaging dla różnych wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="c50c3-208">Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są uważane za:</span><span class="sxs-lookup"><span data-stu-id="c50c3-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="c50c3-209">Nie mogą być adresowane inicjatora: Inicjator jest za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="c50c3-210">Adresy inicjatorów: Inicjatora i Responder można wysłać żądania HTTP; innymi słowy może zostać nawiązana dwóch połączeń HTTP prawdą.</span><span class="sxs-lookup"><span data-stu-id="c50c3-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="c50c3-211">Jednokierunkowa, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="c50c3-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="c50c3-212">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c50c3-212">Binding</span></span>

<span data-ttu-id="c50c3-213">Usługi WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji przez jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="c50c3-214">Usługi WCF używa żądania HTTP do przesłania wszystkie komunikaty z usługi RMS RMD i odpowiedzi HTTP do przesłania wszystkie komunikaty z RMD na serwer RMS.</span><span class="sxs-lookup"><span data-stu-id="c50c3-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="c50c3-215">CreateSequence — Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-215">CreateSequence Exchange</span></span>

<span data-ttu-id="c50c3-216">Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="c50c3-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="c50c3-217">Obiekt odpowiadający w trybie WCF zapewnia `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="c50c3-218">Obiekt odpowiadający w trybie WCF zdecyduje się odpowiedzieć `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="c50c3-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="c50c3-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="c50c3-220">Inicjator WCF przetwarza potwierdzeń na odpowiedź wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="c50c3-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="c50c3-221">Obiekt odpowiadający w trybie WCF zawsze generuje autonomicznej potwierdzenia w odpowiedzi na oba sekwencji i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="c50c3-222">Komunikat TerminateteSequence</span><span class="sxs-lookup"><span data-stu-id="c50c3-222">TerminateSequence message</span></span>

<span data-ttu-id="c50c3-223">Traktuje WCF `TerminateSequence` jako Operacja jednokierunkowa, co oznacza odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="c50c3-224">Jednym ze sposobów, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="c50c3-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="c50c3-225">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c50c3-225">Binding</span></span>

<span data-ttu-id="c50c3-226">Usługi WCF zapewnia wymiany komunikatów jednokierunkową przy użyciu jednej sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanał Http.</span><span class="sxs-lookup"><span data-stu-id="c50c3-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="c50c3-227">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c50c3-228">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="c50c3-229">CreateSequence — Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-229">CreateSequence Exchange</span></span>

<span data-ttu-id="c50c3-230">Generuje inicjatora WCF `CreateSequence` wiadomości z żadne oferty.</span><span class="sxs-lookup"><span data-stu-id="c50c3-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="c50c3-231">Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma żadne oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="c50c3-232">Obiekt odpowiadający w trybie WCF przesyła `CreateSequenceResponse` komunikat na żądania HTTP kierowane za pomocą `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="c50c3-233">Duplex, Addressable Initiator</span><span class="sxs-lookup"><span data-stu-id="c50c3-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="c50c3-234">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c50c3-234">Binding</span></span>

<span data-ttu-id="c50c3-235">Usługi WCF zapewnia wymiany komunikatów pełni asynchronicznych dwukierunkowe przy użyciu dwóch sekwencji dla ruchu przychodzącego i wychodzącego kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="c50c3-236">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c50c3-237">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="c50c3-238">CreateSequence — Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-238">CreateSequence Exchange</span></span>

<span data-ttu-id="c50c3-239">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="c50c3-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="c50c3-240">Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="c50c3-241">Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`firmy `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="c50c3-242">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="c50c3-242">Sequence Lifetime</span></span>

<span data-ttu-id="c50c3-243">Usługi WCF traktuje dwie sekwencje jako jedna sesja w pełni dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="c50c3-244">Podczas generowania błędów, które błędów jednej sekwencji, WCF oczekuje, że zdalny punkt końcowy do błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="c50c3-245">Podczas czytania błędów, które błędów jednej sekwencji, WCF błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="c50c3-246">WCF można zamknąć jego ruchu wychodzącego sekwencji i dalsze przetwarzanie komunikatów w jego przychodzących sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="c50c3-247">Z drugiej strony WCF jest przetwarzanie Zamknij sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości w jego ruchu wychodzącego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="c50c3-248">Żądanie odpowiedź, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="c50c3-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="c50c3-249">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c50c3-249">Binding</span></span>

<span data-ttu-id="c50c3-250">Usługi WCF zapewnia jednokierunkowe i wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji jednego kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="c50c3-251">Usługi WCF używa żądań HTTP przesyłają komunikaty z sekwencji żądań i przesyłają komunikaty z sekwencji odpowiedzi przy użyciu odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="c50c3-252">CreateSequence — Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-252">CreateSequence Exchange</span></span>

<span data-ttu-id="c50c3-253">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="c50c3-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="c50c3-254">Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="c50c3-255">Obiekt odpowiadający w trybie WCF zdecyduje się odpowiedzieć `CreateSequence` żądania z `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="c50c3-256">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="c50c3-256">One-way Message</span></span>

<span data-ttu-id="c50c3-257">Pomyślnie protokół wymiany komunikat jednokierunkowy, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="c50c3-258">`SequenceAcknowledgement` Należy potwierdzić wiadomości przesyłane.</span><span class="sxs-lookup"><span data-stu-id="c50c3-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="c50c3-259">Obiekt odpowiadający w trybie WCF można odpowiedzieć na żądanie z potwierdzeniem, błędów lub odpowiedzi z pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="c50c3-260">Dwa komunikaty sposób</span><span class="sxs-lookup"><span data-stu-id="c50c3-260">Two Way Messages</span></span>

<span data-ttu-id="c50c3-261">Pomyślnie protokołem dwukierunkowej wiadomości programu exchange, inicjator WCF przesyła komunikat z żądaniem kolejności na żądania HTTP i odbiera komunikat sekwencji odpowiedzi na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="c50c3-262">Odpowiedzi muszą posiadać `SequenceAcknowledgement` potwierdzając komunikat sekwencji żądanie przesyłane.</span><span class="sxs-lookup"><span data-stu-id="c50c3-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="c50c3-263">Obiekt odpowiadający w trybie WCF można odpowiedzieć na żądanie przy użyciu odpowiedzi aplikacji, błąd lub odpowiedzi z pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="c50c3-264">Ze względu na obecność jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu żądania sekwencji numer sekwencyjny komunikatu odpowiedzi się brak korelacji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="c50c3-265">Trwa ponawianie próby odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="c50c3-265">Retrying Replies</span></span>

<span data-ttu-id="c50c3-266">Usługi WCF opiera się na korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="c50c3-267">W związku z tym inicjatora WCF nie zatrzymuje ponawianie próby komunikat z żądaniem sekwencji, gdy komunikat sekwencji żądania zostało potwierdzone, lecz raczej w przypadku, gdy odpowiedź HTTP niesie ze sobą, potwierdzenia dla użytkownika komunikat o i błędów.</span><span class="sxs-lookup"><span data-stu-id="c50c3-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="c50c3-268">Obiekt odpowiadający w trybie WCF ponawia próbę odpowiedzi na gałęzi żądania HTTP, żądania, do którego jest korelowany z odpowiedzią.</span><span class="sxs-lookup"><span data-stu-id="c50c3-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="c50c3-269">LastMessage programu Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-269">LastMessage Exchange</span></span>

<span data-ttu-id="c50c3-270">Inicjator WCF generuje i przesyła pustego komunikatu ostatniej zabudowanego na gałęzi żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="c50c3-271">Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat rzeczywiste odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c50c3-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="c50c3-272">Obiekt odpowiadający w trybie usługi WCF odpowiada na sekwencji żądanie zabudowanych pusta ostatni komunikat przy użyciu sekwencji odpowiedzi zabudowanych pusta ostatniego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c50c3-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="c50c3-273">Jeśli obiekt odpowiadający w trybie WCF otrzyma ostatniej wiadomości, w którym identyfikator URI akcji nie jest `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF odpowiedzi z ostatnią wiadomość.</span><span class="sxs-lookup"><span data-stu-id="c50c3-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="c50c3-274">W przypadku protokół wymiany komunikatów dwukierunkowe komunikatu ostatniej niesie komunikat aplikacji; w przypadku protokół wymiany komunikat jednokierunkowy ostatni komunikat jest pusty.</span><span class="sxs-lookup"><span data-stu-id="c50c3-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="c50c3-275">Obiekt odpowiadający w trybie usługi WCF nie wymaga potwierdzenia komunikatu ostatniej zabudowanych pusta sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c50c3-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="c50c3-276">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="c50c3-277">Gdy wszystkie żądania otrzymane prawidłowy odpowiedzi, inicjator WCF generuje i przesyła sekwencji żądanie `TerminateSequence` komunikat na gałęzi żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="c50c3-278">Usługi WCF wymaga odpowiedzi, ale ignoruje komunikat rzeczywiste odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c50c3-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="c50c3-279">Obiekt odpowiadający w trybie WCF odpowiada sekwencji żądanie `TerminateSequence` wiadomości z sekwencji odpowiedzi `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="c50c3-280">W normalnych zamykania zarówno `TerminateSequence` komunikaty zawierają pełny zakres `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="c50c3-281">Żądanie/nietypizowana odpowiedź, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="c50c3-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="c50c3-282">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="c50c3-282">Binding</span></span>

<span data-ttu-id="c50c3-283">Usługi WCF zapewnia wymiany komunikatów typu żądanie odpowiedź przy użyciu dwóch sekwencji za pośrednictwem ruchu przychodzącego i wychodzącego kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="c50c3-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="c50c3-284">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c50c3-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="c50c3-285">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="c50c3-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="c50c3-286">CreateSequence — Exchange</span><span class="sxs-lookup"><span data-stu-id="c50c3-286">CreateSequence Exchange</span></span>

<span data-ttu-id="c50c3-287">Generuje inicjatora WCF `CreateSequence` wiadomości z ofertą.</span><span class="sxs-lookup"><span data-stu-id="c50c3-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="c50c3-288">Obiekt odpowiadający w trybie usługi WCF, masz pewność, że `CreateSequence` ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="c50c3-289">Wysyła WCF `CreateSequenceResponse` na żądanie HTTP skierowane do `CreateSequence`firmy `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="c50c3-290">Korelacja żądanie/nietypizowana odpowiedź</span><span class="sxs-lookup"><span data-stu-id="c50c3-290">Request/Reply Correlation</span></span>

<span data-ttu-id="c50c3-291">Inicjator WCF zapewnia wszystkie opatrzone komunikaty żądania aplikacji `MessageId` i `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="c50c3-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="c50c3-292">Stosuje inicjatora WCF `CreateSequence` wiadomości `ReplyTo` odwołania do punktu końcowego dla każdego komunikatu żądania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c50c3-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="c50c3-293">Obiekt odpowiadający w trybie WCF wymaga to żądanie przychodzące komunikaty należy sobie zdawać sprawę `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="c50c3-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="c50c3-294">Obiekt odpowiadający w trybie WCF zapewnia, że identyfikator URI odwołania do punktu końcowego w obu `CreateSequence` i wszystkie komunikaty żądania aplikacji są identyczne.</span><span class="sxs-lookup"><span data-stu-id="c50c3-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

---
title: Reliable Messaging Protocol w wersji 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143448"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="71a50-102">Reliable Messaging Protocol w wersji 1.0</span><span class="sxs-lookup"><span data-stu-id="71a50-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="71a50-103">W tym temacie omówiono szczegóły implementacji programu Windows Communication Foundation (WCF) dotyczące protokołu WS-niezawodnej obsługi komunikatów 2005 (wersja 1,0) niezbędnego do przeprowadzenia operacji międzyoperacyjnego przy użyciu transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="71a50-104">Funkcja WCF zgodna ze specyfikacją WS-niezawodnej obsługi komunikatów z ograniczeniami i wyjaśnieniami wyjaśnionymi w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="71a50-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="71a50-105">Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1,0 jest implementowany począwszy od programu WinFX.</span><span class="sxs-lookup"><span data-stu-id="71a50-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="71a50-106">Protokół WS-niezawodnej obsługi komunikatów w lutym 2005 jest implementowany w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="71a50-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="71a50-107">Dla wygody w temacie są stosowane następujące role:</span><span class="sxs-lookup"><span data-stu-id="71a50-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="71a50-108">Inicjator: klient inicjujący tworzenie niezawodnych sekwencji komunikatów usługi WS-niezawodny</span><span class="sxs-lookup"><span data-stu-id="71a50-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="71a50-109">Responder: usługa odbierająca żądania inicjatora</span><span class="sxs-lookup"><span data-stu-id="71a50-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="71a50-110">W tym dokumencie są stosowane prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="71a50-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="71a50-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="71a50-111">Prefix</span></span>|<span data-ttu-id="71a50-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="71a50-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="71a50-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="71a50-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="71a50-114">netrm</span><span class="sxs-lookup"><span data-stu-id="71a50-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="71a50-115">s</span><span class="sxs-lookup"><span data-stu-id="71a50-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="71a50-116">WSA</span><span class="sxs-lookup"><span data-stu-id="71a50-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="71a50-117">wsse</span><span class="sxs-lookup"><span data-stu-id="71a50-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="71a50-118">Obsługa komunikatów</span><span class="sxs-lookup"><span data-stu-id="71a50-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="71a50-119">Komunikaty dotyczące sekwencji</span><span class="sxs-lookup"><span data-stu-id="71a50-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="71a50-120">Funkcja WCF implementuje `CreateSequence` i `CreateSequenceResponse` wysyła komunikaty w celu ustanowienia niezawodnej sekwencji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="71a50-121">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="71a50-121">The following constraints apply:</span></span>

- <span data-ttu-id="71a50-122">B1101: inicjator WCF nie generuje opcjonalnego elementu Expires w `CreateSequence` komunikacie lub, w przypadkach, gdy `CreateSequence` komunikat zawiera `Offer` element, opcjonalny `Expires` element w `Offer` elemencie.</span><span class="sxs-lookup"><span data-stu-id="71a50-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="71a50-123">B1102: podczas uzyskiwania dostępu do `CreateSequence` komunikatu Funkcja WCF `Responder` wysyła i odbiera oba `Expires` elementy, jeśli istnieją, ale nie używa ich wartości.</span><span class="sxs-lookup"><span data-stu-id="71a50-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="71a50-124">Obsługa komunikatów w usłudze WS-niezawodny wprowadza `Offer` mechanizm do ustanowienia dwóch odwrotnych sekwencji skorelowanych, które tworzą sesję.</span><span class="sxs-lookup"><span data-stu-id="71a50-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="71a50-125">R1103: Jeśli `CreateSequence` zawiera `Offer` element, obiekt odpowiadający niezawodnej obsługi komunikatów musi akceptować sekwencję i odpowiadać, `CreateSequenceResponse` która zawiera `wsrm:Accept` element, tworząc dwie skorelowane sekwencje lub odrzucić `CreateSequence` żądanie.</span><span class="sxs-lookup"><span data-stu-id="71a50-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="71a50-126">R1104: `SequenceAcknowledgement` i komunikaty aplikacji przepływające na sekwencję odwrotną muszą być wysyłane `ReplyTo` do odwołania do punktu końcowego `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="71a50-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="71a50-127">R1105: `AcksTo` i `ReplyTo` odwołania do punktów końcowych w elemencie `CreateSequence` muszą mieć wartości adresu, które pasują do oktetu.</span><span class="sxs-lookup"><span data-stu-id="71a50-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="71a50-128">Obiekt odpowiadający WCF sprawdza, czy część `AcksTo` i EPRs identyfikatora URI `ReplyTo` są identyczne przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="71a50-129">R1106: `AcksTo` i `ReplyTo` odwołania do punktów końcowych w elemencie `CreateSequence` powinny mieć ten sam zestaw parametrów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="71a50-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="71a50-130">Funkcja WCF nie wymusił wymuszania, ale zakłada, że [parametry referencyjne] dla `AcksTo` i `ReplyTo` on `CreateSequence` są identyczne i używa [parametrów referencyjnych] z `ReplyTo` odwołania do punktu końcowego dla potwierdzeń i komunikatów sekwencji z kolejnością.</span><span class="sxs-lookup"><span data-stu-id="71a50-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="71a50-131">R1107: Kiedy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` a komunikaty aplikacji przepływające na sekwencje odwrotne muszą być wysyłane do `ReplyTo` odwołania do punktu końcowego `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="71a50-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="71a50-132">R1108: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu oferty, `[address]` Właściwość `wsrm:AcksTo` elementu podrzędnego odwołania do punktu końcowego `wsrm:Accept` elementu `CreateSequenceResponse` musi być zgodna z docelowym identyfikatorem URI `CreateSequence` .</span><span class="sxs-lookup"><span data-stu-id="71a50-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="71a50-133">R1109: Kiedy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, komunikaty wysyłane przez inicjatora i potwierdzenia do wiadomości według obiektu odpowiadającego muszą być wysyłane do tego samego odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="71a50-134">Funkcja WCF używa protokołu WS-niezawodnej obsługi komunikatów do ustanawiania niezawodnych sesji między inicjatorem a obiektem odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="71a50-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="71a50-135">Implementacja nieniezawodnej obsługi komunikatów w usłudze WCF zapewnia niezawodną sesję w przypadku wzorców jednokierunkowych, odpowiedzi na żądanie i pełnego dupleksu.</span><span class="sxs-lookup"><span data-stu-id="71a50-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="71a50-136">Mechanizm obsługi komunikatów w usłudze WS-niezawodny `Offer` w systemie `CreateSequence` / `CreateSequenceResponse` umożliwia ustanowienie dwóch skorelowanych sekwencji i zapewnia protokół sesji odpowiedni dla wszystkich punktów końcowych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="71a50-137">Ponieważ WCF zapewnia gwarancję zabezpieczeń dla takiej sesji, w tym kompleksową ochronę integralności sesji, praktyczne jest zapewnienie, że komunikaty przeznaczone dla tej samej strony docierają do tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="71a50-138">Umożliwia to również piggye potwierdzeń sekwencji w komunikatach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71a50-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="71a50-139">W związku z tym ograniczenia R1104, R1105 i R1108 dotyczą usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="71a50-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="71a50-140">Przykład `CreateSequence` komunikatu.</span><span class="sxs-lookup"><span data-stu-id="71a50-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="71a50-141">Przykład `CreateSequenceResponse` komunikatu.</span><span class="sxs-lookup"><span data-stu-id="71a50-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="71a50-142">Sequence</span><span class="sxs-lookup"><span data-stu-id="71a50-142">Sequence</span></span>

<span data-ttu-id="71a50-143">Poniżej znajduje się lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="71a50-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="71a50-144">B1201: Funkcja WCF generuje numery sekwencji i uzyskuje do nich dostęp, nie wyższą niż `xs:long` Maksymalna wartość łącznie, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="71a50-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="71a50-145">B1202: Funkcja WCF zawsze generuje pustą ostatnią wiadomość z identyfikatorem URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="71a50-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="71a50-146">B1203: Funkcja WCF odbiera i dostarcza komunikat z nagłówkiem sekwencji, który zawiera element, o ile `LastMessage` nie jest to identyfikator URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="71a50-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="71a50-147">Przykład nagłówka sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="71a50-148">AckRequested — nagłówek</span><span class="sxs-lookup"><span data-stu-id="71a50-148">AckRequested Header</span></span>

<span data-ttu-id="71a50-149">WCF używa `AckRequested` nagłówka jako mechanizmu Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="71a50-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="71a50-150">Funkcja WCF nie generuje opcjonalnego `MessageNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="71a50-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="71a50-151">Po odebraniu komunikatu z `AckRequested` nagłówkiem zawierającym `MessageNumber` element WCF ignoruje `MessageNumber` wartość elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71a50-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="71a50-152">SequenceAcknowledgement — nagłówek</span><span class="sxs-lookup"><span data-stu-id="71a50-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="71a50-153">Funkcja WCF używa mechanizmu piggy-back dla potwierdzeń sekwencji zapewnianych w ramach komunikatów usługi WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="71a50-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="71a50-154">R1401: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu `Offer` mechanizmu, `SequenceAcknowledgement` nagłówek może być zawarty w komunikacie aplikacji przesyłanym do zamierzonego odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="71a50-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="71a50-155">B1402: Gdy WCF musi wygenerować potwierdzenie przed odebraniem jakichkolwiek komunikatów sekwencji (na przykład w celu zaspokojenia `AckRequested` wiadomości), WCF generuje nagłówek zawierający `SequenceAcknowledgement` zakres 0-0, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71a50-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="71a50-156">B1403: Funkcja WCF nie generuje `SequenceAcknowledgement` nagłówków zawierających element, `Nack` ale obsługuje `Nack` elementy.</span><span class="sxs-lookup"><span data-stu-id="71a50-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="71a50-157">Błędy WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="71a50-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="71a50-158">Poniżej znajduje się lista ograniczeń, które dotyczą implementacji WCF niezawodnych komunikatów usługi WS-niezawodny:</span><span class="sxs-lookup"><span data-stu-id="71a50-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="71a50-159">B1501: Funkcja WCF nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="71a50-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="71a50-160">B1502: punkt końcowy WCF może generować `CreateSequenceRefused` Błędy zgodnie z opisem w specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="71a50-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="71a50-161">B1503: gdy punkt końcowy usługi osiągnie limit połączeń i nie może przetwarzać nowych połączeń, usługa WCF generuje dodatkowy `CreateSequenceRefused` podkod błędu, `netrm:ConnectionLimitReached` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71a50-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="71a50-162">Usługi WS-Addressing faults</span><span class="sxs-lookup"><span data-stu-id="71a50-162">WS-Addressing Faults</span></span>

<span data-ttu-id="71a50-163">Ponieważ obsługa komunikatów w usłudze WS-niezawodny używa protokołu WS-Addressing, implementacja obsługi komunikatów w usłudze WCF WS-niezawodny może generować błędy WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="71a50-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="71a50-164">W tej sekcji omówiono błędy usługi WS-Addressing jawnie generowane przez usługę WCF w warstwie komunikatów niezawodnych:</span><span class="sxs-lookup"><span data-stu-id="71a50-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="71a50-165">B1601: Funkcja WCF generuje nagłówek adresowania komunikatu o błędzie wymagany, gdy jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="71a50-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="71a50-166">Brak `Sequence` nagłówka i nagłówka w wiadomości `Action` .</span><span class="sxs-lookup"><span data-stu-id="71a50-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="71a50-167">`CreateSequence`Brak nagłówka w wiadomości `MessageId` .</span><span class="sxs-lookup"><span data-stu-id="71a50-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="71a50-168">`CreateSequence`Brak nagłówka w wiadomości `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="71a50-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="71a50-169">B1602: Funkcja WCF generuje nieobsługiwaną akcję błędu w odpowiedzi na komunikat, który nie zawiera `Sequence` nagłówka i ma `Action` nagłówek, który nie jest rozpoznawany w specyfikacji obsługi komunikatów w usłudze WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="71a50-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="71a50-170">B1603: Funkcja WCF generuje punkt końcowy błędu niedostępny, aby wskazać, że punkt końcowy nie przetwarza sekwencji na podstawie badania `CreateSequence` nagłówków adresowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71a50-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="71a50-171">Kompozycja protokołu</span><span class="sxs-lookup"><span data-stu-id="71a50-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="71a50-172">Tworzenie kompozycji przy użyciu protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="71a50-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="71a50-173">WCF obsługuje dwie wersje WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1,0 rekomendacje [WS-ADDR-CORE] i [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="71a50-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="71a50-174">Chociaż Specyfikacja komunikatów niezawodnych WS zawiera tylko adresy WS-Addressing 2004/08, nie ogranicza do użycia wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="71a50-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="71a50-175">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="71a50-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="71a50-176">R2101: adresy WS-Addressing 2004/08 i WS-Addressing 1,0 mogą być używane z obsługą komunikatów przy użyciu protokołu WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="71a50-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="71a50-177">R2102: jedna wersja WS-Addressing musi być używana w ramach danej sekwencji komunikatów z obsługą protokołu WS-niezawodnego lub parę sekwencji odwrotnych skorelowanych przy użyciu `wsrm:Offer` mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="71a50-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="71a50-178">Kompozycja przy użyciu protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="71a50-178">Composition with SOAP</span></span>

<span data-ttu-id="71a50-179">Usługa WCF obsługuje używanie protokołu SOAP 1,1 i protokołu SOAP 1,2 z obsługą komunikatów przy użyciu protokołu WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="71a50-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="71a50-180">Tworzenie kompozycji przy użyciu protokołu WS-Security i WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="71a50-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="71a50-181">Funkcja WCF zapewnia ochronę dla niezawodnych sekwencji komunikatów przy użyciu protokołu Secure transport (HTTPS), składa się z protokołu WS-Security i kompozycji przy użyciu funkcji WS-Secure konwersacja.</span><span class="sxs-lookup"><span data-stu-id="71a50-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="71a50-182">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="71a50-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="71a50-183">R2301: aby chronić integralność sekwencji komunikatów z obsługą protokołu WS-niezawodnego oraz integralność i poufność poszczególnych komunikatów, WCF wymaga użycia protokołu WS-Secure konwersacja.</span><span class="sxs-lookup"><span data-stu-id="71a50-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="71a50-184">R2302: AWS — należy ustanowić sesję bezpiecznej konwersacji przed ustanowieniem niezawodnych sekwencji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="71a50-185">R2303: Jeśli okres istnienia sekwencji wiadomości w usłudze WS-niezawodny przekroczy okres istnienia sesji komunikacji za pośrednictwem protokołu WS-Secure, `SecurityContextToken` ustanowiony przy użyciu protokołu WS-Secure konwersacja należy odnowić przy użyciu odpowiedniego powiązania odnowienia konwersacji WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="71a50-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="71a50-186">B2304: sekwencja obsługi komunikatów w usłudze WS-niezawodny lub para powiązanych sekwencji są zawsze powiązane z jedną sesją usługi WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="71a50-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="71a50-187">Źródło WCF generuje `wsse:SecurityTokenReference` element w sekcji rozszerzalności elementu `CreateSequence` komunikatu.</span><span class="sxs-lookup"><span data-stu-id="71a50-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="71a50-188">R2305: gdy jest tworzony z konwersacją WS-Secure, `CreateSequence` komunikat musi zawierać `wsse:SecurityTokenReference` element.</span><span class="sxs-lookup"><span data-stu-id="71a50-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="71a50-189">Potwierdzenie protokołu WS-niezawodnej obsługi komunikatów WS-Policy</span><span class="sxs-lookup"><span data-stu-id="71a50-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="71a50-190">Funkcja WCF używa protokołu WS-niezawodnej obsługi komunikatów usługi WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="71a50-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="71a50-191">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="71a50-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="71a50-192">B3001: Funkcja WCF dołącza `wsrm:RMAssertion` do elementów potwierdzenie WS-Policy `wsdl:binding` .</span><span class="sxs-lookup"><span data-stu-id="71a50-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="71a50-193">Program WCF obsługuje oba załączniki `wsdl:binding` do `wsdl:port` elementów i.</span><span class="sxs-lookup"><span data-stu-id="71a50-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="71a50-194">B3002: usługa WCF obsługuje następujące opcjonalne właściwości potwierdzania niezawodnych komunikatów i zapewnia kontrolę nad nimi w programie WCF `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="71a50-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="71a50-195">Poniżej przedstawiono przykład.</span><span class="sxs-lookup"><span data-stu-id="71a50-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="71a50-196">Sterowanie przepływem — rozszerzenie WS-niezawodnej obsługi komunikatów</span><span class="sxs-lookup"><span data-stu-id="71a50-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="71a50-197">Funkcja WCF używa rozszerzalności komunikatów niezawodnych w celu zapewnienia opcjonalnej dodatkowej, ściślejszej kontroli przepływu komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="71a50-198">Sterowanie przepływem jest włączane przez ustawienie <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> właściwości na `true` .</span><span class="sxs-lookup"><span data-stu-id="71a50-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="71a50-199">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="71a50-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="71a50-200">B4001: gdy jest włączona funkcja niezawodne sterowanie przepływem komunikatów, usługa WCF generuje `netrm:BufferRemaining` element w rozszerzeniu elementu w `SequenceAcknowledgement` nagłówku.</span><span class="sxs-lookup"><span data-stu-id="71a50-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="71a50-201">B4002: gdy jest włączona funkcja niezawodnej kontroli przepływu komunikatów, usługa WCF nie wymaga, `netrm:BufferRemaining` aby element był obecny w `SequenceAcknowledgement` nagłówku, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="71a50-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="71a50-202">B4003: Funkcja WCF służy `netrm:BufferRemaining` do wskazywania, ile nowych komunikatów może buforować niezawodne miejsce docelowe komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="71a50-203">B4004: usługa niezawodnej obsługi komunikatów programu WCF ogranicza liczbę komunikatów przesyłanych, gdy aplikacja docelowa niezawodnej obsługi komunikatów nie może szybko odbierać wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71a50-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="71a50-204">Komunikaty o niezawodnych buforach docelowych komunikatów i wartości elementu spadnie do 0.</span><span class="sxs-lookup"><span data-stu-id="71a50-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="71a50-205">B4005: Funkcja WCF generuje `netrm:BufferRemaining` wartości całkowite z zakresu od 0 do 4096 włącznie i odczytuje wartości całkowite z przedziału od 0 do `xs:int` `maxInclusive` 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="71a50-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="71a50-206">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="71a50-206">Message Exchange Patterns</span></span>

<span data-ttu-id="71a50-207">W tej sekcji opisano zachowanie programu WCF, gdy obsługa komunikatów przy użyciu protokołu WS-niezawodny jest używana w przypadku różnych wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="71a50-208">Dla każdego wzorca wymiany komunikatów są brane pod uwagę następujące dwa scenariusze wdrażania:</span><span class="sxs-lookup"><span data-stu-id="71a50-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="71a50-209">Inicjator bez adresu: inicjator znajduje się za zaporą; Obiekt odpowiadający może dostarczać komunikaty do inicjatora tylko na odpowiedziach HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="71a50-210">Inicjator obsługujący adresy: zarówno inicjator, jak i obiekt odpowiadający mogą wysyłać żądania HTTP; Innymi słowy, można nawiązać dwa odwrotne połączenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="71a50-211">Jednokierunkowy inicjator bez adresu</span><span class="sxs-lookup"><span data-stu-id="71a50-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="71a50-212">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="71a50-212">Binding</span></span>

<span data-ttu-id="71a50-213">Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji na jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="71a50-214">Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z usługi RMS do RMD i odpowiedzi HTTP w celu przesyłania wszystkich komunikatów z RMD do usługi RMS.</span><span class="sxs-lookup"><span data-stu-id="71a50-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="71a50-215">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="71a50-215">CreateSequence Exchange</span></span>

<span data-ttu-id="71a50-216">Inicjator WCF generuje `CreateSequence` komunikat bez oferty.</span><span class="sxs-lookup"><span data-stu-id="71a50-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="71a50-217">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` nie ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="71a50-218">Obiekt odpowiadający WCF odpowiada na `CreateSequence` żądanie z `CreateSequenceResponse` komunikatem.</span><span class="sxs-lookup"><span data-stu-id="71a50-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="71a50-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="71a50-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="71a50-220">Inicjator WCF przetwarza potwierdzenia odpowiedzi wszystkich komunikatów poza `CreateSequence` komunikatami i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="71a50-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="71a50-221">Obiekt odpowiadający WCF zawsze generuje autonomiczną potwierdzenie w odpowiedzi na sekwencję i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="71a50-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="71a50-222">Komunikat TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="71a50-222">TerminateSequence message</span></span>

<span data-ttu-id="71a50-223">WCF traktuje `TerminateSequence` się jako operację jednokierunkową, co oznacza, że odpowiedź HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="71a50-224">Jeden ze sposobów, inicjator adresowany</span><span class="sxs-lookup"><span data-stu-id="71a50-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="71a50-225">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="71a50-225">Binding</span></span>

<span data-ttu-id="71a50-226">Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji przez ruch przychodzący i wychodzący.</span><span class="sxs-lookup"><span data-stu-id="71a50-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="71a50-227">Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="71a50-228">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="71a50-229">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="71a50-229">CreateSequence Exchange</span></span>

<span data-ttu-id="71a50-230">Inicjator WCF generuje `CreateSequence` komunikat bez oferty.</span><span class="sxs-lookup"><span data-stu-id="71a50-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="71a50-231">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` nie ma oferty przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="71a50-232">Obiekt odpowiadający WCF przesyła `CreateSequenceResponse` komunikat w ŻĄDANIU http, który jest kierowany do `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="71a50-233">Dupleks, inicjator z adresami</span><span class="sxs-lookup"><span data-stu-id="71a50-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="71a50-234">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="71a50-234">Binding</span></span>

<span data-ttu-id="71a50-235">Usługa WCF udostępnia w pełni asynchroniczny wzorzec wymiany komunikatów dwukierunkowych przy użyciu dwóch sekwencji za pośrednictwem przychodzącego i wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="71a50-236">Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="71a50-237">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="71a50-238">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="71a50-238">CreateSequence Exchange</span></span>

<span data-ttu-id="71a50-239">Inicjator WCF generuje `CreateSequence` komunikat z ofertą.</span><span class="sxs-lookup"><span data-stu-id="71a50-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="71a50-240">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="71a50-241">Usługa WCF wysyła `CreateSequenceResponse` żądanie HTTP do `CreateSequence` `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="71a50-242">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="71a50-242">Sequence Lifetime</span></span>

<span data-ttu-id="71a50-243">Usługa WCF traktuje dwie sekwencje jako jedną sesję w pełni dupleks.</span><span class="sxs-lookup"><span data-stu-id="71a50-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="71a50-244">Po wygenerowaniu błędu, który powoduje błąd jednej sekwencji, usługa WCF oczekuje, że zdalny punkt końcowy wystąpi błąd obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="71a50-245">Po odczytaniu błędu powodującego błąd jednej sekwencji błędy programu WCF są obie sekwencją.</span><span class="sxs-lookup"><span data-stu-id="71a50-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="71a50-246">Funkcja WCF może zamknąć swoją sekwencję wychodzącą i kontynuować przetwarzanie komunikatów w sekwencji przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="71a50-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="71a50-247">Z kolei WCF może przetworzyć zamknięcie sekwencji przychodzącej i kontynuować wysyłanie komunikatów do sekwencji wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="71a50-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="71a50-248">Inicjator żądania-odpowiedź, niebędący w adresie</span><span class="sxs-lookup"><span data-stu-id="71a50-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="71a50-249">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="71a50-249">Binding</span></span>

<span data-ttu-id="71a50-250">Usługa WCF udostępnia wzorzec wymiany komunikatów jednokierunkowych i z żądaniami odpowiedzi przy użyciu dwóch sekwencji w ramach jednego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="71a50-251">Funkcja WCF używa żądań HTTP do przesyłania komunikatów sekwencji żądań i używa odpowiedzi HTTP do przesyłania komunikatów sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="71a50-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="71a50-252">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="71a50-252">CreateSequence Exchange</span></span>

<span data-ttu-id="71a50-253">Inicjator WCF generuje `CreateSequence` komunikat z ofertą.</span><span class="sxs-lookup"><span data-stu-id="71a50-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="71a50-254">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="71a50-255">Obiekt odpowiadający WCF odpowiada na `CreateSequence` żądanie z `CreateSequenceResponse` komunikatem.</span><span class="sxs-lookup"><span data-stu-id="71a50-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="71a50-256">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="71a50-256">One-way Message</span></span>

<span data-ttu-id="71a50-257">Aby pomyślnie ukończyć jednokierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera w `SequenceAcknowledgement` odpowiedzi HTTP komunikat autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="71a50-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="71a50-258">`SequenceAcknowledgement`Musi potwierdzić komunikat przesłany.</span><span class="sxs-lookup"><span data-stu-id="71a50-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="71a50-259">Obiekt odpowiadający WCF może odpowiedzieć na żądanie z potwierdzeniem, błędem lub odpowiedzią z pustym identyfikatorem treści i kodem stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="71a50-260">Komunikaty dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="71a50-260">Two Way Messages</span></span>

<span data-ttu-id="71a50-261">Aby pomyślnie wykonać dwukierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera komunikat sekwencji odpowiedzi w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="71a50-262">Odpowiedź musi zawierać `SequenceAcknowledgement` potwierdzenie przesłania komunikatu sekwencji żądania.</span><span class="sxs-lookup"><span data-stu-id="71a50-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="71a50-263">Obiekt odpowiadający WCF może odpowiedzieć na żądanie za pomocą odpowiedzi aplikacji, błędu lub odpowiedzi z pustym identyfikatorem treści i kodem stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="71a50-264">Ze względu na obecność komunikatów jednokierunkowych i chronometrażu odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądań i numer sekwencyjny komunikatu odpowiedzi nie mają korelacji.</span><span class="sxs-lookup"><span data-stu-id="71a50-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="71a50-265">Ponawianie odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="71a50-265">Retrying Replies</span></span>

<span data-ttu-id="71a50-266">Funkcja WCF korzysta z korelacji żądanie HTTP-odpowiedź dla dwukierunkowej korelacji protokołu wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="71a50-267">W związku z tym inicjator WCF nie przerywa ponawiania próby wysłania komunikatu sekwencji żądania, gdy komunikat sekwencji żądań zostanie potwierdzony, ale gdy odpowiedź HTTP przeprowadzi potwierdzenie, komunikat użytkownika lub błąd.</span><span class="sxs-lookup"><span data-stu-id="71a50-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="71a50-268">Obiekt odpowiadający w programie WCF ponawia odpowiedzi na etapie żądania HTTP żądania, do którego jest skorelowana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="71a50-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="71a50-269">LastMessage Exchange</span><span class="sxs-lookup"><span data-stu-id="71a50-269">LastMessage Exchange</span></span>

<span data-ttu-id="71a50-270">Inicjator WCF generuje i przesyła pustą ostatnią wiadomość z zabudowanego komunikatu w postawce żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="71a50-271">Funkcja WCF wymaga odpowiedzi, ale ignoruje rzeczywisty komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="71a50-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="71a50-272">Obiekt odpowiadający programu WCF odpowiada ostatniemu komunikatowi o pustej zaposiadaniu żądania sekwencji odpowiedzi z pustą wiadomością.</span><span class="sxs-lookup"><span data-stu-id="71a50-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="71a50-273">Jeśli obiekt odpowiadający programu WCF odbiera ostatni komunikat, w którym nie jest identyfikator URI akcji `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , program WCF będzie odpowiedzi z ostatnim komunikatem.</span><span class="sxs-lookup"><span data-stu-id="71a50-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="71a50-274">W przypadku protokołu wymiany komunikatów dwukierunkowych ostatni komunikat przenosi komunikat aplikacji. w przypadku protokołu wymiany komunikatów jednokierunkowych ostatni komunikat jest pusty.</span><span class="sxs-lookup"><span data-stu-id="71a50-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="71a50-275">Obiekt odbiorczy programu WCF nie wymaga potwierdzenia dla ostatniego zabudowanego komunikatu sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="71a50-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="71a50-276">Wymiana TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="71a50-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="71a50-277">Po odebraniu przez wszystkie żądania prawidłowej odpowiedzi inicjator WCF generuje i przesyła komunikat sekwencji żądania `TerminateSequence` w postawce żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="71a50-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="71a50-278">Funkcja WCF wymaga odpowiedzi, ale ignoruje rzeczywisty komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="71a50-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="71a50-279">Obiekt odpowiadający programu WCF odpowiada na komunikat sekwencji żądań `TerminateSequence` z komunikatem o sekwencji odpowiedzi `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="71a50-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="71a50-280">W normalnej sekwencji zamykania oba komunikaty mają `TerminateSequence` pełen zakres `SequenceAcknowledgement` .</span><span class="sxs-lookup"><span data-stu-id="71a50-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="71a50-281">Żądanie/odpowiedź, inicjator z adresami</span><span class="sxs-lookup"><span data-stu-id="71a50-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="71a50-282">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="71a50-282">Binding</span></span>

<span data-ttu-id="71a50-283">Funkcja WCF udostępnia wzorzec wymiany komunikatów typu żądanie-odpowiedź przy użyciu dwóch sekwencji w ramach ruchu przychodzącego i wychodzącego.</span><span class="sxs-lookup"><span data-stu-id="71a50-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="71a50-284">Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="71a50-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="71a50-285">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="71a50-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="71a50-286">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="71a50-286">CreateSequence Exchange</span></span>

<span data-ttu-id="71a50-287">Inicjator WCF generuje `CreateSequence` komunikat z ofertą.</span><span class="sxs-lookup"><span data-stu-id="71a50-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="71a50-288">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma ofertę przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="71a50-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="71a50-289">Usługa WCF wysyła `CreateSequenceResponse` żądanie HTTP do `CreateSequence` `ReplyTo` odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="71a50-290">Korelacja żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="71a50-290">Request/Reply Correlation</span></span>

<span data-ttu-id="71a50-291">Inicjator WCF gwarantuje, że wszystkie komunikaty żądania aplikacji są opatrzone `MessageId` i `ReplyTo` odwołaniem do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="71a50-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="71a50-292">Inicjator WCF stosuje odwołanie do `CreateSequence` `ReplyTo` punktu końcowego komunikatu dla każdego komunikatu żądania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71a50-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="71a50-293">Obiekt odpowiadający WCF wymaga, aby przychodzące komunikaty żądań miały `MessageId` a i `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="71a50-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="71a50-294">Obiekt odpowiadający WCF gwarantuje, że identyfikator URI odwołania punktu końcowego obu `CreateSequence` komunikatów żądania aplikacji jest identyczny.</span><span class="sxs-lookup"><span data-stu-id="71a50-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

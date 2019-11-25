---
title: Reliable Messaging Protocol w wersji 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283314"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="4c61b-102">Reliable Messaging Protocol w wersji 1,1</span><span class="sxs-lookup"><span data-stu-id="4c61b-102">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="4c61b-103">W tym temacie omówiono szczegóły implementacji Windows Communication Foundation (WCF) dotyczące protokołu WS-ReliableMessaging luty 2007 (wersja 1,1) niezbędnego do przeprowadzenia operacji międzyoperacyjnego przy użyciu transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="4c61b-104">Funkcja WCF jest zgodna ze specyfikacją WS-ReliableMessaging z ograniczeniami i wyjaśnieniami opisanymi w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="4c61b-105">Należy pamiętać, że protokół WS-ReliableMessaging w wersji 1,1 jest zaimplementowany począwszy od .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="4c61b-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="4c61b-106">Protokół WS-ReliableMessaging luty 2007 jest zaimplementowany w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="4c61b-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="4c61b-107">Dla wygody w temacie są stosowane następujące role:</span><span class="sxs-lookup"><span data-stu-id="4c61b-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="4c61b-108">Inicjator: klient inicjujący tworzenie niezawodnych sekwencji komunikatów przez usługę WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="4c61b-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="4c61b-109">Responder: usługa, która odbiera żądania inicjatora.</span><span class="sxs-lookup"><span data-stu-id="4c61b-109">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="4c61b-110">W tym dokumencie są stosowane prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4c61b-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="4c61b-111">prefiks</span><span class="sxs-lookup"><span data-stu-id="4c61b-111">Prefix</span></span>|<span data-ttu-id="4c61b-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4c61b-112">Namespace</span></span>|
|-|-|
|<span data-ttu-id="4c61b-113">WSRM</span><span class="sxs-lookup"><span data-stu-id="4c61b-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|<span data-ttu-id="4c61b-114">netrm</span><span class="sxs-lookup"><span data-stu-id="4c61b-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="4c61b-115">s</span><span class="sxs-lookup"><span data-stu-id="4c61b-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="4c61b-116">WSA</span><span class="sxs-lookup"><span data-stu-id="4c61b-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="4c61b-117">wsse</span><span class="sxs-lookup"><span data-stu-id="4c61b-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|<span data-ttu-id="4c61b-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="4c61b-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|<span data-ttu-id="4c61b-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="4c61b-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|<span data-ttu-id="4c61b-120">wsp</span><span class="sxs-lookup"><span data-stu-id="4c61b-120">wsp</span></span>|<span data-ttu-id="4c61b-121">(WS-Policy 1,2 lub WS-Policy 1,5)</span><span class="sxs-lookup"><span data-stu-id="4c61b-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="4c61b-122">Obsługa komunikatów</span><span class="sxs-lookup"><span data-stu-id="4c61b-122">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="4c61b-123">Tworzenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="4c61b-123">Sequence Creation</span></span>

<span data-ttu-id="4c61b-124">Funkcja WCF implementuje `CreateSequence` i `CreateSequenceResponse` komunikatów w celu ustanowienia niezawodnej sekwencji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="4c61b-125">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4c61b-125">The following constraints apply:</span></span>

- <span data-ttu-id="4c61b-126">B1101: inicjator WCF używa tego samego odwołania do punktu końcowego, co `ReplyTo``CreateSequence` komunikatu, `AcksTo` i `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="4c61b-127">R1102: odwołania do punktów końcowych `AcksTo`, `ReplyTo` i `Offer/Endpoint` w komunikacie `CreateSequence` muszą mieć wartości adresów z identycznymi reprezentacjami ciągów, tak że są one zgodne z oktetem.</span><span class="sxs-lookup"><span data-stu-id="4c61b-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="4c61b-128">Obiekt odpowiadający programu WCF sprawdza, czy część identyfikatora URI `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="4c61b-129">R1103: odwołania do punktów końcowych `AcksTo`, `ReplyTo` i `Offer/Endpoint` w komunikacie `CreateSequence` powinny mieć ten sam zestaw parametrów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="4c61b-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="4c61b-130">Funkcja WCF nie wymusi, ale zakłada, że parametry odniesienia `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktów końcowych na `CreateSequence` są identyczne i używają parametrów referencyjnych z odwołania `ReplyTo` punktów końcowych dla potwierdzeń i komunikatów sekwencji z kolejnością.</span><span class="sxs-lookup"><span data-stu-id="4c61b-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="4c61b-131">B1104: inicjator WCF nie generuje opcjonalnego elementu `Expires` lub `Offer/Expires` w komunikacie `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="4c61b-132">B1105: podczas uzyskiwania dostępu do komunikatu `CreateSequence`, obiekt odpowiadający WCF używa wartości `Expires` w elemencie `CreateSequence` jako wartość `Expires` w `CreateSequenceResponse` elemencie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="4c61b-133">W przeciwnym razie obiekt odpowiadający WCF odczytuje i ignoruje wartości `Expires` i `Offer/Expires`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="4c61b-134">B1106: podczas uzyskiwania dostępu do komunikatu `CreateSequenceResponse` inicjator WCF odczytuje opcjonalną wartość `Expires`, ale nie używa jej.</span><span class="sxs-lookup"><span data-stu-id="4c61b-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="4c61b-135">B1107: inicjator WCF i obiekt odpowiadający zawsze generują opcjonalny element `IncompleteSequenceBehavior` w elementach `CreateSequence/Offer` i `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="4c61b-136">B1108: WCF używa tylko wartości `DiscardFollowingFirstGap` i `NoDiscard` w elemencie `IncompleteSequenceBehavior`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="4c61b-137">WS-ReliableMessaging wykorzystuje mechanizm `Offer` do ustanowienia dwóch odwrotnych sekwencji skorelowanych, które tworzą sesję.</span><span class="sxs-lookup"><span data-stu-id="4c61b-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="4c61b-138">B1109: Jeśli `CreateSequence` zawiera element `Offer`, jeden ze sposobów obiekt odpowiadający WCF odrzuca oferowaną sekwencję, odpowiadając na `CreateSequenceResponse` bez elementu `Accept`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="4c61b-139">B1110: Jeśli obiekt odpowiadający niezawodnej obsługi komunikatów odrzuci proponowaną sekwencję, inicjator WCF błędnie wyznaczonej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="4c61b-140">B1111: Jeśli `CreateSequence` nie zawiera elementu `Offer`, dwukierunkowy obiekt odbiorczy WCF odrzuca oferowaną sekwencję, odpowiadając na błąd `CreateSequenceRefused`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="4c61b-141">R1112: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, właściwość `[address]` odwołania do punktu końcowego `CreateSequenceResponse/Accept/AcksTo` musi być zgodna z docelowym identyfikatorem URI `CreateSequence` bajt komunikatu dla bajtu.</span><span class="sxs-lookup"><span data-stu-id="4c61b-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="4c61b-142">R1113: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, wszystkie komunikaty przesyłane z inicjatora do obiektu odpowiadającego muszą być wysyłane do tego samego odwołania do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4c61b-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="4c61b-143">WCF używa protokołu WS-ReliableMessaging do ustanawiania niezawodnych sesji między inicjatorem a obiektem odpowiadającym.</span><span class="sxs-lookup"><span data-stu-id="4c61b-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="4c61b-144">Implementacja WS-ReliableMessaging WCF zapewnia niezawodną sesję w przypadku wzorców jednokierunkowych, odpowiedzi na żądanie i pełnego dupleksu.</span><span class="sxs-lookup"><span data-stu-id="4c61b-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="4c61b-145">Mechanizm `Offer` WS-ReliableMessaging na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanowienie dwóch skorelowanych sekwencji i udostępnia protokół sesji odpowiedni dla wszystkich punktów końcowych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="4c61b-146">Ponieważ WCF zapewnia gwarancję zabezpieczeń dla takiej sesji, w tym kompleksową ochronę integralności sesji, praktyczne jest zapewnienie, że komunikaty przeznaczone dla tej samej strony docierają do tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="4c61b-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="4c61b-147">Umożliwia to również "piggy-back" potwierdzeń sekwencji w komunikatach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="4c61b-148">W związku z tym ograniczenia R1102, R1112 i R1113 dotyczą usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4c61b-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="4c61b-149">Przykład komunikatu `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-149">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="4c61b-150">Przykład komunikatu `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-150">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a><span data-ttu-id="4c61b-151">Zamykanie sekwencji</span><span class="sxs-lookup"><span data-stu-id="4c61b-151">Closing a Sequence</span></span>

<span data-ttu-id="4c61b-152">Usługa WCF używa komunikatów `CloseSequence` i `CloseSequenceResponse` do wyłączania niezawodnego zainicjowanego źródła komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="4c61b-153">Miejsce docelowe niezawodnej obsługi komunikatów WCF nie inicjuje zamknięcia, a źródło niezawodnej obsługi komunikatów w programie WCF nie obsługuje zamykania niezawodnej obsługi komunikatów w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="4c61b-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="4c61b-154">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4c61b-154">The following constraints apply:</span></span>

- <span data-ttu-id="4c61b-155">B1201: Źródło niezawodnej obsługi komunikatów WCF zawsze wysyła komunikat `CloseSequence`, aby zamknąć sekwencję.</span><span class="sxs-lookup"><span data-stu-id="4c61b-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="4c61b-156">B1202: Źródło niezawodnej obsługi komunikatów oczekuje na potwierdzenie pełnego zakresu komunikatów sekwencji przed wysłaniem komunikatu `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="4c61b-157">B1203: Źródło niezawodnej obsługi komunikatów zawsze zawiera opcjonalny element `LastMsgNumber`, chyba że sekwencja nie zawiera komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="4c61b-158">R1204: Niezawodna lokalizacja docelowa obsługi komunikatów nie może zainicjować zamknięcia, wysyłając wiadomość `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="4c61b-159">B1205: po odebraniu komunikatu `CloseSequence`, Źródło niezawodnej obsługi komunikatów programu WCF uważa niekompletną sekwencję i wysyła błąd.</span><span class="sxs-lookup"><span data-stu-id="4c61b-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="4c61b-160">Przykład komunikatu `CloseSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-160">An example of a `CloseSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="4c61b-161">Przykładowy komunikat `CloseSequenceResponse`:</span><span class="sxs-lookup"><span data-stu-id="4c61b-161">Example `CloseSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a><span data-ttu-id="4c61b-162">Zakończenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="4c61b-162">Sequence Termination</span></span>

<span data-ttu-id="4c61b-163">Funkcja WCF używa przede wszystkim uzgodnienia `TerminateSequence/TerminateSequenceResponse` po zakończeniu uzgadniania `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-163">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="4c61b-164">Miejsce docelowe niezawodnej obsługi komunikatów w programie WCF nie inicjuje zakończenia, a źródło niezawodnej obsługi komunikatów nie obsługuje wykończenia niezawodnego działania w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="4c61b-164">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="4c61b-165">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4c61b-165">The following constraints apply:</span></span>

- <span data-ttu-id="4c61b-166">B1301: inicjator WCF wysyła komunikat `TerminateSequence` po pomyślnym zakończeniu uzgadniania `CloseSequence/CloseSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-166">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="4c61b-167">R1302: Funkcja WCF sprawdza, czy element `LastMsgNumber` jest spójny dla wszystkich `CloseSequence` i komunikatów `TerminateSequence` dla danej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-167">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="4c61b-168">Oznacza to, że `LastMsgNumber` nie są obecne we wszystkich `CloseSequence` i `TerminateSequence` wiadomościach, albo jest obecne i identyczne na wszystkich `CloseSequence` i `TerminateSequence` komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-168">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="4c61b-169">B1303: w przypadku odebrania komunikatu `TerminateSequence` po uzgadnianiu `CloseSequence/CloseSequenceResponse`, miejsce docelowe wiadomości jest odpowiedzią na komunikat `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-169">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="4c61b-170">Ze względu na to, że źródło niezawodnej obsługi komunikatów ma ostateczne potwierdzenie przed wysłaniem komunikatu `TerminateSequence`, Niezawodna docelowa obsługa komunikatów wie, że sekwencja kończy się niewątpliwie i natychmiast przejmuje zasoby.</span><span class="sxs-lookup"><span data-stu-id="4c61b-170">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="4c61b-171">B1304: podczas otrzymywania komunikatu `TerminateSequence` przed uzgodnieniem `CloseSequence/CloseSequenceResponse`, miejsce docelowe niezawodnej obsługi komunikatów WCF odpowiada za pomocą wiadomości `TerminateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-171">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="4c61b-172">Jeśli miejsce docelowe niezawodnej obsługi komunikatów określa, że nie występują żadne niespójności w sekwencji, niezawodna lokalizacja docelowa do obsługi komunikatów oczekuje na odinstalowanie zasobów przez określony czas docelowy aplikacji, aby umożliwić klientowi otrzymanie szansy ostateczne potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-172">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="4c61b-173">W przeciwnym razie Niezawodna docelowa obsługa komunikatów natychmiast przejmuje zasoby i wskazuje na miejsce docelowe aplikacji, którą sekwencja ma wątpliwości, poprzez podnoszenie poziomu zdarzenia `Faulted`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-173">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="4c61b-174">Przykład komunikatu `TerminateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-174">An example of a `TerminateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="4c61b-175">Przykładowy komunikat `TerminateSequenceResponse`:</span><span class="sxs-lookup"><span data-stu-id="4c61b-175">Example `TerminateSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a><span data-ttu-id="4c61b-176">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="4c61b-176">Sequences</span></span>

<span data-ttu-id="4c61b-177">Poniżej znajduje się lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="4c61b-177">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="4c61b-178">B1401: Funkcja WCF generuje numery sekwencji i uzyskuje do nich dostęp, nie wyższą `xs:long`niż maksymalna wartość, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="4c61b-178">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="4c61b-179">Przykład nagłówka `Sequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-179">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="4c61b-180">Potwierdzenie żądania</span><span class="sxs-lookup"><span data-stu-id="4c61b-180">Request Acknowledgement</span></span>

<span data-ttu-id="4c61b-181">Funkcja WCF używa nagłówka `AckRequested` jako mechanizmu Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="4c61b-181">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="4c61b-182">Przykład nagłówka `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-182">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="4c61b-183">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4c61b-183">SequenceAcknowledgement</span></span>

<span data-ttu-id="4c61b-184">Funkcja WCF używa mechanizmu "piggy-back" dla potwierdzeń sekwencji udostępnianych w ramach komunikatów usługi WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="4c61b-184">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="4c61b-185">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4c61b-185">The following constraints apply:</span></span>

- <span data-ttu-id="4c61b-186">R1601: gdy dwie sekwencje odwrotne są ustanawiane przy użyciu mechanizmu `Offer`, nagłówek `SequenceAcknowledgement` może być zawarty w komunikacie aplikacji przesyłanym do zamierzonego odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="4c61b-186">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="4c61b-187">Zdalny punkt końcowy musi mieć możliwość dostępu do nagłówka `SequenceAcknowledgement` piggybacked.</span><span class="sxs-lookup"><span data-stu-id="4c61b-187">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="4c61b-188">B1602: Funkcja WCF nie generuje nagłówków `SequenceAcknowledgement` zawierających elementy `Nack`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-188">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="4c61b-189">Funkcja WCF sprawdza, czy każdy element `Nack` zawiera numer sekwencyjny, ale w przeciwnym razie ignoruje `Nack` element i wartość.</span><span class="sxs-lookup"><span data-stu-id="4c61b-189">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="4c61b-190">Przykład nagłówka `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-190">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="4c61b-191">Błędy WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="4c61b-191">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="4c61b-192">Poniżej znajduje się lista ograniczeń, które dotyczą implementacji WCF błędów WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="4c61b-192">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="4c61b-193">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="4c61b-193">The following constraints apply:</span></span>

- <span data-ttu-id="4c61b-194">B1701: Funkcja WCF nie generuje błędów `MessageNumberRollover`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-194">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="4c61b-195">B1702: za pośrednictwem protokołu SOAP 1,2, gdy punkt końcowy usługi osiągnie limit połączeń i nie może przetwarzać nowych połączeń, funkcja WCF generuje zagnieżdżony kod `CreateSequenceRefused` błędów `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-195">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a><span data-ttu-id="4c61b-196">Usługi WS-Addressing faults</span><span class="sxs-lookup"><span data-stu-id="4c61b-196">WS-Addressing Faults</span></span>

<span data-ttu-id="4c61b-197">Ponieważ WS-ReliableMessaging używa WS-Addressing, implementacja WS-ReliableMessaging programu WCF może generować i przesyłać błędy dotyczące adresowania WS-Exception.</span><span class="sxs-lookup"><span data-stu-id="4c61b-197">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="4c61b-198">W tej sekcji opisano błędy WS-Addressing, które jawnie generują i przesyłają w ramach warstwy WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="4c61b-198">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="4c61b-199">B1801: Funkcja WCF generuje i przesyła błąd `Message Addressing Header Required`, gdy jest spełniony jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="4c61b-199">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="4c61b-200">`CreateSequence`, `CloseSequence` lub `TerminateSequence` wiadomości brakuje nagłówka `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-200">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="4c61b-201">`CreateSequence`, `CloseSequence` lub `TerminateSequence` wiadomości brakuje nagłówka `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="4c61b-202">W wiadomości `CreateSequenceResponse`, `CloseSequenceResponse`lub `TerminateSequenceResponse` brakuje nagłówka `RelatesTo`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-202">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="4c61b-203">B1802: Funkcja WCF generuje i przesyła błąd `Endpoint Unavailable`, aby wskazać, że nie ma punktu końcowego nasłuchu, który może przetworzyć sekwencję w oparciu o badanie nagłówków adresowych w komunikacie `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-203">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="4c61b-204">Kompozycja protokołu</span><span class="sxs-lookup"><span data-stu-id="4c61b-204">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="4c61b-205">Tworzenie kompozycji przy użyciu protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="4c61b-205">Composition with WS-Addressing</span></span>

<span data-ttu-id="4c61b-206">WCF obsługuje dwie wersje WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1,0 rekomendacje [WS-ADDR-CORE] i [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="4c61b-206">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="4c61b-207">Chociaż Specyfikacja WS-ReliableMessaging wymienia tylko adresy WS-Addressing 2004/08, nie ogranicza do użycia wersji WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4c61b-207">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="4c61b-208">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="4c61b-208">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4c61b-209">R2101: adresy WS-Addressing 2004/08 i WS-Addressing 1,0 mogą być używane z obsługą komunikatów przy użyciu protokołu WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="4c61b-209">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="4c61b-210">R2102: jedna wersja WS-Addressing musi być używana przez daną sekwencję WS-ReliableMessaging lub parę sekwencji odwrotnych skorelowanych przy użyciu mechanizmu `Offer`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-210">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="4c61b-211">Kompozycja przy użyciu protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="4c61b-211">Composition with SOAP</span></span>

<span data-ttu-id="4c61b-212">Usługa WCF obsługuje używanie protokołu SOAP 1,1 i protokołu SOAP 1,2 z obsługą komunikatów przy użyciu protokołu WS-niezawodny.</span><span class="sxs-lookup"><span data-stu-id="4c61b-212">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="4c61b-213">Tworzenie kompozycji przy użyciu protokołu WS-Security i WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="4c61b-213">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="4c61b-214">Funkcja WCF zapewnia ochronę dla sekwencji WS-ReliableMessaging przy użyciu protokołu Secure transport (HTTPS), składa się z protokołu WS-Security i kompozycji przy użyciu funkcji WS-Secure konwersacja.</span><span class="sxs-lookup"><span data-stu-id="4c61b-214">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="4c61b-215">Protokół WS-ReliableMessaging 1,1, protokół WS-Security 1,1 i WS-Secure 1,3 konwersacje w protokole SSL powinny być używane razem.</span><span class="sxs-lookup"><span data-stu-id="4c61b-215">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="4c61b-216">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="4c61b-216">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4c61b-217">R2301: aby chronić integralność sekwencji WS-ReliableMessaging, a także integralność i poufność poszczególnych komunikatów, WCF wymaga użycia protokołu WS-Secure konwersacja.</span><span class="sxs-lookup"><span data-stu-id="4c61b-217">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="4c61b-218">R2302: AWS — należy ustanowić sesję bezpiecznej konwersacji przed ustanowieniem sekwencji WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="4c61b-218">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="4c61b-219">R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekroczy okres istnienia sesji komunikacji za pomocą protokołu WS-Secure, `SecurityContextToken` ustanowiony przy użyciu usługi WS-Secure konwersacja musi zostać odnowiony przy użyciu odpowiedniego powiązania odnowienia konwersacji WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="4c61b-219">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="4c61b-220">B2304: Metoda WS-ReliableMessaging lub para skorelowanych sekwencji są zawsze powiązane z jedną sesją WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="4c61b-220">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="4c61b-221">R2305: Jeśli jest tworzony przy użyciu konwersacji WS-Secure, obiekt odbiorczy programu WCF wymaga, aby komunikat `CreateSequence` zawierał element `wsse:SecurityTokenReference` i nagłówek `wsrm:UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-221">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="4c61b-222">Przykład nagłówka `UsesSequenceSTR`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-222">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="4c61b-223">Kompozycja z sesjami SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="4c61b-223">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="4c61b-224">Funkcja WCF nie obsługuje tworzenia kompozycji z użyciem sesji SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="4c61b-224">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="4c61b-225">B2401: Funkcja WCF nie generuje nagłówka `wsrm:UsesSequenceSSL`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-225">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="4c61b-226">R2402: inicjator niezawodnej obsługi komunikatów nie może wysyłać komunikatu `CreateSequence` z nagłówkiem `wsrm:UsesSequenceSSL` do obiektu odpowiadającego programu WCF.</span><span class="sxs-lookup"><span data-stu-id="4c61b-226">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="4c61b-227">Kompozycja przy użyciu usługi WS-Policy</span><span class="sxs-lookup"><span data-stu-id="4c61b-227">Composition with WS-Policy</span></span>

<span data-ttu-id="4c61b-228">WCF obsługuje dwie wersje WS-Policy: WS-Policy 1,2 i WS-Policy 1,5.</span><span class="sxs-lookup"><span data-stu-id="4c61b-228">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="4c61b-229">Potwierdzenie WS-ReliableMessaging WS-Policy</span><span class="sxs-lookup"><span data-stu-id="4c61b-229">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="4c61b-230">W programie WCF są stosowane usługi WS-ReliableMessaging WS-Policy `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="4c61b-230">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="4c61b-231">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="4c61b-231">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4c61b-232">B3001: Funkcja WCF dołącza `wsrmn:RMAssertion` potwierdzenia WS-Policy do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-232">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="4c61b-233">Program WCF obsługuje obydwa załączniki do `wsdl:binding` i `wsdl:port` elementów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-233">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="4c61b-234">B3002: WCF nigdy nie generuje tagu `wsp:Optional`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-234">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="4c61b-235">B3003: podczas uzyskiwania dostępu do `wsrmp:RMAssertion` protokołu WS-Policy WCF ignoruje znacznik `wsp:Optional` i traktuje zasady WS-RM jako obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="4c61b-235">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="4c61b-236">R3004: ponieważ WCF nie składa się z sesji SSL/TLS, funkcja WCF nie akceptuje zasad, które określają `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-236">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="4c61b-237">B3005: Funkcja WCF zawsze generuje element `wsrmp:DeliveryAssurance`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-237">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="4c61b-238">B3006: Funkcja WCF zawsze określa `wsrmp:ExactlyOnce` gwarancja dostarczania.</span><span class="sxs-lookup"><span data-stu-id="4c61b-238">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="4c61b-239">B3007: Funkcja WCF generuje i odczytuje następujące właściwości potwierdzenia WS-ReliableMessaging i zapewnia kontrolę nad nimi w`ReliableSessionBindingElement`WCF:</span><span class="sxs-lookup"><span data-stu-id="4c61b-239">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="4c61b-240">Przykład `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-240">An example of a `RMAssertion`.</span></span>

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="4c61b-241">Rozszerzenie WS-ReliableMessaging sterowania przepływem</span><span class="sxs-lookup"><span data-stu-id="4c61b-241">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="4c61b-242">Funkcja WCF używa rozszerzalności WS-ReliableMessaging w celu zapewnienia opcjonalnej dodatkowej, ściślejszej kontroli przepływu komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-242">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="4c61b-243">Sterowanie przepływem jest włączane przez ustawienie właściwości <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-243">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="4c61b-244">Poniżej znajduje się lista ograniczeń dotyczących programu WCF:</span><span class="sxs-lookup"><span data-stu-id="4c61b-244">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="4c61b-245">B4001: gdy jest włączona funkcja niezawodne sterowanie przepływem komunikatów, usługa WCF generuje element `netrm:BufferRemaining` w rozszerzeniu `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-245">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="4c61b-246">B4002: nawet w przypadku włączenia niezawodnej kontroli przepływów komunikatów Funkcja WCF nie wymaga elementu `netrm:BufferRemaining` w nagłówku `SequenceAcknowledgement`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-246">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="4c61b-247">B4003: miejsce docelowe komunikatów niezawodnych WCF używa `netrm:BufferRemaining`, aby wskazać liczbę nowych komunikatów, które może buforować.</span><span class="sxs-lookup"><span data-stu-id="4c61b-247">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="4c61b-248">B4004: gdy jest włączona funkcja niezawodnej kontroli przepływu komunikatów, Źródło niezawodnych komunikatów WCF używa wartości `netrm:BufferRemaining`, aby ograniczyć przesyłanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-248">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="4c61b-249">B4005: Funkcja WCF generuje `netrm:BufferRemaining` wartość całkowitą z zakresu od 0 do 4096 włącznie i odczytuje wartości całkowite z przedziału od 0 do `xs:int``maxInclusive` wartość 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="4c61b-249">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="4c61b-250">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="4c61b-250">Message Exchange Patterns</span></span>

<span data-ttu-id="4c61b-251">W tej sekcji opisano zachowanie WCF, gdy funkcja WS-ReliableMessaging jest używana w przypadku różnych wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-251">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="4c61b-252">Dla każdego wzorca wymiany komunikatów są brane pod uwagę następujące dwa scenariusze wdrażania:</span><span class="sxs-lookup"><span data-stu-id="4c61b-252">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="4c61b-253">Inicjator bez adresu: inicjator znajduje się za zaporą; Obiekt odpowiadający może dostarczać komunikaty do inicjatora tylko na odpowiedziach HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-253">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="4c61b-254">Inicjator obsługujący adresy: zarówno inicjator, jak i obiekt odpowiadający mogą wysyłać żądania HTTP; Innymi słowy, można nawiązać dwa odwrotne połączenia HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-254">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="4c61b-255">Jednokierunkowy inicjator bez adresu</span><span class="sxs-lookup"><span data-stu-id="4c61b-255">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4c61b-256">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="4c61b-256">Binding</span></span>

<span data-ttu-id="4c61b-257">Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji na jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-257">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="4c61b-258">Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z inicjatora do obiektu odpowiadającego i odpowiedzi HTTP w celu przesłania wszystkich komunikatów z obiektu odpowiadającego do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="4c61b-258">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4c61b-259">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="4c61b-259">CreateSequence Exchange</span></span>

<span data-ttu-id="4c61b-260">Inicjator WCF przesyła komunikat `CreateSequence` bez elementu `Offer` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-260">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4c61b-261">Obiekt odpowiadający WCF tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` bez elementu `Accept` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-261">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="4c61b-262">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="4c61b-262">SequenceAcknowledgement</span></span>

<span data-ttu-id="4c61b-263">Inicjator WCF przetwarza potwierdzenia odpowiedzi wszystkich komunikatów z wyjątkiem komunikatu `CreateSequence` i komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="4c61b-263">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="4c61b-264">Obiekt odpowiadający WCF zawsze przesyła autonomiczną potwierdzenie w odpowiedzi HTTP do wszystkich komunikatów sekwencji i `AckRequested`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-264">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="4c61b-265">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4c61b-265">CloseSequence Exchange</span></span>

<span data-ttu-id="4c61b-266">Inicjator WCF przesyła komunikat `CloseSequence` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-266">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4c61b-267">Obiekt odpowiadający WCF przesyła komunikat `CloseSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-267">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="4c61b-268">Wymiana TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="4c61b-268">TerminateSequence Exchange</span></span>

<span data-ttu-id="4c61b-269">Inicjator WCF przesyła komunikat `TerminateSequence` w żądaniu HTTP i oczekuje komunikatu `TerminateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-269">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4c61b-270">Obiekt odpowiadający WCF przesyła komunikat `TerminateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-270">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="4c61b-271">Jeden ze sposobów, inicjator adresowany</span><span class="sxs-lookup"><span data-stu-id="4c61b-271">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4c61b-272">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="4c61b-272">Binding</span></span>

<span data-ttu-id="4c61b-273">Usługa WCF zapewnia jednokierunkowy wzorzec wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał ruchu przychodzącego i jednego ruchu wychodzącego HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-273">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4c61b-274">Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-274">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4c61b-275">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4c61b-275">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4c61b-276">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="4c61b-276">CreateSequence Exchange</span></span>

<span data-ttu-id="4c61b-277">Inicjator WCF przesyła komunikat `CreateSequence` bez elementu `Offer` w żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-277">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4c61b-278">Obiekt odpowiadający WCF tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` bez elementu `Accept` w żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-278">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="4c61b-279">Dupleks, inicjator z adresami</span><span class="sxs-lookup"><span data-stu-id="4c61b-279">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4c61b-280">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="4c61b-280">Binding</span></span>

<span data-ttu-id="4c61b-281">Funkcja WCF udostępnia w pełni asynchroniczny, dwukierunkowy wzorzec wymiany komunikatów przy użyciu dwóch sekwencji w ramach jednego ruchu przychodzącego i jednego wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-281">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4c61b-282">Ten wzorzec wymiany komunikatów może być mieszany z `Request/Reply`, `Addressable` wzorzec wymiany komunikatów inicjatora w ograniczony sposób.</span><span class="sxs-lookup"><span data-stu-id="4c61b-282">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="4c61b-283">Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-283">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4c61b-284">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4c61b-284">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4c61b-285">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="4c61b-285">CreateSequence Exchange</span></span>

<span data-ttu-id="4c61b-286">Inicjator WCF przesyła `CreateSequence` komunikat z elementem `Offer` w żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-286">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4c61b-287">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma `Offer` elementu, a następnie tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` z elementem `Accept`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-287">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="4c61b-288">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="4c61b-288">Sequence Lifetime</span></span>

<span data-ttu-id="4c61b-289">Usługa WCF traktuje dwie sekwencje jako jedną sesję w pełni dupleks.</span><span class="sxs-lookup"><span data-stu-id="4c61b-289">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="4c61b-290">Po wygenerowaniu błędu, który powoduje błąd jednej sekwencji, usługa WCF oczekuje, że zdalny punkt końcowy wystąpi błąd obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-290">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="4c61b-291">Po odczytaniu błędu powodującego błąd jednej sekwencji błędy programu WCF są obie sekwencją.</span><span class="sxs-lookup"><span data-stu-id="4c61b-291">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="4c61b-292">Funkcja WCF może zamknąć swoją sekwencję wychodzącą i kontynuować przetwarzanie komunikatów w sekwencji przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="4c61b-292">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="4c61b-293">Z kolei WCF może przetworzyć zamknięcie sekwencji przychodzącej i kontynuować wysyłanie komunikatów do sekwencji wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="4c61b-293">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="4c61b-294">"Żądanie-odpowiedź" i "jednokierunkowy" inicjator bez adresu</span><span class="sxs-lookup"><span data-stu-id="4c61b-294">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4c61b-295">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="4c61b-295">Binding</span></span>

<span data-ttu-id="4c61b-296">Usługa WCF udostępnia wzorzec wymiany komunikatów jednokierunkowych i z żądaniami odpowiedzi przy użyciu dwóch sekwencji w ramach jednego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-296">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="4c61b-297">Funkcja WCF używa żądań HTTP do przesyłania wszystkich komunikatów z inicjatora do obiektu odpowiadającego i odpowiedzi HTTP w celu przesłania wszystkich komunikatów z obiektu odpowiadającego do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="4c61b-297">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4c61b-298">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="4c61b-298">CreateSequence Exchange</span></span>

<span data-ttu-id="4c61b-299">Inicjator WCF przesyła komunikat `CreateSequence` z elementem `Offer` w żądaniu HTTP i oczekuje komunikatu `CreateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-299">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="4c61b-300">Obiekt odpowiadający WCF tworzy sekwencję i przesyła `CreateSequenceResponse` komunikat z elementem `Accept` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-300">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="4c61b-301">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="4c61b-301">One-way Message</span></span>

<span data-ttu-id="4c61b-302">Aby pomyślnie zakończyć wymianę komunikatów jednokierunkowych, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera autonomiczny komunikat `SequenceAcknowledgement` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-302">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="4c61b-303">`SequenceAcknowledgement` musi potwierdzić komunikat przesłany.</span><span class="sxs-lookup"><span data-stu-id="4c61b-303">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="4c61b-304">Obiekt odpowiadający WCF może odpowiedzieć na żądanie z potwierdzeniem, błędem lub odpowiedzią z pustym identyfikatorem treści i kodem stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4c61b-304">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="4c61b-305">Komunikaty dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="4c61b-305">Two Way Messages</span></span>

<span data-ttu-id="4c61b-306">Aby pomyślnie wykonać dwukierunkową metodę wymiany komunikatów, inicjator WCF przesyła komunikat sekwencji żądania w żądaniu HTTP i odbiera komunikat sekwencji odpowiedzi w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-306">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="4c61b-307">Odpowiedź musi zawierać `SequenceAcknowledgement` potwierdzenia przesyłanego komunikatu sekwencji żądania.</span><span class="sxs-lookup"><span data-stu-id="4c61b-307">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="4c61b-308">Obiekt odpowiadający WCF może odpowiedzieć na żądanie za pomocą odpowiedzi aplikacji, błędu lub odpowiedzi z pustym identyfikatorem treści i kodem stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4c61b-308">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="4c61b-309">Ze względu na obecność komunikatów jednokierunkowych i chronometrażu odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądań i numer sekwencyjny komunikatu odpowiedzi nie mają korelacji.</span><span class="sxs-lookup"><span data-stu-id="4c61b-309">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="4c61b-310">Ponawianie odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="4c61b-310">Retrying Replies</span></span>

<span data-ttu-id="4c61b-311">Funkcja WCF korzysta z korelacji żądanie HTTP-odpowiedź dla dwukierunkowej korelacji protokołu wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-311">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="4c61b-312">W związku z tym inicjator WCF nie przerywa próby przeprowadzenia komunikatu sekwencji żądania, gdy komunikat sekwencji żądań zostanie potwierdzony, ale zamiast tego, gdy odpowiedź HTTP przeprowadzi `SequenceAcknowledgement`, odpowiedzi aplikacji lub błędu.</span><span class="sxs-lookup"><span data-stu-id="4c61b-312">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="4c61b-313">Obiekt odpowiadający programu WCF ponawia odpowiedzi na odpowiedź HTTP żądania, z którym jest skorelowana odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="4c61b-313">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="4c61b-314">CloseSequence Exchange</span><span class="sxs-lookup"><span data-stu-id="4c61b-314">CloseSequence Exchange</span></span>

<span data-ttu-id="4c61b-315">Po odebraniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń dla wszystkich jednokierunkowych komunikatów sekwencji żądania inicjator WCF przesyła `CloseSequence` komunikat dla sekwencji żądań w żądaniu HTTP i oczekuje `CloseSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-315">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="4c61b-316">Zamknięcie sekwencji żądań niejawnie powoduje zamknięcie sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4c61b-316">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="4c61b-317">Oznacza to, że inicjator WCF obejmuje ostateczną `SequenceAcknowledgement` sekwencji odpowiedzi w komunikacie `CloseSequence`, a sekwencja odpowiedzi nie ma `CloseSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="4c61b-317">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="4c61b-318">Obiekt odpowiadający WCF gwarantuje, że wszystkie odpowiedzi są potwierdzane i przesyła komunikat `CloseSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-318">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="4c61b-319">Wymiana TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="4c61b-319">TerminateSequence Exchange</span></span>

<span data-ttu-id="4c61b-320">Po odebraniu komunikatu `CloseSequenceResponse` inicjator WCF przesyła komunikat `TerminateSequence` dla sekwencji żądań w żądaniu HTTP i oczekuje `TerminateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-320">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="4c61b-321">Podobnie jak w przypadku `CloseSequence` Exchange, zakończenie sekwencji żądań niejawnie kończy sekwencję odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4c61b-321">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="4c61b-322">Oznacza to, że inicjator WCF obejmuje ostateczną `SequenceAcknowledgement` sekwencji odpowiedzi w komunikacie `TerminateSequence`, a sekwencja odpowiedzi nie ma `TerminateSequence` Exchange.</span><span class="sxs-lookup"><span data-stu-id="4c61b-322">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="4c61b-323">Obiekt odpowiadający WCF przesyła komunikat `TerminateSequenceResponse` w odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-323">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="4c61b-324">Żądanie/odpowiedź, inicjator z adresami</span><span class="sxs-lookup"><span data-stu-id="4c61b-324">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="4c61b-325">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="4c61b-325">Binding</span></span>

<span data-ttu-id="4c61b-326">Funkcja WCF udostępnia wzorzec wymiany komunikatów typu żądanie-odpowiedź przy użyciu dwóch sekwencji w ramach jednego ruchu przychodzącego i jednego wychodzącego kanału HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-326">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="4c61b-327">Ten wzorzec wymiany komunikatów może być mieszany z `Duplex, Addressable` wzorzec wymiany komunikatów inicjatora w ograniczony sposób.</span><span class="sxs-lookup"><span data-stu-id="4c61b-327">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="4c61b-328">Usługa WCF używa żądań HTTP do przesyłania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4c61b-328">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="4c61b-329">Wszystkie odpowiedzi HTTP mają pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="4c61b-329">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="4c61b-330">Sekwencja w programie</span><span class="sxs-lookup"><span data-stu-id="4c61b-330">CreateSequence Exchange</span></span>

<span data-ttu-id="4c61b-331">Inicjator WCF przesyła `CreateSequence` komunikat z elementem `Offer` w żądaniu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4c61b-331">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="4c61b-332">Obiekt odpowiadający WCF gwarantuje, że `CreateSequence` ma element `Offer`, a następnie tworzy sekwencję i przesyła komunikat `CreateSequenceResponse` z elementem `Accept`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-332">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="4c61b-333">Korelacja żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="4c61b-333">Request/Reply Correlation</span></span>

<span data-ttu-id="4c61b-334">Poniższe zasady dotyczą wszystkich skorelowanych żądań i odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="4c61b-334">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="4c61b-335">Funkcja WCF gwarantuje, że wszystkie komunikaty żądania aplikacji zawierają `ReplyTo` odwołanie do punktu końcowego i `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-335">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="4c61b-336">Program WCF stosuje odwołanie do lokalnego punktu końcowego, ponieważ każdy komunikat żądania aplikacji jest `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-336">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="4c61b-337">Odwołanie do lokalnego punktu końcowego jest `ReplyTo` komunikatu `CreateSequence` dla inicjatora i `To` komunikatu `CreateSequence` dla obiektu odpowiadającego.</span><span class="sxs-lookup"><span data-stu-id="4c61b-337">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="4c61b-338">Funkcja WCF zapewnia, że przychodzące komunikaty żądania zawierają `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="4c61b-338">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="4c61b-339">Funkcja WCF zapewnia, że identyfikator URI odwołania do punktu końcowego `ReplyTo` wszystkich komunikatów żądania aplikacji jest zgodny z odwołaniem do lokalnego punktu końcowego zgodnie z definicją wcześniejszą.</span><span class="sxs-lookup"><span data-stu-id="4c61b-339">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="4c61b-340">Funkcja WCF gwarantuje, że wszystkie odpowiedzi będą mieć poprawne `RelatesTo` i `To` nagłówki po `wsa` reguł korelacji żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4c61b-340">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

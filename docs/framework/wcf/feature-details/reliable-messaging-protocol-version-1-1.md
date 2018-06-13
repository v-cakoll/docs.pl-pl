---
title: Reliable Messaging Protocol w wersji 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496961"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="7babf-102">Reliable Messaging Protocol w wersji 1,1</span><span class="sxs-lookup"><span data-stu-id="7babf-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="7babf-103">W tym temacie omówiono szczegóły implementacji usługi Windows Communication Foundation (WCF) dla protokołu WS-ReliableMessaging protokołu lutego 2007 (w wersji 1.1) niezbędne do współpracy przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="7babf-104">Usługi WCF zgodna ze specyfikacją WS-ReliableMessaging, ograniczenia i wyjaśnienia opisanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="7babf-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="7babf-105">Należy pamiętać, że protokołu WS-ReliableMessaging w wersji 1.1 jest wykonywane, począwszy od [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7babf-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="7babf-106">WS-ReliableMessaging February 2007 protokół jest zaimplementowana w programie WCF przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="7babf-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="7babf-107">Dla wygody tematu są używane następujące role:</span><span class="sxs-lookup"><span data-stu-id="7babf-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="7babf-108">Inicjator: Klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="7babf-109">Obiekt odpowiadający w trybie: Usługa służącą do odbierania żądań inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7babf-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="7babf-110">Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7babf-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="7babf-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="7babf-111">Prefix</span></span>|<span data-ttu-id="7babf-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7babf-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="7babf-113">Menedżer zasobów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7babf-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|<span data-ttu-id="7babf-114">netrm</span><span class="sxs-lookup"><span data-stu-id="7babf-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|  
|<span data-ttu-id="7babf-115">s</span><span class="sxs-lookup"><span data-stu-id="7babf-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|  
|<span data-ttu-id="7babf-116">wsa</span><span class="sxs-lookup"><span data-stu-id="7babf-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|<span data-ttu-id="7babf-117">wsse</span><span class="sxs-lookup"><span data-stu-id="7babf-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="7babf-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="7babf-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|<span data-ttu-id="7babf-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="7babf-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|<span data-ttu-id="7babf-120">WSP</span><span class="sxs-lookup"><span data-stu-id="7babf-120">wsp</span></span>|<span data-ttu-id="7babf-121">(WS-Policy 1.2 lub WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="7babf-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="7babf-122">Obsługa wiadomości</span><span class="sxs-lookup"><span data-stu-id="7babf-122">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="7babf-123">Tworzenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="7babf-123">Sequence Creation</span></span>  
 <span data-ttu-id="7babf-124">Implementuje WCF `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić niezawodna obsługa komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="7babf-125">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7babf-125">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="7babf-126">B1101: Odwołanie do tego samego punktu końcowego jako używa inicjatora WCF `CreateSequence` komunikatu `ReplyTo`, `AcksTo` i `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="7babf-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="7babf-127">R1102: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości musi mieć adres wartości z reprezentacji ciągu identyczne tak, aby odpowiadały octet-wise.</span><span class="sxs-lookup"><span data-stu-id="7babf-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="7babf-128">Obiekt odpowiadający w trybie WCF sprawdza, czy identyfikator URI części `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne, przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="7babf-129">R1103: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości powinny mieć ten sam zestaw parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="7babf-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   <span data-ttu-id="7babf-130">Usługi WCF nie wymusza, ale przyjęto założenie, że odwołanie parametry `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołuje się do punktu końcowego na `CreateSequence` są identyczne i korzysta z parametrów odwołania z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="7babf-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="7babf-131">B1104: Inicjator WCF nie generuje opcjonalny `Expires` lub `Offer/Expires` element `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="7babf-132">B1105: Podczas uzyskiwania dostępu do `CreateSequence` używa obiektu odpowiadającego w trybie WCF wiadomości, `Expires` wartość w `CreateSequence` element jako `Expires` wartość w `CreateSequenceResponse` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="7babf-133">W przeciwnym wypadku obiekt odpowiadający w trybie WCF odczytuje i ignoruje `Expires` i `Offer/Expires` wartości.</span><span class="sxs-lookup"><span data-stu-id="7babf-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="7babf-134">B1106: Podczas uzyskiwania dostępu do `CreateSequenceResponse` komunikat, inicjator WCF: opcjonalny `Expires` wartość, ale nie używa ich.</span><span class="sxs-lookup"><span data-stu-id="7babf-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="7babf-135">B1107: WCF Inicjator i obiekt odpowiadający zawsze Generuj opcjonalny `IncompleteSequenceBehavior` element `CreateSequence/Offer` i `CreateSequenceResponse` elementy.</span><span class="sxs-lookup"><span data-stu-id="7babf-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="7babf-136">B1108: WCF używa tylko `DiscardFollowingFirstGap` i `NoDiscard` wartości w `IncompleteSequenceBehavior` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="7babf-137">Korzysta z protokołu WS-ReliableMessaging `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.</span><span class="sxs-lookup"><span data-stu-id="7babf-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="7babf-138">B1109: Jeśli `CreateSequence` zawiera `Offer` elementu jednokierunkowej udzielenia WCF odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="7babf-139">B1110: Jeśli obiekt odpowiadający niezawodnej obsługi komunikatów odrzuci oferowany sekwencji, inicjator WCF błędów nowo utworzonego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="7babf-140">B1111: Jeśli `CreateSequence` nie zawiera `Offer` elementu dwukierunkowe udzielenia WCF odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceRefused` usterek.</span><span class="sxs-lookup"><span data-stu-id="7babf-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="7babf-141">R1112: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `[address]` właściwość `CreateSequenceResponse/Accept/AcksTo` odwołania do punktu końcowego musi być zgodna docelowego identyfikatora URI z `CreateSequence` bajtów wiadomości dla bajtu.</span><span class="sxs-lookup"><span data-stu-id="7babf-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="7babf-142">R1113: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, wszystkie komunikaty o obu sekwencji wynikających z inicjatora do udzielenia muszą zostać przesłane do odwołania do tego samego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7babf-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 <span data-ttu-id="7babf-143">Usługi WCF używa WS-ReliableMessaging do nawiązywania niezawodnych sesji między Inicjator i obiekt odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="7babf-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="7babf-144">Implementacja WCF WS-ReliableMessaging udostępnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7babf-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="7babf-145">WS-ReliableMessaging `Offer` mechanizmu na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanawianie odwrotnej skorelowane dwóch sekwencji i zapewnia protokołu sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="7babf-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="7babf-146">Ponieważ WCF zapewnia gwarancję zabezpieczeń dla sesji, w tym na trasie ochronę integralności sesji, jest praktyczne upewnij się, że wiadomości przeznaczony dla tej samej strony do tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="7babf-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="7babf-147">Umożliwia to także "piggy zapasowy" potwierdzeń sekwencji komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7babf-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="7babf-148">W związku z tym ograniczenia R1102, R1112 i R1113 dotyczą WCF.</span><span class="sxs-lookup"><span data-stu-id="7babf-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>  
  
 <span data-ttu-id="7babf-149">Przykład `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-149">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="7babf-150">Przykład `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-150">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="7babf-151">Zamknięcie sekwencji</span><span class="sxs-lookup"><span data-stu-id="7babf-151">Closing a Sequence</span></span>  
 <span data-ttu-id="7babf-152">Używa WCF `CloseSequence` i `CloseSequenceResponse` komunikatów dla niezawodna obsługa komunikatów zamknięcia zainicjowanego źródła.</span><span class="sxs-lookup"><span data-stu-id="7babf-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="7babf-153">Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie zainicjować operacji zamykania i źródło niezawodna obsługa komunikatów usługi WCF nie obsługuje zamknięcia zainicjowanego przez miejsce docelowe niezawodna obsługa komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7babf-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="7babf-154">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7babf-154">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="7babf-155">B1201: Źródło niezawodna obsługa komunikatów usługi WCF zawsze wysyła `CloseSequence` komunikat zamknięcia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="7babf-156">B1202: Źródło niezawodna obsługa komunikatów czeka na potwierdzenie pełnego zakresu sekwencji wiadomości przed wysłaniem `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="7babf-157">B1203: Źródło niezawodna obsługa komunikatów zawsze zawiera opcjonalny `LastMsgNumber` element chyba, że sekwencja nie zawiera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="7babf-158">R1204: Niezawodna obsługa komunikatów w miejscu docelowym musi nie zainicjować operacji zamykania, wysyłając `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="7babf-159">B1205: odebrane `CloseSequence` wiadomości, uznaje sekwencji, niekompletna źródła niezawodna obsługa komunikatów usługi WCF i wysyła błąd.</span><span class="sxs-lookup"><span data-stu-id="7babf-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="7babf-160">Przykład `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-160">An example of a `CloseSequence` message.</span></span>  
  
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
Example CloseSequenceResponse message:  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="7babf-161">Zakończenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="7babf-161">Sequence Termination</span></span>  
 <span data-ttu-id="7babf-162">Przede wszystkim używa WCF `TerminateSequence/TerminateSequenceResponse` uzgadniania po zakończeniu `CloseSequence/CloseSequenceResponse` uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="7babf-162">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="7babf-163">Niezawodna obsługa komunikatów usługi WCF w miejscu docelowym nie inicjuje zakończenia i źródła niezawodna obsługa komunikatów nie obsługuje zakończenia niezawodna obsługa komunikatów zainicjowanego przez miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="7babf-163">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="7babf-164">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7babf-164">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="7babf-165">B1301: Inicjator WCF wysyła tylko `TerminateSequence` komunikat po pomyślnym zarejestrowaniu `CloseSequence/CloseSequenceResponse` uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="7babf-165">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="7babf-166">R1302: WCF sprawdza, czy `LastMsgNumber` element jest spójny we wszystkich `CloseSequence` i `TerminateSequence` wiadomości dla danej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-166">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="7babf-167">Oznacza to, że `LastMsgNumber` albo nie występuje na wszystkie `CloseSequence` i `TerminateSequence` wiadomości, lub jest obecny i identyczne we wszystkich `CloseSequence` i `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-167">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="7babf-168">B1303: Podczas odbierania `TerminateSequence` komunikatu po `CloseSequence/CloseSequenceResponse` uzgadniania odpowiada docelowego niezawodna obsługa komunikatów `TerminateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-168">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="7babf-169">Ponieważ źródła niezawodna obsługa komunikatów ma ostateczne potwierdzenie przed wysłaniem `TerminateSequence` wiadomości, niezawodna obsługa komunikatów w miejscu docelowym zna bez wątpienia czy kończy się sekwencja i natychmiast zwraca zasobów.</span><span class="sxs-lookup"><span data-stu-id="7babf-169">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="7babf-170">B1304: Podczas odbierania `TerminateSequence` komunikatów przed `CloseSequence/CloseSequenceResponse` uzgadniania odpowiada docelowego WCF niezawodna obsługa komunikatów `TerminateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-170">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="7babf-171">Jeśli docelowy niezawodna obsługa komunikatów Określa, że nie ma żadnych niespójności w sekwencji, docelowy niezawodna obsługa komunikatów oczekiwania przez czas określony docelowy aplikacji przed odzyskiwanie zasobów, aby umożliwić klientom możliwość odbierania ostateczne potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="7babf-171">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="7babf-172">W przeciwnym razie wartość docelową niezawodnej obsługi komunikatów natychmiast zwraca zasobów i wskazuje przeznaczenia aplikacji, że sekwencja kończy się wątpliwości, podnosząc `Faulted` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7babf-172">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="7babf-173">Przykład `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-173">An example of a `TerminateSequence` message.</span></span>  
  
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
Example TerminateSequenceResponse message:  
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
  
### <a name="sequences"></a><span data-ttu-id="7babf-174">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="7babf-174">Sequences</span></span>  
 <span data-ttu-id="7babf-175">Oto lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="7babf-175">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="7babf-176">Generuje B1401:WCF i uzyskuje dostęp do sekwencji liczb nie jest wyższa niż `xs:long`na maksymalną wartość z wartościami granicznymi 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="7babf-176">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="7babf-177">Przykład `Sequence` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-177">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="7babf-178">Potwierdzenie żądania</span><span class="sxs-lookup"><span data-stu-id="7babf-178">Request Acknowledgement</span></span>  
 <span data-ttu-id="7babf-179">Używa WCF `AckRequested` nagłówka jako mechanizmu keep-alive.</span><span class="sxs-lookup"><span data-stu-id="7babf-179">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="7babf-180">Przykład `AckRequested` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-180">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="7babf-181">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="7babf-181">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="7babf-182">Usługi WCF używa mechanizmu "nakładka" dla potwierdzeń sekwencji w WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-182">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="7babf-183">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7babf-183">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="7babf-184">R1601: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata.</span><span class="sxs-lookup"><span data-stu-id="7babf-184">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="7babf-185">Zdalny punkt końcowy musi mieć możliwość dostępu nakładane `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-185">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="7babf-186">B1602: Usługi WCF nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementów.</span><span class="sxs-lookup"><span data-stu-id="7babf-186">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="7babf-187">Usługi WCF weryfikuje każdy `Nack` element zawiera numer sekwencji, ale w przeciwnym razie ignoruje `Nack` elementu i wartość.</span><span class="sxs-lookup"><span data-stu-id="7babf-187">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="7babf-188">Przykład `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-188">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="7babf-189">Błędy protokołu WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-189">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="7babf-190">Poniżej znajduje się lista ograniczenia, które dotyczą implementacji WCF błędów WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-190">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="7babf-191">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7babf-191">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="7babf-192">B1701: Usługi WCF nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="7babf-192">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="7babf-193">B1702: Za pośrednictwem protokołu SOAP 1.2, gdy punkt końcowy usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia, WCF generuje zagnieżdżoną `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7babf-193">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="7babf-194">Protokół WS-Addressing błędów</span><span class="sxs-lookup"><span data-stu-id="7babf-194">WS-Addressing Faults</span></span>  
 <span data-ttu-id="7babf-195">Ponieważ WS-ReliableMessaging korzysta z protokołu WS-Addressing, implementacji protokołu WS-ReliableMessaging WCF może generować i przekazywania błędów protokołu WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="7babf-195">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="7babf-196">W tej sekcji omówiono WS-Addressing usterek, które jawnie WCF generuje i przesyła w warstwie usługi WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="7babf-196">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="7babf-197">B1801:WCF generuje i przesyła `Message Addressing Header Required` fault, gdy spełniony jest jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7babf-197">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="7babf-198">A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `MessageId` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-198">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="7babf-199">A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `ReplyTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-199">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="7babf-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, lub `TerminateSequenceResponse` Brak komunikatu `RelatesTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-200">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="7babf-201">B1802:WCF generuje i przesyła `Endpoint Unavailable` błędów, aby wskazać żadnego punktu końcowego nasłuchiwania, który może przetwarzać sekwencji oparte na badania adresowania nagłówków `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-201">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="7babf-202">Protokół kompozycji</span><span class="sxs-lookup"><span data-stu-id="7babf-202">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="7babf-203">Kompozycja z protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="7babf-203">Composition with WS-Addressing</span></span>  
 <span data-ttu-id="7babf-204">Usługi WCF obsługuje dwie wersje usługi WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].</span><span class="sxs-lookup"><span data-stu-id="7babf-204">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="7babf-205">Podczas uwagi specyfikacji WS-ReliableMessaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia.</span><span class="sxs-lookup"><span data-stu-id="7babf-205">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="7babf-206">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7babf-206">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="7babf-207">R2101: Zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-207">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="7babf-208">R2102: Jednej wersji WS-Addressing można używać w danej sekwencji WS-ReliableMessaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `Offer` mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="7babf-208">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="7babf-209">Kompozycja z protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="7babf-209">Composition with SOAP</span></span>  
 <span data-ttu-id="7babf-210">Usługi WCF obsługuje SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-210">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="7babf-211">Kompozycja i WS-Security WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="7babf-211">Composition with WS-Security and WS-SecureConversation</span></span>  
 <span data-ttu-id="7babf-212">Usługi WCF zapewnia ochronę sekwencji WS-ReliableMessaging za pomocą zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji.</span><span class="sxs-lookup"><span data-stu-id="7babf-212">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="7babf-213">Protokół WS-ReliableMessaging 1.1, WS-Security 1.1 i zabezpieczenia WS konwersacji 1.3 protokołu powinny być używane razem.</span><span class="sxs-lookup"><span data-stu-id="7babf-213">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="7babf-214">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7babf-214">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="7babf-215">R2301: Aby chronić integralność sekwencji WS-ReliableMessaging oprócz integralności i poufności poszczególne wiadomości, WCF wymaga, należy użyć zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="7babf-215">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="7babf-216">R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="7babf-216">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="7babf-217">R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="7babf-217">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="7babf-218">B2304:ws-sekwencji ReliableMessaging dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="7babf-218">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="7babf-219">R2305: Jeżeli składa się z zabezpieczenia WS konwersacji, obiekt odpowiadający w trybie WCF wymaga, aby `CreateSequence` komunikat zawiera `wsse:SecurityTokenReference` elementu i `wsrm:UsesSequenceSTR` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-219">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="7babf-220">Przykład `UsesSequenceSTR` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-220">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="7babf-221">Kompozycja z sesji SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="7babf-221">Composition with SSL/TLS sessions</span></span>  
 <span data-ttu-id="7babf-222">Usługi WCF nie obsługuje kompozycji z sesji SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="7babf-222">WCF does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="7babf-223">B2401: Usługi WCF nie generuje `wsrm:UsesSequenceSSL` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-223">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="7babf-224">R2402: Niezawodnej inicjatora wiadomości nie musi wysyłać `CreateSequence` komunikatów z `wsrm:UsesSequenceSSL` nagłówka do obiekt odpowiadający WCF.</span><span class="sxs-lookup"><span data-stu-id="7babf-224">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="7babf-225">Kompozycja z WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="7babf-225">Composition with WS-Policy</span></span>  
 <span data-ttu-id="7babf-226">Usługi WCF obsługuje dwie wersje usługi WS-Policy: WS-Policy 1.2 i 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="7babf-226">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="7babf-227">WS-ReliableMessaging WS-potwierdzenia zasad</span><span class="sxs-lookup"><span data-stu-id="7babf-227">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 <span data-ttu-id="7babf-228">Usługi WCF używa protokołu WS-ReliableMessaging WS-Policy potwierdzenia `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="7babf-228">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="7babf-229">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7babf-229">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="7babf-230">B3001: Dołącza WCF `wsrmn:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="7babf-230">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="7babf-231">Usługi WCF obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="7babf-231">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="7babf-232">B3002: Nigdy nie generuje WCF `wsp:Optional` tagu.</span><span class="sxs-lookup"><span data-stu-id="7babf-232">B3002: WCF never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="7babf-233">B3003: Podczas uzyskiwania dostępu do `wsrmp:RMAssertion` ignoruje WCF potwierdzenia WS-Policy `wsp:Optional` tagu i traktuje zasady protokołu WS-RM jako obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="7babf-233">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="7babf-234">R3004: Ponieważ WCF nie tworzą z sesji SSL/TLS, usługi WCF nie akceptuje zasady, które określają `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="7babf-234">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="7babf-235">B3005: WCF zawsze generuje `wsrmp:DeliveryAssurance` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-235">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="7babf-236">B3006: WCF określa zawsze `wsrmp:ExactlyOnce` gwarancji dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="7babf-236">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="7babf-237">B3007: WCF generuje i odczytuje następujące właściwości potwierdzenia WS-ReliableMessaging i zapewnia kontrolę nad nimi na usługi WCF`ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="7babf-237">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="7babf-238">Przykład `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="7babf-238">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="7babf-239">Przepływ sterowania WS-ReliableMessaging rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="7babf-239">Flow Control WS-ReliableMessaging Extension</span></span>  
 <span data-ttu-id="7babf-240">Usługi WCF używa rozszerzalności WS-ReliableMessaging, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-240">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="7babf-241">Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``boolean` właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="7babf-241">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="7babf-242">Oto lista ograniczeń, które są stosowane do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="7babf-242">The following is a list of constraints that apply to WCF:</span></span>  
  
-   <span data-ttu-id="7babf-243">B4001: Po włączeniu niezawodnej obsługi komunikatów sterowanie przepływem WCF generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7babf-243">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="7babf-244">B4002: Nawet wtedy, gdy niezawodnej obsługi komunikatów sterowanie przepływem jest włączone, usługi WCF nie wymaga `netrm:BufferRemaining` element `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="7babf-244">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="7babf-245">B4003: Używa WCF niezawodnej obsługi komunikatów docelowego `netrm:BufferRemaining` można buforu wskazująca, jak wiele nowych komunikatów go.</span><span class="sxs-lookup"><span data-stu-id="7babf-245">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="7babf-246">B4004:when niezawodnej obsługi komunikatów sterowanie przepływem jest włączona, źródło WCF niezawodnej obsługi komunikatów używa wartości `netrm:BufferRemaining` do ograniczania przesyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7babf-246">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="7babf-247">B4005: Generuje WCF `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="7babf-247">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="7babf-248">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="7babf-248">Message Exchange Patterns</span></span>  
 <span data-ttu-id="7babf-249">W tej sekcji opisano zachowanie WCF w przypadku WS-ReliableMessaging służy do różnych wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-249">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="7babf-250">Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:</span><span class="sxs-lookup"><span data-stu-id="7babf-250">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="7babf-251">Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-251">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="7babf-252">Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="7babf-252">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="7babf-253">Jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="7babf-253">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="7babf-254">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="7babf-254">Binding</span></span>  
 <span data-ttu-id="7babf-255">Usługi WCF zawiera jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-255">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="7babf-256">WCF używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7babf-256">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="7babf-257">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-257">CreateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-258">Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-258">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="7babf-259">Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-259">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="7babf-260">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="7babf-260">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="7babf-261">Inicjator WCF przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="7babf-261">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="7babf-262">Obiekt odpowiadający w trybie WCF zawsze przesyła autonomicznej potwierdzenia w odpowiedzi HTTP do wszystkich sekwencji i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-262">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="7babf-263">CloseSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-263">CloseSequence Exchange</span></span>  
 <span data-ttu-id="7babf-264">Przesyła inicjatora WCF `CloseSequence` wiadomości na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-264">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="7babf-265">Obiekt odpowiadający w trybie WCF przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-265">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="7babf-266">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-266">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-267">Przesyła inicjatora WCF `TerminateSequence` wiadomości na żądania HTTP i oczekuje `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-267">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="7babf-268">Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-268">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="7babf-269">Jednym ze sposobów, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="7babf-269">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="7babf-270">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="7babf-270">Binding</span></span>  
 <span data-ttu-id="7babf-271">WCF zapewnia jednokierunkowe wymiany komunikatów za pomocą jednego sekwencji za pośrednictwem jednej dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-271">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="7babf-272">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-272">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="7babf-273">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="7babf-273">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="7babf-274">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-274">CreateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-275">Przesyła inicjatora WCF `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-275">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="7babf-276">Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-276">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="7babf-277">Dupleks, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="7babf-277">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="7babf-278">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="7babf-278">Binding</span></span>  
 <span data-ttu-id="7babf-279">Udostępnia WCF pełni asynchroniczne, dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-279">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="7babf-280">Ta wymiany komunikatów można łączyć z `Request/Reply`, `Addressable` inicjatora wymiany komunikatów w sposób ograniczony.</span><span class="sxs-lookup"><span data-stu-id="7babf-280">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="7babf-281">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-281">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="7babf-282">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="7babf-282">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="7babf-283">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-283">CreateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-284">Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-284">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="7babf-285">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma `Offer` elementu, następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-285">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="7babf-286">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="7babf-286">Sequence Lifetime</span></span>  
 <span data-ttu-id="7babf-287">Usługi WCF traktuje dwóch sekwencji jako jedna sesja pełni duplex.</span><span class="sxs-lookup"><span data-stu-id="7babf-287">WCF treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="7babf-288">Podczas generowania błędów, które błędów jedną sekwencję, WCF oczekuje, że zdalny punkt końcowy do obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-288">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="7babf-289">Podczas odczytywania usterek, które błędów jedną sekwencję, WCF błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-289">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>  
  
 <span data-ttu-id="7babf-290">WCF można zamknąć ich wychodzącego sekwencji i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-290">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="7babf-291">Z drugiej strony WCF można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.</span><span class="sxs-lookup"><span data-stu-id="7babf-291">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="7babf-292">Żądanie odpowiedź i jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="7babf-292">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="7babf-293">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="7babf-293">Binding</span></span>  
 <span data-ttu-id="7babf-294">Usługi WCF zapewnia jednokierunkowe i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-294">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="7babf-295">WCF używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="7babf-295">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="7babf-296">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-296">CreateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-297">Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-297">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="7babf-298">Obiekt odpowiadający w trybie WCF tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-298">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="7babf-299">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="7babf-299">One-way Message</span></span>  
 <span data-ttu-id="7babf-300">Można pomyślnie ukończyć exchange komunikat jednokierunkowy inicjatora WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-300">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="7babf-301">`SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.</span><span class="sxs-lookup"><span data-stu-id="7babf-301">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="7babf-302">Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="7babf-302">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="7babf-303">Dwa komunikaty sposób</span><span class="sxs-lookup"><span data-stu-id="7babf-303">Two Way Messages</span></span>  
 <span data-ttu-id="7babf-304">Pomyślnie protokół exchange dwukierunkowej wiadomości, inicjator WCF przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera odpowiedź komunikatu sekwencji odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-304">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="7babf-305">Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.</span><span class="sxs-lookup"><span data-stu-id="7babf-305">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="7babf-306">Obiekt odpowiadający w trybie WCF może odpowiedzieć na żądanie odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="7babf-306">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="7babf-307">Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="7babf-307">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="7babf-308">Ponawianie próby odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="7babf-308">Retrying Replies</span></span>  
 <span data-ttu-id="7babf-309">Usługi WCF zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-309">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="7babf-310">W związku z tym inicjatora WCF nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji żądanie sekwencji komunikat zostaje potwierdzony, ale raczej, jeśli odpowiedź HTTP niesie `SequenceAcknowledgement`, odpowiedzi aplikacji lub fault.</span><span class="sxs-lookup"><span data-stu-id="7babf-310">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="7babf-311">Obiekt odpowiadający w trybie WCF ponowi próbę odpowiedzi na odpowiedzi HTTP żądania, do której są korelowane z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7babf-311">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="7babf-312">CloseSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-312">CloseSequence Exchange</span></span>  
 <span data-ttu-id="7babf-313">Po otrzymaniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń wszystkich komunikatów sekwencji żądań jednokierunkowej, przesyła inicjatora WCF `CloseSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `CloseSequenceResponse` na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-313">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="7babf-314">Niejawnie zamknięciem sekwencji żądań zamyka sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7babf-314">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="7babf-315">Oznacza to, że inicjatora WCF obejmuje Final sekwencji odpowiedzi `SequenceAcknowledgement` na `CloseSequence` komunikat i sekwencji odpowiedzi nie ma `CloseSequence` programu exchange.</span><span class="sxs-lookup"><span data-stu-id="7babf-315">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="7babf-316">Obiekt odpowiadający w trybie WCF zapewnia wszystkie odpowiedzi są potwierdzone i przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-316">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="7babf-317">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-317">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-318">Od momentu odebrania `CloseSequenceResponse` przesyła inicjatora WCF wiadomości, `TerminateSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `TerminateSequenceResponse` na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-318">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="7babf-319">Podobnie jak `CloseSequence` programu exchange, niejawnie przerywanie sekwencji żądanie kończy sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="7babf-319">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="7babf-320">Oznacza to, że inicjatora WCF obejmuje final sekwencji odpowiedzi `SequenceAcknowledgement` na `TerminateSequence` komunikat i sekwencji odpowiedzi nie ma `TerminateSequence` programu exchange.</span><span class="sxs-lookup"><span data-stu-id="7babf-320">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="7babf-321">Obiekt odpowiadający w trybie WCF przesyła `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-321">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="7babf-322">Żądanie/odpowiedź, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="7babf-322">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="7babf-323">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="7babf-323">Binding</span></span>  
 <span data-ttu-id="7babf-324">Udostępnia WCF wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-324">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="7babf-325">Ta wymiany komunikatów można łączyć z `Duplex, Addressable` inicjatora wymiany komunikatów w sposób ograniczony.</span><span class="sxs-lookup"><span data-stu-id="7babf-325">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="7babf-326">WCF używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7babf-326">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="7babf-327">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="7babf-327">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="7babf-328">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="7babf-328">CreateSequence Exchange</span></span>  
 <span data-ttu-id="7babf-329">Przesyła inicjatora WCF `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="7babf-329">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="7babf-330">Obiekt odpowiadający w trybie WCF upewnia się, że `CreateSequence` ma `Offer` element następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="7babf-330">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="7babf-331">Żądanie i odpowiedź korelacji</span><span class="sxs-lookup"><span data-stu-id="7babf-331">Request/Reply Correlation</span></span>  
 <span data-ttu-id="7babf-332">Poniższe informacje dotyczą wszystkich skorelowane żądań i odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="7babf-332">The following applies to all correlated requests and replies:</span></span>  
  
-   <span data-ttu-id="7babf-333">Usługi WCF zapewnia wszystkie posiadają komunikaty żądania aplikacji `ReplyTo` odwołania do punktu końcowego i `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="7babf-333">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   <span data-ttu-id="7babf-334">Usługi WCF odnoszą się odwołania do lokalnego punktu końcowego jako każdy komunikat żądania aplikacji `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="7babf-334">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="7babf-335">Odwołanie do lokalnego punktu końcowego jest `CreateSequence` komunikatu `ReplyTo` inicjatora i `CreateSequence` komunikatu `To` obiektu odpowiadającego w trybie.</span><span class="sxs-lookup"><span data-stu-id="7babf-335">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   <span data-ttu-id="7babf-336">Usługi WCF zapewnia to żądanie przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="7babf-336">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   <span data-ttu-id="7babf-337">Zapewnia WCF `ReplyTo` URI punktu końcowego odwołania wszystkich komunikatów żądania aplikacji odpowiada odwołaniu do lokalnego punktu końcowego, zgodnie z definicją wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7babf-337">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   <span data-ttu-id="7babf-338">WCF gwarantuje, że wszystkie odpowiedzi zawierać poprawny `RelatesTo` i `To` następujące nagłówki `wsa` żądania/odpowiedzi reguły korelacji.</span><span class="sxs-lookup"><span data-stu-id="7babf-338">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

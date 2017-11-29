---
title: Reliable Messaging Protocol w wersji 1,1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 98fe8ac04b7ac811802466cf63c58ea4cebd791e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="dfc2b-102">Reliable Messaging Protocol w wersji 1,1</span><span class="sxs-lookup"><span data-stu-id="dfc2b-102">Reliable Messaging Protocol version 1.1</span></span>
<span data-ttu-id="dfc2b-103">W tym temacie omówiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] szczegóły implementacji protokołu WS-ReliableMessaging February 2007 (w wersji 1.1) protokołu niezbędne do współpracy przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-103">This topic covers [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-104">zgodna ze specyfikacją WS-ReliableMessaging, ograniczenia i wyjaśnienia opisanego w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-104"> follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="dfc2b-105">Należy pamiętać, że protokołu WS-ReliableMessaging w wersji 1.1 jest wykonywane, począwszy od [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfc2b-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with the [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].</span></span>  
  
 <span data-ttu-id="dfc2b-106">WS-ReliableMessaging February 2007 protokół jest zaimplementowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przez <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-106">The WS-ReliableMessaging February 2007 protocol is implemented in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>  
  
 <span data-ttu-id="dfc2b-107">Dla wygody tematu są używane następujące role:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-107">For convenience, the topic uses the following roles:</span></span>  
  
-   <span data-ttu-id="dfc2b-108">Inicjator: Klienta, który inicjuje tworzenia sekwencji WS-Reliable wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>  
  
-   <span data-ttu-id="dfc2b-109">Obiekt odpowiadający w trybie: Usługa służącą do odbierania żądań inicjatora.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-109">Responder: The service that receives the initiator's requests.</span></span>  
  
 <span data-ttu-id="dfc2b-110">Ten dokument używa prefiksy i przestrzenie nazw w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-110">This document uses the prefixes and namespaces in the following table.</span></span>  
  
|<span data-ttu-id="dfc2b-111">Prefiks</span><span class="sxs-lookup"><span data-stu-id="dfc2b-111">Prefix</span></span>|<span data-ttu-id="dfc2b-112">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dfc2b-112">Namespace</span></span>|  
|-|-|  
|<span data-ttu-id="dfc2b-113">Menedżer zasobów systemu Windows</span><span class="sxs-lookup"><span data-stu-id="dfc2b-113">wsrm</span></span>|<span data-ttu-id="dfc2b-114">http://docs.oasis-open.org/ws-Rx/WSRM/200702</span><span class="sxs-lookup"><span data-stu-id="dfc2b-114">http://docs.oasis-open.org/ws-rx/wsrm/200702</span></span>|  
|<span data-ttu-id="dfc2b-115">netrm</span><span class="sxs-lookup"><span data-stu-id="dfc2b-115">netrm</span></span>|<span data-ttu-id="dfc2b-116">http://schemas.microsoft.com/ws/2006/05/RM</span><span class="sxs-lookup"><span data-stu-id="dfc2b-116">http://schemas.microsoft.com/ws/2006/05/rm</span></span>|  
|<span data-ttu-id="dfc2b-117">s</span><span class="sxs-lookup"><span data-stu-id="dfc2b-117">s</span></span>|<span data-ttu-id="dfc2b-118">http://www.w3.org/2003/05/SOAP-Envelope</span><span class="sxs-lookup"><span data-stu-id="dfc2b-118">http://www.w3.org/2003/05/soap-envelope</span></span>|  
|<span data-ttu-id="dfc2b-119">wsa</span><span class="sxs-lookup"><span data-stu-id="dfc2b-119">wsa</span></span>|<span data-ttu-id="dfc2b-120">http://schemas.xmlsoap.org/ws/2005/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="dfc2b-120">http://schemas.xmlsoap.org/ws/2005/08/addressing</span></span>|  
|<span data-ttu-id="dfc2b-121">wsse</span><span class="sxs-lookup"><span data-stu-id="dfc2b-121">wsse</span></span>|<span data-ttu-id="dfc2b-122">http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span><span class="sxs-lookup"><span data-stu-id="dfc2b-122">http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd</span></span>|  
|<span data-ttu-id="dfc2b-123">wsrmp</span><span class="sxs-lookup"><span data-stu-id="dfc2b-123">wsrmp</span></span>|<span data-ttu-id="dfc2b-124">http://docs.oasis-open.org/ws-Rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="dfc2b-124">http://docs.oasis-open.org/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="dfc2b-125">netrmp</span><span class="sxs-lookup"><span data-stu-id="dfc2b-125">netrmp</span></span>|<span data-ttu-id="dfc2b-126">http://schemas.microsoft.com/ws-Rx/wsrmp/200702</span><span class="sxs-lookup"><span data-stu-id="dfc2b-126">http://schemas.microsoft.com/ws-rx/wsrmp/200702</span></span>|  
|<span data-ttu-id="dfc2b-127">WSP</span><span class="sxs-lookup"><span data-stu-id="dfc2b-127">wsp</span></span>|<span data-ttu-id="dfc2b-128">(WS-Policy 1.2 lub WS-Policy 1.5)</span><span class="sxs-lookup"><span data-stu-id="dfc2b-128">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|  
  
## <a name="messaging"></a><span data-ttu-id="dfc2b-129">Obsługa wiadomości</span><span class="sxs-lookup"><span data-stu-id="dfc2b-129">Messaging</span></span>  
  
### <a name="sequence-creation"></a><span data-ttu-id="dfc2b-130">Tworzenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-130">Sequence Creation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-131">implementuje `CreateSequence` i `CreateSequenceResponse` komunikaty, aby ustanowić niezawodna obsługa komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-131"> implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="dfc2b-132">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-132">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dfc2b-133">B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora używa odwołania do tego samego punktu końcowego jako `CreateSequence` komunikatu `ReplyTo`, `AcksTo` i `Offer/Endpoint`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-133">B1101: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>  
  
-   <span data-ttu-id="dfc2b-134">R1102: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości musi mieć adres wartości z reprezentacji ciągu identyczne tak, aby odpowiadały octet-wise.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-134">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>  
  
    -   <span data-ttu-id="dfc2b-135">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie sprawdza, czy identyfikator URI części `AcksTo`, `ReplyTo` i `Endpoint` odwołania do punktu końcowego są identyczne, przed utworzeniem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-135">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>  
  
-   <span data-ttu-id="dfc2b-136">R1103: `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołania do punktu końcowego w `CreateSequence` wiadomości powinny mieć ten sam zestaw parametrów odwołania.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-136">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-137">nie wymusza, ale przyjęto założenie, które zawierają odniesienia parametry `AcksTo`, `ReplyTo` i `Offer/Endpoint` odwołuje się do punktu końcowego na `CreateSequence` są identyczne i korzysta z parametrów odwołania z `ReplyTo` odwołania do punktu końcowego dla Potwierdzanie i komunikaty sekwencji odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-137"> does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>  
  
-   <span data-ttu-id="dfc2b-138">B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie generuje opcjonalny `Expires` lub `Offer/Expires` element `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-138">B1104: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>  
  
-   <span data-ttu-id="dfc2b-139">B1105: Podczas uzyskiwania dostępu do `CreateSequence` wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa obiektu odpowiadającego w trybie `Expires` wartość w `CreateSequence` element jako `Expires` wartość w `CreateSequenceResponse` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-139">B1105: When accessing the `CreateSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="dfc2b-140">W przeciwnym razie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie odczytuje i ignoruje `Expires` i `Offer/Expires` wartości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-140">Otherwise, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>  
  
-   <span data-ttu-id="dfc2b-141">B1106: Podczas uzyskiwania dostępu do `CreateSequenceResponse` wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora odczytuje opcjonalny `Expires` wartość, ale nie używa ich.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-141">B1106: When accessing the `CreateSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator reads the optional `Expires` value but does not use it.</span></span>  
  
-   <span data-ttu-id="dfc2b-142">B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjator i obiekt odpowiadający zawsze Generuj opcjonalny `IncompleteSequenceBehavior` element `CreateSequence/Offer` i `CreateSequenceResponse` elementy.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-142">B1107: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>  
  
-   <span data-ttu-id="dfc2b-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa tylko `DiscardFollowingFirstGap` i `NoDiscard` wartości w `IncompleteSequenceBehavior` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-143">B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>  
  
    -   <span data-ttu-id="dfc2b-144">Korzysta z protokołu WS-ReliableMessaging `Offer` mechanizmu ustanowienie dwa konwersacji skorelowane sekwencji, które tworzą sesji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-144">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>  
  
-   <span data-ttu-id="dfc2b-145">B1109: Jeśli `CreateSequence` zawiera `Offer` elementu, jeden sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceResponse` bez `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-145">B1109: If `CreateSequence` contains an `Offer` element, the one way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>  
  
-   <span data-ttu-id="dfc2b-146">B1110: Jeśli sekwencja oferowany odrzuca niezawodnej obsługi komunikatów obiektu odpowiadającego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora błędów nowo utworzonego sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-146">B1110: If a Reliable Messaging Responder rejects the offered sequence, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator faults the newly established sequence.</span></span>  
  
-   <span data-ttu-id="dfc2b-147">B1111: Jeśli `CreateSequence` nie zawiera `Offer` element, dwukierunkowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie odrzuca oferowany sekwencji odpowiedzi z `CreateSequenceRefused` usterek.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-147">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>  
  
-   <span data-ttu-id="dfc2b-148">R1112: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `[address]` właściwość `CreateSequenceResponse/Accept/AcksTo` odwołania do punktu końcowego musi być zgodna docelowego identyfikatora URI z `CreateSequence` bajtów wiadomości dla bajtu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-148">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>  
  
-   <span data-ttu-id="dfc2b-149">R1113: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, wszystkie komunikaty o obu sekwencji wynikających z inicjatora do udzielenia muszą zostać przesłane do odwołania do tego samego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-149">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-150">używa protokołu WS-ReliableMessaging do nawiązywania niezawodnych sesji między Inicjator i obiekt odpowiadający.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-150"> uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="dfc2b-151">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Implementacja protokołu WS-ReliableMessaging udostępnia niezawodnej sesji dla jednokierunkowe żądanie odpowiedź i pełny dupleks wzorców do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-151">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="dfc2b-152">WS-ReliableMessaging `Offer` mechanizmu na `CreateSequence` i `CreateSequenceResponse` umożliwia ustanawianie odwrotnej skorelowane dwóch sekwencji i zapewnia protokołu sesji, które jest odpowiednie dla wszystkich komunikatów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-152">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="dfc2b-153">Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia gwarancję zabezpieczeń takich sesji w tym end-to-end ochronę integralności sesji, jest praktyczne upewnij się, że wiadomości przeznaczony dla tej samej strony do tego samego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-153">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="dfc2b-154">Umożliwia to także "piggy zapasowy" potwierdzeń sekwencji komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-154">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="dfc2b-155">W związku z tym ograniczenia R1102, R1112 i R1113 dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfc2b-155">Therefore, constraints R1102, R1112, and R1113 apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="dfc2b-156">Przykład `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-156">An example of a `CreateSequence` message.</span></span>  
  
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
  
 <span data-ttu-id="dfc2b-157">Przykład `CreateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-157">An example of a `CreateSequenceResponse` message.</span></span>  
  
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
  
### <a name="closing-a-sequence"></a><span data-ttu-id="dfc2b-158">Zamknięcie sekwencji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-158">Closing a Sequence</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-159">używa `CloseSequence` i `CloseSequenceResponse` komunikatów dla niezawodna obsługa komunikatów zamknięcia zainicjowanego źródła.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-159"> uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="dfc2b-160">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Niezawodna obsługa komunikatów docelowego nie zainicjować operacji zamykania i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodna obsługa komunikatów źródło nie obsługuje zamknięcia zainicjowanego przez miejsce docelowe niezawodna obsługa komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-160">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate shutdown and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="dfc2b-161">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-161">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dfc2b-162">B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodna obsługa komunikatów źródła zawsze wysyła `CloseSequence` komunikat zamknięcia sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-162">B1201: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>  
  
-   <span data-ttu-id="dfc2b-163">B1202: Źródło niezawodna obsługa komunikatów czeka na potwierdzenie pełnego zakresu sekwencji wiadomości przed wysłaniem `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-163">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="dfc2b-164">B1203: Źródło niezawodna obsługa komunikatów zawsze zawiera opcjonalny `LastMsgNumber` element chyba, że sekwencja nie zawiera wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-164">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>  
  
-   <span data-ttu-id="dfc2b-165">R1204: Niezawodna obsługa komunikatów w miejscu docelowym musi nie zainicjować operacji zamykania, wysyłając `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-165">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>  
  
-   <span data-ttu-id="dfc2b-166">B1205: odebrane `CloseSequence` komunikat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodna obsługa komunikatów źródła uzna sekwencji, niekompletna i wysyła błąd.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-166">B1205: Upon receiving a `CloseSequence` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>  
  
 <span data-ttu-id="dfc2b-167">Przykład `CloseSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-167">An example of a `CloseSequence` message.</span></span>  
  
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
  
### <a name="sequence-termination"></a><span data-ttu-id="dfc2b-168">Zakończenie sekwencji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-168">Sequence Termination</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-169">przede wszystkim używa `TerminateSequence/TerminateSequenceResponse` uzgadniania po zakończeniu `CloseSequence/CloseSequenceResponse` uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-169"> primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="dfc2b-170">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Niezawodna obsługa komunikatów docelowego nie inicjuje zakończenia i niezawodna obsługa komunikatów źródło nie obsługuje zakończenia niezawodna obsługa komunikatów zainicjowanego przez miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-170">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="dfc2b-171">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-171">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dfc2b-172">B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora tylko wysyła `TerminateSequence` komunikat po pomyślnym zarejestrowaniu `CloseSequence/CloseSequenceResponse` uzgadniania.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-172">B1301: The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>  
  
-   <span data-ttu-id="dfc2b-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawdza, czy `LastMsgNumber` element jest spójny we wszystkich `CloseSequence` i `TerminateSequence` wiadomości dla danej sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-173">R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="dfc2b-174">Oznacza to, że `LastMsgNumber` albo nie występuje na wszystkie `CloseSequence` i `TerminateSequence` wiadomości, lub jest obecny i identyczne we wszystkich `CloseSequence` i `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-174">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>  
  
-   <span data-ttu-id="dfc2b-175">B1303: Podczas odbierania `TerminateSequence` komunikatu po `CloseSequence/CloseSequenceResponse` uzgadniania odpowiada docelowego niezawodna obsługa komunikatów `TerminateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-175">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="dfc2b-176">Ponieważ źródła niezawodna obsługa komunikatów ma ostateczne potwierdzenie przed wysłaniem `TerminateSequence` wiadomości, niezawodna obsługa komunikatów w miejscu docelowym zna bez wątpienia czy kończy się sekwencja i natychmiast zwraca zasobów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-176">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>  
  
-   <span data-ttu-id="dfc2b-177">B1304: Podczas odbierania `TerminateSequence` komunikatów przed `CloseSequence/CloseSequenceResponse` uzgadniania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] niezawodna obsługa komunikatów docelowego odpowiada `TerminateSequenceResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-177">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="dfc2b-178">Jeśli docelowy niezawodna obsługa komunikatów Określa, że nie ma żadnych niespójności w sekwencji, docelowy niezawodna obsługa komunikatów oczekiwania przez czas określony docelowy aplikacji przed odzyskiwanie zasobów, aby umożliwić klientom możliwość odbierania ostateczne potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-178">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="dfc2b-179">W przeciwnym razie wartość docelową niezawodnej obsługi komunikatów natychmiast zwraca zasobów i wskazuje przeznaczenia aplikacji, że sekwencja kończy się wątpliwości, podnosząc `Faulted` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-179">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>  
  
 <span data-ttu-id="dfc2b-180">Przykład `TerminateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-180">An example of a `TerminateSequence` message.</span></span>  
  
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
  
### <a name="sequences"></a><span data-ttu-id="dfc2b-181">Sekwencje</span><span class="sxs-lookup"><span data-stu-id="dfc2b-181">Sequences</span></span>  
 <span data-ttu-id="dfc2b-182">Oto lista ograniczeń, które są stosowane do sekwencji:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-182">The following is a list of constraints that apply to sequences:</span></span>  
  
-   <span data-ttu-id="dfc2b-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i uzyskuje dostęp do numerów sekwencji. nie jest wyższa niż `xs:long`przez wartość maksymalna włącznie, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-183">B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>  
  
 <span data-ttu-id="dfc2b-184">Przykład `Sequence` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-184">An example of a `Sequence` header.</span></span>  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a><span data-ttu-id="dfc2b-185">Potwierdzenie żądania</span><span class="sxs-lookup"><span data-stu-id="dfc2b-185">Request Acknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-186">używa `AckRequested` nagłówka jako mechanizmu keep-alive.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-186"> uses the `AckRequested` header as a keep-alive mechanism.</span></span>  
  
 <span data-ttu-id="dfc2b-187">Przykład `AckRequested` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-187">An example of an `AckRequested` header.</span></span>  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a><span data-ttu-id="dfc2b-188">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="dfc2b-188">SequenceAcknowledgement</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-189">używa mechanizmu "nakładka" dla potwierdzeń sekwencji w WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-189"> uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="dfc2b-190">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-190">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dfc2b-191">R1601: Gdy dwa konwersacji sekwencje są ustanawianie za pomocą `Offer` mechanizmu, `SequenceAcknowledgement` nagłówka może być zawarta w każdej wiadomości aplikacji przesyłane do określonego adresata.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-191">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="dfc2b-192">Zdalny punkt końcowy musi mieć możliwość dostępu nakładane `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-192">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="dfc2b-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `SequenceAcknowledgement` nagłówki, które zawierają `Nack` elementów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-193">B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-194">weryfikuje każdy `Nack` element zawiera numer sekwencji, ale w przeciwnym razie ignoruje `Nack` elementu i wartość.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-194"> validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>  
  
 <span data-ttu-id="dfc2b-195">Przykład `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-195">An example of a `SequenceAcknowledgement` header.</span></span>  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="dfc2b-196">Błędy protokołu WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-196">WS-ReliableMessaging Faults</span></span>  
 <span data-ttu-id="dfc2b-197">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-ReliableMessaging błędów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-197">The following is a list of constraints that apply to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="dfc2b-198">Obowiązują następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-198">The following constraints apply:</span></span>  
  
-   <span data-ttu-id="dfc2b-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `MessageNumberRollover` błędów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-199">B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate `MessageNumberRollover` faults.</span></span>  
  
-   <span data-ttu-id="dfc2b-200">B1702: Za pośrednictwem protokołu SOAP 1.2, gdy punkt końcowy usługi przez nią miejsce osiągnie limit liczby połączeń i nie może przetworzyć nowe połączenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje zagnieżdżoną `CreateSequenceRefused` fault podrzędny, `netrm:ConnectionLimitReached`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-200">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>  
  
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
  
### <a name="ws-addressing-faults"></a><span data-ttu-id="dfc2b-201">Protokół WS-Addressing błędów</span><span class="sxs-lookup"><span data-stu-id="dfc2b-201">WS-Addressing Faults</span></span>  
 <span data-ttu-id="dfc2b-202">Ponieważ WS-ReliableMessaging korzysta z protokołu WS-Addressing, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacji protokołu WS-ReliableMessaging może wygenerować i przekazywania błędów protokołu WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-202">Because WS-ReliableMessaging uses WS-Addressing, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="dfc2b-203">Ta obejmuje sekcji WS-Addressing błędów, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jawnie generuje i przesyła w warstwie usługi WS-ReliableMessaging:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-203">This section covers the WS-Addressing faults that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>  
  
-   <span data-ttu-id="dfc2b-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i przesyła `Message Addressing Header Required` fault, gdy spełniony jest jeden z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-204">B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>  
  
    -   <span data-ttu-id="dfc2b-205">A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `MessageId` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-205">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>  
  
    -   <span data-ttu-id="dfc2b-206">A `CreateSequence`, `CloseSequence` lub `TerminateSequence` Brak komunikatu `ReplyTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-206">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>  
  
    -   <span data-ttu-id="dfc2b-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, lub `TerminateSequenceResponse` Brak komunikatu `RelatesTo` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-207">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>  
  
-   <span data-ttu-id="dfc2b-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i przesyła `Endpoint Unavailable` błędów, aby wskazać żadnego punktu końcowego nasłuchiwania, który może przetwarzać sekwencji oparte na badania adresowania nagłówków `CreateSequence` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-208">B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>  
  
## <a name="protocol-composition"></a><span data-ttu-id="dfc2b-209">Protokół kompozycji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-209">Protocol Composition</span></span>  
  
### <a name="composition-with-ws-addressing"></a><span data-ttu-id="dfc2b-210">Kompozycja z protokołu WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="dfc2b-210">Composition with WS-Addressing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-211">obsługuje protokół WS-Addressing dwie wersje: WS-Addressing 2004/08 [WS-ADDR] i W3C WS-Addressing 1.0 zalecenia [WS-ADDR-CORE] i [WS-ADDR — SOAP].</span><span class="sxs-lookup"><span data-stu-id="dfc2b-211"> supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>  
  
 <span data-ttu-id="dfc2b-212">Podczas uwagi specyfikacji WS-ReliableMessaging tylko WS-Addressing 2004-08 nie uniemożliwia wersji WS-Addressing do użycia.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-212">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="dfc2b-213">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-213">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="dfc2b-214">R2101: Zarówno WS-Addressing 2004/08 i WS-Addressing 1.0 mogą być używane z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-214">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>  
  
-   <span data-ttu-id="dfc2b-215">R2102: Jednej wersji WS-Addressing można używać w danej sekwencji WS-ReliableMessaging dysków lub para skorelowane przy użyciu sekwencji odwrotnej `Offer` mechanizmu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-215">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>  
  
### <a name="composition-with-soap"></a><span data-ttu-id="dfc2b-216">Kompozycja z protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="dfc2b-216">Composition with SOAP</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-217">obsługuje zarówno SOAP 1.1 i SOAP 1.2 z WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-217"> supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="dfc2b-218">Kompozycja i WS-Security WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="dfc2b-218">Composition with WS-Security and WS-SecureConversation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-219">zapewnia ochronę sekwencji WS-ReliableMessaging za pomocą zabezpieczenia WS konwersacji bezpieczne transportowych (HTTPS), kompozycji z WS-Security i kompozycji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-219"> provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="dfc2b-220">Protokół WS-ReliableMessaging 1.1, WS-Security 1.1 i zabezpieczenia WS konwersacji 1.3 protokołu powinny być używane razem.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-220">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="dfc2b-221">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-221">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="dfc2b-222">R2301: Aby chronić integralność WS-ReliableMessaging sekwencji dodatkowo integralności i poufności poszczególne wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga, należy użyć zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-222">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires that WS-Secure Conversation must be used.</span></span>  
  
-   <span data-ttu-id="dfc2b-223">R2302:AWS-Secure Conversation sesji muszą być ustalane przed ustanawianie sequence(s) WS-ReliableMessaging.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-223">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>  
  
-   <span data-ttu-id="dfc2b-224">R2303: Jeśli okres istnienia sekwencji WS-ReliableMessaging przekracza zabezpieczenia WS konwersacji istnienia sesji `SecurityContextToken` ustanowione przy użyciu zabezpieczenia WS konwersacji należy odnawiać przy użyciu odpowiedniego powiązania odnawiania zabezpieczenia WS konwersacji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-224">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>  
  
-   <span data-ttu-id="dfc2b-225">B2304:ws-sekwencji ReliableMessaging dysków lub para skorelowane odwrotnej sekwencje są zawsze powiązane z jednej sesji WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-225">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>  
  
-   <span data-ttu-id="dfc2b-226">R2305: Gdy składa się z zabezpieczenia WS konwersacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie wymaga, aby `CreateSequence` komunikat zawiera `wsse:SecurityTokenReference` elementu i `wsrm:UsesSequenceSTR` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-226">R2305: When composed with WS-Secure Conversation, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>  
  
 <span data-ttu-id="dfc2b-227">Przykład `UsesSequenceSTR` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-227">An example of a `UsesSequenceSTR` header.</span></span>  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="dfc2b-228">Kompozycja z sesji SSL/TLS</span><span class="sxs-lookup"><span data-stu-id="dfc2b-228">Composition with SSL/TLS sessions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-229">nie obsługuje kompozycji z sesji SSL/TLS:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-229"> does not support composition with SSL/TLS sessions:</span></span>  
  
-   <span data-ttu-id="dfc2b-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie generuje `wsrm:UsesSequenceSSL` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-230">B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not generate the `wsrm:UsesSequenceSSL` header.</span></span>  
  
-   <span data-ttu-id="dfc2b-231">R2402: Niezawodnej inicjatora wiadomości nie musi wysyłać `CreateSequence` komunikatów z `wsrm:UsesSequenceSSL` nagłówka do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu odpowiadającego w trybie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-231">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder.</span></span>  
  
### <a name="composition-with-ws-policy"></a><span data-ttu-id="dfc2b-232">Kompozycja z WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-232">Composition with WS-Policy</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-233">obsługuje dwie wersje usługi WS-Policy: WS-Policy 1.2 i 1.5 WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-233"> supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="dfc2b-234">WS-ReliableMessaging WS-potwierdzenia zasad</span><span class="sxs-lookup"><span data-stu-id="dfc2b-234">WS-ReliableMessaging WS-Policy Assertion</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-235">używa protokołu WS-ReliableMessaging WS-Policy potwierdzenia `wsrm:RMAssertion` do opisywania możliwości punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-235"> uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="dfc2b-236">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-236">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="dfc2b-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dołącza `wsrmn:RMAssertion` WS-Policy potwierdzenia do `wsdl:binding` elementów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-237">B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-238">obsługuje zarówno załączników do `wsdl:binding` i `wsdl:port` elementy.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-238"> supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>  
  
-   <span data-ttu-id="dfc2b-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nigdy nie generuje `wsp:Optional` tagu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-239">B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] never generates the `wsp:Optional` tag.</span></span>  
  
-   <span data-ttu-id="dfc2b-240">B3003: Podczas uzyskiwania dostępu do `wsrmp:RMAssertion` potwierdzenia WS-Policy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `wsp:Optional` tagu i traktuje zasady protokołu WS-RM jako obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-240">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>  
  
-   <span data-ttu-id="dfc2b-241">R3004: Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie tworzą z sesji SSL/TLS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie akceptuje zasady, które określają `wsrmp:SequenceTransportSecurity`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-241">R3004: Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not compose with SSL/TLS sessions, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>  
  
-   <span data-ttu-id="dfc2b-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze generuje `wsrmp:DeliveryAssurance` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-242">B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always generates the `wsrmp:DeliveryAssurance` element.</span></span>  
  
-   <span data-ttu-id="dfc2b-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawsze Określa `wsrmp:ExactlyOnce` gwarancji dostarczenia.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-243">B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>  
  
-   <span data-ttu-id="dfc2b-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje i odczytuje następujące właściwości potwierdzenia WS-ReliableMessaging i zapewnia kontrolę nad nimi na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-244">B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]`ReliableSessionBindingElement`:</span></span>  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     <span data-ttu-id="dfc2b-245">Przykład `RMAssertion`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-245">An example of a `RMAssertion`.</span></span>  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="dfc2b-246">Przepływ sterowania WS-ReliableMessaging rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="dfc2b-246">Flow Control WS-ReliableMessaging Extension</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-247">używa rozszerzeń protokołu WS-ReliableMessaging, aby zapewnić opcjonalne dodatkowe zwiększenie poziomu kontrolę nad przepływ komunikatów sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-247"> uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>  
  
 <span data-ttu-id="dfc2b-248">Przez ustawienie włączone jest sterowanie przepływem `ReliableSessionBindingElement`w `FlowControlEnabled``boolean` właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-248">Flow control is enabled by setting the `ReliableSessionBindingElement`’s `FlowControlEnabled``boolean` property to `true`.</span></span> <span data-ttu-id="dfc2b-249">Poniżej przedstawiono listę ograniczenia, które dotyczą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-249">The following is a list of constraints that apply to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:</span></span>  
  
-   <span data-ttu-id="dfc2b-250">B4001: Podczas kontroli przepływu komunikatów niezawodnej jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` elementu w element możliwość rozszerzania `SequenceAcknowledgement` nagłówka, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-250">B4001: When Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   <span data-ttu-id="dfc2b-251">B4002: Nawet wtedy, gdy jest to niezawodny sterowanie przepływem wiadomości jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wymaga `netrm:BufferRemaining` element `SequenceAcknowledgement` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-251">B4002: Even when Reliable Messaging Flow Control is enabled, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>  
  
-   <span data-ttu-id="dfc2b-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa niezawodnej obsługi komunikatów docelowego `netrm:BufferRemaining` można buforu wskazująca, jak wiele nowych komunikatów go.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-252">B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>  
  
-   <span data-ttu-id="dfc2b-253">B4004:when niezawodnej obsługi komunikatów sterowanie przepływem jest włączona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiarygodnego źródła komunikatów używa wartości `netrm:BufferRemaining` do ograniczania przesyłania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-253">B4004:When Reliable Messaging Flow Control is enabled, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>  
  
-   <span data-ttu-id="dfc2b-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` liczby całkowitej wartości z zakresu od 0 do 4096 włącznie i odczytuje wartości Liczba całkowita między 0 a `xs:int`w `maxInclusive` wartość 214748364 włącznie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-254">B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>  
  
## <a name="message-exchange-patterns"></a><span data-ttu-id="dfc2b-255">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="dfc2b-255">Message Exchange Patterns</span></span>  
 <span data-ttu-id="dfc2b-256">W tej sekcji opisano [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tego zachowania, gdy WS-ReliableMessaging służy do różnych wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-256">This section describes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="dfc2b-257">Dla każdego wymiany komunikatów w następujących scenariuszach dwa wdrożenia są traktowane jako:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-257">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>  
  
-   <span data-ttu-id="dfc2b-258">Inicjator nie rozpozna: Inicjator znajduje się za zaporą; Obiekt odpowiadający w trybie wiadomości mogą być dostarczane do inicjatora tylko na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-258">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>  
  
-   <span data-ttu-id="dfc2b-259">Inicjator adresowanego: Inicjator i obiekt odpowiadający mogą być wysyłane żądania HTTP; innymi słowy można ustanowić dwa połączenia HTTP odwrotnej.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-259">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>  
  
### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="dfc2b-260">Jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="dfc2b-260">One-way, Non-addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dfc2b-261">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="dfc2b-261">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-262">udostępnia jednokierunkowe wymiany komunikatów przy użyciu jednej sekwencji przez jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-262"> provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-263">używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-263"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dfc2b-264">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-264">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-265">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-265">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-266">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-266">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>  
  
#### <a name="sequenceacknowledgement"></a><span data-ttu-id="dfc2b-267">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="dfc2b-267">SequenceAcknowledgement</span></span>  
 <span data-ttu-id="dfc2b-268">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Inicjatora przetwarza potwierdzenia w odpowiedzi wszystkie komunikaty z wyjątkiem `CreateSequence` komunikat i komunikaty o błędach.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-268">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="dfc2b-269">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie zawsze przesyła autonomicznej potwierdzenia w odpowiedzi HTTP do wszystkich sekwencji i `AckRequested` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-269">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="dfc2b-270">CloseSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-270">CloseSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-271">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CloseSequence` wiadomości na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-271">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-272">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła obiektu odpowiadającego w trybie `CloseSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-272">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="dfc2b-273">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-273">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `TerminateSequence` wiadomości na żądania HTTP i oczekuje `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła obiektu odpowiadającego w trybie `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="one-way-addressable-initiator"></a><span data-ttu-id="dfc2b-276">Jednym ze sposobów, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="dfc2b-276">One Way, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dfc2b-277">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="dfc2b-277">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-278">udostępnia jednokierunkowe wymiany komunikatów za pomocą jednego sekwencji za pośrednictwem jednej dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-278"> provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-279">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-279"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dfc2b-280">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-280">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dfc2b-281">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-281">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-282">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CreateSequence` wiadomość bez `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-282">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dfc2b-283">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie tworzy sekwencję i przesyła `CreateSequenceResponse` wiadomość bez `Accept` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-283">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>  
  
### <a name="duplex-addressable-initiator"></a><span data-ttu-id="dfc2b-284">Dupleks, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="dfc2b-284">Duplex, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dfc2b-285">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="dfc2b-285">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-286">zawiera w pełni asynchroniczne, dwukierunkowe wymiany komunikatów za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-286"> provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="dfc2b-287">Ta wymiany komunikatów można łączyć z `Request/Reply`, `Addressable` inicjatora wymiany komunikatów w sposób ograniczony.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-287">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-288">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-288"> uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dfc2b-289">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-289">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dfc2b-290">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-290">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-291">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-291">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dfc2b-292">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma `Offer` elementu, następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-292">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="sequence-lifetime"></a><span data-ttu-id="dfc2b-293">Okres istnienia sekwencji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-293">Sequence Lifetime</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-294">traktuje dwóch sekwencji jako jedna sesja pełni duplex.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-294"> treats the two sequences as one fully-duplex session.</span></span>  
  
 <span data-ttu-id="dfc2b-295">Podczas generowania błędów, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oczekuje, że zdalny punkt końcowy do obu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-295">Upon generating a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="dfc2b-296">Podczas odczytywania usterek, które błędów jedną sekwencję [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] błędów zarówno sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-296">Upon reading a fault that faults one sequence, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faults both sequences.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-297">Zamknij jego sekwencji wychodzących i dalsze przetwarzanie komunikatów na jego przychodzących sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-297"> can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="dfc2b-298">Z drugiej strony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] można przetwarzać zamknięcia sekwencji dla ruchu przychodzącego i kontynuować wysyłanie wiadomości na jego wychodzące sekwencji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-298">Conversely, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="dfc2b-299">Żądanie odpowiedź i jednokierunkowe, nie mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="dfc2b-299">Request-Reply and One-Way, Non-Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dfc2b-300">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="dfc2b-300">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-301">zapewnia możliwość jednokierunkowych i żądanie odpowiedź wymiany komunikatów za pomocą dwóch sekwencji ponad jeden kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-301"> provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-302">używa żądania HTTP do przekazywania wszystkich komunikatów z inicjatora obiektu odpowiadającego w trybie i HTTP odpowiedzi do przesyłania wszystkie komunikaty z udzielenia do inicjatora.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-302"> uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dfc2b-303">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-303">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-304">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP i oczekuje `CreateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-304">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-305">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-305">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>  
  
#### <a name="one-way-message"></a><span data-ttu-id="dfc2b-306">Komunikat jednokierunkowy</span><span class="sxs-lookup"><span data-stu-id="dfc2b-306">One-way Message</span></span>  
 <span data-ttu-id="dfc2b-307">Aby ukończyć exchange komunikat jednokierunkowy pomyślnie, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbiera autonomiczny `SequenceAcknowledgement` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-307">To complete a one-way message exchange successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-308">`SequenceAcknowledgement` Musi potwierdzić wiadomości przesyłane.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-308">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>  
  
 <span data-ttu-id="dfc2b-309">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiadać na żądania z potwierdzeniem, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-309">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="two-way-messages"></a><span data-ttu-id="dfc2b-310">Dwa komunikaty sposób</span><span class="sxs-lookup"><span data-stu-id="dfc2b-310">Two Way Messages</span></span>  
 <span data-ttu-id="dfc2b-311">Pomyślnie protokół exchange dwukierunkowej wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora przesyła żądanie komunikatu sekwencji na żądania HTTP i odbierania komunikatu sekwencji odpowiedzi na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-311">To complete a two way message exchange protocol successfully, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="dfc2b-312">Odpowiedzi muszą oni nosić przy sobie `SequenceAcknowledgement` potwierdzeniem wiadomość sekwencji żądanie przesyłane.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-312">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>  
  
 <span data-ttu-id="dfc2b-313">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie może odpowiadać na żądania o odpowiedzi aplikacji, błąd lub odpowiedzi o pustej treści i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-313">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>  
  
 <span data-ttu-id="dfc2b-314">Z powodu obecności jednokierunkowe komunikaty i czas odpowiedzi aplikacji numer sekwencyjny komunikatu sekwencji żądania i numer sekwencyjny komunikatu odpowiedzi mają nie korelacji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-314">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>  
  
#### <a name="retrying-replies"></a><span data-ttu-id="dfc2b-315">Ponawianie próby odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="dfc2b-315">Retrying Replies</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-316">zależy od korelacja żądań i odpowiedzi HTTP dla korelacji protokół exchange dwukierunkowej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-316"> relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="dfc2b-317">W związku z tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora nie zatrzymuje ponowieniem próby wykonania żądania komunikatu sekwencji żądanie sekwencji komunikat zostaje potwierdzony, ale raczej, jeśli odpowiedź HTTP niesie `SequenceAcknowledgement`, odpowiedzi aplikacji lub fault.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-317">Because of this, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="dfc2b-318">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego w trybie ponowi próbę odpowiedzi na odpowiedzi HTTP żądania, do której są korelowane z odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-318">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>  
  
#### <a name="closesequence-exchange"></a><span data-ttu-id="dfc2b-319">CloseSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-319">CloseSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-320">Po otrzymaniu wszystkich komunikatów sekwencji odpowiedzi i potwierdzeń wszystkich komunikatów sekwencji żądań jednokierunkowej, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przesyła inicjatora `CloseSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `CloseSequenceResponse` na HTTP odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-320">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="dfc2b-321">Niejawnie zamknięciem sekwencji żądań zamyka sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-321">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="dfc2b-322">Oznacza to, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora obejmuje Final sekwencji odpowiedzi `SequenceAcknowledgement` na `CloseSequence` komunikat i sekwencji odpowiedzi nie ma `CloseSequence` programu exchange.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-322">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>  
  
 <span data-ttu-id="dfc2b-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu wszystkie odpowiedzi są potwierdzone i przesyła `CloseSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-323">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>  
  
#### <a name="terminatesequence-exchange"></a><span data-ttu-id="dfc2b-324">TerminateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-324">TerminateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-325">Od momentu odebrania `CloseSequenceResponse` wiadomości, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przesyła inicjatora `TerminateSequence` wiadomości dla żądania kolejności na żądania HTTP i oczekuje `TerminateSequenceResponse` na odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-325">After receiving the `CloseSequenceResponse` message, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>  
  
 <span data-ttu-id="dfc2b-326">Podobnie jak `CloseSequence` programu exchange, niejawnie przerywanie sekwencji żądanie kończy sekwencji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-326">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="dfc2b-327">Oznacza to, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inicjatora obejmuje final sekwencji odpowiedzi `SequenceAcknowledgement` na `TerminateSequence` komunikat i sekwencji odpowiedzi nie ma `TerminateSequence` programu exchange.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-327">This means the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>  
  
 <span data-ttu-id="dfc2b-328">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła obiektu odpowiadającego w trybie `TerminateSequenceResponse` komunikat odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-328">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>  
  
### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="dfc2b-329">Żądanie/odpowiedź, mogą być adresowane inicjatora</span><span class="sxs-lookup"><span data-stu-id="dfc2b-329">Request/Reply, Addressable Initiator</span></span>  
  
#### <a name="binding"></a><span data-ttu-id="dfc2b-330">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="dfc2b-330">Binding</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-331">udostępnia wymiany komunikatów "żądanie-odpowiedź" za pomocą dwóch sekwencji do jednego dla ruchu przychodzącego i jeden wychodzący kanał HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-331"> provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="dfc2b-332">Ta wymiany komunikatów można łączyć z `Duplex, Addressable` inicjatora wymiany komunikatów w sposób ograniczony.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-332">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-333">używa żądania HTTP do przekazywania wszystkich wiadomości.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-333"> uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="dfc2b-334">Wszystkie odpowiedzi HTTP ma pustą treść i kod stanu HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-334">All HTTP responses have an empty body and HTTP 202 status code.</span></span>  
  
#### <a name="createsequence-exchange"></a><span data-ttu-id="dfc2b-335">CreateSequence programu Exchange</span><span class="sxs-lookup"><span data-stu-id="dfc2b-335">CreateSequence Exchange</span></span>  
 <span data-ttu-id="dfc2b-336">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Przesyła inicjatora `CreateSequence` komunikatów z `Offer` elementu na żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-336">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="dfc2b-337">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Obiektu odpowiadającego temu `CreateSequence` ma `Offer` element następnie tworzy sekwencję i przesyła `CreateSequenceResponse` komunikatów z `Accept` elementu.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-337">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>  
  
#### <a name="requestreply-correlation"></a><span data-ttu-id="dfc2b-338">Żądanie i odpowiedź korelacji</span><span class="sxs-lookup"><span data-stu-id="dfc2b-338">Request/Reply Correlation</span></span>  
 <span data-ttu-id="dfc2b-339">Poniższe informacje dotyczą wszystkich skorelowane żądań i odpowiedzi:</span><span class="sxs-lookup"><span data-stu-id="dfc2b-339">The following applies to all correlated requests and replies:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-340">zapewnia wszystkie posiadają komunikaty żądania aplikacji `ReplyTo` odwołania do punktu końcowego i `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-340"> ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-341">stosuje się odwołanie do lokalnego punktu końcowego jako każdy komunikat żądania aplikacji `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-341"> applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="dfc2b-342">Odwołanie do lokalnego punktu końcowego jest `CreateSequence` komunikatu `ReplyTo` inicjatora i `CreateSequence` komunikatu `To` obiektu odpowiadającego w trybie.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-342">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-343">zapewnia to żądanie przychodzące komunikaty opatrzone `MessageId` i `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-343"> ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-344">zapewnia `ReplyTo` URI punktu końcowego odwołania wszystkich komunikatów żądania aplikacji odpowiada odwołaniu do lokalnego punktu końcowego, zgodnie z definicją wcześniej.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-344"> ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dfc2b-345">zapewnia, że wszystkie odpowiedzi zawierać poprawny `RelatesTo` i `To` następujące nagłówki `wsa` żądania/odpowiedzi reguły korelacji.</span><span class="sxs-lookup"><span data-stu-id="dfc2b-345"> ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>

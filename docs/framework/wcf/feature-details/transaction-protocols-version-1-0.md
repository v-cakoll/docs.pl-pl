---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a1501bbd5364773359f9b62602ba4bb684f076ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764630"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="a5f26-102">Protokoły transakcyjne wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="a5f26-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="a5f26-103">Windows Communication Foundation (WCF) w wersji 1 implementuje wersji 1.0 protokołów WS-Atomic Transaction i WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="a5f26-104">Aby uzyskać więcej informacji o wersji 1.1, zobacz [protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="a5f26-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="a5f26-105">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="a5f26-105">Specification/Document</span></span>|<span data-ttu-id="a5f26-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="a5f26-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="a5f26-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="a5f26-107">WS-Coordination</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="a5f26-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="a5f26-108">WS-AtomicTransaction</span></span>|<http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="a5f26-109">Współdziałanie w specyfikacji protokołu jest wymagany na dwóch poziomach: między aplikacjami i między menedżerowie transakcji (patrz poniższy rysunek).</span><span class="sxs-lookup"><span data-stu-id="a5f26-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="a5f26-110">Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="a5f26-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="a5f26-111">Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie jak w przypadku regularnego aplikacji programu exchange.</span><span class="sxs-lookup"><span data-stu-id="a5f26-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="a5f26-112">Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy w określonym powiązaniu, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a5f26-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="a5f26-113">W tym temacie opisuje kompozycję specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="a5f26-114">Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacji m.in. IBM IONA, Sun Microsystems i inne.</span><span class="sxs-lookup"><span data-stu-id="a5f26-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="a5f26-115">Współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje, aplikacja 1 i 2 aplikacji przedstawiono na poniższym rysunku:</span><span class="sxs-lookup"><span data-stu-id="a5f26-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Zrzut ekranu pokazujący menedżerów interakcji między transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="a5f26-117">Należy rozważyć typowy scenariusz protokołu WS-koordynacji/WS-Atomic Transaction za pomocą jednego inicjatora (I) i jednego uczestnika (P).</span><span class="sxs-lookup"><span data-stu-id="a5f26-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="a5f26-118">Inicjator i uczestnika, który ma menedżerowie transakcji (ITM i PTM, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="a5f26-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="a5f26-119">Dwufazowego, jest nazywana 2PC, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a5f26-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5f26-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="a5f26-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="a5f26-121">12. Odpowiedź komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="a5f26-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="a5f26-123">13. Zatwierdź (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="a5f26-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="a5f26-124">3. Rejestr (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="a5f26-124">3. Register (Completion)</span></span>|<span data-ttu-id="a5f26-125">14. Przygotowywanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="a5f26-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-126">4. RegisterResponse</span></span>|<span data-ttu-id="a5f26-127">15. Przygotowywanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="a5f26-128">5. Komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-128">5. Application Message</span></span>|<span data-ttu-id="a5f26-129">16. Przygotowany (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="a5f26-130">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="a5f26-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="a5f26-131">17. Przygotowany (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="a5f26-132">7. Rejestr (trwałość)</span><span class="sxs-lookup"><span data-stu-id="a5f26-132">7. Register (Durable)</span></span>|<span data-ttu-id="a5f26-133">18. Zatwierdzone (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="a5f26-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="a5f26-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-134">8. RegisterResponse</span></span>|<span data-ttu-id="a5f26-135">19. Zatwierdzania (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="a5f26-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="a5f26-137">20. Zatwierdzania (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="a5f26-138">10. Rejestr (trwałość)</span><span class="sxs-lookup"><span data-stu-id="a5f26-138">10. Register (Durable)</span></span>|<span data-ttu-id="a5f26-139">21. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="a5f26-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-140">11. RegisterResponse</span></span>|<span data-ttu-id="a5f26-141">22. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="a5f26-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="a5f26-142">Ten dokument opisuje kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="a5f26-143">Podejście opisane w tym dokumencie został przetestowany z innymi implementacjami WS-AT i WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="a5f26-144">Ilustracja i tabela przedstawiają cztery klasy wiadomości z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="a5f26-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="a5f26-145">Aktywacja wiadomości (CreateCoordinationContext CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="a5f26-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="a5f26-146">Rejestracja wiadomości (Zarejestruj się i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="a5f26-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="a5f26-147">Komunikaty protokołu (przygotowywanie, wycofywanie, zatwierdzania, Aborted i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="a5f26-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="a5f26-148">Komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-148">Application messages.</span></span>  
  
 <span data-ttu-id="a5f26-149">Pierwszej klasy trzy wiadomości są traktowane jako komunikaty Menedżera transakcji, a ich konfiguracja powiązania jest opisana w "Aplikacji wiadomości programu Exchange" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a5f26-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="a5f26-150">Czwarty klasę wiadomości jest komunikatów aplikacji i zostało opisane w sekcji "Przykłady komunikatu" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a5f26-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="a5f26-151">W tej sekcji opisano powiązania protokołu używany dla każdej z tych klas przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="a5f26-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="a5f26-152">Następujące obszary nazw XML i skojarzone prefiksy są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="a5f26-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="a5f26-153">Prefiks</span><span class="sxs-lookup"><span data-stu-id="a5f26-153">Prefix</span></span>|<span data-ttu-id="a5f26-154">Identyfikator URI Namespace</span><span class="sxs-lookup"><span data-stu-id="a5f26-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="a5f26-155">s11</span><span class="sxs-lookup"><span data-stu-id="a5f26-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="a5f26-156">wsa</span><span class="sxs-lookup"><span data-stu-id="a5f26-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="a5f26-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="a5f26-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="a5f26-158">wsat</span><span class="sxs-lookup"><span data-stu-id="a5f26-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="a5f26-159">t</span><span class="sxs-lookup"><span data-stu-id="a5f26-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="a5f26-160">o</span><span class="sxs-lookup"><span data-stu-id="a5f26-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="a5f26-161">xsd</span><span class="sxs-lookup"><span data-stu-id="a5f26-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="a5f26-162">Menedżer transakcji powiązania</span><span class="sxs-lookup"><span data-stu-id="a5f26-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="a5f26-163">R1001: Menedżerowie transakcji, należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-Atomic Transaction i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="a5f26-164">Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="a5f26-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="a5f26-165">Menedżer transakcji HTTPS powiązania</span><span class="sxs-lookup"><span data-stu-id="a5f26-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="a5f26-166">Powiązanie HTTPS Menedżera transakcji opiera się wyłącznie na zabezpieczenia transportu do osiągnięcia zabezpieczeń i ustanowienia relacji zaufania między sąsiednimi odbiorcy nadawcy w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="a5f26-167">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="a5f26-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="a5f26-168">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="a5f26-169">Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegół implementacji:</span><span class="sxs-lookup"><span data-stu-id="a5f26-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="a5f26-170">R1111: Certyfikaty X.509 przedstawione przez sieć musi mieć nazwę podmiotu, który pasuje do w pełni kwalifikowana nazwa domeny (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a5f26-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="a5f26-171">B1112: DNS musi działać każda para odbiorcy nadawcy w systemie kontroli nazwy podmiotu X.509 zakończyło się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="a5f26-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="a5f26-172">Aktywacja i powiązań konfiguracji rejestracji</span><span class="sxs-lookup"><span data-stu-id="a5f26-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="a5f26-173">Usługi WCF wymaga dwukierunkowego powiązania żądanie/nietypizowana odpowiedź z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5f26-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="a5f26-174">(Aby uzyskać więcej informacji na temat korelacji i opisy wzorców żądanie/nietypizowana odpowiedź wiadomości programu exchange, zobacz WS-Atomic Transaction, sekcja 8).</span><span class="sxs-lookup"><span data-stu-id="a5f26-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="a5f26-175">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="a5f26-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="a5f26-176">Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5f26-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="a5f26-177">Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="a5f26-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="a5f26-178">B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="a5f26-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="a5f26-179">Menedżer transakcji mieszane powiązanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a5f26-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="a5f26-180">Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używana w połączeniu z modelem usługi WS-koordynacji wystawionego tokenu potrzeby określania tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a5f26-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="a5f26-181">Aktywacja i rejestracja są tylko elementy, które różnią się między dwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="a5f26-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="a5f26-182">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="a5f26-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="a5f26-183">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="a5f26-184">Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="a5f26-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="a5f26-185">Konfiguracja powiązania komunikatów aktywacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="a5f26-186">Komunikaty o aktywacji zwykle nie uczestniczą w współdziałanie ponieważ występują najczęściej między aplikacją a swój lokalny Menedżer transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="a5f26-187">B1221: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="a5f26-188">Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="a5f26-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="a5f26-189">Specyfikacja WS-Atomic Transaction, sekcja 8 opisano dalsze szczegółowe informacje dotyczące korelacji i wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a5f26-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="a5f26-190">R1222: Odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`.</span><span class="sxs-lookup"><span data-stu-id="a5f26-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="a5f26-191">Ten token jest zwracany w `t:IssuedTokens` nagłówka następujące specyfikację WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="a5f26-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="a5f26-192">R1223: Jeśli aktywacja odbywa się w ramach istniejącego kontekstu koordynacji, `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekście musi przepływać ze `CreateCoordinationContext` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a5f26-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="a5f26-193">Nowy `t:IssuedTokens` musi zostać wygenerowany nagłówek do dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a5f26-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="a5f26-194">Konfiguracja powiązania komunikat rejestracji</span><span class="sxs-lookup"><span data-stu-id="a5f26-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="a5f26-195">B1231: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="a5f26-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="a5f26-196">Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="a5f26-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="a5f26-197">WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dalsze szczegółowe informacje o korelacji i opisy wzorców wiadomości programu exchange.</span><span class="sxs-lookup"><span data-stu-id="a5f26-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="a5f26-198">R1232: Wychodzące `wscoor:Register` wiadomości należy użyć `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="a5f26-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="a5f26-199">`wsse:Timestamp` Element musi być podpisany przy użyciu `SecurityContextToken STx` wydane.</span><span class="sxs-lookup"><span data-stu-id="a5f26-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="a5f26-200">Ta sygnatura jest dowód przesyłany tokenu skojarzone z danej transakcji i jest używany do uwierzytelniania uczestnik rejestrowanie w transakcji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="a5f26-201">RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5f26-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="a5f26-202">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="a5f26-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="a5f26-203">Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a5f26-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="a5f26-204">Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="a5f26-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="a5f26-205">B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="a5f26-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="a5f26-206">Wymiana komunikatów w aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-206">Application Message Exchange</span></span>  
 <span data-ttu-id="a5f26-207">Aplikacje są bezpłatne korzystanie z dowolnego określonego powiązania dla wiadomości w aplikacji do aplikacji, tak długo, jak wiązanie spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="a5f26-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="a5f26-208">R2001: Komunikaty aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z `CoordinationContext` w nagłówku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a5f26-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="a5f26-209">R2002: Integralności i poufności `t:IssuedToken` musi zostać podana.</span><span class="sxs-lookup"><span data-stu-id="a5f26-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="a5f26-210">`CoordinationContext` Nagłówek zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="a5f26-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="a5f26-211">Podczas gdy definicja `xsd:AnyURI` umożliwia korzystanie z identyfikatorów URI względne i bezwzględne WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględne identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="a5f26-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="a5f26-212">Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względny identyfikator URI, błędy, które zostaną zwrócone z transakcji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a5f26-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="a5f26-213">Przykłady komunikatów</span><span class="sxs-lookup"><span data-stu-id="a5f26-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="a5f26-214">Komunikatów żądań/odpowiedzi CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="a5f26-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="a5f26-215">Następujące komunikaty wykonaj wzorzec żądań/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a5f26-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="a5f26-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="a5f26-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="a5f26-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="a5f26-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="a5f26-218">Rejestracja wiadomości</span><span class="sxs-lookup"><span data-stu-id="a5f26-218">Registration Messages</span></span>  
 <span data-ttu-id="a5f26-219">Następujące komunikaty są komunikatów rejestracji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="a5f26-220">Rejestruj</span><span class="sxs-lookup"><span data-stu-id="a5f26-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="a5f26-221">Rejestrowanie odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="a5f26-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="a5f26-222">Dwóch faza zatwierdzania protokołu komunikatów</span><span class="sxs-lookup"><span data-stu-id="a5f26-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="a5f26-223">Następujący komunikat o odnosi się do Protokół dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="a5f26-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="a5f26-224">Zatwierdzenia</span><span class="sxs-lookup"><span data-stu-id="a5f26-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="a5f26-225">Komunikaty aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-225">Application Messages</span></span>  
 <span data-ttu-id="a5f26-226">Następujące komunikaty są komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5f26-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="a5f26-227">Żądanie komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="a5f26-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```

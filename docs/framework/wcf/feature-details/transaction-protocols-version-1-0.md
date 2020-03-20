---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: a19329b56bb569a04195b38877a42d635996ff1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184372"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="371a2-102">Protokoły transakcyjne wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="371a2-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="371a2-103">Windows Communication Foundation (WCF) wersja 1 implementuje wersję 1.0 protokołów WS-Atomic Transaction i WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="371a2-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="371a2-104">Aby uzyskać więcej informacji na temat wersji 1.1, zobacz [Protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="371a2-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="371a2-105">Specyfikacja/dokument</span><span class="sxs-lookup"><span data-stu-id="371a2-105">Specification/Document</span></span>|<span data-ttu-id="371a2-106">Link</span><span class="sxs-lookup"><span data-stu-id="371a2-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="371a2-107">Koordynacja WS</span><span class="sxs-lookup"><span data-stu-id="371a2-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="371a2-108">WS-AtomicTransakcja</span><span class="sxs-lookup"><span data-stu-id="371a2-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="371a2-109">Interoperacyjność tych specyfikacji protokołu jest wymagana na dwóch poziomach: między aplikacjami i między menedżerami transakcji (patrz poniższy rysunek).</span><span class="sxs-lookup"><span data-stu-id="371a2-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="371a2-110">Specyfikacje opisują bardzo szczegółowo formaty wiadomości i wymiany wiadomości dla obu poziomów interoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="371a2-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="371a2-111">Niektóre zabezpieczenia, niezawodność i kodowania dla wymiany aplikacji do aplikacji mają zastosowanie, jak to zrobić dla regularnej wymiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="371a2-112">Jednak pomyślna interoperacyjność między menedżerami transakcji wymaga porozumienia w sprawie określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="371a2-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="371a2-113">W tym temacie opisano skład specyfikacji transakcji WS-Atomic (WS-AT) z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="371a2-114">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-Coordination, w tym IBM, IONA, Sun Microsystems i innymi.</span><span class="sxs-lookup"><span data-stu-id="371a2-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="371a2-115">Poniższy rysunek przedstawia interoperacyjność między dwoma menedżerami transakcji, Menedżer transakcji 1 i Menedżer transakcji 2, i dwie aplikacje, Application 1 i Application 2:</span><span class="sxs-lookup"><span data-stu-id="371a2-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Zrzut ekranu przedstawiający interakcję między menedżerami transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="371a2-117">Należy wziąć pod uwagę typowy scenariusz WS-Koordynacja/WS-Atomic transaction z jednym inicjatorem (I) i jeden uczestnik (P).</span><span class="sxs-lookup"><span data-stu-id="371a2-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="371a2-118">Zarówno inicjator, jak i uczestnik mają menedżerów transakcji (odpowiednio ITM i PTM).</span><span class="sxs-lookup"><span data-stu-id="371a2-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="371a2-119">Zatwierdzanie dwufazowe jest określane jako 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="371a2-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="371a2-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="371a2-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="371a2-121">12. Odpowiedź na wiadomość aplikacji</span><span class="sxs-lookup"><span data-stu-id="371a2-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="371a2-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="371a2-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="371a2-123">13. Zatwierdzenie (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="371a2-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="371a2-124">3. Zarejestruj się (Zakończenie)</span><span class="sxs-lookup"><span data-stu-id="371a2-124">3. Register (Completion)</span></span>|<span data-ttu-id="371a2-125">14. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="371a2-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="371a2-126">4. RegisterResponse</span></span>|<span data-ttu-id="371a2-127">15. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="371a2-128">5. Komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="371a2-128">5. Application Message</span></span>|<span data-ttu-id="371a2-129">16. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="371a2-130">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="371a2-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="371a2-131">17. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="371a2-132">7. Zarejestruj się (trwały)</span><span class="sxs-lookup"><span data-stu-id="371a2-132">7. Register (Durable)</span></span>|<span data-ttu-id="371a2-133">18. Popełnione (Zakończenie)</span><span class="sxs-lookup"><span data-stu-id="371a2-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="371a2-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="371a2-134">8. RegisterResponse</span></span>|<span data-ttu-id="371a2-135">19. Zatwierdzenie (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="371a2-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="371a2-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="371a2-137">20. Zatwierdzenie (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="371a2-138">10. Zarejestruj się (trwały)</span><span class="sxs-lookup"><span data-stu-id="371a2-138">10. Register (Durable)</span></span>|<span data-ttu-id="371a2-139">21. Popełnione (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="371a2-140">11. RejestracjaOdpowiedzialność</span><span class="sxs-lookup"><span data-stu-id="371a2-140">11. RegisterResponse</span></span>|<span data-ttu-id="371a2-141">22. Popełnione (2PC)</span><span class="sxs-lookup"><span data-stu-id="371a2-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="371a2-142">W tym dokumencie opisano skład specyfikacji WS-AtomicTransaction z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="371a2-143">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="371a2-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="371a2-144">Rysunek i tabela ilustrują cztery klasy wiadomości z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="371a2-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="371a2-145">Komunikaty aktywacji (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="371a2-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="371a2-146">Komunikaty rejestracyjne (Zarejestruj się i ZarejestrujOdpowiedzialność)</span><span class="sxs-lookup"><span data-stu-id="371a2-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="371a2-147">Komunikaty protokołu (Przygotowanie, Wycofywanie, Zatwierdzanie, Przerwane i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="371a2-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="371a2-148">Komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-148">Application messages.</span></span>  
  
 <span data-ttu-id="371a2-149">Pierwsze trzy klasy wiadomości są uważane za komunikaty Menedżera transakcji, a ich konfiguracja powiązania jest opisana w "Application Message Exchange" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="371a2-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="371a2-150">Czwarta klasa wiadomości jest aplikacją do komunikatów aplikacji i jest opisana w sekcji "Przykłady wiadomości" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="371a2-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="371a2-151">W tej sekcji opisano powiązania protokołu używane dla każdej z tych klas przez WCF.</span><span class="sxs-lookup"><span data-stu-id="371a2-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="371a2-152">W całym tym dokumencie używane są następujące obszary nazw XML i skojarzone z nimi prefiksy.</span><span class="sxs-lookup"><span data-stu-id="371a2-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="371a2-153">Prefiks</span><span class="sxs-lookup"><span data-stu-id="371a2-153">Prefix</span></span>|<span data-ttu-id="371a2-154">Identyfikator URI obszaru nazw</span><span class="sxs-lookup"><span data-stu-id="371a2-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="371a2-155">s11</span><span class="sxs-lookup"><span data-stu-id="371a2-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="371a2-156">Wsa</span><span class="sxs-lookup"><span data-stu-id="371a2-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="371a2-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="371a2-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="371a2-158">wsat</span><span class="sxs-lookup"><span data-stu-id="371a2-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="371a2-159">t</span><span class="sxs-lookup"><span data-stu-id="371a2-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="371a2-160">o</span><span class="sxs-lookup"><span data-stu-id="371a2-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="371a2-161">Xsd</span><span class="sxs-lookup"><span data-stu-id="371a2-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="371a2-162">Powiązania menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="371a2-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="371a2-163">R1001: Menedżerowie transakcji muszą używać protokołu SOAP 1.1 i WS-Addressing 2004/08 dla wymiany komunikatów WS-Atomic i WS-Coordination.</span><span class="sxs-lookup"><span data-stu-id="371a2-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="371a2-164">Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane później.</span><span class="sxs-lookup"><span data-stu-id="371a2-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="371a2-165">Powiązanie HTTPS menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="371a2-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="371a2-166">Powiązanie HTTPS menedżera transakcji opiera się wyłącznie na zabezpieczeniach transportu, aby osiągnąć bezpieczeństwo i ustanowić zaufanie między każdą parą nadawca-odbiorca w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="371a2-167">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="371a2-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="371a2-168">Certyfikaty X.509 są używane do ustanawiania tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="371a2-169">Uwierzytelnianie klient/serwer jest wymagane, a autoryzacja klient/serwer pozostaje jako szczegóły implementacji:</span><span class="sxs-lookup"><span data-stu-id="371a2-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="371a2-170">R1111: Certyfikaty X.509 prezentowane za jego przewodowo muszą mieć nazwę podmiotu odpowiadającą w pełni kwalifikowanej nazwie domeny (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="371a2-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="371a2-171">B1112: System DNS musi działać między każdą parą nadawca-odbiorca w systemie, aby sprawdzanie nazwy podmiotu X.509 zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="371a2-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="371a2-172">Konfiguracja wiązania aktywacji i rejestracji</span><span class="sxs-lookup"><span data-stu-id="371a2-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="371a2-173">WCF wymaga żądania/odpowiedzi powiązania dupleksu z korelacji za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="371a2-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="371a2-174">(Aby uzyskać więcej informacji na temat korelacji i opisów wzorców wymiany komunikatów żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8.)</span><span class="sxs-lookup"><span data-stu-id="371a2-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="371a2-175">Konfiguracja wiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="371a2-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="371a2-176">WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="371a2-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="371a2-177">Korelacja między wiadomościami pozostaje jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="371a2-178">B2131: Implementacje `wsa:ReferenceParameters` muszą obsługiwać zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC WCF.</span><span class="sxs-lookup"><span data-stu-id="371a2-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="371a2-179">Mieszane powiązanie zabezpieczeń menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="371a2-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="371a2-180">Jest to powiązanie alternatywne (tryb mieszany), który używa zabezpieczeń transportu w połączeniu z modelem tokenu wystawionego przez ws-koordynacji dla celów ustanowienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="371a2-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="371a2-181">Aktywacja i rejestracja są tylko elementy, które różnią się między dwoma powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="371a2-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="371a2-182">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="371a2-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="371a2-183">Certyfikaty X.509 są używane do ustanawiania tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="371a2-184">Uwierzytelnianie klient/serwer jest wymagane, a autoryzacja klient/serwer pozostaje jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="371a2-185">Konfiguracja wiązania komunikatu aktywacji</span><span class="sxs-lookup"><span data-stu-id="371a2-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="371a2-186">Komunikaty aktywacji zwykle nie uczestniczą w współdziałania, ponieważ zazwyczaj występują między aplikacją a jej lokalnym Menedżerem transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="371a2-187">B1221: WCF używa dupleksu powiązania HTTPS (opisane w [protokołach wiadomości)](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)dla komunikatów aktywacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="371a2-188">Żądania i odpowiedz wiadomości są skorelowane przy użyciu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="371a2-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="371a2-189">Specyfikacja transakcji WS-Atomic, sekcja 8, opisuje dalsze szczegóły dotyczące korelacji i wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="371a2-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="371a2-190">R1222: Po otrzymaniu `CreateCoordinationContext`, koordynator musi `SecurityContextToken` wydać z `STx`powiązanym kluczem tajemnicy .</span><span class="sxs-lookup"><span data-stu-id="371a2-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="371a2-191">Ten token jest `t:IssuedTokens` zwracany wewnątrz nagłówka zgodnie ze specyfikacją WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="371a2-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="371a2-192">R1223: Jeśli aktywacja występuje w `t:IssuedTokens` istniejącym `SecurityContextToken` kontekście koordynacji, nagłówek `CreateCoordinationContext` z skojarzonym z istniejącym kontekstem musi przepływać w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="371a2-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="371a2-193">Nowy `t:IssuedTokens` nagłówek powinien zostać wygenerowany do `wscoor:CreateCoordinationContextResponse` dołączania do wiadomości wychodzącej.</span><span class="sxs-lookup"><span data-stu-id="371a2-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="371a2-194">Konfiguracja powiązania wiadomości rejestracji</span><span class="sxs-lookup"><span data-stu-id="371a2-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="371a2-195">B1231: WCF używa powiązania HTTPS dwustronnego (opisanego w [protokołach wiadomości).](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)</span><span class="sxs-lookup"><span data-stu-id="371a2-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="371a2-196">Żądania i odpowiedz wiadomości są skorelowane przy użyciu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="371a2-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="371a2-197">WS-AtomicTransaction, Sekcja 8, opisuje dalsze szczegóły dotyczące korelacji i opisy wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="371a2-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="371a2-198">R1232: `wscoor:Register` Wiadomości wychodzące `IssuedTokenOverTransport` muszą korzystać z trybu uwierzytelniania opisanego w [protokołach zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="371a2-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="371a2-199">Element `wsse:Timestamp` musi być podpisany `SecurityContextToken STx` przy użyciu wystawione.</span><span class="sxs-lookup"><span data-stu-id="371a2-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="371a2-200">Ten podpis jest dowodem posiadania tokenu skojarzonego z określoną transakcją i jest używany do uwierzytelniania uczestnika rejestrowania w transakcji.</span><span class="sxs-lookup"><span data-stu-id="371a2-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="371a2-201">Komunikat RegistrationResponse jest wysyłany z powrotem za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="371a2-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="371a2-202">Konfiguracja wiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="371a2-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="371a2-203">WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="371a2-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="371a2-204">Korelacja między wiadomościami pozostaje jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="371a2-205">B2131: Implementacje `wsa:ReferenceParameters` muszą obsługiwać zgodnie z opisem w WS-Addressing, aby osiągnąć korelację komunikatów 2PC WCF.</span><span class="sxs-lookup"><span data-stu-id="371a2-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="371a2-206">Wymiana komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="371a2-206">Application Message Exchange</span></span>  
 <span data-ttu-id="371a2-207">Aplikacje mogą używać dowolnego szczególnego powiązania dla komunikatów aplikacji do aplikacji, o ile powiązanie spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="371a2-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="371a2-208">R2001: Komunikaty aplikacji do aplikacji `t:IssuedTokens` muszą przepływać nagłówek wraz z `CoordinationContext` nagłówkiem wiadomości.</span><span class="sxs-lookup"><span data-stu-id="371a2-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="371a2-209">R2002: Należy zapewnić `t:IssuedToken` integralność i poufność.</span><span class="sxs-lookup"><span data-stu-id="371a2-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="371a2-210">Nagłówek `CoordinationContext` zawiera `wscoor:Identifier`plik .</span><span class="sxs-lookup"><span data-stu-id="371a2-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="371a2-211">Podczas gdy `xsd:AnyURI` definicja pozwala na użycie zarówno bezwzględnych, jak `wscoor:Identifiers`i względnych identyfikatorów URI, WCF obsługuje tylko , które są bezwzględnymi identyfikatorami URI.</span><span class="sxs-lookup"><span data-stu-id="371a2-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="371a2-212">Jeśli `wscoor:Identifier` jest `wscoor:CoordinationContext` względny identyfikator URI, błędy zostaną zwrócone z transakcyjnych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="371a2-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="371a2-213">Przykłady wiadomości</span><span class="sxs-lookup"><span data-stu-id="371a2-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="371a2-214">CreateCoordinationContext Wiadomości żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="371a2-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="371a2-215">Następujące komunikaty wykonaj wzorzec żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="371a2-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="371a2-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="371a2-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="371a2-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="371a2-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="371a2-218">Komunikaty rejestracyjne</span><span class="sxs-lookup"><span data-stu-id="371a2-218">Registration Messages</span></span>  
 <span data-ttu-id="371a2-219">Następujące komunikaty są komunikaty rejestracyjne.</span><span class="sxs-lookup"><span data-stu-id="371a2-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="371a2-220">Zarejestruj</span><span class="sxs-lookup"><span data-stu-id="371a2-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="371a2-221">Zarejestruj odpowiedź</span><span class="sxs-lookup"><span data-stu-id="371a2-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="371a2-222">Komunikaty protokołu zatwierdzania dwufazowego</span><span class="sxs-lookup"><span data-stu-id="371a2-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="371a2-223">Poniższy komunikat odnosi się do protokołu zatwierdzania dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="371a2-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="371a2-224">Zatwierdzenie</span><span class="sxs-lookup"><span data-stu-id="371a2-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="371a2-225">Komunikaty aplikacji</span><span class="sxs-lookup"><span data-stu-id="371a2-225">Application Messages</span></span>  
 <span data-ttu-id="371a2-226">Następujące komunikaty są komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="371a2-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="371a2-227">Żądanie komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="371a2-227">Application message-Request</span></span>  
  
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

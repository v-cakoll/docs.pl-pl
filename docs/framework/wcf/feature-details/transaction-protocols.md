---
title: Protokoły transakcji
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 60b9da567e8c82edf505a974c9884f6f1738747b
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066247"
---
# <a name="transaction-protocols"></a><span data-ttu-id="17de3-102">Protokoły transakcji</span><span class="sxs-lookup"><span data-stu-id="17de3-102">Transaction Protocols</span></span>
<span data-ttu-id="17de3-103">Windows Communication Foundation (WCF) implementuje usługi WS-Atomic Transaction i WS-koordynacji protokoły.</span><span class="sxs-lookup"><span data-stu-id="17de3-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="17de3-104">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="17de3-104">Specification/Document</span></span>|<span data-ttu-id="17de3-105">Wersja</span><span class="sxs-lookup"><span data-stu-id="17de3-105">Version</span></span>|<span data-ttu-id="17de3-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="17de3-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="17de3-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="17de3-107">WS-Coordination</span></span>|<span data-ttu-id="17de3-108">1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-108">1.0</span></span><br /><br /> <span data-ttu-id="17de3-109">1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-109">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96104](https://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="17de3-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="17de3-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="17de3-111">1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-111">1.0</span></span><br /><br /> <span data-ttu-id="17de3-112">1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-112">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> https://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="17de3-113">Współdziałanie w specyfikacji protokołu jest wymagany na dwóch poziomach: między aplikacjami i między menedżerowie transakcji (patrz poniższy rysunek).</span><span class="sxs-lookup"><span data-stu-id="17de3-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="17de3-114">Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="17de3-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="17de3-115">Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie jak w przypadku regularnego aplikacji programu exchange.</span><span class="sxs-lookup"><span data-stu-id="17de3-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="17de3-116">Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy w określonym powiązaniu, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="17de3-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="17de3-117">W tym temacie opisuje kompozycję specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="17de3-118">Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacji m.in. IBM IONA, Sun Microsystems i inne.</span><span class="sxs-lookup"><span data-stu-id="17de3-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="17de3-119">Na poniższym rysunku przedstawiono współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje, aplikacja 1 i 2 w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="17de3-120">![Protokoły transakcji](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="17de3-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="17de3-121">Należy rozważyć typowy scenariusz protokołu WS-koordynacji/WS-Atomic Transaction za pomocą jednego inicjatora (I) i jednego uczestnika (P).</span><span class="sxs-lookup"><span data-stu-id="17de3-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="17de3-122">Inicjator i uczestnika, który ma menedżerowie transakcji (ITM i PTM, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="17de3-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="17de3-123">Dwufazowego, jest nazywana 2PC, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="17de3-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17de3-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="17de3-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="17de3-125">12. Odpowiedź komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="17de3-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="17de3-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="17de3-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="17de3-127">13. Zatwierdź (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="17de3-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="17de3-128">3. Rejestr (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="17de3-128">3. Register (Completion)</span></span>|<span data-ttu-id="17de3-129">14. Przygotowywanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="17de3-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="17de3-130">4. RegisterResponse</span></span>|<span data-ttu-id="17de3-131">15. Przygotowywanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="17de3-132">5. Komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="17de3-132">5. Application Message</span></span>|<span data-ttu-id="17de3-133">16. Przygotowany (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="17de3-134">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="17de3-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="17de3-135">17. Przygotowany (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="17de3-136">7. Rejestr (trwałość)</span><span class="sxs-lookup"><span data-stu-id="17de3-136">7. Register (Durable)</span></span>|<span data-ttu-id="17de3-137">18. Zatwierdzone (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="17de3-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="17de3-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="17de3-138">8. RegisterResponse</span></span>|<span data-ttu-id="17de3-139">19. Zatwierdzania (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="17de3-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="17de3-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="17de3-141">20. Zatwierdzania (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="17de3-142">10. Rejestr (trwałość)</span><span class="sxs-lookup"><span data-stu-id="17de3-142">10. Register (Durable)</span></span>|<span data-ttu-id="17de3-143">21. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="17de3-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="17de3-144">11. RegisterResponse</span></span>|<span data-ttu-id="17de3-145">22. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="17de3-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="17de3-146">Ten dokument opisuje kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerowie transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="17de3-147">Podejście opisane w tym dokumencie został przetestowany z innymi implementacjami WS-AT i WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="17de3-148">Ilustracja i tabela przedstawiają cztery klasy wiadomości z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="17de3-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="17de3-149">Aktywacja wiadomości (CreateCoordinationContext CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="17de3-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="17de3-150">Rejestracja wiadomości (Zarejestruj się i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="17de3-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="17de3-151">Komunikaty protokołu (przygotowywanie, wycofywanie, zatwierdzania, Aborted i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="17de3-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="17de3-152">Komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-152">Application messages.</span></span>  
  
 <span data-ttu-id="17de3-153">Pierwszej klasy trzy wiadomości są traktowane jako komunikaty Menedżera transakcji, a ich konfiguracja powiązania jest opisana w "Aplikacji wiadomości programu Exchange" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="17de3-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="17de3-154">Czwarty klasę wiadomości jest komunikatów aplikacji i zostało opisane w sekcji "Przykłady komunikatu" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="17de3-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="17de3-155">W tej sekcji opisano powiązania protokołu używany dla każdej z tych klas przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="17de3-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="17de3-156">Następujące obszary nazw XML i skojarzone prefiksy są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="17de3-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="17de3-157">Prefiks</span><span class="sxs-lookup"><span data-stu-id="17de3-157">Prefix</span></span>|<span data-ttu-id="17de3-158">Wersja</span><span class="sxs-lookup"><span data-stu-id="17de3-158">Version</span></span>|<span data-ttu-id="17de3-159">Identyfikator URI Namespace</span><span class="sxs-lookup"><span data-stu-id="17de3-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="17de3-160">s11</span><span class="sxs-lookup"><span data-stu-id="17de3-160">s11</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96014](https://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="17de3-161">wsa</span><span class="sxs-lookup"><span data-stu-id="17de3-161">wsa</span></span>|<span data-ttu-id="17de3-162">Wstępnie 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="17de3-163">1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96022](https://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="17de3-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="17de3-164">wscoor</span></span>|<span data-ttu-id="17de3-165">1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-165">1.0</span></span><br /><br /> <span data-ttu-id="17de3-166">1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-166">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96078](https://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96079](https://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="17de3-167">wsat</span><span class="sxs-lookup"><span data-stu-id="17de3-167">wsat</span></span>|<span data-ttu-id="17de3-168">1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-168">1.0</span></span><br /><br /> <span data-ttu-id="17de3-169">1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-169">1.1</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96080](https://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96081](https://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="17de3-170">t</span><span class="sxs-lookup"><span data-stu-id="17de3-170">t</span></span>|<span data-ttu-id="17de3-171">Pre 1.3</span><span class="sxs-lookup"><span data-stu-id="17de3-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="17de3-172">1.3</span><span class="sxs-lookup"><span data-stu-id="17de3-172">1.3</span></span>|[https://go.microsoft.com/fwlink/?LinkId=96082](https://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [https://go.microsoft.com/fwlink/?LinkId=96100](https://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="17de3-173">o</span><span class="sxs-lookup"><span data-stu-id="17de3-173">o</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96101](https://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="17de3-174">xsd</span><span class="sxs-lookup"><span data-stu-id="17de3-174">xsd</span></span>||[https://go.microsoft.com/fwlink/?LinkId=96102](https://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="17de3-175">Menedżer transakcji powiązania</span><span class="sxs-lookup"><span data-stu-id="17de3-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="17de3-176">R1001: Menedżerowie transakcji udział w transakcji WS-AT 1.0, musisz użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-Atomic Transaction i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="17de3-177">R1002: Menedżerowie transakcji udział w transakcji WS-AT 1.1, należy użyć protokołu SOAP 1.1 i WS-Addressing 2005/08 dla protokołu WS-Atomic Transaction i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="17de3-178">Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="17de3-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="17de3-179">Menedżer transakcji HTTPS powiązania</span><span class="sxs-lookup"><span data-stu-id="17de3-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="17de3-180">Powiązanie HTTPS Menedżera transakcji opiera się wyłącznie na zabezpieczenia transportu do osiągnięcia zabezpieczeń i ustanowienia relacji zaufania między sąsiednimi odbiorcy nadawcy w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="17de3-181">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="17de3-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="17de3-182">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="17de3-183">Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegół implementacji:</span><span class="sxs-lookup"><span data-stu-id="17de3-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="17de3-184">R1111: Certyfikaty X.509 przedstawione przez sieć musi mieć nazwę podmiotu, który pasuje do w pełni kwalifikowana nazwa domeny (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="17de3-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="17de3-185">B1112: DNS musi działać każda para odbiorcy nadawcy w systemie kontroli nazwy podmiotu X.509 zakończyło się sukcesem.</span><span class="sxs-lookup"><span data-stu-id="17de3-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="17de3-186">Aktywacja i powiązań konfiguracji rejestracji</span><span class="sxs-lookup"><span data-stu-id="17de3-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="17de3-187">Usługi WCF wymaga dwukierunkowego powiązania żądanie/nietypizowana odpowiedź z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="17de3-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="17de3-188">(Aby uzyskać więcej informacji na temat korelacji i opisy wzorców żądanie/nietypizowana odpowiedź wiadomości programu exchange, zobacz WS-Atomic Transaction, sekcja 8).</span><span class="sxs-lookup"><span data-stu-id="17de3-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="17de3-189">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="17de3-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="17de3-190">Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="17de3-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="17de3-191">Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="17de3-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="17de3-192">B1131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="17de3-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="17de3-193">Menedżer transakcji mieszane powiązanie zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="17de3-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="17de3-194">Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używana w połączeniu z modelem usługi WS-koordynacji wystawionego tokenu potrzeby określania tożsamości.</span><span class="sxs-lookup"><span data-stu-id="17de3-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="17de3-195">Aktywacja i rejestracja są tylko elementy, które różnią się między dwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="17de3-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="17de3-196">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="17de3-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="17de3-197">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="17de3-198">Wymagane jest uwierzytelnienie klienta/serwera i klienta/serwera autoryzacji zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="17de3-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="17de3-199">Konfiguracja powiązania komunikatów aktywacji</span><span class="sxs-lookup"><span data-stu-id="17de3-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="17de3-200">Komunikaty o aktywacji zwykle nie uczestniczą w współdziałanie ponieważ występują najczęściej między aplikacją a swój lokalny Menedżer transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="17de3-201">B1221: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="17de3-202">Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="17de3-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="17de3-203">Specyfikacja WS-Atomic Transaction, sekcja 8 opisano dalsze szczegółowe informacje dotyczące korelacji i wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="17de3-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="17de3-204">R1222: Odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`.</span><span class="sxs-lookup"><span data-stu-id="17de3-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="17de3-205">Ten token jest zwracany w `t:IssuedTokens` nagłówka następujące specyfikację WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="17de3-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="17de3-206">R1223: Jeśli aktywacja odbywa się w ramach istniejącego kontekstu koordynacji, `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekście musi przepływać ze `CreateCoordinationContext` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="17de3-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="17de3-207">Nowy `t:IssuedTokens` musi zostać wygenerowany nagłówek do dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="17de3-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="17de3-208">Konfiguracja powiązania komunikat rejestracji</span><span class="sxs-lookup"><span data-stu-id="17de3-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="17de3-209">B1231: Dwukierunkowego powiązania HTTPS korzysta z usługi WCF (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="17de3-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="17de3-210">Skorelowane żądanie i odpowiedź przy użyciu usługi WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 WS-AT 1.1.</span><span class="sxs-lookup"><span data-stu-id="17de3-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="17de3-211">WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dalsze szczegółowe informacje o korelacji i opisy wzorców wiadomości programu exchange.</span><span class="sxs-lookup"><span data-stu-id="17de3-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="17de3-212">R1232: Wychodzące `wscoor:Register` wiadomości należy użyć `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="17de3-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="17de3-213">`wsse:Timestamp` Element musi być podpisany przy użyciu `SecurityContextToken STx` wydane.</span><span class="sxs-lookup"><span data-stu-id="17de3-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="17de3-214">Ta sygnatura jest dowód przesyłany tokenu skojarzone z danej transakcji i jest używany do uwierzytelniania uczestnik rejestrowanie w transakcji.</span><span class="sxs-lookup"><span data-stu-id="17de3-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="17de3-215">RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="17de3-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="17de3-216">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="17de3-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="17de3-217">Usługi WCF obsługuje wiadomości jednokierunkowe (datagram) przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="17de3-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="17de3-218">Korelacja między wiadomości zostanie pozostawiony jako szczegółowo opisuje implementacja.</span><span class="sxs-lookup"><span data-stu-id="17de3-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="17de3-219">B1241: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="17de3-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="17de3-220">Wymiana komunikatów w aplikacji</span><span class="sxs-lookup"><span data-stu-id="17de3-220">Application Message Exchange</span></span>  
 <span data-ttu-id="17de3-221">Aplikacje są bezpłatne korzystanie z dowolnego określonego powiązania dla wiadomości w aplikacji do aplikacji, tak długo, jak wiązanie spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="17de3-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="17de3-222">R2001: Komunikaty aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z `CoordinationContext` w nagłówku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="17de3-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="17de3-223">R2002: Integralności i poufności `t:IssuedToken` musi zostać podana.</span><span class="sxs-lookup"><span data-stu-id="17de3-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="17de3-224">`CoordinationContext` Nagłówek zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="17de3-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="17de3-225">Podczas gdy definicja `xsd:AnyURI` umożliwia korzystanie z identyfikatorów URI względne i bezwzględne WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględne identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="17de3-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="17de3-226">B2003: Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względny identyfikator URI, błędy, które zostaną zwrócone z transakcji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="17de3-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="17de3-227">Przykłady komunikatów</span><span class="sxs-lookup"><span data-stu-id="17de3-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="17de3-228">Komunikatów żądań/odpowiedzi CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="17de3-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="17de3-229">Następujące komunikaty wykonaj wzorzec żądań/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="17de3-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="17de3-230">CreateCoordinationContext z WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="17de3-231">CreateCoordinationContext z WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>   
<s:Header>  
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContext</Action>  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="17de3-232">CreateCoordinationContextResponse zaufania Pre-1.3 i WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="17de3-233">CreateCoordinationContextResponse Trust 1.3 i WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<!-- Data below is shown in the clear for illustration purposes only. -->   
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/CreateCoordinationContextResponse </a:Action>  
<a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
<a:To s:mustUnderstand="1">https://... </a:To>   
<t:IssuedTokens>   
<wst:RequestSecurityTokenResponse   
xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"   
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
xmlns:wst="http://docs.oasis-open.org/ws-sx/ws-trust/200512"  
xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
<wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
<wst:RequestedSecurityToken>   
<wsc:SecurityContextToken>   
<wssu:Identifier> http://fabrikam123.com/SCTi  
</wssu:Identifier>   
</wsc:SecurityContextToken>   
</wst:RequestedSecurityToken>   
<wsp:AppliesTo> http://fabrikam123.com/CCi </wsp:AppliesTo>  
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
  Type="http://docs.oasis-open.org/ws-sx/ws-trust/200512/SymmetricKey">  
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
<wscoor:Identifier> http://fabrikam123.com/CCi  
</wscoor:Identifier>   
<wscoor:Expires>...</wscoor:Expires>  
<wscoor:CoordinationType>...</wscoor:CoordinationType>  
<wscoor:RegistrationService>   
<a:Address>https://...</a:Address>  
<a:ReferenceParameters> ...  
</a:ReferenceParameters>  
</wscoor:RegistrationService>   
</wscoor:CoordinationContext>   
</wscoor:CreateCoordinationContextResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="17de3-234">Rejestracja wiadomości</span><span class="sxs-lookup"><span data-stu-id="17de3-234">Registration Messages</span></span>  
 <span data-ttu-id="17de3-235">Następujące komunikaty są komunikatów rejestracji.</span><span class="sxs-lookup"><span data-stu-id="17de3-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="17de3-236">Zarejestrowanie WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="17de3-237">Zarejestrowanie WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-237">Register with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wscoor/2006/06/Register</a:Action>   
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
<wssu:Identifier> http://fabrikam123.com/SCTi  
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
<ds:DigestMethod  
Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>   
<ds:DigestValue> alRzyhjLgoUOYoh8cx4n75eTcUk=  
</ds:DigestValue>   
</ds:Reference>   
</ds:SignedInfo>  
<ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=  
</ds:SignatureValue>  
<ds:KeyInfo>   
<wsse:SecurityTokenReference xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
  <wsse:Reference URI="http://fabrikam123.com/SCTi"/>  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="17de3-238">Zarejestrowanie odpowiedzi WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="17de3-239">Zarejestrowanie odpowiedzi WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-239">Register Response with WSCoor 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action> http://docs.oasis-open.org/ws-tx/wscoor/2006/06/RegisterResponse  
</a:Action>   
<a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
<a:RelatesTo> urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e </a:RelatesTo>  
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
<a:ReferenceParameters> ... </a:ReferenceParameters>  
</wscoor:CoordinatorProtocolService>   
</wscoor:RegisterResponse>   
</s:Body>   
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="17de3-240">Dwóch faza zatwierdzania protokołu komunikatów</span><span class="sxs-lookup"><span data-stu-id="17de3-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="17de3-241">Następujący komunikat o odnosi się do Protokół dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="17de3-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="17de3-242">Zatwierdź z WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="17de3-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="17de3-243">Zatwierdź z WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="17de3-243">Commit with WSAT 1.1</span></span>  
  
```xml  
<s:Envelope>  
<s:Header>   
<a:Action>http://docs.oasis-open.org/ws-tx/wsat/2006/06</a:Action>  
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
  
### <a name="application-messages"></a><span data-ttu-id="17de3-244">Komunikaty aplikacji</span><span class="sxs-lookup"><span data-stu-id="17de3-244">Application Messages</span></span>  
 <span data-ttu-id="17de3-245">Następujące komunikaty są komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17de3-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="17de3-246">Żądanie komunikatu aplikacji</span><span class="sxs-lookup"><span data-stu-id="17de3-246">Application message-Request</span></span>  
  
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

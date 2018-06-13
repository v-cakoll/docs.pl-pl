---
title: Protokoły transakcji
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 8841a9cf414ae94da7e63bd7312a3c541ab6de1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508445"
---
# <a name="transaction-protocols"></a><span data-ttu-id="e395f-102">Protokoły transakcji</span><span class="sxs-lookup"><span data-stu-id="e395f-102">Transaction Protocols</span></span>
<span data-ttu-id="e395f-103">Windows Communication Foundation (WCF) implementuje usługi WS-Atomic Transaction i koordynacji WS protokoły.</span><span class="sxs-lookup"><span data-stu-id="e395f-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="e395f-104">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="e395f-104">Specification/Document</span></span>|<span data-ttu-id="e395f-105">Wersja</span><span class="sxs-lookup"><span data-stu-id="e395f-105">Version</span></span>|<span data-ttu-id="e395f-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="e395f-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="e395f-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="e395f-107">WS-Coordination</span></span>|<span data-ttu-id="e395f-108">1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-108">1.0</span></span><br /><br /> <span data-ttu-id="e395f-109">1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-109">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96104](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="e395f-110">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="e395f-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="e395f-111">1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-111">1.0</span></span><br /><br /> <span data-ttu-id="e395f-112">1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-112">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> http://go.microsoft.com/fwlink/?LinkId=96081|  
  
 <span data-ttu-id="e395f-113">Współdziałanie z tymi specyfikacjami protokołu jest wymagany na dwa poziomy: między aplikacjami i między menedżerowie transakcji (zobacz poniższą ilustrację).</span><span class="sxs-lookup"><span data-stu-id="e395f-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="e395f-114">Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="e395f-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="e395f-115">Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie tak samo, jak dla programu exchange regularne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="e395f-116">Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy dla określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e395f-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="e395f-117">W tym temacie opisuje kompozycji specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e395f-118">Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS tym IBM, IONA Sun Microsystems i inne.</span><span class="sxs-lookup"><span data-stu-id="e395f-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="e395f-119">Na poniższym rysunku przedstawiono współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje aplikacji 1 i 2 aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="e395f-120">![Protokoły transakcji](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="e395f-120">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="e395f-121">Należy wziąć pod uwagę typowy scenariusz WS-koordynacji/protokołu WS-AT z jednego inicjatora (I) i jednego uczestnika (P).</span><span class="sxs-lookup"><span data-stu-id="e395f-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="e395f-122">Inicjator i uczestnika ma menedżerowie transakcji (ITM i PTM, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="e395f-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="e395f-123">Dwufazowe nazywa się 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="e395f-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e395f-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="e395f-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="e395f-125">12. Odpowiedzi na komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="e395f-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="e395f-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e395f-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e395f-127">13. Zatwierdź (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="e395f-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="e395f-128">3. Rejestr (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="e395f-128">3. Register (Completion)</span></span>|<span data-ttu-id="e395f-129">14. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e395f-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e395f-130">4. RegisterResponse</span></span>|<span data-ttu-id="e395f-131">15. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="e395f-132">5. Komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="e395f-132">5. Application Message</span></span>|<span data-ttu-id="e395f-133">16. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e395f-134">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="e395f-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="e395f-135">17. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="e395f-136">7. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="e395f-136">7. Register (Durable)</span></span>|<span data-ttu-id="e395f-137">18. Zatwierdzone (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="e395f-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="e395f-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e395f-138">8. RegisterResponse</span></span>|<span data-ttu-id="e395f-139">19. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="e395f-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="e395f-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="e395f-141">20. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="e395f-142">10. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="e395f-142">10. Register (Durable)</span></span>|<span data-ttu-id="e395f-143">21. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="e395f-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="e395f-144">11. RegisterResponse</span></span>|<span data-ttu-id="e395f-145">22. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="e395f-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="e395f-146">Ten dokument opisuje kompozycji specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="e395f-147">Podejście opisane w tym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS.</span><span class="sxs-lookup"><span data-stu-id="e395f-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="e395f-148">Ilustracja i tabela przedstawiono cztery rodzaje komunikaty z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="e395f-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="e395f-149">Aktywacja wiadomości (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="e395f-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="e395f-150">Rejestracja wiadomości (rejestr i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="e395f-150">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="e395f-151">Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzania, przerwane i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="e395f-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="e395f-152">Komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-152">Application messages.</span></span>  
  
 <span data-ttu-id="e395f-153">Pierwszy klas trzy wiadomości są traktowane jako wiadomości Menedżera transakcji i ich konfiguracja powiązania jest opisany w "Wymianie wiadomości aplikacji" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e395f-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="e395f-154">Czwarty klasę wiadomości jest komunikatów aplikacji i jest opisana w sekcji "Komunikat przykłady" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e395f-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="e395f-155">W tej sekcji opisano powiązania protokołu używane dla każdego z tych klas przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="e395f-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="e395f-156">Następujące obszary nazw XML i prefiksy skojarzone są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="e395f-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="e395f-157">Prefiks</span><span class="sxs-lookup"><span data-stu-id="e395f-157">Prefix</span></span>|<span data-ttu-id="e395f-158">Wersja</span><span class="sxs-lookup"><span data-stu-id="e395f-158">Version</span></span>|<span data-ttu-id="e395f-159">Identyfikator URI Namespace</span><span class="sxs-lookup"><span data-stu-id="e395f-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="e395f-160">s11</span><span class="sxs-lookup"><span data-stu-id="e395f-160">s11</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96014](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="e395f-161">wsa</span><span class="sxs-lookup"><span data-stu-id="e395f-161">wsa</span></span>|<span data-ttu-id="e395f-162">Wstępnie 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="e395f-163">1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-163">1.0</span></span>|http://www.w3.org/2004/08/addressing<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96022](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="e395f-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="e395f-164">wscoor</span></span>|<span data-ttu-id="e395f-165">1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-165">1.0</span></span><br /><br /> <span data-ttu-id="e395f-166">1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-166">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96078](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96079](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="e395f-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="e395f-167">wsat</span></span>|<span data-ttu-id="e395f-168">1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-168">1.0</span></span><br /><br /> <span data-ttu-id="e395f-169">1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-169">1.1</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96080](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96081](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="e395f-170">t</span><span class="sxs-lookup"><span data-stu-id="e395f-170">t</span></span>|<span data-ttu-id="e395f-171">1.3 wstępnie</span><span class="sxs-lookup"><span data-stu-id="e395f-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="e395f-172">1.3</span><span class="sxs-lookup"><span data-stu-id="e395f-172">1.3</span></span>|[http://go.microsoft.com/fwlink/?LinkId=96082](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [http://go.microsoft.com/fwlink/?LinkId=96100](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="e395f-173">o</span><span class="sxs-lookup"><span data-stu-id="e395f-173">o</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96101](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="e395f-174">XSD</span><span class="sxs-lookup"><span data-stu-id="e395f-174">xsd</span></span>||[http://go.microsoft.com/fwlink/?LinkId=96102](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="e395f-175">Menedżer transakcji powiązania</span><span class="sxs-lookup"><span data-stu-id="e395f-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="e395f-176">R1001: Udział w transakcji usługi WS-AT 1.0 menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="e395f-177">R1002: Udział w transakcji usługi WS-AT 1.1 menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2005/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="e395f-178">Komunikaty aplikacji nie są ograniczone do tych powiązań i opisano później.</span><span class="sxs-lookup"><span data-stu-id="e395f-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="e395f-179">Powiązanie HTTPS Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="e395f-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="e395f-180">Powiązanie HTTPS Menedżera transakcji korzysta wyłącznie z zabezpieczeń transportu, aby osiągnąć zabezpieczeń i ustanowienia relacji zaufania między każda para odbiornika nadawcy w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e395f-181">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="e395f-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e395f-182">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e395f-183">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegółów implementacji:</span><span class="sxs-lookup"><span data-stu-id="e395f-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="e395f-184">R1111: Certyfikatów X.509 przedstawianych przez sieć musi mieć nazwę podmiotu, która jest zgodna z w pełni kwalifikowaną nazwę (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e395f-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="e395f-185">B1112: DNS musi być funkcjonalności każda para odbiornika nadawcy w systemie kontroli nazwa podmiotu X.509 powiodło się.</span><span class="sxs-lookup"><span data-stu-id="e395f-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="e395f-186">Aktywacja i rejestracja powiązania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e395f-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="e395f-187">Usługi WCF wymaga dwukierunkowego powiązania żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e395f-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="e395f-188">(Aby uzyskać więcej informacji na temat korelacji i opisy wzorców wymiany wiadomości żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8).</span><span class="sxs-lookup"><span data-stu-id="e395f-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e395f-189">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="e395f-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e395f-190">Usługi WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e395f-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e395f-191">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e395f-192">B1131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="e395f-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="e395f-193">Menedżer transakcji mieszanym powiązania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="e395f-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="e395f-194">Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używa połączeniu z modelem koordynacji WS wystawionego tokenu na potrzeby określania tożsamości.</span><span class="sxs-lookup"><span data-stu-id="e395f-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="e395f-195">Aktywacji i rejestracji są tylko elementy, które różnią się między dwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="e395f-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="e395f-196">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="e395f-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="e395f-197">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="e395f-198">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="e395f-199">Konfiguracja powiązania komunikat aktywacji</span><span class="sxs-lookup"><span data-stu-id="e395f-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="e395f-200">Aktywacja komunikaty zwykle nie uczestniczą w współdziałanie ponieważ zwykle występują między aplikacją a jego lokalnego Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="e395f-201">B1221: WCF używa dwukierunkowego powiązania HTTPS (opisanego w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="e395f-202">Skorelowane żądanie i odpowiedź przy użyciu protokołu WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="e395f-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="e395f-203">Specyfikacja WS-Atomic Transaction, 8 sekcji opisano dalsze szczegóły dotyczące korelacji i wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="e395f-204">R1222: odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`.</span><span class="sxs-lookup"><span data-stu-id="e395f-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="e395f-205">Token ten jest zwracany wewnątrz `t:IssuedTokens` nagłówka następującej specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="e395f-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="e395f-206">R1223: W przypadku aktywacji w ramach istniejącego kontekstu koordynacji `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekstu musi przepływać na `CreateCoordinationContext` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="e395f-207">Nowy `t:IssuedTokens` nagłówka ma być generowany dla dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="e395f-208">Konfiguracja powiązania komunikatu rejestracji</span><span class="sxs-lookup"><span data-stu-id="e395f-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="e395f-209">B1231: WCF używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="e395f-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="e395f-210">Skorelowane żądanie i odpowiedź przy użyciu protokołu WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="e395f-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="e395f-211">WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dodatkowe szczegóły dotyczące korelacji i opisy wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="e395f-212">R1232: Wychodzące `wscoor:Register` komunikaty muszą używać `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="e395f-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="e395f-213">`wsse:Timestamp` Elementu muszą być podpisane przy użyciu `SecurityContextToken``STx` wystawione.</span><span class="sxs-lookup"><span data-stu-id="e395f-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="e395f-214">Podpis jest potwierdzenie posiadania token skojarzony z określonej transakcji i jest używany do uwierzytelniania uczestnika rejestracji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="e395f-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="e395f-215">RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e395f-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="e395f-216">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="e395f-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="e395f-217">Usługi WCF obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e395f-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="e395f-218">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="e395f-219">B1241: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing do osiągnięcia korelacji wiadomości 2PC firmy WCF.</span><span class="sxs-lookup"><span data-stu-id="e395f-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="e395f-220">Komunikat aplikacji programu Exchange</span><span class="sxs-lookup"><span data-stu-id="e395f-220">Application Message Exchange</span></span>  
 <span data-ttu-id="e395f-221">Aplikacje mogą użyć dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, tak długo, jak powiązania spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="e395f-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="e395f-222">R2001: Komunikatów aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z programem `CoordinationContext` w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="e395f-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="e395f-223">R2002: Integralności i poufności `t:IssuedToken` należy podać.</span><span class="sxs-lookup"><span data-stu-id="e395f-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="e395f-224">`CoordinationContext` Nagłówek zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="e395f-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="e395f-225">Podczas definicji `xsd:AnyURI` zezwala na korzystanie z względne i bezwzględny identyfikator URI usługi WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="e395f-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="e395f-226">B2003: Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędów, które zostaną zwrócone z transakcyjnych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="e395f-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="e395f-227">Przykłady wiadomości</span><span class="sxs-lookup"><span data-stu-id="e395f-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="e395f-228">Komunikaty CreateCoordinationContext żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="e395f-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="e395f-229">Następujące komunikaty wykonaj wzorzec żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e395f-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="e395f-230">CreateCoordinationContext z WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="e395f-231">CreateCoordinationContext z WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="e395f-232">CreateCoordinationContextResponse zaufania Pre-1.3 i WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="e395f-233">CreateCoordinationContextResponse zaufania 1.3 i WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-     wssecurity-utility-1.0.xsd"   
xmlns:wst=http://docs.oasis-open.org/ws-sx/ws-trust/200512  
xmlns:wsc=http://schemas.xmlsoap.org/ws/2005/02/sc  
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
  ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
  URI="http://fabrikam123.com/SCTi"/>  
</wsse:SecurityTokenReference>   
</wst:RequestedAttachedReference>   
<wst:RequestedUnattachedReference>   
<wsse:SecurityTokenReference>   
<wsse:Reference  
 ValueType=http://schemas.xmlsoap.org/ws/2005/02/sc/sct  
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
  
### <a name="registration-messages"></a><span data-ttu-id="e395f-234">Rejestracja wiadomości</span><span class="sxs-lookup"><span data-stu-id="e395f-234">Registration Messages</span></span>  
 <span data-ttu-id="e395f-235">Następujące komunikaty są komunikaty rejestracji.</span><span class="sxs-lookup"><span data-stu-id="e395f-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="e395f-236">Zarejestruj WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="e395f-237">Zarejestruj WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="e395f-238">Zarejestruj odpowiedzi WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="e395f-239">Zarejestruj odpowiedzi WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="e395f-240">Dwa komunikaty protokołu zatwierdzania fazy</span><span class="sxs-lookup"><span data-stu-id="e395f-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="e395f-241">Następujący komunikat odnosi się do protokołu dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="e395f-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="e395f-242">Zatwierdź z WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="e395f-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="e395f-243">Zatwierdź z WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="e395f-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="e395f-244">Komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="e395f-244">Application Messages</span></span>  
 <span data-ttu-id="e395f-245">Następujące komunikaty są komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e395f-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="e395f-246">Komunikat żądania aplikacji</span><span class="sxs-lookup"><span data-stu-id="e395f-246">Application message-Request</span></span>  
  
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

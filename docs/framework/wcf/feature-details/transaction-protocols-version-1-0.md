---
title: Protokoły transakcyjne wersja 1.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60867daa7b8519f745c37371604807c51aa1cbb9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="60bf3-102">Protokoły transakcyjne wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="60bf3-102">Transaction Protocols version 1.0</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="60bf3-103"> Wersja 1 implementuje wersji 1.0 protokołów WS-Atomic Transaction i koordynacji WS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-103"> version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="60bf3-104">Aby uzyskać więcej informacji o wersji 1.1, zobacz [protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="60bf3-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="60bf3-105">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="60bf3-105">Specification/Document</span></span>|<span data-ttu-id="60bf3-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="60bf3-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="60bf3-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="60bf3-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="60bf3-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="60bf3-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="60bf3-109">Współdziałanie z tymi specyfikacjami protokołu jest wymagany na dwa poziomy: między aplikacjami i między menedżerowie transakcji (zobacz poniższą ilustrację).</span><span class="sxs-lookup"><span data-stu-id="60bf3-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="60bf3-110">Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="60bf3-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="60bf3-111">Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie tak samo, jak dla programu exchange regularne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="60bf3-112">Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy dla określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="60bf3-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="60bf3-113">W tym temacie opisuje kompozycji specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="60bf3-114">Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS tym IBM, IONA Sun Microsystems i inne.</span><span class="sxs-lookup"><span data-stu-id="60bf3-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="60bf3-115">Na poniższym rysunku przedstawiono współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje aplikacji 1 i 2 aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="60bf3-116">![Protokoły transakcji](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="60bf3-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="60bf3-117">Należy wziąć pod uwagę typowy scenariusz WS-koordynacji/protokołu WS-AT z jednego inicjatora (I) i jednego uczestnika (P).</span><span class="sxs-lookup"><span data-stu-id="60bf3-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="60bf3-118">Inicjator i uczestnika ma menedżerowie transakcji (ITM i PTM, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="60bf3-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="60bf3-119">Dwufazowe nazywa się 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="60bf3-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60bf3-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="60bf3-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="60bf3-121">12. Odpowiedzi na komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="60bf3-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="60bf3-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="60bf3-123">13. Zatwierdź (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="60bf3-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="60bf3-124">3. Rejestr (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="60bf3-124">3. Register (Completion)</span></span>|<span data-ttu-id="60bf3-125">14. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="60bf3-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-126">4. RegisterResponse</span></span>|<span data-ttu-id="60bf3-127">15. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="60bf3-128">5. Komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="60bf3-128">5. Application Message</span></span>|<span data-ttu-id="60bf3-129">16. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="60bf3-130">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="60bf3-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="60bf3-131">17. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="60bf3-132">7. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="60bf3-132">7. Register (Durable)</span></span>|<span data-ttu-id="60bf3-133">18. Zatwierdzone (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="60bf3-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="60bf3-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-134">8. RegisterResponse</span></span>|<span data-ttu-id="60bf3-135">19. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="60bf3-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="60bf3-137">20. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="60bf3-138">10. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="60bf3-138">10. Register (Durable)</span></span>|<span data-ttu-id="60bf3-139">21. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="60bf3-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-140">11. RegisterResponse</span></span>|<span data-ttu-id="60bf3-141">22. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="60bf3-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="60bf3-142">Ten dokument opisuje kompozycji specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="60bf3-143">Podejście opisane w tym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="60bf3-144">Ilustracja i tabela przedstawiono cztery rodzaje komunikaty z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="60bf3-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="60bf3-145">Aktywacja wiadomości (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="60bf3-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="60bf3-146">Rejestracja wiadomości (rejestr i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="60bf3-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="60bf3-147">Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzania, przerwane i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="60bf3-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="60bf3-148">Komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-148">Application messages.</span></span>  
  
 <span data-ttu-id="60bf3-149">Pierwszy klas trzy wiadomości są traktowane jako wiadomości Menedżera transakcji i ich konfiguracja powiązania jest opisany w "Wymianie wiadomości aplikacji" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="60bf3-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="60bf3-150">Czwarty klasę wiadomości jest komunikatów aplikacji i jest opisana w sekcji "Komunikat przykłady" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="60bf3-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="60bf3-151">W tej sekcji opisano powiązania protokołu używane dla każdego z tych klas przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60bf3-151">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="60bf3-152">Następujące obszary nazw XML i prefiksy skojarzone są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="60bf3-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="60bf3-153">Prefiks</span><span class="sxs-lookup"><span data-stu-id="60bf3-153">Prefix</span></span>|<span data-ttu-id="60bf3-154">Identyfikator URI Namespace</span><span class="sxs-lookup"><span data-stu-id="60bf3-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="60bf3-155">s11</span><span class="sxs-lookup"><span data-stu-id="60bf3-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="60bf3-156">wsa</span><span class="sxs-lookup"><span data-stu-id="60bf3-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="60bf3-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="60bf3-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="60bf3-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="60bf3-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="60bf3-159">t</span><span class="sxs-lookup"><span data-stu-id="60bf3-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="60bf3-160">o</span><span class="sxs-lookup"><span data-stu-id="60bf3-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="60bf3-161">XSD</span><span class="sxs-lookup"><span data-stu-id="60bf3-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="60bf3-162">Menedżer transakcji powiązania</span><span class="sxs-lookup"><span data-stu-id="60bf3-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="60bf3-163">R1001: Menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="60bf3-164">Komunikaty aplikacji nie są ograniczone do tych powiązań i opisano później.</span><span class="sxs-lookup"><span data-stu-id="60bf3-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="60bf3-165">Powiązanie HTTPS Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="60bf3-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="60bf3-166">Powiązanie HTTPS Menedżera transakcji korzysta wyłącznie z zabezpieczeń transportu, aby osiągnąć zabezpieczeń i ustanowienia relacji zaufania między każda para odbiornika nadawcy w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="60bf3-167">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="60bf3-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="60bf3-168">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="60bf3-169">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegółów implementacji:</span><span class="sxs-lookup"><span data-stu-id="60bf3-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="60bf3-170">R1111: Certyfikatów X.509 przedstawianych przez sieć musi mieć nazwę podmiotu, która jest zgodna z w pełni kwalifikowaną nazwę (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="60bf3-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="60bf3-171">B1112: DNS musi być funkcjonalności każda para odbiornika nadawcy w systemie kontroli nazwa podmiotu X.509 powiodło się.</span><span class="sxs-lookup"><span data-stu-id="60bf3-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="60bf3-172">Aktywacja i rejestracja powiązania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="60bf3-172">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="60bf3-173"> wymaga dwukierunkowego powiązania żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-173"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="60bf3-174">(Aby uzyskać więcej informacji na temat korelacji i opisy wzorców wymiany wiadomości żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8).</span><span class="sxs-lookup"><span data-stu-id="60bf3-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="60bf3-175">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="60bf3-175">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="60bf3-176"> obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-176"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="60bf3-177">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="60bf3-178">B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="60bf3-179">Menedżer transakcji mieszanym powiązania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="60bf3-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="60bf3-180">Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używa połączeniu z modelem koordynacji WS wystawionego tokenu na potrzeby określania tożsamości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="60bf3-181">Aktywacji i rejestracji są tylko elementy, które różnią się między dwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="60bf3-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="60bf3-182">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="60bf3-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="60bf3-183">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="60bf3-184">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="60bf3-185">Konfiguracja powiązania komunikat aktywacji</span><span class="sxs-lookup"><span data-stu-id="60bf3-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="60bf3-186">Aktywacja komunikaty zwykle nie uczestniczą w współdziałanie ponieważ zwykle występują między aplikacją a jego lokalnego Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="60bf3-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-187">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="60bf3-188">Za pomocą usługi WS-Addressing 2004/08 są skorelowane żądanie i odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="60bf3-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="60bf3-189">Specyfikacja WS-Atomic Transaction, 8 sekcji opisano dalsze szczegóły dotyczące korelacji i wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="60bf3-190">R1222: odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`.</span><span class="sxs-lookup"><span data-stu-id="60bf3-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="60bf3-191">Token ten jest zwracany wewnątrz `t:IssuedTokens` nagłówka następującej specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="60bf3-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="60bf3-192">R1223: W przypadku aktywacji w ramach istniejącego kontekstu koordynacji `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekstu musi przepływać na `CreateCoordinationContext` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="60bf3-193">Nowy `t:IssuedTokens` nagłówka ma być generowany dla dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="60bf3-194">Konfiguracja powiązania komunikatu rejestracji</span><span class="sxs-lookup"><span data-stu-id="60bf3-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="60bf3-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="60bf3-195">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="60bf3-196">Za pomocą usługi WS-Addressing 2004/08 są skorelowane żądanie i odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="60bf3-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="60bf3-197">WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dodatkowe szczegóły dotyczące korelacji i opisy wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="60bf3-198">R1232: Wychodzące `wscoor:Register` komunikaty muszą używać `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="60bf3-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="60bf3-199">`wsse:Timestamp` Elementu muszą być podpisane przy użyciu `SecurityContextToken``STx` wystawione.</span><span class="sxs-lookup"><span data-stu-id="60bf3-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="60bf3-200">Podpis jest potwierdzenie posiadania token skojarzony z określonej transakcji i jest używany do uwierzytelniania uczestnika rejestracji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="60bf3-201">RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="60bf3-202">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="60bf3-202">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="60bf3-203"> obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="60bf3-203"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="60bf3-204">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="60bf3-205">B2131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="60bf3-206">Komunikat aplikacji programu Exchange</span><span class="sxs-lookup"><span data-stu-id="60bf3-206">Application Message Exchange</span></span>  
 <span data-ttu-id="60bf3-207">Aplikacje mogą użyć dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, tak długo, jak powiązania spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="60bf3-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="60bf3-208">R2001: Komunikatów aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z programem `CoordinationContext` w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="60bf3-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="60bf3-209">R2002: Integralności i poufności `t:IssuedToken` należy podać.</span><span class="sxs-lookup"><span data-stu-id="60bf3-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="60bf3-210">`CoordinationContext` Nagłówek zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="60bf3-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="60bf3-211">Podczas definicji `xsd:AnyURI` umożliwia wykorzystanie bezwzględne i względne identyfikatory URI, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko `wscoor:Identifiers`, będące bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="60bf3-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="60bf3-212">Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędów, które zostaną zwrócone z transakcyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="60bf3-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="60bf3-213">Przykłady wiadomości</span><span class="sxs-lookup"><span data-stu-id="60bf3-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="60bf3-214">Komunikaty CreateCoordinationContext żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="60bf3-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="60bf3-215">Następujące komunikaty wykonaj wzorzec żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="60bf3-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="60bf3-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="60bf3-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="60bf3-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="60bf3-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="60bf3-218">Rejestracja wiadomości</span><span class="sxs-lookup"><span data-stu-id="60bf3-218">Registration Messages</span></span>  
 <span data-ttu-id="60bf3-219">Następujące komunikaty są komunikaty rejestracji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="60bf3-220">Rejestruj</span><span class="sxs-lookup"><span data-stu-id="60bf3-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="60bf3-221">Zarejestruj odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="60bf3-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="60bf3-222">Dwa komunikaty protokołu zatwierdzania fazy</span><span class="sxs-lookup"><span data-stu-id="60bf3-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="60bf3-223">Następujący komunikat odnosi się do protokołu dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="60bf3-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="60bf3-224">Zatwierdź</span><span class="sxs-lookup"><span data-stu-id="60bf3-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="60bf3-225">Komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="60bf3-225">Application Messages</span></span>  
 <span data-ttu-id="60bf3-226">Następujące komunikaty są komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60bf3-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="60bf3-227">Komunikat żądania aplikacji</span><span class="sxs-lookup"><span data-stu-id="60bf3-227">Application message-Request</span></span>  
  
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

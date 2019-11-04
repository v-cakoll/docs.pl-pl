---
title: Protokoły transakcyjne wersja 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: 5ca0210c15afd6a3fc2e05bc3b9016a1fcd929b7
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460273"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="f2aee-102">Protokoły transakcyjne wersja 1.0</span><span class="sxs-lookup"><span data-stu-id="f2aee-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="f2aee-103">Windows Communication Foundation (WCF) w wersji 1 implementuje wersję 1,0 transakcji WS-i protokołów koordynacyjnych WS-AT.</span><span class="sxs-lookup"><span data-stu-id="f2aee-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="f2aee-104">Aby uzyskać więcej informacji na temat wersji 1,1, zobacz [Protokoły transakcji](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="f2aee-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="f2aee-105">Specyfikacja/dokument</span><span class="sxs-lookup"><span data-stu-id="f2aee-105">Specification/Document</span></span>|<span data-ttu-id="f2aee-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="f2aee-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="f2aee-107">Usługa WS-koordynacja</span><span class="sxs-lookup"><span data-stu-id="f2aee-107">WS-Coordination</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wscoor/wscoor.pdf>|  
|<span data-ttu-id="f2aee-108">Protokół WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="f2aee-108">WS-AtomicTransaction</span></span>|<https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf>|  
  
 <span data-ttu-id="f2aee-109">Współdziałanie z tymi specyfikacjami protokołu jest wymagane na dwóch poziomach: między aplikacjami i menedżerami transakcji (patrz poniższy rysunek).</span><span class="sxs-lookup"><span data-stu-id="f2aee-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="f2aee-110">Specyfikacja zawiera szczegółowe informacje o formatach komunikatów i wymianie komunikatów dla obu poziomów współdziałania.</span><span class="sxs-lookup"><span data-stu-id="f2aee-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="f2aee-111">Niektóre zabezpieczenia, niezawodność i kodowanie dla wymiany między aplikacjami mają zastosowanie w przypadku regularnego wymiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="f2aee-112">Jednak pomyślne współdziałanie między menedżerami transakcji wymaga zawarcia umowy w ramach określonego powiązania, ponieważ zazwyczaj nie jest ona konfigurowana przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f2aee-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="f2aee-113">W tym temacie opisano kompozycję specyfikacji transakcji WS-AT (WS-AT) z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="f2aee-114">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych, w tym IBM, IONA, Sun Microsystems i innych.</span><span class="sxs-lookup"><span data-stu-id="f2aee-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="f2aee-115">Na poniższej ilustracji przedstawiono współdziałanie między dwoma menedżerami transakcji, menedżerem transakcji 1 i menedżerem transakcji 2 oraz dwiema aplikacjami, aplikacjami 1 i aplikacją 2:</span><span class="sxs-lookup"><span data-stu-id="f2aee-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Zrzut ekranu przedstawiający interakcję między menedżerami transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="f2aee-117">Rozważmy typowy scenariusz transakcji WS-koordynacyjny/WS-Atomowej z jednym inicjatorem (I) i jednym uczestnikiem (P).</span><span class="sxs-lookup"><span data-stu-id="f2aee-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="f2aee-118">Inicjator i uczestnik mają menedżerów transakcji (odpowiednio ITM i PTM).</span><span class="sxs-lookup"><span data-stu-id="f2aee-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="f2aee-119">Dwufazowe zatwierdzanie jest określane jako 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="f2aee-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2aee-120">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="f2aee-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="f2aee-121">12. odpowiedź na komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2aee-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="f2aee-122">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="f2aee-123">13. zatwierdzenie (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="f2aee-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="f2aee-124">3. Rejestr (uzupełnianie)</span><span class="sxs-lookup"><span data-stu-id="f2aee-124">3. Register (Completion)</span></span>|<span data-ttu-id="f2aee-125">14. Przygotuj (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="f2aee-126">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-126">4. RegisterResponse</span></span>|<span data-ttu-id="f2aee-127">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="f2aee-128">5. komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2aee-128">5. Application Message</span></span>|<span data-ttu-id="f2aee-129">16. przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="f2aee-130">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="f2aee-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="f2aee-131">17. przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="f2aee-132">7. Zarejestruj (trwałe)</span><span class="sxs-lookup"><span data-stu-id="f2aee-132">7. Register (Durable)</span></span>|<span data-ttu-id="f2aee-133">18. zatwierdzone (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="f2aee-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="f2aee-134">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-134">8. RegisterResponse</span></span>|<span data-ttu-id="f2aee-135">19. zatwierdzenie (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="f2aee-136">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="f2aee-137">20. Zatwierdzanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="f2aee-138">10. Rejestr (trwałe)</span><span class="sxs-lookup"><span data-stu-id="f2aee-138">10. Register (Durable)</span></span>|<span data-ttu-id="f2aee-139">21. zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="f2aee-140">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-140">11. RegisterResponse</span></span>|<span data-ttu-id="f2aee-141">22. zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="f2aee-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="f2aee-142">W tym dokumencie opisano kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="f2aee-143">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych.</span><span class="sxs-lookup"><span data-stu-id="f2aee-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="f2aee-144">Ilustracja i tabela przedstawiają cztery klasy komunikatów z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="f2aee-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="f2aee-145">Komunikaty aktywacji (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="f2aee-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="f2aee-146">Wiadomości rejestracyjne (Register i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="f2aee-146">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="f2aee-147">Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzenie, przerwane itd.).</span><span class="sxs-lookup"><span data-stu-id="f2aee-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="f2aee-148">Komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-148">Application messages.</span></span>  
  
 <span data-ttu-id="f2aee-149">Pierwsze trzy klasy komunikatów są uznawane za komunikaty Menedżera transakcji, a ich konfiguracja powiązań została opisana w sekcji "Wymiana komunikatów aplikacji" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f2aee-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="f2aee-150">Czwarta klasa komunikatu to aplikacja do komunikatów aplikacji i została opisana w sekcji "Przykłady komunikatów" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f2aee-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="f2aee-151">W tej sekcji opisano powiązania protokołów używane dla każdej z tych klas przez funkcję WCF.</span><span class="sxs-lookup"><span data-stu-id="f2aee-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="f2aee-152">W tym dokumencie są używane następujące przestrzenie nazw XML i skojarzone prefiksy.</span><span class="sxs-lookup"><span data-stu-id="f2aee-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="f2aee-153">prefiks</span><span class="sxs-lookup"><span data-stu-id="f2aee-153">Prefix</span></span>|<span data-ttu-id="f2aee-154">Identyfikator URI przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="f2aee-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="f2aee-155">s11</span><span class="sxs-lookup"><span data-stu-id="f2aee-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="f2aee-156">WSA</span><span class="sxs-lookup"><span data-stu-id="f2aee-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="f2aee-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="f2aee-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="f2aee-158">WSAT</span><span class="sxs-lookup"><span data-stu-id="f2aee-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="f2aee-159">t</span><span class="sxs-lookup"><span data-stu-id="f2aee-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="f2aee-160">o</span><span class="sxs-lookup"><span data-stu-id="f2aee-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="f2aee-161">XSD</span><span class="sxs-lookup"><span data-stu-id="f2aee-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="f2aee-162">Powiązania Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="f2aee-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="f2aee-163">R1001: menedżerowie transakcji muszą używać protokołu SOAP 1,1 i WS-Addressing 2004/08 dla transakcji WS-i wymiany komunikatów z obsługą protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="f2aee-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="f2aee-164">Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="f2aee-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="f2aee-165">Powiązanie HTTPS Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="f2aee-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="f2aee-166">Powiązanie HTTPS Menedżera transakcji polega wyłącznie na zabezpieczeniach transportu, aby zapewnić bezpieczeństwo i ustanowić relację zaufania między każdą parę nadawcy-odbiornik w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="f2aee-167">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="f2aee-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="f2aee-168">Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="f2aee-169">Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji:</span><span class="sxs-lookup"><span data-stu-id="f2aee-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="f2aee-170">R1111: certyfikat X. 509 przedstawiony w sieci musi mieć nazwę podmiotu zgodną z w pełni kwalifikowaną nazwą domeny (FQDN) maszyny źródłowej.</span><span class="sxs-lookup"><span data-stu-id="f2aee-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="f2aee-171">B1112: usługa DNS musi być funkcjonalna między poszczególnymi parami nadawcy a odbiornikiem w systemie dla nazwy podmiotu X. 509.</span><span class="sxs-lookup"><span data-stu-id="f2aee-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="f2aee-172">Konfiguracja powiązania aktywacji i rejestracji</span><span class="sxs-lookup"><span data-stu-id="f2aee-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="f2aee-173">Funkcja WCF wymaga powiązania dwustronnego żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f2aee-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="f2aee-174">(Aby uzyskać więcej informacji na temat korelacji i opisów wzorców wymiany komunikatów żądania/odpowiedzi, zobacz temat transakcja WS-niepodzielna, sekcja 8.)</span><span class="sxs-lookup"><span data-stu-id="f2aee-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="f2aee-175">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="f2aee-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="f2aee-176">Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f2aee-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="f2aee-177">Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="f2aee-178">B2131: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing w celu osiągnięcia korelacji komunikatów 2PC w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="f2aee-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="f2aee-179">Mieszane powiązanie zabezpieczeń programu Transaction Manager</span><span class="sxs-lookup"><span data-stu-id="f2aee-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="f2aee-180">Jest to alternatywne powiązanie (w trybie mieszanym), które korzysta z zabezpieczeń transportu połączonej z modelem tokenów wystawionych przez usługę WS-koordynacyjny do celów ustanowienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="f2aee-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="f2aee-181">Aktywacja i rejestracja są jedynymi elementami, które różnią się między dwoma powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="f2aee-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="f2aee-182">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="f2aee-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="f2aee-183">Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="f2aee-184">Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="f2aee-185">Konfiguracja powiązania komunikatów aktywacji</span><span class="sxs-lookup"><span data-stu-id="f2aee-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="f2aee-186">Komunikaty o aktywacji zwykle nie uczestniczą w współdziałaniu, ponieważ zazwyczaj występują między aplikacją a jej lokalnym menedżerem transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="f2aee-187">B1221: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla komunikatów aktywacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="f2aee-188">Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f2aee-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="f2aee-189">Specyfikacja transakcji WS-niepodzielna, sekcja 8, opis dalszych szczegółowych informacji o korelacji i wzorcach wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f2aee-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="f2aee-190">R1222: po odebraniu `CreateCoordinationContext`koordynator musi wydać `SecurityContextToken` ze skojarzonym `STx`tajnym.</span><span class="sxs-lookup"><span data-stu-id="f2aee-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="f2aee-191">Ten token jest zwracany w nagłówku `t:IssuedTokens` po specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="f2aee-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="f2aee-192">R1223: Jeśli aktywacja odbywa się w istniejącym kontekście koordynacji, nagłówek `t:IssuedTokens` z `SecurityContextToken` skojarzony z istniejącym kontekstem musi przepływać w komunikacie `CreateCoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="f2aee-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="f2aee-193">Nowy nagłówek `t:IssuedTokens` powinien zostać wygenerowany w celu dołączenia do wiadomości wychodzącej `wscoor:CreateCoordinationContextResponse`.</span><span class="sxs-lookup"><span data-stu-id="f2aee-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="f2aee-194">Konfiguracja powiązania komunikatu rejestracji</span><span class="sxs-lookup"><span data-stu-id="f2aee-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="f2aee-195">B1231: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="f2aee-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="f2aee-196">Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08.</span><span class="sxs-lookup"><span data-stu-id="f2aee-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="f2aee-197">WS-AtomicTransaction, sekcja 8, zawiera szczegółowe informacje o korelacji i opisach wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f2aee-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="f2aee-198">R1232: komunikaty wychodzące `wscoor:Register` muszą używać trybu uwierzytelniania `IssuedTokenOverTransport` opisanego w [protokole zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="f2aee-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="f2aee-199">Element `wsse:Timestamp` musi być podpisany przy użyciu wystawionego `SecurityContextToken STx`.</span><span class="sxs-lookup"><span data-stu-id="f2aee-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="f2aee-200">Podpis jest dowodem posiadania tokenu powiązanego z określoną transakcją i jest używany do uwierzytelniania uczestnika rejestracji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="f2aee-201">Wiadomość RegistrationResponse jest wysyłana z powrotem za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f2aee-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="f2aee-202">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="f2aee-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="f2aee-203">Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f2aee-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="f2aee-204">Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="f2aee-205">B2131: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing w celu osiągnięcia korelacji komunikatów 2PC w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="f2aee-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="f2aee-206">Wymiana komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2aee-206">Application Message Exchange</span></span>  
 <span data-ttu-id="f2aee-207">Aplikacje mogą korzystać z dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, o ile powiązanie spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="f2aee-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="f2aee-208">R2001: komunikaty aplikacji do aplikacji muszą przepływać nagłówka `t:IssuedTokens` wraz z `CoordinationContext` w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f2aee-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="f2aee-209">R2002: należy podać integralność i poufność `t:IssuedToken`.</span><span class="sxs-lookup"><span data-stu-id="f2aee-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="f2aee-210">Nagłówek `CoordinationContext` zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="f2aee-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="f2aee-211">Chociaż definicja `xsd:AnyURI` umożliwia użycie zarówno bezwzględnych, jak i względnych identyfikatorów URI, WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględnymi identyfikatorami URI.</span><span class="sxs-lookup"><span data-stu-id="f2aee-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="f2aee-212">Jeśli `wscoor:Identifier` `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędy zostaną zwrócone z transakcyjnych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="f2aee-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="f2aee-213">Przykłady komunikatów</span><span class="sxs-lookup"><span data-stu-id="f2aee-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="f2aee-214">Komunikaty żądania/odpowiedzi CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="f2aee-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="f2aee-215">Poniższe komunikaty obserwują wzorzec żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f2aee-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="f2aee-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="f2aee-216">CreateCoordinationContext</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="f2aee-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="f2aee-217">CreateCoordinationContextResponse</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="f2aee-218">Komunikaty rejestracji</span><span class="sxs-lookup"><span data-stu-id="f2aee-218">Registration Messages</span></span>  
 <span data-ttu-id="f2aee-219">Następujące komunikaty są komunikatami rejestracji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="f2aee-220">Rejestruj</span><span class="sxs-lookup"><span data-stu-id="f2aee-220">Register</span></span>  
  
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
  
#### <a name="register-response"></a><span data-ttu-id="f2aee-221">Rejestruj odpowiedź</span><span class="sxs-lookup"><span data-stu-id="f2aee-221">Register Response</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="f2aee-222">Komunikaty protokołu zatwierdzania dwóch faz</span><span class="sxs-lookup"><span data-stu-id="f2aee-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="f2aee-223">Następujący komunikat odnosi się do protokołu zatwierdzania dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="f2aee-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="f2aee-224">Zleca</span><span class="sxs-lookup"><span data-stu-id="f2aee-224">Commit</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="f2aee-225">Komunikaty aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2aee-225">Application Messages</span></span>  
 <span data-ttu-id="f2aee-226">Następujące komunikaty są komunikatami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2aee-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="f2aee-227">Komunikat aplikacji — żądanie</span><span class="sxs-lookup"><span data-stu-id="f2aee-227">Application message-Request</span></span>  
  
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

---
title: Protokoły transakcji
ms.date: 03/30/2017
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
ms.openlocfilehash: 32c5da24eb7b23145d79c33a9ca1f5e5bcc22c06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742728"
---
# <a name="transaction-protocols"></a><span data-ttu-id="4a049-102">Protokoły transakcji</span><span class="sxs-lookup"><span data-stu-id="4a049-102">Transaction Protocols</span></span>
<span data-ttu-id="4a049-103">Windows Communication Foundation (WCF) implementuje transakcję WS-i protokoły koordynujące WS-i.</span><span class="sxs-lookup"><span data-stu-id="4a049-103">Windows Communication Foundation (WCF) implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="4a049-104">Specyfikacja/dokument</span><span class="sxs-lookup"><span data-stu-id="4a049-104">Specification/Document</span></span>|<span data-ttu-id="4a049-105">Wersja</span><span class="sxs-lookup"><span data-stu-id="4a049-105">Version</span></span>|<span data-ttu-id="4a049-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="4a049-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="4a049-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="4a049-107">WS-Coordination</span></span>|<span data-ttu-id="4a049-108">1.0</span><span class="sxs-lookup"><span data-stu-id="4a049-108">1.0</span></span><br /><br /> <span data-ttu-id="4a049-109">1.1</span><span class="sxs-lookup"><span data-stu-id="4a049-109">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="4a049-110">Protokół WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="4a049-110">WS-AtomicTransaction</span></span>|<span data-ttu-id="4a049-111">1.0</span><span class="sxs-lookup"><span data-stu-id="4a049-111">1.0</span></span><br /><br /> <span data-ttu-id="4a049-112">1.1</span><span class="sxs-lookup"><span data-stu-id="4a049-112">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
  
 <span data-ttu-id="4a049-113">Współdziałanie z tymi specyfikacjami protokołu jest wymagane na dwóch poziomach: między aplikacjami i menedżerami transakcji (patrz poniższy rysunek).</span><span class="sxs-lookup"><span data-stu-id="4a049-113">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="4a049-114">Specyfikacja zawiera szczegółowe informacje o formatach komunikatów i wymianie komunikatów dla obu poziomów współdziałania.</span><span class="sxs-lookup"><span data-stu-id="4a049-114">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="4a049-115">Niektóre zabezpieczenia, niezawodność i kodowanie dla wymiany między aplikacjami mają zastosowanie w przypadku regularnego wymiany aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-115">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="4a049-116">Jednak pomyślne współdziałanie między menedżerami transakcji wymaga zawarcia umowy w ramach określonego powiązania, ponieważ zazwyczaj nie jest ona konfigurowana przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a049-116">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="4a049-117">W tym temacie opisano kompozycję specyfikacji transakcji WS-AT (WS-AT) z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-117">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="4a049-118">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych, w tym IBM, IONA, Sun Microsystems i innych.</span><span class="sxs-lookup"><span data-stu-id="4a049-118">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="4a049-119">Na poniższej ilustracji przedstawiono współdziałanie między dwoma menedżerami transakcji, menedżerem transakcji 1 i menedżerem transakcji 2 oraz dwiema aplikacjami, aplikacjami 1 i aplikacją 2:</span><span class="sxs-lookup"><span data-stu-id="4a049-119">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2:</span></span>  
  
 ![Zrzut ekranu przedstawiający interakcję między menedżerami transakcji.](./media/transaction-protocols/transaction-managers-flow.gif)  
  
 <span data-ttu-id="4a049-121">Rozważmy typowy scenariusz transakcji WS-koordynacyjny/WS-Atomowej z jednym inicjatorem (I) i jednym uczestnikiem (P).</span><span class="sxs-lookup"><span data-stu-id="4a049-121">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="4a049-122">Inicjator i uczestnik mają menedżerów transakcji (odpowiednio ITM i PTM).</span><span class="sxs-lookup"><span data-stu-id="4a049-122">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="4a049-123">Dwufazowe zatwierdzanie jest określane jako 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="4a049-123">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4a049-124">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="4a049-124">1. CreateCoordinationContext</span></span>|<span data-ttu-id="4a049-125">12. odpowiedź na komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a049-125">12. Application Message Response</span></span>|  
|<span data-ttu-id="4a049-126">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="4a049-126">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="4a049-127">13. zatwierdzenie (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="4a049-127">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="4a049-128">3. Rejestr (uzupełnianie)</span><span class="sxs-lookup"><span data-stu-id="4a049-128">3. Register (Completion)</span></span>|<span data-ttu-id="4a049-129">14. Przygotuj (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-129">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="4a049-130">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="4a049-130">4. RegisterResponse</span></span>|<span data-ttu-id="4a049-131">15. Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-131">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="4a049-132">5. komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a049-132">5. Application Message</span></span>|<span data-ttu-id="4a049-133">16. przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-133">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="4a049-134">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="4a049-134">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="4a049-135">17. przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-135">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="4a049-136">7. Zarejestruj (trwałe)</span><span class="sxs-lookup"><span data-stu-id="4a049-136">7. Register (Durable)</span></span>|<span data-ttu-id="4a049-137">18. zatwierdzone (zakończenie)</span><span class="sxs-lookup"><span data-stu-id="4a049-137">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="4a049-138">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="4a049-138">8. RegisterResponse</span></span>|<span data-ttu-id="4a049-139">19. zatwierdzenie (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-139">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="4a049-140">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="4a049-140">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="4a049-141">20. Zatwierdzanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-141">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="4a049-142">10. Rejestr (trwałe)</span><span class="sxs-lookup"><span data-stu-id="4a049-142">10. Register (Durable)</span></span>|<span data-ttu-id="4a049-143">21. zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-143">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="4a049-144">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="4a049-144">11. RegisterResponse</span></span>|<span data-ttu-id="4a049-145">22. zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="4a049-145">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="4a049-146">W tym dokumencie opisano kompozycję specyfikacji WS-AtomicTransaction z zabezpieczeniami i opisano bezpieczne powiązanie używane do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-146">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="4a049-147">Podejście opisane w tym dokumencie zostało pomyślnie przetestowane z innymi implementacjami WS-AT i WS-koordynacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4a049-147">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="4a049-148">Ilustracja i tabela przedstawiają cztery klasy komunikatów z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="4a049-148">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
- <span data-ttu-id="4a049-149">Komunikaty aktywacji (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="4a049-149">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
- <span data-ttu-id="4a049-150">Wiadomości rejestracyjne (Register i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="4a049-150">Registration messages (Register and RegisterResponse)</span></span>  
  
- <span data-ttu-id="4a049-151">Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzenie, przerwane itd.).</span><span class="sxs-lookup"><span data-stu-id="4a049-151">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
- <span data-ttu-id="4a049-152">Komunikaty aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-152">Application messages.</span></span>  
  
 <span data-ttu-id="4a049-153">Pierwsze trzy klasy komunikatów są uznawane za komunikaty Menedżera transakcji, a ich konfiguracja powiązań została opisana w sekcji "Wymiana komunikatów aplikacji" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4a049-153">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="4a049-154">Czwarta klasa komunikatu to aplikacja do komunikatów aplikacji i została opisana w sekcji "Przykłady komunikatów" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4a049-154">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="4a049-155">W tej sekcji opisano powiązania protokołów używane dla każdej z tych klas przez funkcję WCF.</span><span class="sxs-lookup"><span data-stu-id="4a049-155">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="4a049-156">W tym dokumencie są używane następujące przestrzenie nazw XML i skojarzone prefiksy.</span><span class="sxs-lookup"><span data-stu-id="4a049-156">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="4a049-157">Prefiks</span><span class="sxs-lookup"><span data-stu-id="4a049-157">Prefix</span></span>|<span data-ttu-id="4a049-158">Wersja</span><span class="sxs-lookup"><span data-stu-id="4a049-158">Version</span></span>|<span data-ttu-id="4a049-159">Identyfikator URI przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="4a049-159">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="4a049-160">s11</span><span class="sxs-lookup"><span data-stu-id="4a049-160">s11</span></span>||<https://schemas.xmlsoap.org/soap/envelope/>|  
|<span data-ttu-id="4a049-161">WSA</span><span class="sxs-lookup"><span data-stu-id="4a049-161">wsa</span></span>|<span data-ttu-id="4a049-162">Pre-1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-162">Pre-1.0</span></span><br /><br /> <span data-ttu-id="4a049-163">1.0</span><span class="sxs-lookup"><span data-stu-id="4a049-163">1.0</span></span>|`http://www.w3.org/2004/08/addressing`<br /><br /> <https://www.w3.org/2005/08/addressing/>|  
|<span data-ttu-id="4a049-164">wscoor</span><span class="sxs-lookup"><span data-stu-id="4a049-164">wscoor</span></span>|<span data-ttu-id="4a049-165">1.0</span><span class="sxs-lookup"><span data-stu-id="4a049-165">1.0</span></span><br /><br /> <span data-ttu-id="4a049-166">1.1</span><span class="sxs-lookup"><span data-stu-id="4a049-166">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wscoor/><br /><br /> <https://docs.oasis-open.org/ws-tx/wscoor/2006/06>|  
|<span data-ttu-id="4a049-167">WSAT</span><span class="sxs-lookup"><span data-stu-id="4a049-167">wsat</span></span>|<span data-ttu-id="4a049-168">1.0</span><span class="sxs-lookup"><span data-stu-id="4a049-168">1.0</span></span><br /><br /> <span data-ttu-id="4a049-169">1.1</span><span class="sxs-lookup"><span data-stu-id="4a049-169">1.1</span></span>|<http://schemas.xmlsoap.org/ws/2004/10/wsat/><br /><br /> <https://docs.oasis-open.org/ws-tx/wsat/2006/06>|  
|<span data-ttu-id="4a049-170">t</span><span class="sxs-lookup"><span data-stu-id="4a049-170">t</span></span>|<span data-ttu-id="4a049-171">Pre-1,3</span><span class="sxs-lookup"><span data-stu-id="4a049-171">Pre-1.3</span></span><br /><br /> <span data-ttu-id="4a049-172">1.3</span><span class="sxs-lookup"><span data-stu-id="4a049-172">1.3</span></span>|<http://schemas.xmlsoap.org/ws/2005/02/trust/><br /><br /> <https://docs.oasis-open.org/ws-sx/ws-trust/200512>|  
|<span data-ttu-id="4a049-173">o</span><span class="sxs-lookup"><span data-stu-id="4a049-173">o</span></span>||<https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd>|  
|<span data-ttu-id="4a049-174">XSD</span><span class="sxs-lookup"><span data-stu-id="4a049-174">xsd</span></span>||<https://www.w3.org/2001/XMLSchema>|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="4a049-175">Powiązania Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="4a049-175">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="4a049-176">R1001: menedżerowie transakcji uczestniczący w transakcji WS-AT 1,0 muszą używać protokołu SOAP 1,1 i WS-Addressing 2004/08 dla transakcji WS-i wymiany komunikatów z obsługą protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="4a049-176">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="4a049-177">R1002: menedżerowie transakcji uczestniczący w transakcji WS-AT 1,1 muszą używać protokołu SOAP 1,1 i WS-Addressing 2005/08 dla transakcji WS-i wymiany komunikatów z obsługą protokołu WS-AT.</span><span class="sxs-lookup"><span data-stu-id="4a049-177">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="4a049-178">Komunikaty aplikacji nie są ograniczone do tych powiązań i są opisane w dalszej części.</span><span class="sxs-lookup"><span data-stu-id="4a049-178">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="4a049-179">Powiązanie HTTPS Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="4a049-179">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="4a049-180">Powiązanie HTTPS Menedżera transakcji polega wyłącznie na zabezpieczeniach transportu, aby zapewnić bezpieczeństwo i ustanowić relację zaufania między każdą parę nadawcy-odbiornik w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-180">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="4a049-181">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="4a049-181">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="4a049-182">Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-182">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="4a049-183">Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji:</span><span class="sxs-lookup"><span data-stu-id="4a049-183">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
- <span data-ttu-id="4a049-184">R1111: certyfikat X. 509 przedstawiony w sieci musi mieć nazwę podmiotu zgodną z w pełni kwalifikowaną nazwą domeny (FQDN) maszyny źródłowej.</span><span class="sxs-lookup"><span data-stu-id="4a049-184">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
- <span data-ttu-id="4a049-185">B1112: usługa DNS musi być funkcjonalna między poszczególnymi parami nadawcy a odbiornikiem w systemie dla nazwy podmiotu X. 509.</span><span class="sxs-lookup"><span data-stu-id="4a049-185">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="4a049-186">Konfiguracja powiązania aktywacji i rejestracji</span><span class="sxs-lookup"><span data-stu-id="4a049-186">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="4a049-187">Funkcja WCF wymaga powiązania dwustronnego żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a049-187">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="4a049-188">(Aby uzyskać więcej informacji na temat korelacji i opisów wzorców wymiany komunikatów żądania/odpowiedzi, zobacz temat transakcja WS-niepodzielna, sekcja 8.)</span><span class="sxs-lookup"><span data-stu-id="4a049-188">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="4a049-189">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="4a049-189">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="4a049-190">Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a049-190">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="4a049-191">Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-191">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="4a049-192">B1131: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing w celu osiągnięcia korelacji komunikatów 2PC w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="4a049-192">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="4a049-193">Mieszane powiązanie zabezpieczeń programu Transaction Manager</span><span class="sxs-lookup"><span data-stu-id="4a049-193">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="4a049-194">Jest to alternatywne powiązanie (w trybie mieszanym), które korzysta z zabezpieczeń transportu połączonej z modelem tokenów wystawionych przez usługę WS-koordynacyjny do celów ustanowienia tożsamości.</span><span class="sxs-lookup"><span data-stu-id="4a049-194">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="4a049-195">Aktywacja i rejestracja są jedynymi elementami, które różnią się między dwoma powiązaniami.</span><span class="sxs-lookup"><span data-stu-id="4a049-195">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="4a049-196">Konfiguracja transportu HTTPS</span><span class="sxs-lookup"><span data-stu-id="4a049-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="4a049-197">Certyfikaty X. 509 są używane do ustanowienia tożsamości Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="4a049-198">Wymagane jest uwierzytelnianie klient/serwer, a autoryzacja klienta/serwera jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-198">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="4a049-199">Konfiguracja powiązania komunikatów aktywacji</span><span class="sxs-lookup"><span data-stu-id="4a049-199">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="4a049-200">Komunikaty o aktywacji zwykle nie uczestniczą w współdziałaniu, ponieważ zazwyczaj występują między aplikacją a jej lokalnym menedżerem transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-200">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="4a049-201">B1221: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla komunikatów aktywacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-201">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="4a049-202">Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08 dla WS-AT 1,0 i WS-Addressing 2005/08 for WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="4a049-202">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="4a049-203">Specyfikacja transakcji WS-niepodzielna, sekcja 8, opis dalszych szczegółowych informacji o korelacji i wzorcach wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4a049-203">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
- <span data-ttu-id="4a049-204">R1222: po odebraniu `CreateCoordinationContext`koordynator musi wydać `SecurityContextToken` ze skojarzonym `STx`tajnym.</span><span class="sxs-lookup"><span data-stu-id="4a049-204">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="4a049-205">Ten token jest zwracany w nagłówku `t:IssuedTokens` po specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="4a049-205">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
- <span data-ttu-id="4a049-206">R1223: Jeśli aktywacja odbywa się w istniejącym kontekście koordynacji, nagłówek `t:IssuedTokens` z `SecurityContextToken` skojarzony z istniejącym kontekstem musi przepływać w komunikacie `CreateCoordinationContext`.</span><span class="sxs-lookup"><span data-stu-id="4a049-206">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="4a049-207">Nowy nagłówek `t:IssuedTokens` powinien zostać wygenerowany w celu dołączenia do wiadomości wychodzącej `wscoor:CreateCoordinationContextResponse`.</span><span class="sxs-lookup"><span data-stu-id="4a049-207">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="4a049-208">Konfiguracja powiązania komunikatu rejestracji</span><span class="sxs-lookup"><span data-stu-id="4a049-208">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="4a049-209">B1231: WCF używa dupleksowego powiązania HTTPS (opisanego w [protokole obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="4a049-209">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="4a049-210">Komunikaty Request i reply są skorelowane przy użyciu protokołu WS-Addressing 2004/08 dla WS-AT 1,0 i WS-Addressing 2005/08 for WS-AT 1,1.</span><span class="sxs-lookup"><span data-stu-id="4a049-210">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="4a049-211">WS-AtomicTransaction, sekcja 8, zawiera szczegółowe informacje o korelacji i opisach wzorców wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4a049-211">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="4a049-212">R1232: komunikaty wychodzące `wscoor:Register` muszą używać trybu uwierzytelniania `IssuedTokenOverTransport` opisanego w [protokole zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="4a049-212">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="4a049-213">Element `wsse:Timestamp` musi być podpisany przy użyciu wystawionego `SecurityContextToken STx`.</span><span class="sxs-lookup"><span data-stu-id="4a049-213">The `wsse:Timestamp` element must be signed using the `SecurityContextToken STx` issued.</span></span> <span data-ttu-id="4a049-214">Podpis jest dowodem posiadania tokenu powiązanego z określoną transakcją i jest używany do uwierzytelniania uczestnika rejestracji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="4a049-214">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="4a049-215">Wiadomość RegistrationResponse jest wysyłana z powrotem za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a049-215">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="4a049-216">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="4a049-216">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="4a049-217">Usługa WCF obsługuje jednokierunkowe komunikaty (Datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a049-217">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="4a049-218">Korelacja wśród komunikatów jest pozostawiana jako szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-218">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="4a049-219">B1241: implementacje muszą obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing w celu osiągnięcia korelacji komunikatów 2PC w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="4a049-219">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="4a049-220">Wymiana komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a049-220">Application Message Exchange</span></span>  
 <span data-ttu-id="4a049-221">Aplikacje mogą korzystać z dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, o ile powiązanie spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="4a049-221">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
- <span data-ttu-id="4a049-222">R2001: komunikaty aplikacji do aplikacji muszą przepływać nagłówka `t:IssuedTokens` wraz z `CoordinationContext` w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4a049-222">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
- <span data-ttu-id="4a049-223">R2002: należy podać integralność i poufność `t:IssuedToken`.</span><span class="sxs-lookup"><span data-stu-id="4a049-223">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="4a049-224">Nagłówek `CoordinationContext` zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="4a049-224">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="4a049-225">Chociaż definicja `xsd:AnyURI` umożliwia użycie zarówno bezwzględnych, jak i względnych identyfikatorów URI, WCF obsługuje tylko `wscoor:Identifiers`, które są bezwzględnymi identyfikatorami URI.</span><span class="sxs-lookup"><span data-stu-id="4a049-225">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="4a049-226">B2003: Jeśli `wscoor:Identifier` `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędy zostaną zwrócone z transakcyjnych usług WCF.</span><span class="sxs-lookup"><span data-stu-id="4a049-226">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="4a049-227">Przykłady komunikatów</span><span class="sxs-lookup"><span data-stu-id="4a049-227">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="4a049-228">Komunikaty żądania/odpowiedzi CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="4a049-228">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="4a049-229">Poniższe komunikaty obserwują wzorzec żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="4a049-229">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="4a049-230">CreateCoordinationContext z WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-230">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="4a049-231">CreateCoordinationContext z WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="4a049-231">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="4a049-232">CreateCoordinationContextResponse z zaufaniem sprzed 1,3 i WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-232">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="4a049-233">CreateCoordinationContextResponse z zaufaniem 1,3 i WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="4a049-233">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="4a049-234">Komunikaty rejestracji</span><span class="sxs-lookup"><span data-stu-id="4a049-234">Registration Messages</span></span>  
 <span data-ttu-id="4a049-235">Następujące komunikaty są komunikatami rejestracji.</span><span class="sxs-lookup"><span data-stu-id="4a049-235">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="4a049-236">Zarejestruj się w usłudze WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-236">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="4a049-237">Zarejestruj się w usłudze WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="4a049-237">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="4a049-238">Rejestrowanie odpowiedzi w programie WSCoor 1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-238">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="4a049-239">Rejestrowanie odpowiedzi w programie WSCoor 1,1</span><span class="sxs-lookup"><span data-stu-id="4a049-239">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="4a049-240">Komunikaty protokołu zatwierdzania dwóch faz</span><span class="sxs-lookup"><span data-stu-id="4a049-240">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="4a049-241">Następujący komunikat odnosi się do protokołu zatwierdzania dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="4a049-241">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="4a049-242">Zatwierdź z WSAT 1,0</span><span class="sxs-lookup"><span data-stu-id="4a049-242">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="4a049-243">Zatwierdź z WSAT 1,1</span><span class="sxs-lookup"><span data-stu-id="4a049-243">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="4a049-244">Komunikaty aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a049-244">Application Messages</span></span>  
 <span data-ttu-id="4a049-245">Następujące komunikaty są komunikatami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a049-245">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="4a049-246">Komunikat aplikacji — żądanie</span><span class="sxs-lookup"><span data-stu-id="4a049-246">Application message-Request</span></span>  
  
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

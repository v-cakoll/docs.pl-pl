---
title: "Protokoły transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2820b0ec-2f32-430c-b299-1f0e95e1f2dc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6343a67f7fc333b863aee4fc5ab31edd15efabe1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-protocols"></a><span data-ttu-id="63c6a-102">Protokoły transakcji</span><span class="sxs-lookup"><span data-stu-id="63c6a-102">Transaction Protocols</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="63c6a-103">implementuje usługi WS-Atomic Transaction i koordynacji WS protokoły.</span><span class="sxs-lookup"><span data-stu-id="63c6a-103"> implements WS-Atomic Transaction and WS-Coordination protocols.</span></span>  
  
|<span data-ttu-id="63c6a-104">Specyfikacja/dokumentu</span><span class="sxs-lookup"><span data-stu-id="63c6a-104">Specification/Document</span></span>|<span data-ttu-id="63c6a-105">Wersja</span><span class="sxs-lookup"><span data-stu-id="63c6a-105">Version</span></span>|<span data-ttu-id="63c6a-106">Łącze</span><span class="sxs-lookup"><span data-stu-id="63c6a-106">Link</span></span>|  
|-----------------------------|-------------|----------|  
|<span data-ttu-id="63c6a-107">Koordynacji WS</span><span class="sxs-lookup"><span data-stu-id="63c6a-107">WS-Coordination</span></span>|<span data-ttu-id="63c6a-108">1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-108">1.0</span></span><br /><br /> <span data-ttu-id="63c6a-109">1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-109">1.1</span></span>|[<span data-ttu-id="63c6a-110">http://go.microsoft.com/fwlink/?LinkId=96104</span><span class="sxs-lookup"><span data-stu-id="63c6a-110">http://go.microsoft.com/fwlink/?LinkId=96104</span></span>](http://go.microsoft.com/fwlink/?LinkId=96104)<br /><br /> [<span data-ttu-id="63c6a-111">http://go.microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="63c6a-111">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="63c6a-112">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="63c6a-112">WS-AtomicTransaction</span></span>|<span data-ttu-id="63c6a-113">1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-113">1.0</span></span><br /><br /> <span data-ttu-id="63c6a-114">1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-114">1.1</span></span>|[<span data-ttu-id="63c6a-115">http://go.microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="63c6a-115">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> <span data-ttu-id="63c6a-116">http://go.microsoft.com/fwlink/?LinkId=96081</span><span class="sxs-lookup"><span data-stu-id="63c6a-116">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>|  
  
 <span data-ttu-id="63c6a-117">Współdziałanie z tymi specyfikacjami protokołu jest wymagany na dwa poziomy: między aplikacjami i między menedżerowie transakcji (zobacz poniższą ilustrację).</span><span class="sxs-lookup"><span data-stu-id="63c6a-117">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="63c6a-118">Specyfikacje opisano szczegółowo formaty wiadomości i wiadomości programu exchange na obu poziomach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="63c6a-118">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="63c6a-119">Niektóre bezpieczeństwa, niezawodności i kodowania dla aplikacji do aplikacji programu exchange mają zastosowanie tak samo, jak dla programu exchange regularne aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-119">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="63c6a-120">Pomyślne współdziałanie menedżerowie transakcji wymaga jednak umowy dla określonego powiązania, ponieważ zwykle nie jest skonfigurowany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="63c6a-120">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="63c6a-121">W tym temacie opisuje kompozycji specyfikacji WS-Atomic Transaction (WS-AT) z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-121">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="63c6a-122">Podejście opisane w niniejszym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS tym IBM, IONA Sun Microsystems i inne.</span><span class="sxs-lookup"><span data-stu-id="63c6a-122">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="63c6a-123">Na poniższym rysunku przedstawiono współdziałanie między dwa menedżerowie transakcji transakcji Menedżera 1 i 2 Menedżera transakcji, a dwie aplikacje aplikacji 1 i 2 aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-123">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="63c6a-124">![Protokoły transakcji](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span><span class="sxs-lookup"><span data-stu-id="63c6a-124">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="63c6a-125">Należy wziąć pod uwagę typowy scenariusz WS-koordynacji/protokołu WS-AT z jednego inicjatora (I) i jednego uczestnika (P).</span><span class="sxs-lookup"><span data-stu-id="63c6a-125">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="63c6a-126">Inicjator i uczestnika ma menedżerowie transakcji (ITM i PTM, odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="63c6a-126">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="63c6a-127">Dwufazowe nazywa się 2PC w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="63c6a-127">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63c6a-128">1. CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="63c6a-128">1. CreateCoordinationContext</span></span>|<span data-ttu-id="63c6a-129">12. Odpowiedzi na komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="63c6a-129">12. Application Message Response</span></span>|  
|<span data-ttu-id="63c6a-130">2. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="63c6a-130">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="63c6a-131">13. Zatwierdź (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="63c6a-131">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="63c6a-132">3. Rejestr (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="63c6a-132">3. Register (Completion)</span></span>|<span data-ttu-id="63c6a-133">14. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-133">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="63c6a-134">4. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="63c6a-134">4. RegisterResponse</span></span>|<span data-ttu-id="63c6a-135">15. Przygotowanie (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-135">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="63c6a-136">5. Komunikat aplikacji</span><span class="sxs-lookup"><span data-stu-id="63c6a-136">5. Application Message</span></span>|<span data-ttu-id="63c6a-137">16. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-137">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="63c6a-138">6. CreateCoordinationContext z kontekstem</span><span class="sxs-lookup"><span data-stu-id="63c6a-138">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="63c6a-139">17. Przygotowane (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-139">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="63c6a-140">7. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="63c6a-140">7. Register (Durable)</span></span>|<span data-ttu-id="63c6a-141">18. Zatwierdzone (zakończenia)</span><span class="sxs-lookup"><span data-stu-id="63c6a-141">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="63c6a-142">8. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="63c6a-142">8. RegisterResponse</span></span>|<span data-ttu-id="63c6a-143">19. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-143">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="63c6a-144">9. CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="63c6a-144">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="63c6a-145">20. Zatwierdź (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-145">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="63c6a-146">10. Rejestr (niezawodny)</span><span class="sxs-lookup"><span data-stu-id="63c6a-146">10. Register (Durable)</span></span>|<span data-ttu-id="63c6a-147">21. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-147">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="63c6a-148">11. RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="63c6a-148">11. RegisterResponse</span></span>|<span data-ttu-id="63c6a-149">22. Zatwierdzone (2PC)</span><span class="sxs-lookup"><span data-stu-id="63c6a-149">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="63c6a-150">Ten dokument opisuje kompozycji specyfikacji WS-AtomicTransaction z zabezpieczeniami oraz bezpiecznego powiązania, używany do komunikacji między menedżerami transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-150">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="63c6a-151">Podejście opisane w tym dokumencie zostały pomyślnie przetestowane z innych implementacji protokołu WS-AT i koordynacji WS.</span><span class="sxs-lookup"><span data-stu-id="63c6a-151">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="63c6a-152">Ilustracja i tabela przedstawiono cztery rodzaje komunikaty z punktu widzenia zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="63c6a-152">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="63c6a-153">Aktywacja wiadomości (CreateCoordinationContext i CreateCoordinationContextResponse).</span><span class="sxs-lookup"><span data-stu-id="63c6a-153">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="63c6a-154">Rejestracja wiadomości (rejestr i RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="63c6a-154">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="63c6a-155">Komunikaty protokołu (przygotowanie, wycofanie, zatwierdzania, przerwane i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="63c6a-155">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="63c6a-156">Komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-156">Application messages.</span></span>  
  
 <span data-ttu-id="63c6a-157">Pierwszy klas trzy wiadomości są traktowane jako wiadomości Menedżera transakcji i ich konfiguracja powiązania jest opisany w "Wymianie wiadomości aplikacji" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="63c6a-157">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="63c6a-158">Czwarty klasę wiadomości jest komunikatów aplikacji i jest opisana w sekcji "Komunikat przykłady" w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="63c6a-158">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="63c6a-159">W tej sekcji opisano powiązania protokołu używane dla każdego z tych klas przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63c6a-159">This section describes the protocol bindings used for each of these classes by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="63c6a-160">Następujące obszary nazw XML i prefiksy skojarzone są używane w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="63c6a-160">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="63c6a-161">Prefiks</span><span class="sxs-lookup"><span data-stu-id="63c6a-161">Prefix</span></span>|<span data-ttu-id="63c6a-162">Wersja</span><span class="sxs-lookup"><span data-stu-id="63c6a-162">Version</span></span>|<span data-ttu-id="63c6a-163">Identyfikator URI Namespace</span><span class="sxs-lookup"><span data-stu-id="63c6a-163">Namespace URI</span></span>|  
|------------|-------------|-------------------|  
|<span data-ttu-id="63c6a-164">S11</span><span class="sxs-lookup"><span data-stu-id="63c6a-164">s11</span></span>||[<span data-ttu-id="63c6a-165">http://go.microsoft.com/fwlink/?LinkId=96014</span><span class="sxs-lookup"><span data-stu-id="63c6a-165">http://go.microsoft.com/fwlink/?LinkId=96014</span></span>](http://go.microsoft.com/fwlink/?LinkId=96014)|  
|<span data-ttu-id="63c6a-166">wsa</span><span class="sxs-lookup"><span data-stu-id="63c6a-166">wsa</span></span>|<span data-ttu-id="63c6a-167">Wstępnie 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-167">Pre-1.0</span></span><br /><br /> <span data-ttu-id="63c6a-168">1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-168">1.0</span></span>|<span data-ttu-id="63c6a-169">http://www.w3.org/2004/08/Addressing</span><span class="sxs-lookup"><span data-stu-id="63c6a-169">http://www.w3.org/2004/08/addressing</span></span><br /><br /> [<span data-ttu-id="63c6a-170">http://go.microsoft.com/fwlink/?LinkId=96022</span><span class="sxs-lookup"><span data-stu-id="63c6a-170">http://go.microsoft.com/fwlink/?LinkId=96022</span></span>](http://go.microsoft.com/fwlink/?LinkId=96022)|  
|<span data-ttu-id="63c6a-171">wscoor</span><span class="sxs-lookup"><span data-stu-id="63c6a-171">wscoor</span></span>|<span data-ttu-id="63c6a-172">1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-172">1.0</span></span><br /><br /> <span data-ttu-id="63c6a-173">1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-173">1.1</span></span>|[<span data-ttu-id="63c6a-174">http://go.microsoft.com/fwlink/?LinkId=96078</span><span class="sxs-lookup"><span data-stu-id="63c6a-174">http://go.microsoft.com/fwlink/?LinkId=96078</span></span>](http://go.microsoft.com/fwlink/?LinkId=96078)<br /><br /> [<span data-ttu-id="63c6a-175">http://go.microsoft.com/fwlink/?LinkId=96079</span><span class="sxs-lookup"><span data-stu-id="63c6a-175">http://go.microsoft.com/fwlink/?LinkId=96079</span></span>](http://go.microsoft.com/fwlink/?LinkId=96079)|  
|<span data-ttu-id="63c6a-176">WSAT</span><span class="sxs-lookup"><span data-stu-id="63c6a-176">wsat</span></span>|<span data-ttu-id="63c6a-177">1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-177">1.0</span></span><br /><br /> <span data-ttu-id="63c6a-178">1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-178">1.1</span></span>|[<span data-ttu-id="63c6a-179">http://go.microsoft.com/fwlink/?LinkId=96080</span><span class="sxs-lookup"><span data-stu-id="63c6a-179">http://go.microsoft.com/fwlink/?LinkId=96080</span></span>](http://go.microsoft.com/fwlink/?LinkId=96080)<br /><br /> [<span data-ttu-id="63c6a-180">http://go.microsoft.com/fwlink/?LinkId=96081</span><span class="sxs-lookup"><span data-stu-id="63c6a-180">http://go.microsoft.com/fwlink/?LinkId=96081</span></span>](http://go.microsoft.com/fwlink/?LinkId=96081)|  
|<span data-ttu-id="63c6a-181">t</span><span class="sxs-lookup"><span data-stu-id="63c6a-181">t</span></span>|<span data-ttu-id="63c6a-182">1.3 wstępnie</span><span class="sxs-lookup"><span data-stu-id="63c6a-182">Pre-1.3</span></span><br /><br /> <span data-ttu-id="63c6a-183">1.3</span><span class="sxs-lookup"><span data-stu-id="63c6a-183">1.3</span></span>|[<span data-ttu-id="63c6a-184">http://go.microsoft.com/fwlink/?LinkId=96082</span><span class="sxs-lookup"><span data-stu-id="63c6a-184">http://go.microsoft.com/fwlink/?LinkId=96082</span></span>](http://go.microsoft.com/fwlink/?LinkId=96082)<br /><br /> [<span data-ttu-id="63c6a-185">http://go.microsoft.com/fwlink/?LinkId=96100</span><span class="sxs-lookup"><span data-stu-id="63c6a-185">http://go.microsoft.com/fwlink/?LinkId=96100</span></span>](http://go.microsoft.com/fwlink/?LinkId=96100)|  
|<span data-ttu-id="63c6a-186">O</span><span class="sxs-lookup"><span data-stu-id="63c6a-186">o</span></span>||[<span data-ttu-id="63c6a-187">http://go.microsoft.com/fwlink/?LinkId=96101</span><span class="sxs-lookup"><span data-stu-id="63c6a-187">http://go.microsoft.com/fwlink/?LinkId=96101</span></span>](http://go.microsoft.com/fwlink/?LinkId=96101)|  
|<span data-ttu-id="63c6a-188">XSD</span><span class="sxs-lookup"><span data-stu-id="63c6a-188">xsd</span></span>||[<span data-ttu-id="63c6a-189">http://go.microsoft.com/fwlink/?LinkId=96102</span><span class="sxs-lookup"><span data-stu-id="63c6a-189">http://go.microsoft.com/fwlink/?LinkId=96102</span></span>](http://go.microsoft.com/fwlink/?LinkId=96102)|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="63c6a-190">Menedżer transakcji powiązania</span><span class="sxs-lookup"><span data-stu-id="63c6a-190">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="63c6a-191">R1001: Udział w transakcji usługi WS-AT 1.0 menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2004/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-191">R1001: Transaction Managers participating in a WS-AT 1.0 transaction must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="63c6a-192">R1002: Udział w transakcji usługi WS-AT 1.1 menedżerowie transakcji należy użyć protokołu SOAP 1.1 i WS-Addressing 2005/08 dla protokołu WS-AT i wymiany wiadomości WS-koordynacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-192">R1002: Transaction Managers participating in a WS-AT 1.1 transaction must use SOAP 1.1 and WS-Addressing 2005/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="63c6a-193">Komunikaty aplikacji nie są ograniczone do tych powiązań i opisano później.</span><span class="sxs-lookup"><span data-stu-id="63c6a-193">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="63c6a-194">Powiązanie HTTPS Menedżera transakcji</span><span class="sxs-lookup"><span data-stu-id="63c6a-194">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="63c6a-195">Powiązanie HTTPS Menedżera transakcji korzysta wyłącznie z zabezpieczeń transportu, aby osiągnąć zabezpieczeń i ustanowienia relacji zaufania między każda para odbiornika nadawcy w drzewie transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-195">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="63c6a-196">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="63c6a-196">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="63c6a-197">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-197">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="63c6a-198">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegółów implementacji:</span><span class="sxs-lookup"><span data-stu-id="63c6a-198">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="63c6a-199">R1111: Certyfikatów X.509 przedstawianych przez sieć musi mieć nazwę podmiotu, która jest zgodna z w pełni kwalifikowaną nazwę (FQDN) komputera źródłowego.</span><span class="sxs-lookup"><span data-stu-id="63c6a-199">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="63c6a-200">B1112: DNS musi być funkcjonalności każda para odbiornika nadawcy w systemie kontroli nazwa podmiotu X.509 powiodło się.</span><span class="sxs-lookup"><span data-stu-id="63c6a-200">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="63c6a-201">Aktywacja i rejestracja powiązania konfiguracji</span><span class="sxs-lookup"><span data-stu-id="63c6a-201">Activation and Registration Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="63c6a-202">wymaga dwukierunkowego powiązania żądania/odpowiedzi z korelacją za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c6a-202"> requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="63c6a-203">(Aby uzyskać więcej informacji na temat korelacji i opisy wzorców wymiany wiadomości żądania/odpowiedzi, zobacz WS-Atomic Transaction, sekcja 8).</span><span class="sxs-lookup"><span data-stu-id="63c6a-203">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="63c6a-204">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="63c6a-204">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="63c6a-205">obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c6a-205"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="63c6a-206">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-206">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="63c6a-207">B1131: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-207">B1131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="63c6a-208">Menedżer transakcji mieszanym powiązania zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="63c6a-208">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="63c6a-209">Jest to alternatywny (tryb mieszany) powiązanie zabezpieczenia transportu używa połączeniu z modelem koordynacji WS wystawionego tokenu na potrzeby określania tożsamości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-209">This is an alternate (mixed mode) binding that uses transport security combined with the WS-Coordination Issued Token model for identity establishment purposes.</span></span> <span data-ttu-id="63c6a-210">Aktywacji i rejestracji są tylko elementy, które różnią się między dwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="63c6a-210">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="63c6a-211">Konfiguracja HTTPS transportu</span><span class="sxs-lookup"><span data-stu-id="63c6a-211">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="63c6a-212">Certyfikaty X.509 są używane do ustalenia tożsamości menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-212">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="63c6a-213">Wymagane jest uwierzytelnienie klienta i serwera, a klient/serwer autoryzacji pozostaje szczegóły implementacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-213">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="63c6a-214">Konfiguracja powiązania komunikat aktywacji</span><span class="sxs-lookup"><span data-stu-id="63c6a-214">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="63c6a-215">Aktywacja komunikaty zwykle nie uczestniczą w współdziałanie ponieważ zwykle występują między aplikacją a jego lokalnego Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-215">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="63c6a-216">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) dla wiadomości aktywacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-216">B1221: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="63c6a-217">Skorelowane żądanie i odpowiedź przy użyciu protokołu WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="63c6a-217">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="63c6a-218">Specyfikacja WS-Atomic Transaction, 8 sekcji opisano dalsze szczegóły dotyczące korelacji i wzorce wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-218">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="63c6a-219">R1222: odebrane `CreateCoordinationContext`, należy wygenerować koordynator `SecurityContextToken` z skojarzony klucz tajny `STx`.</span><span class="sxs-lookup"><span data-stu-id="63c6a-219">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="63c6a-220">Token ten jest zwracany wewnątrz `t:IssuedTokens` nagłówka następującej specyfikacji WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="63c6a-220">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="63c6a-221">R1223: W przypadku aktywacji w ramach istniejącego kontekstu koordynacji `t:IssuedTokens` nagłówek o `SecurityContextToken` skojarzony z istniejącym kontekstu musi przepływać na `CreateCoordinationContext` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-221">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="63c6a-222">Nowy `t:IssuedTokens` nagłówka ma być generowany dla dołączania do wychodzącej `wscoor:CreateCoordinationContextResponse` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-222">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="63c6a-223">Konfiguracja powiązania komunikatu rejestracji</span><span class="sxs-lookup"><span data-stu-id="63c6a-223">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="63c6a-224">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa dwukierunkowego powiązania HTTPS (opisany w [protokoły obsługi komunikatów](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span><span class="sxs-lookup"><span data-stu-id="63c6a-224">B1231: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="63c6a-225">Skorelowane żądanie i odpowiedź przy użyciu protokołu WS-Addressing 2004/08 WS-AT 1.0 i WS-Addressing 2005/08 1.1 WS-AT.</span><span class="sxs-lookup"><span data-stu-id="63c6a-225">Request and Reply messages are correlated using WS-Addressing 2004/08 for WS-AT 1.0 and WS-Addressing 2005/08 for WS-AT 1.1.</span></span>  
  
 <span data-ttu-id="63c6a-226">WS-AtomicTransaction, 8 sekcji, w tym artykule opisano dodatkowe szczegóły dotyczące korelacji i opisy wzorców wymiany wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-226">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="63c6a-227">R1232: Wychodzące `wscoor:Register` komunikaty muszą używać `IssuedTokenOverTransport` tryb uwierzytelniania opisanego w [protokołów zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="63c6a-227">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="63c6a-228">`wsse:Timestamp` Elementu muszą być podpisane przy użyciu `SecurityContextToken``STx` wystawione.</span><span class="sxs-lookup"><span data-stu-id="63c6a-228">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="63c6a-229">Podpis jest potwierdzenie posiadania token skojarzony z określonej transakcji i jest używany do uwierzytelniania uczestnika rejestracji w transakcji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-229">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="63c6a-230">RegistrationResponse wiadomości jest ponownie przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c6a-230">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="63c6a-231">Konfiguracja powiązania protokołu 2PC</span><span class="sxs-lookup"><span data-stu-id="63c6a-231">2PC Protocol Binding Configuration</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="63c6a-232">obsługuje komunikaty jednokierunkowe (datagram) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="63c6a-232"> supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="63c6a-233">Szczegóły implementacji pozostaje korelacji między wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-233">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="63c6a-234">B1241: Implementacje musi obsługiwać `wsa:ReferenceParameters` zgodnie z opisem w WS-Addressing, aby osiągnąć korelacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]firmy 2PC wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-234">B1241: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="63c6a-235">Komunikat aplikacji programu Exchange</span><span class="sxs-lookup"><span data-stu-id="63c6a-235">Application Message Exchange</span></span>  
 <span data-ttu-id="63c6a-236">Aplikacje mogą użyć dowolnego określonego powiązania dla komunikatów aplikacji do aplikacji, tak długo, jak powiązania spełnia następujące wymagania dotyczące zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="63c6a-236">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="63c6a-237">R2001: Komunikatów aplikacji do aplikacji musi przepływać `t:IssuedTokens` nagłówka wraz z programem `CoordinationContext` w nagłówku wiadomości.</span><span class="sxs-lookup"><span data-stu-id="63c6a-237">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="63c6a-238">R2002: Integralności i poufności `t:IssuedToken` należy podać.</span><span class="sxs-lookup"><span data-stu-id="63c6a-238">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="63c6a-239">`CoordinationContext` Nagłówek zawiera `wscoor:Identifier`.</span><span class="sxs-lookup"><span data-stu-id="63c6a-239">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="63c6a-240">Podczas definicji `xsd:AnyURI` umożliwia wykorzystanie bezwzględne i względne identyfikatory URI, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko `wscoor:Identifiers`, będące bezwzględny identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="63c6a-240">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="63c6a-241">B2003: Jeśli `wscoor:Identifier` z `wscoor:CoordinationContext` jest względnym identyfikatorem URI, błędów, które zostaną zwrócone z transakcyjnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="63c6a-241">B2003: If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="63c6a-242">Przykłady wiadomości</span><span class="sxs-lookup"><span data-stu-id="63c6a-242">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="63c6a-243">Komunikaty CreateCoordinationContext żądania/odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="63c6a-243">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="63c6a-244">Następujące komunikaty wykonaj wzorzec żądań i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="63c6a-244">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext-with-wscoor-10"></a><span data-ttu-id="63c6a-245">CreateCoordinationContext z WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-245">CreateCoordinationContext with WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontext-with-wscoor-11"></a><span data-ttu-id="63c6a-246">CreateCoordinationContext z WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-246">CreateCoordinationContext with WSCoor 1.1</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-pre-13-and-wscoor-10"></a><span data-ttu-id="63c6a-247">CreateCoordinationContextResponse zaufania Pre-1.3 i WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-247">CreateCoordinationContextResponse with Trust Pre-1.3 and WSCoor 1.0</span></span>  
  
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
  
#### <a name="createcoordinationcontextresponse-with-trust-13-and-wscoor-11"></a><span data-ttu-id="63c6a-248">CreateCoordinationContextResponse zaufania 1.3 i WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-248">CreateCoordinationContextResponse with Trust 1.3 and WSCoor 1.1</span></span>  
  
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
  
### <a name="registration-messages"></a><span data-ttu-id="63c6a-249">Rejestracja wiadomości</span><span class="sxs-lookup"><span data-stu-id="63c6a-249">Registration Messages</span></span>  
 <span data-ttu-id="63c6a-250">Następujące komunikaty są komunikaty rejestracji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-250">The following messages are registration messages.</span></span>  
  
#### <a name="register-with-wscoor-10"></a><span data-ttu-id="63c6a-251">Zarejestruj WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-251">Register with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-with-wscoor-11"></a><span data-ttu-id="63c6a-252">Zarejestruj WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-252">Register with WSCoor 1.1</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-10"></a><span data-ttu-id="63c6a-253">Zarejestruj odpowiedzi WSCoor 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-253">Register Response with WSCoor 1.0</span></span>  
  
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
  
#### <a name="register-response-with-wscoor-11"></a><span data-ttu-id="63c6a-254">Zarejestruj odpowiedzi WSCoor 1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-254">Register Response with WSCoor 1.1</span></span>  
  
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
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="63c6a-255">Dwa komunikaty protokołu zatwierdzania fazy</span><span class="sxs-lookup"><span data-stu-id="63c6a-255">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="63c6a-256">Następujący komunikat odnosi się do protokołu dwufazowego (2PC).</span><span class="sxs-lookup"><span data-stu-id="63c6a-256">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit-with-wsat-10"></a><span data-ttu-id="63c6a-257">Zatwierdź z WSAT 1.0</span><span class="sxs-lookup"><span data-stu-id="63c6a-257">Commit with WSAT 1.0</span></span>  
  
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
  
#### <a name="commit-with-wsat-11"></a><span data-ttu-id="63c6a-258">Zatwierdź z WSAT 1.1</span><span class="sxs-lookup"><span data-stu-id="63c6a-258">Commit with WSAT 1.1</span></span>  
  
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
  
### <a name="application-messages"></a><span data-ttu-id="63c6a-259">Komunikatów aplikacji</span><span class="sxs-lookup"><span data-stu-id="63c6a-259">Application Messages</span></span>  
 <span data-ttu-id="63c6a-260">Następujące komunikaty są komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63c6a-260">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="63c6a-261">Komunikat żądania aplikacji</span><span class="sxs-lookup"><span data-stu-id="63c6a-261">Application message-Request</span></span>  
  
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

---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c29b3900a36d8d5c41fee49c408a2e3fdf67680b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991422"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="a196e-102">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="a196e-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="a196e-103">Wyjątki są używane do komunikowania się błędy lokalnie w implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="a196e-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="a196e-104">Błędy, z drugiej strony, są używane do komunikacji błędów przez granice usługi, takie jak z serwera do klienta lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="a196e-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="a196e-105">Oprócz błędów kanały transportu często używają mechanizmów specyficznych dla transportu do komunikowania się błędy na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="a196e-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="a196e-106">Na przykład transportu HTTP używa kodów stanu, takie jak 404 do komunikowania się nieistniejące adresu URL punktu końcowego (jest nie punktu końcowego do odesłania błędów).</span><span class="sxs-lookup"><span data-stu-id="a196e-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="a196e-107">Ten dokument zawiera trzy sekcje, które zapewniają wskazówki autorom w niestandardowym kanale.</span><span class="sxs-lookup"><span data-stu-id="a196e-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="a196e-108">Pierwsza sekcja zawiera wskazówki dotyczące kiedy i jak zdefiniować i zgłaszać wyjątki.</span><span class="sxs-lookup"><span data-stu-id="a196e-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="a196e-109">Druga sekcja zawiera wskazówki dotyczące generowania i korzystanie z błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="a196e-110">Trzecia sekcja wyjaśnia, jak Podaj informacje o śledzeniu ułatwiające użytkownika niestandardowego kanału Rozwiązywanie problemów z uruchomionych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="a196e-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="a196e-111">Exceptions</span></span>  
 <span data-ttu-id="a196e-112">Istnieją dwie rzeczy, o których należy pamiętać, gdy zostanie zgłoszony wyjątek: Najpierw musi być typu, który pozwala użytkownikom na zapis poprawny kod, który pozwala reagować odpowiednio do wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a196e-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="a196e-113">Po drugie ma dostarczać wystarczających informacji dla użytkownika, aby zrozumieć, co poszło źle, wpływ awarii i sposobie jego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a196e-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="a196e-114">W poniższych sekcjach znajdują się wskazówki dotyczące typów wyjątków i wiadomości w kanałach usługi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a196e-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="a196e-115">Istnieje również ogólne wskazówki dotyczące wyjątków na platformie .NET w wytycznych projektowych dla dokumentu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a196e-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="a196e-116">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="a196e-116">Exception Types</span></span>  
 <span data-ttu-id="a196e-117">Wszystkie wyjątki generowane przez kanały musi być albo <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, lub typ pochodzący od <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="a196e-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="a196e-118">(Wyjątki, takie jak <xref:System.ObjectDisposedException> może również zostać wygenerowany, ale tylko do wskazania, że kod wywołujący ma niewłaściwego użycia kanału.</span><span class="sxs-lookup"><span data-stu-id="a196e-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="a196e-119">Jeśli kanał jest prawidłowo używana, jego musi tylko wyrzucić danego.) Usługi WCF zawiera siedem typy wyjątków, które wynikają z <xref:System.ServiceModel.CommunicationException> i są przeznaczone do użycia przez kanały.</span><span class="sxs-lookup"><span data-stu-id="a196e-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="a196e-120">Istnieją inne <xref:System.ServiceModel.CommunicationException>-pochodnych wyjątki, które są przeznaczone do użytku przez inne części systemu.</span><span class="sxs-lookup"><span data-stu-id="a196e-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="a196e-121">Te typy wyjątków to:</span><span class="sxs-lookup"><span data-stu-id="a196e-121">These exception types are:</span></span>  
  
|<span data-ttu-id="a196e-122">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="a196e-122">Exception Type</span></span>|<span data-ttu-id="a196e-123">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="a196e-123">Meaning</span></span>|<span data-ttu-id="a196e-124">Wyjątek wewnętrzny zawartości</span><span class="sxs-lookup"><span data-stu-id="a196e-124">Inner Exception Content</span></span>|<span data-ttu-id="a196e-125">Strategia odzyskiwania</span><span class="sxs-lookup"><span data-stu-id="a196e-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="a196e-126">Adres punktu końcowego, określony w celu nasłuchiwania jest już używana.</span><span class="sxs-lookup"><span data-stu-id="a196e-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="a196e-127">Jeśli jest obecny, zawiera więcej szczegółów na temat błędów transportu, który spowodował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a196e-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="a196e-128">Na przykład.</span><span class="sxs-lookup"><span data-stu-id="a196e-128">For example.</span></span> <span data-ttu-id="a196e-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, lub <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="a196e-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="a196e-130">Spróbuj użyć innego adresu.</span><span class="sxs-lookup"><span data-stu-id="a196e-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="a196e-131">Proces nie ma mieć dostęp do adresu punktu końcowego określonego w celu nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="a196e-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="a196e-132">Jeśli jest obecny, zawiera więcej szczegółów na temat błędów transportu, który spowodował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a196e-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="a196e-133">Na przykład <xref:System.IO.PipeException>, lub <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="a196e-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="a196e-134">Spróbuj przy użyciu różnych poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="a196e-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="a196e-135"><xref:System.ServiceModel.ICommunicationObject> Używane jest w stanie Faulted (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="a196e-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="a196e-136">Należy zwrócić uwagę, czy, gdy obiekt z wieloma oczekujących połączeń, przechodzi do stanu Faulted tylko jedno wywołanie zgłasza wyjątek, który jest powiązany z awarii i pozostałe throw wywołania <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="a196e-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="a196e-137">To zwykle wyjątek, ponieważ aplikacja overlooks wyjątek i próbuje użyć obiektu już uszkodzoną, prawdopodobnie w wątku innego niż ten, który Przechwycono wyjątek oryginalny.</span><span class="sxs-lookup"><span data-stu-id="a196e-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="a196e-138">Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="a196e-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="a196e-139">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="a196e-139">Create a new object.</span></span> <span data-ttu-id="a196e-140">Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> błędów w pierwszej kolejności, może istnieć inne prace wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="a196e-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="a196e-141"><xref:System.ServiceModel.ICommunicationObject> Używany zostało przerwane (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="a196e-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="a196e-142">Podobnie jak <xref:System.ServiceModel.CommunicationObjectFaultedException>, jego wyjątku wskazuje Aplikacja wywołała <xref:System.ServiceModel.ICommunicationObject.Abort%2A> dla obiektu, prawdopodobnie z innego wątku, i obiekt nie jest już możliwe z tego powodu.</span><span class="sxs-lookup"><span data-stu-id="a196e-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="a196e-143">Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="a196e-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="a196e-144">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="a196e-144">Create a new object.</span></span> <span data-ttu-id="a196e-145">Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> przerwania w pierwszej kolejności, może być inne prace wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="a196e-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="a196e-146">Zdalny punkt końcowy docelowy nie nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="a196e-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="a196e-147">Może to wynikać z dowolnej części adresu punktu końcowego jest niepoprawny, nierozwiązywalny lub punktu końcowego są w dół.</span><span class="sxs-lookup"><span data-stu-id="a196e-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="a196e-148">Przykłady obejmują błąd DNS, Menedżer kolejki nie są dostępne, a usługa nie działa.</span><span class="sxs-lookup"><span data-stu-id="a196e-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="a196e-149">Wyjątek wewnętrzny zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="a196e-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="a196e-150">Spróbuj użyć innego adresu.</span><span class="sxs-lookup"><span data-stu-id="a196e-150">Try a different address.</span></span> <span data-ttu-id="a196e-151">Alternatywnie nadawca może Poczekaj chwilę i spróbuj ponownie w przypadku, gdy usługa nie działa</span><span class="sxs-lookup"><span data-stu-id="a196e-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="a196e-152">Protokoły komunikacyjne zgodnie z opisem w zasadach punktu końcowego niezgodność między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="a196e-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="a196e-153">Na przykład ramek niezgodność typu zawartości lub Przekroczono rozmiar maksymalny komunikatu.</span><span class="sxs-lookup"><span data-stu-id="a196e-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="a196e-154">Jeśli jest obecny zawiera więcej informacji o błędzie określony protokół.</span><span class="sxs-lookup"><span data-stu-id="a196e-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="a196e-155">Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wewnętrzny wyjątek, gdy przekracza MaxReceivedMessageSize przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="a196e-156">Odzyskiwanie: Upewnij się, nadawca i odebranych protokół, które ustawienia są zgodne.</span><span class="sxs-lookup"><span data-stu-id="a196e-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="a196e-157">Jednym ze sposobów, w tym celu jest ponownie zaimportować metadane punktu końcowego usługi (zasady) i umożliwia powiązanie wygenerowany ponownie utworzyć kanał.</span><span class="sxs-lookup"><span data-stu-id="a196e-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="a196e-158">Zdalny punkt końcowy nasłuchuje, ale nie jest gotowa do przetwarzania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a196e-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="a196e-159">Jeśli jest obecny, wyjątek wewnętrzny zawiera błąd protokołu SOAP lub szczegóły błędu na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="a196e-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="a196e-160">Odzyskiwanie: Zaczekaj i spróbuj ponownie wykonać operację później.</span><span class="sxs-lookup"><span data-stu-id="a196e-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="a196e-161">Operacja nie powiodła się przed upływem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="a196e-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="a196e-162">Może dostarczyć szczegóły limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="a196e-162">May provide details about the timeout.</span></span>|<span data-ttu-id="a196e-163">Zaczekaj i spróbuj ponownie wykonać operację później.</span><span class="sxs-lookup"><span data-stu-id="a196e-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="a196e-164">Zdefiniuj nowy typ wyjątku, tylko wtedy, gdy tego typu odnosi się do strategii odzyskiwania różni się od wszystkich istniejących typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a196e-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="a196e-165">Jeśli zdefiniujesz nowy typ wyjątku, musi pochodzić od <xref:System.ServiceModel.CommunicationException> lub jedna z jej klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="a196e-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="a196e-166">Komunikaty o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="a196e-166">Exception Messages</span></span>  
 <span data-ttu-id="a196e-167">Komunikaty o wyjątkach są przeznaczone dla użytkownika nie program tak powinien zapewniają wystarczające informacje, aby pomóc użytkownikowi zrozumieć i rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="a196e-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="a196e-168">Są trzy podstawowe części komunikatu wyjątku dobrej:</span><span class="sxs-lookup"><span data-stu-id="a196e-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="a196e-169">Co się stało.</span><span class="sxs-lookup"><span data-stu-id="a196e-169">What happened.</span></span> <span data-ttu-id="a196e-170">Wyczyść opisz problem przy użyciu terminów, które odnoszą się do komputera przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a196e-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="a196e-171">Na przykład komunikat o wyjątku zły będzie "Nieprawidłowa konfiguracja sekcji".</span><span class="sxs-lookup"><span data-stu-id="a196e-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="a196e-172">Spowoduje to pozostawienie użytkownika zastanawiasz się, które sekcji konfiguracji jest nieprawidłowy i dlaczego jest on nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a196e-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="a196e-173">Ulepszony komunikat będzie "Nieprawidłowa konfiguracja sekcji \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="a196e-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="a196e-174">Komunikat o jeszcze lepiej byłoby "nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie ma już o nazwie myTransport transportu".</span><span class="sxs-lookup"><span data-stu-id="a196e-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="a196e-175">Jest to bardzo szczegółowy komunikat o błędzie, przy użyciu nazwy użytkownika można łatwo zidentyfikować i warunki, w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="a196e-176">Istnieją jednak jeszcze kilka kluczowych składników. ich brak.</span><span class="sxs-lookup"><span data-stu-id="a196e-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="a196e-177">Znaczenia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-177">The significance of the error.</span></span> <span data-ttu-id="a196e-178">O ile nie jest wyświetlony komunikat z informacją wyraźnie oznacza błąd, użytkownik prawdopodobnie zastanawiasz się, czy jest to błąd krytyczny lub jeśli można go zignorować.</span><span class="sxs-lookup"><span data-stu-id="a196e-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="a196e-179">Ogólnie rzecz biorąc komunikaty powinny prowadzić z znaczenia lub znaczenia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="a196e-180">Aby poprawić w poprzednim przykładzie, może być komunikat "ServiceHost nie udało się otwarty z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie jest już o nazwie myTransport transportu ".</span><span class="sxs-lookup"><span data-stu-id="a196e-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="a196e-181">Jak użytkownika powinno rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="a196e-181">How the user should correct the problem.</span></span> <span data-ttu-id="a196e-182">Najważniejsza część komunikatu pomaga rozwiązać problem użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a196e-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="a196e-183">Komunikat powinien zawierać wskazówek lub wskazówek na temat, co należy sprawdzić lub usunąć w celu rozwiązania problemu.</span><span class="sxs-lookup"><span data-stu-id="a196e-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="a196e-184">Na przykład "ServiceHost nie udało się otwarty z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport powiązanie o nazwie myBinding, ponieważ powiązanie jest już o nazwie myTransport transportu.</span><span class="sxs-lookup"><span data-stu-id="a196e-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="a196e-185">Upewnij się, że istnieje tylko jeden transportu w powiązaniu".</span><span class="sxs-lookup"><span data-stu-id="a196e-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="a196e-186">Błędy przekazywania</span><span class="sxs-lookup"><span data-stu-id="a196e-186">Communicating Faults</span></span>  
 <span data-ttu-id="a196e-187">Protokołu SOAP 1.1 i SOAP 1.2 należy zdefiniować strukturę określonych błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="a196e-188">Istnieją pewne różnice między dwoma specyfikacje, ale ogólnie rzecz biorąc, wiadomości i MessageFault typy są używane do tworzenia i wykorzystywania błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="a196e-189">![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="a196e-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="a196e-190">SOAP 1.2 błędów (po lewej) i protokołu SOAP 1.1 (po prawej) błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="a196e-191">Należy pamiętać, że w SOAP 1.1 element błędów kwalifikowanych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a196e-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="a196e-192">Protokołu SOAP definiuje komunikatu o błędzie jako komunikat, który zawiera element błędów (element, którego nazwa jest `<env:Fault>`) jako element podrzędny elementu `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="a196e-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="a196e-193">Zawartość elementu błędów się nieznacznie różnić między SOAP 1.1 i SOAP 1.2, jak pokazano na rysunku 1.</span><span class="sxs-lookup"><span data-stu-id="a196e-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="a196e-194">Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasy normalizuje te różnice w jeden obiekt modelu:</span><span class="sxs-lookup"><span data-stu-id="a196e-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 <span data-ttu-id="a196e-195">`Code` Właściwość odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="a196e-196">Protokołu SOAP 1.2 definiuje pięć dopuszczalnych wartości dla `faultCode` (na przykład nadawcy i odbiorcy) i definiuje `Subcode` element, który może zawierać żadnej wartości podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a196e-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="a196e-197">(Zobacz [specyfikacji protokołu SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) listę kodów błędów dopuszczalny rozmiar oraz ich znaczenie.) Protokołu SOAP 1.1 ma nieco inny mechanizm: Definiuje cztery `faultCode` wartości (na przykład klient i serwer), które można rozszerzyć, definiując całkowicie nowe lub przy użyciu notacji z kropką w celu utworzenia bardziej szczegółowe `faultCodes`, na przykład Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="a196e-197">(See the [SOAP 1.2 specification](https://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="a196e-198">Używanie MessageFault na błędy programu, FaultCode.Name i FaultCode.Namespace mapuje nazwę i przestrzeń nazw protokołu SOAP 1.2 `env:Code` lub SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="a196e-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="a196e-199">Mapuje FaultCode.SubCode `env:Subcode` dla SOAP 1.2 i ma wartość null dla protokołu SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="a196e-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="a196e-200">Należy utworzyć nowych odporności kody podrzędne (lub nowe kody błędów, jeśli przy użyciu protokołu SOAP 1.1) Jeśli interesujące programowo rozróżnienie błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="a196e-201">Jest to analogiczne do tworzenia nowego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a196e-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="a196e-202">Należy unikać, używając zapisu kropkowego z kodami błędów SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="a196e-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="a196e-203">( [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) również zachęca do używania notacji z kropką kodu błędu.)</span><span class="sxs-lookup"><span data-stu-id="a196e-203">(The [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 <span data-ttu-id="a196e-204">`Reason` Właściwość odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) zrozumiałą dla użytkownika opis warunku błędu odpowiednikiem komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a196e-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="a196e-205">`FaultReason` Klasy (i protokołu SOAP `env:Reason/faultString`) ma wbudowaną obsługę posiadanie wielu tłumaczeń w celu globalizacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 <span data-ttu-id="a196e-206">Zawartość szczegółów błędów są dostępne w MessageFault przy użyciu różnych metod, w tym `GetDetail` \<T > i `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="a196e-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="a196e-207">Szczegóły błędów jest elementem nieprzezroczyste przenoszenia dodatkowe szczegóły dotyczące błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="a196e-208">Jest to przydatne w przypadku niektórych dowolnego szczegółów ze strukturą, które należy wykonać przy użyciu błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="a196e-209">Generowanie błędów</span><span class="sxs-lookup"><span data-stu-id="a196e-209">Generating Faults</span></span>  
 <span data-ttu-id="a196e-210">W tej sekcji opisano proces generowania błąd w odpowiedzi na wykryte w kanale lub we właściwości wiadomości, utworzone przez kanał jest w stanie błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="a196e-211">Typowym przykładem jest wysyłanie ponownie błąd w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="a196e-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="a196e-212">Podczas generowania usterki, niestandardowy kanał nie ma wysyłać usterki bezpośrednio, zamiast powinien zgłosić wyjątek i pozwól warstwy nad zdecydować, czy można przekonwertować tego wyjątku do awarii i jak wysłać go.</span><span class="sxs-lookup"><span data-stu-id="a196e-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="a196e-213">Do pomocy w tej konwersji, powinien udostępniać kanał `FaultConverter` wdrożenia, który można przekonwertować wyjątek w niestandardowym kanale odpowiednią odporność.</span><span class="sxs-lookup"><span data-stu-id="a196e-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="a196e-214">`FaultConverter` definiuje się następująco:</span><span class="sxs-lookup"><span data-stu-id="a196e-214">`FaultConverter` is defined as:</span></span>  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 <span data-ttu-id="a196e-215">Poszczególnych kanałów, które generuje błędy niestandardowe musi implementować `FaultConverter` i przywrócić go po wywołaniu `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="a196e-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="a196e-216">Niestandardowy `OnTryCreateFaultMessage` implementacji należy przekonwertować wyjątek usterki lub delegować do kanału wewnętrzny `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="a196e-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="a196e-217">Jeśli kanał jest transport go należy przekonwertować wyjątek lub przekazać do kodera `FaultConverter` lub wartość domyślną `FaultConverter` dostarczane w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="a196e-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="a196e-218">Wartość domyślna `FaultConverter` konwertuje błędy komunikaty o błędach określone przez WS-Addressing i protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="a196e-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="a196e-219">Oto przykład `OnTryCreateFaultMessage` implementacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="a196e-220">Domniemanie tego wzorca jest, że wyjątki zgłaszane między warstwami dla warunków błędu, które wymagają błędów musi zawierać wystarczających informacji dla odpowiednich generatora błędów do utworzenia poprawne błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="a196e-221">Jako autor niestandardowym kanale może zdefiniować typy wyjątków, które odpowiadają warunki w różnych domenach błędów, jeśli takie wyjątki jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a196e-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="a196e-222">Należy zauważyć, że wyjątki przechodzenie warstwach kanału skontaktować się warunek błędu, a nie dane nieprzezroczyste błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="a196e-223">Kategorie błędów</span><span class="sxs-lookup"><span data-stu-id="a196e-223">Fault Categories</span></span>  
 <span data-ttu-id="a196e-224">Zazwyczaj istnieją trzy kategorie błędów:</span><span class="sxs-lookup"><span data-stu-id="a196e-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="a196e-225">Błędy, które są rozpowszechniona w całym stosie.</span><span class="sxs-lookup"><span data-stu-id="a196e-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="a196e-226">Te błędy można napotkał w dowolnej warstwie stosu kanału, na przykład InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="a196e-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="a196e-227">Błędy, które mogą być napotkał dowolne miejsce powyżej wybranej warstwie w stosie na przykład niektóre błędy, które odnoszą się do transakcji lub do ról zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a196e-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="a196e-228">Błędy, które są kierowane w pojedynczej warstwie w stosie, na przykład błędy, takie jak błędy numer sekwencji WS-RM.</span><span class="sxs-lookup"><span data-stu-id="a196e-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="a196e-229">Kategoria 1.</span><span class="sxs-lookup"><span data-stu-id="a196e-229">Category 1.</span></span> <span data-ttu-id="a196e-230">Błędy są zazwyczaj WS-Addressing i błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="a196e-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="a196e-231">Podstawa `FaultConverter` klasy dostarczone przez architekturę WCF błędy konwertuje komunikaty o błędach określić WS-Addressing i protokołu SOAP, dzięki czemu nie trzeba obsługiwać konwersji tych wyjątków samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a196e-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="a196e-232">Kategoria 2.</span><span class="sxs-lookup"><span data-stu-id="a196e-232">Category 2.</span></span> <span data-ttu-id="a196e-233">Błędy występują, gdy warstwa dodaje właściwość do komunikat, który nie używa całkowicie informacji wiadomości, które odnoszą się do tej warstwy.</span><span class="sxs-lookup"><span data-stu-id="a196e-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="a196e-234">Błędy mogą zostać wykryte później, gdy wyższej warstwie prosi właściwości wiadomości do przetwarzania wiadomości dalszych informacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="a196e-235">Takie kanałów powinny implementować `GetProperty` określonej wcześniej, aby umożliwić wyższej warstwie do odesłania poprawne błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="a196e-236">Na przykład jest TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="a196e-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="a196e-237">Ta właściwość jest dodawany do wiadomości bez w pełni sprawdzania poprawności wszystkie dane w nagłówku (w ten sposób może obejmować, kontaktując się z koordynatorem transakcji rozproszonych (DTC).</span><span class="sxs-lookup"><span data-stu-id="a196e-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="a196e-238">Kategoria 3.</span><span class="sxs-lookup"><span data-stu-id="a196e-238">Category 3.</span></span> <span data-ttu-id="a196e-239">Błędy tylko są generowane i wysyłane przez warstwę w procesorze.</span><span class="sxs-lookup"><span data-stu-id="a196e-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="a196e-240">W związku z tym wszystkie wyjątki są zawarte w obrębie warstwy.</span><span class="sxs-lookup"><span data-stu-id="a196e-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="a196e-241">Aby poprawić spójność kanałów i łatwość konserwacji, niestandardowy kanał należy używać ze wzorcem określonym wcześniej do wygenerowania komunikaty o błędach nawet w przypadku błędów wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="a196e-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="a196e-242">Interpretowanie błędy odebrane</span><span class="sxs-lookup"><span data-stu-id="a196e-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="a196e-243">Ta sekcja zawiera wskazówki dotyczące generowania odpowiedni wyjątek podczas odbierania komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a196e-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="a196e-244">Drzewo decyzyjne dla przetwarzania komunikatu w każdej warstwie stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="a196e-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="a196e-245">Jeśli warstwa uwzględnia komunikatu jest nieprawidłowy, warstwy należy wykonać przetwarzanie "nieprawidłowy komunikat".</span><span class="sxs-lookup"><span data-stu-id="a196e-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="a196e-246">Takie przetwarzanie zależy od warstwy mogą jednak zawierać porzucenie wiadomości, śledzenia, lub zostanie zgłoszony wyjątek są konwertowane na błąd.</span><span class="sxs-lookup"><span data-stu-id="a196e-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="a196e-247">Przykłady obejmują zabezpieczeń odbiera komunikat, który nie jest właściwie zabezpieczona lub odebranie komunikatu z liczbą sekwencji zły Menedżera zasobów.</span><span class="sxs-lookup"><span data-stu-id="a196e-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="a196e-248">W przeciwnym razie jeśli komunikat jest komunikat o błędzie, który odnosi się do warstwy, a komunikat nie ma sensu poza interakcji warstwy, warstwy powinna obsługiwać warunku błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="a196e-249">Na przykład jest błąd odmowa sekwencji Menedżera zasobów jest całkowicie nieprzydatna warstwy powyżej kanału Menedżera zasobów i oznacza to spowodowaniem błędu kanału Menedżera zasobów i zgłaszanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="a196e-250">W przeciwnym razie komunikat powinien być zwracane z Request() lub Receive().</span><span class="sxs-lookup"><span data-stu-id="a196e-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="a196e-251">Obejmuje to przypadki, w której warstwie rozpoznaje usterki, ale błędu tylko wskazuje, że żądanie nie powiodło się, a nie oznacza spowodowaniem błędu kanału i zgłaszanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="a196e-252">Aby zwiększyć użyteczność w takiej sytuacji, należy zaimplementować warstwy `GetProperty<FaultConverter>` i zwracają `FaultConverter` klasy, który można przekonwertować błąd wyjątku przez zastąpienie `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="a196e-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="a196e-253">Poniższy model obiektów obsługuje konwertowania komunikaty wyjątków:</span><span class="sxs-lookup"><span data-stu-id="a196e-253">The following object model supports converting messages to exceptions:</span></span>  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 <span data-ttu-id="a196e-254">Warstwy kanału można zaimplementować `GetProperty<FaultConverter>` do obsługi konwersji komunikaty o błędach do wyjątków.</span><span class="sxs-lookup"><span data-stu-id="a196e-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="a196e-255">Aby to zrobić, należy zastąpić `OnTryCreateException` i sprawdź komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a196e-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="a196e-256">Jeśli rozpoznany, przeprowadzić konwersję, w przeciwnym razie poproś kanału wewnętrzny, aby przekonwertować go.</span><span class="sxs-lookup"><span data-stu-id="a196e-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="a196e-257">Kanały transportu powinny delegować metody do `FaultConverter.GetDefaultFaultConverter` by otrzymać domyślny FaultConverter protokołu SOAP/WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="a196e-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="a196e-258">Typowa implementacja wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="a196e-258">A typical implementation looks like this:</span></span>  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 <span data-ttu-id="a196e-259">Dla warunków określonych błędów, które mają scenariuszy odzyskiwania distinct, należy wziąć pod uwagę definiujący klasę pochodną z `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="a196e-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="a196e-260">Przetwarzanie MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="a196e-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="a196e-261">Protokołu SOAP definiuje ogólnych błędów do sygnalizowania, że wymagany nagłówek nie został zrozumiany przez odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="a196e-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="a196e-262">Ten błąd jest znany jako `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="a196e-263">W programie WCF, nigdy nie Generuj niestandardowe kanały `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="a196e-264">Zamiast tego dyspozytora WCF, która znajduje się w górnej części stos komunikacji WCF, sprawdza, że wszystkie nagłówki, które zostały oznaczone jako MustUndestand = true były zrozumiałe stosu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a196e-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="a196e-265">Jeśli dowolny nie były zrozumiałe `mustUnderstand` błąd jest zgłaszany w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="a196e-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="a196e-266">(Użytkownik może wybrać wyłączyć to `mustUnderstand` przetwarzania i wdróż aplikację otrzymywać wszystkie nagłówki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a196e-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="a196e-267">In that Case aplikacja jest odpowiedzialny za wykonanie `mustUnderstand` przetwarzania.) Wygenerowany błędów zawiera nagłówek NotUnderstood zawierającą nazwy wszystkich nagłówków z MustUnderstand = true, która była niezrozumiała.</span><span class="sxs-lookup"><span data-stu-id="a196e-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="a196e-268">Jeśli kanał protokołu wysyła niestandardowy nagłówek o MustUnderstand = true i odbiera `mustUnderstand` błędów, jego musi ustalić czy jest nagłówek wysłanie go z powodu tego błędu.</span><span class="sxs-lookup"><span data-stu-id="a196e-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="a196e-269">Istnieją dwa elementy członkowskie na `MessageFault` klasy, które są przydatne w tym:</span><span class="sxs-lookup"><span data-stu-id="a196e-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="a196e-270">`IsMustUnderstandFault` Zwraca `true` Jeśli błąd jest `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="a196e-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="a196e-271">`WasHeaderNotUnderstood` Zwraca `true` nagłówka o podanej nazwie i przestrzeni nazw jest uwzględniane w błędów jako nagłówek NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="a196e-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="a196e-272">W przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="a196e-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="a196e-273">Jeśli kanał emituje nagłówek, który jest oznaczony MustUnderstand = true, a warstwa ta powinny również implementować wzorzec interfejsu API generowania wyjątków należy przekonwertować `mustUnderstand` błędy spowodowane nagłówka do bardziej użyteczne wyjątku, zgodnie z wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="a196e-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="a196e-274">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a196e-274">Tracing</span></span>  
 <span data-ttu-id="a196e-275">Program .NET Framework dostarcza mechanizm śledzenia wykonywania programu, jako sposób, aby ułatwić diagnozowanie aplikacji produkcyjnych lub sporadycznych problemów, w którym nie jest możliwe tylko dołączanie debugera i Przechodź przez kod.</span><span class="sxs-lookup"><span data-stu-id="a196e-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="a196e-276">Podstawowe składniki ten mechanizm znajdują się w <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw i składają się:</span><span class="sxs-lookup"><span data-stu-id="a196e-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="a196e-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia do zapisania, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, który jest abstrakcyjna klasa bazowa dla konkretnych obiektów nasłuchujących otrzymywać informacje, które mają być śledzone od <xref:System.Diagnostics.TraceSource> i wyprowadzić dane do miejsca docelowego określonego odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a196e-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="a196e-278">Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="a196e-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="a196e-279">Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który umożliwia użytkownikowi aplikacji, Kontroluj ich szczegółowość śledzenia i zwykle jest określona w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a196e-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="a196e-280">Oprócz podstawowych składników można używać [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) wyszukiwania usługi WCF i wyświetlić ślady.</span><span class="sxs-lookup"><span data-stu-id="a196e-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="a196e-281">To narzędzie jest przeznaczony specjalnie dla plików śledzenia generowane przez program WCF i napisanych przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="a196e-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="a196e-282">Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="a196e-283">![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="a196e-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="a196e-284">Śledzenie za pomocą kanału niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a196e-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="a196e-285">Niestandardowe kanały należy zapisać komunikaty śledzenia, aby pomóc w diagnozowaniu problemów, gdy nie jest możliwe dołączyć debuger do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="a196e-286">Obejmuje to dwa zadania wysokiego poziomu: Utworzenie wystąpienia <xref:System.Diagnostics.TraceSource> i wywoływania jego metody można zapisywać dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="a196e-287">Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, string, należy określić staje się nazwę tego źródła.</span><span class="sxs-lookup"><span data-stu-id="a196e-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="a196e-288">Ta nazwa jest używana do konfigurowania źródła śledzenia (poziom śledzenia Włącz/Wyłącz/set).</span><span class="sxs-lookup"><span data-stu-id="a196e-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="a196e-289">Jest także wyświetlany w śledzeniu danych wyjściowych sam.</span><span class="sxs-lookup"><span data-stu-id="a196e-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="a196e-290">Niestandardowe kanały powinien umożliwia ułatwiają danych wyjściowych śledzenia zrozumienie skąd pochodzą informacje o śledzeniu unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="a196e-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="a196e-291">Częstą praktyką jest, przy użyciu nazwy zestawu, który zapisuje informacje jako nazwy źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="a196e-292">Na przykład WCF używa System.ServiceModel jako źródła śledzenia dla informacje zapisane z zestawu System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="a196e-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="a196e-293">Po utworzeniu źródła śledzenia, należy wywołać jej <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, lub <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metod na zapisywanie wpisów śledzenia do odbiorników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="a196e-294">Dla każdego wpisu śledzenia pisania, należy do klasyfikowania typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="a196e-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="a196e-295">Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji należy określić, czy wpis śledzenia przekazywane są do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a196e-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="a196e-296">Na przykład ustawienie poziomie śledzenia w konfiguracji, aby `Warning` umożliwia `Warning`, `Error` i `Critical` śledzenia wpisy, które ma zostać zapisany, ale bloki informacji i pełne wpisy.</span><span class="sxs-lookup"><span data-stu-id="a196e-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="a196e-297">Oto przykład tworzenia wystąpienia źródła śledzenia i wypisywanie wpis na poziomie informacji:</span><span class="sxs-lookup"><span data-stu-id="a196e-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="a196e-298">Zdecydowanie zaleca się, że podajesz nazwę źródła śledzenia, który jest unikatowy w niestandardowym kanale w celu śledzenia danych wyjściowych użytkownikom zorientować się, skąd pochodzą dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="a196e-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="a196e-299">Integracja z usługą w podglądzie śledzenia</span><span class="sxs-lookup"><span data-stu-id="a196e-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="a196e-300">Dane śledzenia generowane przez kanał może być danych wyjściowych w formacie czytelnym przez [narzędzie śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="a196e-301">Nie jest to coś, deweloper kanału, należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="a196e-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="a196e-302">Jest to raczej użytkownik aplikacji (lub osobę, rozwiązywanie problemów z aplikacji), które należy skonfigurować ten odbiornik śledzenia w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a196e-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="a196e-303">Na przykład następująca konfiguracja generuje informacje ze śledzenia z obu <xref:System.ServiceModel?displayProperty=nameWithType> i `Microsoft.Samples.Udp` pliku o nazwie `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="a196e-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="a196e-304">Śledzenie danych strukturalnych</span><span class="sxs-lookup"><span data-stu-id="a196e-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="a196e-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metodę przyjmującą jeden lub więcej obiektów, które mają być uwzględniane we wpisie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="a196e-306">Ogólnie rzecz biorąc <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda jest wywoływana dla każdego obiektu, a wynikowy ciąg jest zapisywany jako część wpis śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a196e-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="a196e-307">Korzystając z <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> w danych wyjściowych danych śledzenia, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="a196e-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="a196e-308">Wynikowy wpis śledzenia zawiera kod XML podany przez <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a196e-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a196e-309">Poniżej przedstawiono przykładowy wpis z danymi aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="a196e-309">Here is an example entry with XML application data:</span></span>  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 <span data-ttu-id="a196e-310">Przeglądarka śledzenia WCF rozumie schemat `TraceRecord` element przedstawionego wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla go w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="a196e-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="a196e-311">Kanał powinna używać tego schematu śledzenia danych ze strukturą aplikacji aby ułatwić użytkownikom Svctraceviewer.exe odczytywać dane.</span><span class="sxs-lookup"><span data-stu-id="a196e-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 494a0665f5bad2c7da3998cf77ced79314ca2f36
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="94d22-102">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="94d22-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="94d22-103">Wyjątki są używane do komunikacji błędy lokalnie w obrębie implementacji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="94d22-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="94d22-104">Błędy, z drugiej strony, są używane do komunikacji błędy w granicach usługi, takie jak z serwera do klienta lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="94d22-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="94d22-105">Oprócz błędów kanały transportu często używają mechanizmów specyficznych dla transportu do komunikowania się błędy na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="94d22-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="94d22-106">Na przykład transportu HTTP używa kodów stanu, takie jak 404 do komunikowania się nieistniejącego punktu końcowego adresu URL (Brak żaden punkt końcowy do odesłania błędów).</span><span class="sxs-lookup"><span data-stu-id="94d22-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="94d22-107">Ten dokument zawiera trzy sekcje, które zawierają wskazówki autorom niestandardowym kanale.</span><span class="sxs-lookup"><span data-stu-id="94d22-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="94d22-108">Pierwsza sekcja zawiera wskazówki dotyczące czasu i sposób definiowania i zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94d22-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="94d22-109">Druga sekcja zawiera wskazówki dotyczące generowania i korzystanie z błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="94d22-110">Trzeci sekcji opisano sposób Podaj informacje o śledzeniu, aby ułatwić rozwiązywanie problemów uruchamianie aplikacji użytkownika niestandardowego kanału.</span><span class="sxs-lookup"><span data-stu-id="94d22-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="94d22-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="94d22-111">Exceptions</span></span>  
 <span data-ttu-id="94d22-112">Istnieją dwie czynności należy wziąć pod uwagę podczas generowania wyjątku: najpierw musi być typu, który pozwala użytkownikom na zapis prawidłowego kodu, który można reagować odpowiednio wyjątek.</span><span class="sxs-lookup"><span data-stu-id="94d22-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="94d22-113">Po drugie musi on zawierać informacje wystarczające do użytkownika, aby zrozumieć, co poszło źle, wpływ awarii i jak to naprawić.</span><span class="sxs-lookup"><span data-stu-id="94d22-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="94d22-114">W poniższych sekcjach znajdują się wskazówki dotyczące typów wyjątków i wiadomości dla kanałów Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="94d22-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="94d22-115">Istnieje również ogólne wskazówki dotyczące wyjątków w .NET w wytycznych projektowych wyjątki dokumentu.</span><span class="sxs-lookup"><span data-stu-id="94d22-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="94d22-116">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="94d22-116">Exception Types</span></span>  
 <span data-ttu-id="94d22-117">Wszystkie wyjątki zgłaszane przez kanały musi być równa albo <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, lub typ pochodzący od <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="94d22-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="94d22-118">(Wyjątki, takie jak <xref:System.ObjectDisposedException> może również zostać wygenerowany, ale tylko do wskazują, że kod wywołujący ma niewłaściwego użycia kanału.</span><span class="sxs-lookup"><span data-stu-id="94d22-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="94d22-119">Jeśli kanał jest prawidłowo używana, jego musi tylko zgłosić danego wyjątki.) Usługi WCF zawiera siedem typów wyjątków, które pochodzą z <xref:System.ServiceModel.CommunicationException> i mają być używane przez kanały.</span><span class="sxs-lookup"><span data-stu-id="94d22-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="94d22-120">Istnieją inne <xref:System.ServiceModel.CommunicationException>-pochodnych wyjątki, które są przeznaczone do użytku przez inne części systemu.</span><span class="sxs-lookup"><span data-stu-id="94d22-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="94d22-121">Te typy wyjątek to:</span><span class="sxs-lookup"><span data-stu-id="94d22-121">These exception types are:</span></span>  
  
|<span data-ttu-id="94d22-122">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="94d22-122">Exception Type</span></span>|<span data-ttu-id="94d22-123">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="94d22-123">Meaning</span></span>|<span data-ttu-id="94d22-124">Wyjątek wewnętrzny zawartości</span><span class="sxs-lookup"><span data-stu-id="94d22-124">Inner Exception Content</span></span>|<span data-ttu-id="94d22-125">Strategia odzyskiwania</span><span class="sxs-lookup"><span data-stu-id="94d22-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="94d22-126">Podany adres punktu końcowego w celu nasłuchiwania jest już używana.</span><span class="sxs-lookup"><span data-stu-id="94d22-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="94d22-127">Jeśli jest obecny, zawiera więcej informacji o błędzie transport, który spowodował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="94d22-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="94d22-128">Na przykład.</span><span class="sxs-lookup"><span data-stu-id="94d22-128">For example.</span></span> <span data-ttu-id="94d22-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, lub <xref:System.Net.Sockets.SocketException>.</span><span class="sxs-lookup"><span data-stu-id="94d22-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="94d22-130">Spróbuj inny adres.</span><span class="sxs-lookup"><span data-stu-id="94d22-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="94d22-131">Proces nie ma mieć dostęp do podany adres punktu końcowego w celu nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="94d22-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="94d22-132">Jeśli jest obecny, zawiera więcej informacji o błędzie transport, który spowodował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="94d22-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="94d22-133">Na przykład <xref:System.IO.PipeException>, lub <xref:System.Net.HttpListenerException>.</span><span class="sxs-lookup"><span data-stu-id="94d22-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="94d22-134">Spróbuj i ma inne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="94d22-135"><xref:System.ServiceModel.ICommunicationObject> Używany jest w stanie Faulted (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="94d22-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="94d22-136">Należy pamiętać, że gdy obiekt z wieloma do czasu wywołania przejścia w stan końcowy: Faulted, tylko jedno wywołanie zgłasza wyjątek dotyczące awarii i pozostałe throw wywołania <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span><span class="sxs-lookup"><span data-stu-id="94d22-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="94d22-137">Zwykle zgłoszenia tego wyjątku, ponieważ aplikacja overlooks wyjątek i próbuje użyć obiektu już błędnej, prawdopodobnie w wątku innego niż ten, który Przechwycono wyjątek oryginalnego.</span><span class="sxs-lookup"><span data-stu-id="94d22-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="94d22-138">Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="94d22-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="94d22-139">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="94d22-139">Create a new object.</span></span> <span data-ttu-id="94d22-140">Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> do usterki w pierwszej kolejności, mogą być inne zadania wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="94d22-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="94d22-141"><xref:System.ServiceModel.ICommunicationObject> Używany została przerwana (Aby uzyskać więcej informacji, zobacz [opis zmian stanu](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span><span class="sxs-lookup"><span data-stu-id="94d22-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](../../../../docs/framework/wcf/extending/understanding-state-changes.md)).</span></span> <span data-ttu-id="94d22-142">Podobnie jak <xref:System.ServiceModel.CommunicationObjectFaultedException>, jego wyjątek wskazuje aplikacji została wywołana <xref:System.ServiceModel.ICommunicationObject.Abort%2A> dla obiektu, prawdopodobnie z innego wątku, i obiekt nie jest już możliwe z tego powodu.</span><span class="sxs-lookup"><span data-stu-id="94d22-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, his exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="94d22-143">Jeśli jest obecny szczegółowe informacje na temat wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="94d22-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="94d22-144">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="94d22-144">Create a new object.</span></span> <span data-ttu-id="94d22-145">Należy pamiętać, że w zależności od tego, co spowodowało <xref:System.ServiceModel.ICommunicationObject> przerwania w pierwszym rzędzie, może być inne zadania wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="94d22-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="94d22-146">Zdalny punkt końcowy docelowych nie nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="94d22-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="94d22-147">Może to wynikać z częścią adres punktu końcowego jest nieprawidłowy, nierozwiązywalne lub punkt końcowy jest wciśnięty.</span><span class="sxs-lookup"><span data-stu-id="94d22-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="94d22-148">Przykładami błędów DNS, menedżera kolejek nie są dostępne, a usługa nie działa.</span><span class="sxs-lookup"><span data-stu-id="94d22-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="94d22-149">Wyjątek wewnętrzny zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="94d22-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="94d22-150">Spróbuj inny adres.</span><span class="sxs-lookup"><span data-stu-id="94d22-150">Try a different address.</span></span> <span data-ttu-id="94d22-151">Alternatywnie nadawca może Zaczekaj chwilę i spróbuj ponownie w przypadku, gdy usługa nie działa</span><span class="sxs-lookup"><span data-stu-id="94d22-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="94d22-152">Protokoły komunikacji w sposób opisany w zasadach punktu końcowego są niezgodne między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="94d22-152">The communication protocols, as described by the endpoint’s policy, are mismatched between endpoints.</span></span> <span data-ttu-id="94d22-153">Na przykład framing niezgodność typu zawartości lub przekracza rozmiar maksymalny komunikatu.</span><span class="sxs-lookup"><span data-stu-id="94d22-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="94d22-154">Jeśli jest obecny zawiera więcej informacji o błędzie określony protokół.</span><span class="sxs-lookup"><span data-stu-id="94d22-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="94d22-155">Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wyjątek wewnętrzny, gdy przekracza MaxReceivedMessageSize przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="94d22-156">Odzyskiwanie: Upewnij się, nadawcy i protokół odebrane przez ustawienia są zgodne.</span><span class="sxs-lookup"><span data-stu-id="94d22-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="94d22-157">Jednym ze sposobów jest ponownie zaimportować metadane punktu końcowego usługi (zasady) i umożliwia powiązanie wygenerowany ponownie utworzyć kanał.</span><span class="sxs-lookup"><span data-stu-id="94d22-157">One way to do this is to re-import the service endpoint’s metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="94d22-158">Zdalny punkt końcowy nasłuchuje, ale nie jest przygotowany do przetwarzania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="94d22-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="94d22-159">Jeśli jest obecny, wyjątek wewnętrzny zapewnia błędu protokołu SOAP lub szczegółów błąd poziomu transportu.</span><span class="sxs-lookup"><span data-stu-id="94d22-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="94d22-160">Odzyskiwanie: Zaczekaj i spróbuj ponownie wykonać operację później.</span><span class="sxs-lookup"><span data-stu-id="94d22-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="94d22-161">Nie można zakończyć przed upływem limitu czasu operacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="94d22-162">Może zawierają szczegółowe informacje o limicie czasu.</span><span class="sxs-lookup"><span data-stu-id="94d22-162">May provide details about the timeout.</span></span>|<span data-ttu-id="94d22-163">Zaczekaj i spróbuj ponownie wykonać operację później.</span><span class="sxs-lookup"><span data-stu-id="94d22-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="94d22-164">Zdefiniuj nowy typ wyjątku, tylko w przypadku tego typu odnosi się do strategii odzyskiwania określonych różnych ze wszystkich istniejących typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94d22-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="94d22-165">W przypadku definiowania nowy typ wyjątku, musi pochodzić od <xref:System.ServiceModel.CommunicationException> lub jednej z jej klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="94d22-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="94d22-166">Komunikaty o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="94d22-166">Exception Messages</span></span>  
 <span data-ttu-id="94d22-167">Komunikaty o wyjątkach są przeznaczone dla użytkownika nie program, należy zapewniają wystarczających informacji pomóc użytkownikowi zrozumieć i rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="94d22-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="94d22-168">Dostępne są następujące trzy podstawowe części komunikatu dobrej wyjątek:</span><span class="sxs-lookup"><span data-stu-id="94d22-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="94d22-169">Co się stało.</span><span class="sxs-lookup"><span data-stu-id="94d22-169">What happened.</span></span> <span data-ttu-id="94d22-170">Podaj czytelny opis problemu, przy użyciu terminów, które odnoszą się do komputera przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="94d22-170">Provide a clear description of the problem using terms that relate to the user’s experience.</span></span> <span data-ttu-id="94d22-171">Na przykład komunikat wyjątek złego byłoby "Nieprawidłowa konfiguracja sekcji".</span><span class="sxs-lookup"><span data-stu-id="94d22-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="94d22-172">Spowoduje to pozostawienie użytkownika zastanawiasz się w sekcji konfiguracji, które są niepoprawne i dlaczego jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="94d22-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="94d22-173">Ulepszone komunikat będzie "Nieprawidłowa konfiguracja sekcji \<customBinding >".</span><span class="sxs-lookup"><span data-stu-id="94d22-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="94d22-174">Będą jeszcze bardziej poprawić jakość komunikat "nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie jest już transportu o nazwie myTransport".</span><span class="sxs-lookup"><span data-stu-id="94d22-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="94d22-175">Jest to bardzo określonego komunikatu korzystania z warunków i nazw, które użytkownik może łatwo zidentyfikować w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-175">This is a very specific message using terms and names that the user can easily identify in the application’s configuration file.</span></span> <span data-ttu-id="94d22-176">Istnieją jednak nadal kilka kluczowych składników Brak.</span><span class="sxs-lookup"><span data-stu-id="94d22-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="94d22-177">Znaczenia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-177">The significance of the error.</span></span> <span data-ttu-id="94d22-178">O ile w komunikacie wyraźnie oznacza błąd, użytkownik prawdopodobnie zastanawiasz się, czy jest to błąd krytyczny lub jeśli można go zignorować.</span><span class="sxs-lookup"><span data-stu-id="94d22-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="94d22-179">Ogólnie rzecz biorąc wiadomości powinny prowadzić znaczenie lub znaczenia tego błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="94d22-180">Aby zwiększyć w poprzednim przykładzie, komunikat może być "ServiceHost nie powiodło się z powodu błędu konfiguracji Otwórz: nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transportu o nazwie myTransport".</span><span class="sxs-lookup"><span data-stu-id="94d22-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="94d22-181">Jak użytkownik powinien rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="94d22-181">How the user should correct the problem.</span></span> <span data-ttu-id="94d22-182">Najważniejsze część komunikatu pomaga użytkownika Napraw ten problem.</span><span class="sxs-lookup"><span data-stu-id="94d22-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="94d22-183">Komunikat powinna zawierać wskazówek lub wskazówki dotyczące Sprawdź i napraw, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="94d22-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="94d22-184">Na przykład "ServiceHost nie powiodło się z powodu błędu konfiguracji Otwórz: nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie jest już transportu o nazwie myTransport.</span><span class="sxs-lookup"><span data-stu-id="94d22-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="94d22-185">Upewnij się, że istnieje transportu tylko jedno powiązanie".</span><span class="sxs-lookup"><span data-stu-id="94d22-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="94d22-186">Przekazywania błędów</span><span class="sxs-lookup"><span data-stu-id="94d22-186">Communicating Faults</span></span>  
 <span data-ttu-id="94d22-187">SOAP 1.1 i SOAP 1.2 zdefiniować szczególne strukturę błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="94d22-188">Istnieją pewne różnice między dwoma specyfikacje, ale ogólnie rzecz biorąc, typy komunikatu i MessageFault są używane do tworzenia i korzystania z błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="94d22-189">![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="94d22-189">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="94d22-190">SOAP 1.2 usterek (po lewej) i (po prawej) błędu protokołu SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="94d22-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="94d22-191">Należy pamiętać, że w SOAP 1.1 tylko element błędów kwalifikowane w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="94d22-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="94d22-192">SOAP definiuje komunikat o błędzie komunikat, który zawiera element usterek (element o nazwie `<env:Fault>`) jako element podrzędny `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="94d22-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="94d22-193">Zawartość elementu błędów się nieco różnić między SOAP 1.1 i SOAP 1.2, jak pokazano na rysunku 1.</span><span class="sxs-lookup"><span data-stu-id="94d22-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="94d22-194">Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasy normalizuje te różnice w jeden obiekt modelu:</span><span class="sxs-lookup"><span data-stu-id="94d22-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
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
  
 <span data-ttu-id="94d22-195">`Code` Właściwość odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="94d22-196">SOAP 1.2 definiuje pięć dopuszczalnych wartości dla `faultCode` (na przykład nadawcy i odbiorcy) i definiuje `Subcode` element, który może zawierać żadnej wartości podrzędny.</span><span class="sxs-lookup"><span data-stu-id="94d22-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="94d22-197">(Zobacz [Specyfikacja protokołu SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=95176) listę kodów dopuszczalny usterek i ich znaczenie.) SOAP 1.1 ma mechanizm nieco inne: definiuje cztery `faultCode` wartości (na przykład klient i serwer), które mogą być rozszerzane przez zdefiniowanie całkowicie nowe lub przy użyciu notacji kropka można utworzyć bardziej szczegółowe `faultCodes`, na przykład Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="94d22-197">(See the [SOAP 1.2 specification](http://go.microsoft.com/fwlink/?LinkId=95176) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="94d22-198">Używanie MessageFault do błędów programów, FaultCode.Name i FaultCode.Namespace mapuje nazwę i przestrzeń nazw protokołu SOAP 1.2 `env:Code` lub protokołu SOAP 1.1 `faultCode`.</span><span class="sxs-lookup"><span data-stu-id="94d22-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="94d22-199">Mapuje FaultCode.SubCode `env:Subcode` dla SOAP 1.2 i ma wartość null dla SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="94d22-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="94d22-200">Należy utworzyć nowe kody podrzędne usterek (lub nowe kody błędów, jeśli przy użyciu protokołu SOAP 1.1) Jeśli interesujące programowo odróżnienie błąd.</span><span class="sxs-lookup"><span data-stu-id="94d22-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="94d22-201">To jest analogiczne do utworzenia nowego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="94d22-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="94d22-202">Należy unikać używania kropkowego kody błędów SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="94d22-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="94d22-203">( [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) również zachęca do używania kodu błędu kropkowego.)</span><span class="sxs-lookup"><span data-stu-id="94d22-203">(The [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) also discourages the use of the fault code dot notation.)</span></span>  
  
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
  
 <span data-ttu-id="94d22-204">`Reason` Właściwość odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) zrozumiałą dla użytkownika opis warunku błędu odpowiednikiem komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="94d22-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception’s message.</span></span> <span data-ttu-id="94d22-205">`FaultReason` Klasy (i SOAP `env:Reason/faultString`) ma wbudowaną obsługę o wielu tłumaczenia dla globalizacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
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
  
 <span data-ttu-id="94d22-206">Zawartość szczegółów błędów są dostępne w MessageFault przy użyciu różnych metod, w tym `GetDetail` \<T > i `GetReaderAtDetailContents`().</span><span class="sxs-lookup"><span data-stu-id="94d22-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="94d22-207">Szczegół błędu jest elementem nieprzezroczyste przeprowadzania dodatkowe szczegóły dotyczące błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="94d22-208">Jest to przydatne w przypadku niektórych dowolnego szczegółów strukturalnych, które należy wykonać z usterki.</span><span class="sxs-lookup"><span data-stu-id="94d22-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="94d22-209">Generowanie błędów</span><span class="sxs-lookup"><span data-stu-id="94d22-209">Generating Faults</span></span>  
 <span data-ttu-id="94d22-210">W tej sekcji opisano proces generowania błąd w odpowiedzi na błąd wykryto w kanale lub we właściwości wiadomości utworzone przez kanał.</span><span class="sxs-lookup"><span data-stu-id="94d22-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="94d22-211">Typowym przykładem odsyła błąd w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="94d22-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="94d22-212">Podczas generowania usterki, niestandardowym kanale najlepiej nie przesyłać usterki bezpośrednio, zamiast powinien zgłosić wyjątek i pozwól warstwy powyżej zdecydować, czy można przekonwertować tego wyjątku do usterki oraz jak wysłać go.</span><span class="sxs-lookup"><span data-stu-id="94d22-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="94d22-213">W celu ułatwienia tej konwersji, należy podać kanału `FaultConverter` wdrożenia, który można przekonwertować wyjątek w niestandardowym kanale właściwe usterki.</span><span class="sxs-lookup"><span data-stu-id="94d22-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="94d22-214">`FaultConverter` nie zdefiniowano jako:</span><span class="sxs-lookup"><span data-stu-id="94d22-214">`FaultConverter` is defined as:</span></span>  
  
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
  
 <span data-ttu-id="94d22-215">Każdy kanału, który generuje błędy niestandardowe musi implementować `FaultConverter` i zwracać ją w wywołaniu `GetProperty<FaultConverter>`.</span><span class="sxs-lookup"><span data-stu-id="94d22-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="94d22-216">Niestandardowa `OnTryCreateFaultMessage` implementacji musi przekonwertuj wyjątek błąd lub delegowania w wewnętrznym kanale `FaultConverter`.</span><span class="sxs-lookup"><span data-stu-id="94d22-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel’s `FaultConverter`.</span></span> <span data-ttu-id="94d22-217">Jeśli kanał jest transport musi przekonwertować wyjątek lub przekazać do kodera `FaultConverter` lub wartość domyślną `FaultConverter` podany w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="94d22-217">If the channel is a transport it must either convert the exception or delegate to the encoder’s `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="94d22-218">Wartość domyślna `FaultConverter` konwertuje błędy komunikatów "fault" określony przez WS-Addressing i protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="94d22-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="94d22-219">Oto przykład `OnTryCreateFaultMessage` implementacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
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
  
 <span data-ttu-id="94d22-220">Możliwa tego wzorca jest, że wyjątki zgłaszane między warstwami dla warunków błędu, które wymagają błędów muszą zawierać informacje dla odpowiedniego generatora błędów, aby utworzyć poprawne błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="94d22-221">Jako autor niestandardowym kanale mogą określić typy wyjątków, które odpowiadają różnych awarii, jeśli takie wyjątki jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="94d22-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="94d22-222">Należy pamiętać, że wyjątków przechodzi przez kanał warstwy skontaktować się warunku błędu, a nie dane nieprzezroczyste błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="94d22-223">Kategorie błędów</span><span class="sxs-lookup"><span data-stu-id="94d22-223">Fault Categories</span></span>  
 <span data-ttu-id="94d22-224">Zazwyczaj są trzy kategorie błędów:</span><span class="sxs-lookup"><span data-stu-id="94d22-224">There are generally three categories of faults:</span></span>  
  
1.  <span data-ttu-id="94d22-225">Błędy, które są rozpowszechniona w całym cały stos.</span><span class="sxs-lookup"><span data-stu-id="94d22-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="94d22-226">Te błędy można napotkał na wszystkie warstwy stosu kanału, na przykład InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="94d22-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2.  <span data-ttu-id="94d22-227">Błędy, które mogą być napotkał dowolne miejsce powyżej wybranej warstwie w stosie na przykład niektóre błędy, które odnoszą się do przesłanej transakcji lub do ról zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="94d22-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3.  <span data-ttu-id="94d22-228">Błędy, które są kierowane na warstwę stosu, na przykład błędów, takich jak błędy numer sekwencji WS-RM.</span><span class="sxs-lookup"><span data-stu-id="94d22-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="94d22-229">Kategoria 1.</span><span class="sxs-lookup"><span data-stu-id="94d22-229">Category 1.</span></span> <span data-ttu-id="94d22-230">Błędy są zwykle WS-Addressing i błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="94d22-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="94d22-231">Podstawowym `FaultConverter` klasy dostarczane przez usługę WCF błędy konwertuje komunikatów "fault" określony przez WS-Addressing i SOAP dzięki czemu nie trzeba obsłużyć konwersji tych wyjątków samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="94d22-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="94d22-232">Kategoria 2.</span><span class="sxs-lookup"><span data-stu-id="94d22-232">Category 2.</span></span> <span data-ttu-id="94d22-233">Błędów wtedy, gdy warstwy dodaje właściwość do komunikat, który nie zużywa całkowicie komunikat informacji dotyczących tej warstwy.</span><span class="sxs-lookup"><span data-stu-id="94d22-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="94d22-234">Błędy mogą być wykrywane później, gdy właściwość wiadomości przetworzyć komunikatu dalszych informacji o prosi o wyższej warstwie.</span><span class="sxs-lookup"><span data-stu-id="94d22-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="94d22-235">Takie kanałów powinien implementować `GetProperty` określony wcześniej, aby włączyć wyższej warstwie do odesłania poprawne błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="94d22-236">Na przykład jest TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="94d22-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="94d22-237">Ta właściwość jest dodany komunikat bez pełni sprawdzanie poprawności wszystkich danych w nagłówku (zrobić, może obejmować kontaktowania się z koordynatorem transakcji rozproszonych (DTC).</span><span class="sxs-lookup"><span data-stu-id="94d22-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="94d22-238">Kategoria 3.</span><span class="sxs-lookup"><span data-stu-id="94d22-238">Category 3.</span></span> <span data-ttu-id="94d22-239">Błędy są tylko i wysyłane przez warstwę pojedynczy procesor.</span><span class="sxs-lookup"><span data-stu-id="94d22-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="94d22-240">W związku z tym wszystkie wyjątki są zawarte w warstwie.</span><span class="sxs-lookup"><span data-stu-id="94d22-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="94d22-241">Aby zwiększyć zgodność między kanałów i łatwości konserwacji, niestandardowe kanału należy używać wzorzec wcześniej określony do generowania komunikatów "fault" nawet w przypadku błędów wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="94d22-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="94d22-242">Interpretowanie odebranych błędów</span><span class="sxs-lookup"><span data-stu-id="94d22-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="94d22-243">Ta sekcja zawiera wskazówki dotyczące generowania odpowiedni wyjątek, gdy odbiera komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="94d22-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="94d22-244">Drzewo decyzyjne dotyczące przetwarzania komunikatu w każdej warstwie w stosie wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="94d22-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1.  <span data-ttu-id="94d22-245">Jeśli warstwa uwzględnia komunikatu jest nieprawidłowy, warstwy należy wykonać jego przetwarzanie "nieprawidłowy komunikat".</span><span class="sxs-lookup"><span data-stu-id="94d22-245">If the layer considers the message to be invalid, the layer should do its ‘invalid message’ processing.</span></span> <span data-ttu-id="94d22-246">Takie przetwarzanie specyficzne dla warstwy, ale może obejmować usunięcie wiadomości, śledzenie, lub zgłoszeniu wyjątku, który zostaje przekształcona na błąd.</span><span class="sxs-lookup"><span data-stu-id="94d22-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="94d22-247">Przykładami zabezpieczeń odbieranie wiadomości, który nie jest prawidłowo zabezpieczony lub odbieranie wiadomości z liczbą sekwencji zły Menedżera zasobów.</span><span class="sxs-lookup"><span data-stu-id="94d22-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2.  <span data-ttu-id="94d22-248">W przeciwnym razie jeśli komunikat jest komunikat o błędzie, który dotyczy w szczególności do warstwy, a komunikat nie ma sensu poza interakcji przesuwaniu, warstwy powinna obsługiwać warunku błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer’s interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="94d22-249">Na przykład jest błąd odmowy sekwencji RM znaczenia do warstwy powyżej kanału RM i oznacza to spowodowaniem błędu kanału RM i zgłaszanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3.  <span data-ttu-id="94d22-250">W przeciwnym razie wiadomości powinny być zwracane z Request() lub Receive().</span><span class="sxs-lookup"><span data-stu-id="94d22-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="94d22-251">Dotyczy to przypadków, w których warstwy rozpoznaje błędu, ale usterki tylko wskazuje, że żądanie nie powiodło się i nie oznacza spowodowaniem błędu kanału i zgłaszanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="94d22-252">Aby poprawić użyteczność w takim przypadku, powinien implementować warstwy `GetProperty<FaultConverter>` i zwracać `FaultConverter` klasy, który można przekonwertować usterki wyjątek przez zastąpienie `OnTryCreateException`.</span><span class="sxs-lookup"><span data-stu-id="94d22-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="94d22-253">Następujące model obiektów obsługuje konwertowania komunikaty wyjątków:</span><span class="sxs-lookup"><span data-stu-id="94d22-253">The following object model supports converting messages to exceptions:</span></span>  
  
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
  
 <span data-ttu-id="94d22-254">Można zaimplementować w warstwie kanału `GetProperty<FaultConverter>` do obsługi konwertowania komunikatów "fault" wyjątków.</span><span class="sxs-lookup"><span data-stu-id="94d22-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="94d22-255">Aby to zrobić, należy zastąpić `OnTryCreateException` i przejrzyj komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="94d22-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="94d22-256">Rozpoznany, wykonać konwersji, w przeciwnym razie poproś wewnętrzny kanału do konwertowania.</span><span class="sxs-lookup"><span data-stu-id="94d22-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="94d22-257">Kanały transportu powinny być delegowane do `FaultConverter.GetDefaultFaultConverter` by otrzymać domyślny FaultConverter SOAP/WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="94d22-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="94d22-258">Typowa implementacja wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="94d22-258">A typical implementation looks like this:</span></span>  
  
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
  
 <span data-ttu-id="94d22-259">Warunki określonych błędów, które mają scenariuszy odzyskiwania distinct, rozważ zdefiniowanie klasy pochodnej z `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="94d22-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="94d22-260">Atrybut MustUnderstand przetwarzania</span><span class="sxs-lookup"><span data-stu-id="94d22-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="94d22-261">SOAP definiuje ogólne usterki do sygnalizacji wymagany nagłówek nie został zrozumiany przez odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="94d22-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="94d22-262">Ten błąd jest nazywany `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="94d22-263">W programie WCF, nigdy nie Generuj kanałów niestandardowych `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="94d22-264">Zamiast tego dyspozytora WCF, który znajduje się w górnej części stosu komunikacji usługi WCF, sprawdza, czy wszystkie nagłówki, które zostały oznaczone jako MustUndestand = true zostały zrozumiane przez stos podstawowej.</span><span class="sxs-lookup"><span data-stu-id="94d22-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUndestand=true were understood by the underlying stack.</span></span> <span data-ttu-id="94d22-265">Jeśli dowolne są niezrozumiałe, `mustUnderstand` błąd jest zgłaszany w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="94d22-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="94d22-266">(Użytkownik może wyłączyć to `mustUnderstand` przetwarzania i mają otrzymywać wszystkie nagłówki komunikatów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="94d22-267">In that Case aplikacji jest odpowiedzialny za wykonywanie `mustUnderstand` przetwarzania.) Wygenerowany błąd zawiera nagłówek NotUnderstood, zawierającą nazwy wszystkich nagłówków z MustUnderstand = true, które są niezrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="94d22-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="94d22-268">Jeśli kanał protokołu wysyła niestandardowy nagłówek o MustUnderstand = true i odbiera `mustUnderstand` usterka, go musi ustalić czy jest nagłówka ona wysłana z powodu tego błędu.</span><span class="sxs-lookup"><span data-stu-id="94d22-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="94d22-269">Istnieją dwa elementy członkowskie na `MessageFault` klasy, które są przydatne w przypadku to:</span><span class="sxs-lookup"><span data-stu-id="94d22-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
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
  
 <span data-ttu-id="94d22-270">`IsMustUnderstandFault` Zwraca `true` w przypadku błędu `mustUnderstand` błędów.</span><span class="sxs-lookup"><span data-stu-id="94d22-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="94d22-271">`WasHeaderNotUnderstood` Zwraca `true` nagłówek o określonej nazwie i przestrzeni nazw jest uwzględniane w usterek jako nagłówek NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="94d22-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="94d22-272">W przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="94d22-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="94d22-273">Jeśli kanał emituje nagłówek, który jest oznaczony jako atrybut MustUnderstand = true, a następnie tej warstwy powinny również implementować wzorzec interfejsu API generowania wyjątków i należy przekonwertować `mustUnderstand` błędy spowodowane nagłówka do bardziej użyteczne wyjątków opisanych powyżej.</span><span class="sxs-lookup"><span data-stu-id="94d22-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="94d22-274">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="94d22-274">Tracing</span></span>  
 <span data-ttu-id="94d22-275">.NET Framework zapewnia mechanizm do śledzenia realizacji program sposób ułatwiających diagnozowanie aplikacji produkcyjnych i przejściowych problemów, gdy nie jest możliwe tylko dołączenie debugera i kroków kod.</span><span class="sxs-lookup"><span data-stu-id="94d22-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="94d22-276">Podstawowe składniki ten mechanizm znajdują się w <xref:System.Diagnostics?displayProperty=nameWithType> przestrzeni nazw i obejmować:</span><span class="sxs-lookup"><span data-stu-id="94d22-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
-   <span data-ttu-id="94d22-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia do zapisania, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, która jest abstrakcyjna klasa podstawowa dla konkretnych obiektów nasłuchujących odbierać informacje, które mają być śledzone z <xref:System.Diagnostics.TraceSource> i wyjścia go do lokalizacji docelowej, specyficzne dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="94d22-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="94d22-278">Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="94d22-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="94d22-279">Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który umożliwia użytkownikowi aplikacji kontrolować poziom szczegółowości śledzenia i zwykle jest określona w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="94d22-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
-   <span data-ttu-id="94d22-280">Oprócz podstawowych składników, możesz użyć [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) wyszukiwania WCF i wyświetlić śladów.</span><span class="sxs-lookup"><span data-stu-id="94d22-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="94d22-281">Zaprojektowany specjalnie z myślą plików śledzenia, generowane przez usługę WCF i zapisany przy użyciu narzędzia <xref:System.Diagnostics.XmlWriterTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="94d22-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="94d22-282">Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="94d22-283">![Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="94d22-283">![Handling exceptions and faults](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="94d22-284">Śledzenie za pomocą kanału niestandardowe</span><span class="sxs-lookup"><span data-stu-id="94d22-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="94d22-285">Wiadomości śledzenia ułatwiających diagnozowanie problemów, gdy nie jest możliwe dołączanie debugera do uruchomionej aplikacji należy zapisać jego kanałów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="94d22-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="94d22-286">Ten proces obejmuje dwa zadania wysokiego poziomu: Tworzenie wystąpień <xref:System.Diagnostics.TraceSource> i wywołanie jego metody można zapisywać dane śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="94d22-287">Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, należy określić ciąg staje się nazwa tego źródła.</span><span class="sxs-lookup"><span data-stu-id="94d22-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="94d22-288">Ta nazwa jest używana do konfigurowania (set Włącz/Wyłącz śledzenie poziom) źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="94d22-289">Jest także wyświetlany w wyniku sam śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="94d22-290">Kanałów niestandardowych należy używać unikatową nazwę w celu czytników zrozumieć, z której pochodzi informacji o śledzeniu danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="94d22-291">Standardową praktyką jest użycie nazwy zestawu, który zapisuje informacje jak nazwa źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="94d22-292">Na przykład WCF używa System.ServiceModel jako źródła śledzenia informacji z zestawu System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="94d22-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="94d22-293">Po utworzeniu źródła śledzenia, należy wywołać jej <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, lub <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metod na zapisywanie wpisów śledzenia do obiektów nasłuchujących śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="94d22-294">Dla każdego wpisu śledzenia pisania należy sklasyfikować typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w <xref:System.Diagnostics.TraceEventType>.</span><span class="sxs-lookup"><span data-stu-id="94d22-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="94d22-295">Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji należy ustalić, czy wpis śledzenia jest dane wyjściowe do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="94d22-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="94d22-296">Na przykład ustawienie poziomu śledzenia w konfiguracji, aby `Warning` umożliwia `Warning`, `Error` i `Critical` śledzenia wpisy są zapisywane, ale bloki wpisy informacji i pełne.</span><span class="sxs-lookup"><span data-stu-id="94d22-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="94d22-297">Poniżej przedstawiono przykład tworzenia wystąpienia źródła śledzenia i zapisywania wpisu na poziomie informacji:</span><span class="sxs-lookup"><span data-stu-id="94d22-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="94d22-298">Zdecydowanie zaleca się, że podajesz nazwę źródła śledzenia, która jest unikatowa dla niestandardowego kanału pomagające zrozumieć, skąd pochodzą dane wyjściowe czytniki danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="94d22-299">Integrowanie z przeglądarki śledzenia</span><span class="sxs-lookup"><span data-stu-id="94d22-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="94d22-300">Ślady generowane przez kanał może być danych wyjściowych w formacie, który może zostać odczytany przez [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako obiektu nasłuchującego śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="94d22-301">Nie jest to coś, deweloper kanału, należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="94d22-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="94d22-302">Jest to raczej użytkownik aplikacji (lub osoby, rozwiązywanie problemów z aplikacji) który musi skonfigurować tym odbiorniku śledzenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94d22-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application’s configuration file.</span></span> <span data-ttu-id="94d22-303">Na przykład następująca konfiguracja generuje informacje o śledzeniu na obu <xref:System.ServiceModel?displayProperty=nameWithType> i `Microsoft.Samples.Udp` pliku o nazwie `TraceEventsFile.e2e`:</span><span class="sxs-lookup"><span data-stu-id="94d22-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="94d22-304">Śledzenia danych strukturalnych</span><span class="sxs-lookup"><span data-stu-id="94d22-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="94d22-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metody pobierającej jednego lub większej liczby obiektów, które mają być uwzględniane we wpisie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="94d22-306">Ogólnie rzecz biorąc <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda jest wywoływana dla każdego obiektu i wynikowy ciąg jest zapisywany jako część wpis śledzenia.</span><span class="sxs-lookup"><span data-stu-id="94d22-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="94d22-307">Korzystając z <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> do danych wyjściowych danych śledzenia, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="94d22-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="94d22-308">Wynikowy wpis śledzenia zawiera XML podał <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="94d22-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="94d22-309">Oto przykładowy wpis z danych XML aplikacji:</span><span class="sxs-lookup"><span data-stu-id="94d22-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="94d22-310">Przeglądarka śledzenia WCF rozumie schemat `TraceRecord` element przedstawione wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla go w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="94d22-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="94d22-311">Kanał należy używać tego schematu podczas śledzenia danych strukturalnych aplikacji aby ułatwić użytkownikom Svctraceviewer.exe odczytać danych.</span><span class="sxs-lookup"><span data-stu-id="94d22-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

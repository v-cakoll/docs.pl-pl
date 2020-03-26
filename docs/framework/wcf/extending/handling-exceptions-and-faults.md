---
title: Obsługa wyjątków i błędów
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: 7fa045dc6fd6e31eccf29e22ae2e212f59dfaec0
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111871"
---
# <a name="handling-exceptions-and-faults"></a><span data-ttu-id="82746-102">Obsługa wyjątków i błędów</span><span class="sxs-lookup"><span data-stu-id="82746-102">Handling Exceptions and Faults</span></span>
<span data-ttu-id="82746-103">Wyjątki są używane do komunikowania błędów lokalnie w ramach usługi lub implementacji klienta.</span><span class="sxs-lookup"><span data-stu-id="82746-103">Exceptions are used to communicate errors locally within the service or the client implementation.</span></span> <span data-ttu-id="82746-104">Błędy, z drugiej strony, są używane do komunikowania błędów w granicach usługi, takich jak z serwera do klienta lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="82746-104">Faults, on the other hand, are used to communicate errors across service boundaries, such as from the server to the client or vice versa.</span></span> <span data-ttu-id="82746-105">Oprócz usterek kanały transportowe często używają mechanizmów specyficznych dla transportu do przekazywania błędów na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="82746-105">In addition to faults, transport channels often use transport-specific mechanisms to communicate transport-level errors.</span></span> <span data-ttu-id="82746-106">Na przykład transport HTTP używa kodów stanu, takich jak 404 do komunikowania nieistniejącego adresu URL punktu końcowego (nie ma punktu końcowego, aby wysłać z powrotem błąd).</span><span class="sxs-lookup"><span data-stu-id="82746-106">For example, HTTP transport uses status codes such as 404 to communicate a non-existing endpoint URL (there is no endpoint to send back a fault).</span></span> <span data-ttu-id="82746-107">Ten dokument składa się z trzech sekcji, które zawierają wskazówki dla niestandardowych autorów kanałów.</span><span class="sxs-lookup"><span data-stu-id="82746-107">This document consists of three sections that provide guidance to custom channel authors.</span></span> <span data-ttu-id="82746-108">Pierwsza sekcja zawiera wskazówki dotyczące tego, kiedy i jak zdefiniować i zgłosić wyjątki.</span><span class="sxs-lookup"><span data-stu-id="82746-108">The first section provides guidance on when and how to define and throw exceptions.</span></span> <span data-ttu-id="82746-109">Druga sekcja zawiera wskazówki dotyczące generowania i zużywania usterek.</span><span class="sxs-lookup"><span data-stu-id="82746-109">The second section provides guidance around generating and consuming faults.</span></span> <span data-ttu-id="82746-110">W trzeciej sekcji wyjaśniono, jak dostarczyć informacje śledzenia, aby pomóc użytkownikowi kanału niestandardowego w rozwiązywaniu problemów z uruchomionymi aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="82746-110">The third section explains how to provide trace information to aid the user of your custom channel in troubleshooting running applications.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="82746-111">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="82746-111">Exceptions</span></span>  
 <span data-ttu-id="82746-112">Istnieją dwie rzeczy, o których należy pamiętać podczas zgłaszania wyjątku: Najpierw musi być typu, który pozwala użytkownikom napisać poprawny kod, który może odpowiednio reagować na wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82746-112">There are two things to keep in mind when throwing an exception: First it has to be of a type that allows users to write correct code that can react appropriately to the exception.</span></span> <span data-ttu-id="82746-113">Po drugie musi dostarczyć wystarczających informacji dla użytkownika, aby zrozumieć, co poszło nie tak, wpływ awarii i jak go naprawić.</span><span class="sxs-lookup"><span data-stu-id="82746-113">Second, it has to provide enough information for the user to understand what went wrong, the failure impact, and how to fix it.</span></span> <span data-ttu-id="82746-114">W poniższych sekcjach przedstawiono wskazówki dotyczące typów wyjątków i komunikatów dla kanałów Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="82746-114">The following sections give guidance around exception types and messages for Windows Communication Foundation (WCF) channels.</span></span> <span data-ttu-id="82746-115">Istnieją również ogólne wskazówki dotyczące wyjątków w .NET w wskazówki dotyczące projektowania wyjątków dokumentu.</span><span class="sxs-lookup"><span data-stu-id="82746-115">There is also general guidance around exceptions in .NET in the Design Guidelines for Exceptions document.</span></span>  
  
### <a name="exception-types"></a><span data-ttu-id="82746-116">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="82746-116">Exception Types</span></span>  
 <span data-ttu-id="82746-117">Wszystkie wyjątki generowane przez kanały <xref:System.TimeoutException?displayProperty=nameWithType> <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>muszą być albo , <xref:System.ServiceModel.CommunicationException>lub typu pochodnego z .</span><span class="sxs-lookup"><span data-stu-id="82746-117">All exceptions thrown by channels must be either a <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, or a type derived from <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="82746-118">(Wyjątki, <xref:System.ObjectDisposedException> takie jak mogą być również generowane, ale tylko w celu wskazania, że kod wywołujący niewłaściwie kanał.</span><span class="sxs-lookup"><span data-stu-id="82746-118">(Exceptions such as <xref:System.ObjectDisposedException> may also be thrown, but only to indicate that the calling code has misused the channel.</span></span> <span data-ttu-id="82746-119">Jeśli kanał jest używany poprawnie, musi zgłaszać tylko podane wyjątki.) WCF zawiera siedem typów wyjątków, które wynikają z <xref:System.ServiceModel.CommunicationException> i są przeznaczone do użycia przez kanały.</span><span class="sxs-lookup"><span data-stu-id="82746-119">If a channel is used correctly, it must only throw the given exceptions.) WCF provides seven exception types that derive from <xref:System.ServiceModel.CommunicationException> and are designed to be used by channels.</span></span> <span data-ttu-id="82746-120">Istnieją inne <xref:System.ServiceModel.CommunicationException>wyjątki pochodne, które są przeznaczone do użycia przez inne części systemu.</span><span class="sxs-lookup"><span data-stu-id="82746-120">There are other <xref:System.ServiceModel.CommunicationException>-derived exceptions that are designed to be used by other parts of the system.</span></span> <span data-ttu-id="82746-121">Te typy wyjątków są następujące:</span><span class="sxs-lookup"><span data-stu-id="82746-121">These exception types are:</span></span>  
  
|<span data-ttu-id="82746-122">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="82746-122">Exception Type</span></span>|<span data-ttu-id="82746-123">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="82746-123">Meaning</span></span>|<span data-ttu-id="82746-124">Zawartość wyjątku wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="82746-124">Inner Exception Content</span></span>|<span data-ttu-id="82746-125">Strategia odzyskiwania</span><span class="sxs-lookup"><span data-stu-id="82746-125">Recovery Strategy</span></span>|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|<span data-ttu-id="82746-126">Adres punktu końcowego określony do nasłuchiwania jest już używany.</span><span class="sxs-lookup"><span data-stu-id="82746-126">The endpoint address specified for listening is already in use.</span></span>|<span data-ttu-id="82746-127">Jeśli jest obecny, zawiera więcej szczegółów na temat błędu transportu, który spowodował ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82746-127">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="82746-128">Na przykład.</span><span class="sxs-lookup"><span data-stu-id="82746-128">For example.</span></span> <span data-ttu-id="82746-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, <xref:System.Net.Sockets.SocketException>lub .</span><span class="sxs-lookup"><span data-stu-id="82746-129"><xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, or <xref:System.Net.Sockets.SocketException>.</span></span>|<span data-ttu-id="82746-130">Spróbuj użyć innego adresu.</span><span class="sxs-lookup"><span data-stu-id="82746-130">Try a different address.</span></span>|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|<span data-ttu-id="82746-131">Proces nie jest dozwolony dostęp do adresu punktu końcowego określonego do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="82746-131">The process is not allowed access to the endpoint address specified for listening.</span></span>|<span data-ttu-id="82746-132">Jeśli jest obecny, zawiera więcej szczegółów na temat błędu transportu, który spowodował ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82746-132">If present, provides more details about the transport error that caused this exception.</span></span> <span data-ttu-id="82746-133">Na przykład <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>lub .</span><span class="sxs-lookup"><span data-stu-id="82746-133">For example, <xref:System.IO.PipeException>, or <xref:System.Net.HttpListenerException>.</span></span>|<span data-ttu-id="82746-134">Spróbuj z różnymi poświadczeniami.</span><span class="sxs-lookup"><span data-stu-id="82746-134">Try with different credentials.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<span data-ttu-id="82746-135">Używany <xref:System.ServiceModel.ICommunicationObject> jest w stanie Faulted (aby uzyskać więcej informacji, zobacz [Opis zmian stanu).](understanding-state-changes.md)</span><span class="sxs-lookup"><span data-stu-id="82746-135">The <xref:System.ServiceModel.ICommunicationObject> being used is in the Faulted state (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="82746-136">Należy zauważyć, że gdy obiekt z wieloma oczekującymi wywołaniami przechodzi do stanu Faulted, tylko jedno wywołanie <xref:System.ServiceModel.CommunicationObjectFaultedException>zgłasza wyjątek, który jest związany z awarią, a pozostałe wywołania zgłosić .</span><span class="sxs-lookup"><span data-stu-id="82746-136">Note that when an object with multiple pending calls transitions to the Faulted state, only one call throws an exception that is related to the failure and the rest of the calls throw a <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="82746-137">Ten wyjątek jest zazwyczaj zgłaszany, ponieważ aplikacja pomija jakiś wyjątek i próbuje użyć już wadliwego obiektu, prawdopodobnie w wątku innym niż ten, który przechował oryginalny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="82746-137">This exception is typically thrown because an application overlooks some exception and tries to use an already faulted object, possibly on a thread other than the one that caught the original exception.</span></span>|<span data-ttu-id="82746-138">Jeśli present zawiera szczegółowe informacje na temat wyjątku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="82746-138">If present provides details about the inner exception.</span></span>|<span data-ttu-id="82746-139">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="82746-139">Create a new object.</span></span> <span data-ttu-id="82746-140">Należy pamiętać, że <xref:System.ServiceModel.ICommunicationObject> w zależności od tego, co spowodowało błąd w pierwszej kolejności, może być inne prace wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="82746-140">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to fault in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<span data-ttu-id="82746-141">Używany <xref:System.ServiceModel.ICommunicationObject> został przerwany (aby uzyskać więcej informacji, zobacz [Opis zmian stanu).](understanding-state-changes.md)</span><span class="sxs-lookup"><span data-stu-id="82746-141">The <xref:System.ServiceModel.ICommunicationObject> being used has been Aborted (for more information, see [Understanding State Changes](understanding-state-changes.md)).</span></span> <span data-ttu-id="82746-142">Podobny <xref:System.ServiceModel.CommunicationObjectFaultedException>do , ten wyjątek <xref:System.ServiceModel.ICommunicationObject.Abort%2A> wskazuje, że aplikacja wywoływała obiekt, prawdopodobnie z innego wątku, a obiekt nie jest już użyteczny z tego powodu.</span><span class="sxs-lookup"><span data-stu-id="82746-142">Similar to <xref:System.ServiceModel.CommunicationObjectFaultedException>, this exception indicates the application has called <xref:System.ServiceModel.ICommunicationObject.Abort%2A> on the object, possibly from another thread, and the object is no longer usable for that reason.</span></span>|<span data-ttu-id="82746-143">Jeśli present zawiera szczegółowe informacje na temat wyjątku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="82746-143">If present provides details about the inner exception.</span></span>|<span data-ttu-id="82746-144">Utwórz nowy obiekt.</span><span class="sxs-lookup"><span data-stu-id="82746-144">Create a new object.</span></span> <span data-ttu-id="82746-145">Należy zauważyć, że <xref:System.ServiceModel.ICommunicationObject> w zależności od tego, co spowodowało przerwanie w pierwszej kolejności, może być inne prace wymagane do odzyskania.</span><span class="sxs-lookup"><span data-stu-id="82746-145">Note that depending on what caused the <xref:System.ServiceModel.ICommunicationObject> to abort in the first place, there may be other work required to recover.</span></span>|  
|<xref:System.ServiceModel.EndpointNotFoundException>|<span data-ttu-id="82746-146">Docelowy zdalny punkt końcowy nie nasłuchuje.</span><span class="sxs-lookup"><span data-stu-id="82746-146">The target remote endpoint is not listening.</span></span> <span data-ttu-id="82746-147">Może to wynikać z dowolnej części adresu punktu końcowego jest niepoprawna, nierozwiązywalna lub punkt końcowy jest w dół.</span><span class="sxs-lookup"><span data-stu-id="82746-147">This can result from any part of the endpoint address being incorrect, irresolvable, or the endpoint being down.</span></span> <span data-ttu-id="82746-148">Przykłady obejmują błąd DNS, Menedżer kolejek nie jest dostępny i usługa nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="82746-148">Examples include DNS error, Queue Manager not available, and service not running.</span></span>|<span data-ttu-id="82746-149">Wewnętrzny wyjątek zawiera szczegółowe informacje, zazwyczaj z transportu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="82746-149">The inner exception provides details, typically from the underlying transport.</span></span>|<span data-ttu-id="82746-150">Spróbuj użyć innego adresu.</span><span class="sxs-lookup"><span data-stu-id="82746-150">Try a different address.</span></span> <span data-ttu-id="82746-151">Alternatywnie nadawca może chwilę poczekać i spróbować ponownie w przypadku, gdy usługa została wyłączna</span><span class="sxs-lookup"><span data-stu-id="82746-151">Alternatively, the sender may wait a while and try again in case the service was down</span></span>|  
|<xref:System.ServiceModel.ProtocolException>|<span data-ttu-id="82746-152">Protokoły komunikacyjne, zgodnie z opisem w zasadach punktu końcowego, są niezgodne między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="82746-152">The communication protocols, as described by the endpoint's policy, are mismatched between endpoints.</span></span> <span data-ttu-id="82746-153">Na przykład przekroczenie rozmiaru zawartości ramek lub przekroczono maksymalny rozmiar wiadomości.</span><span class="sxs-lookup"><span data-stu-id="82746-153">For example, framing content type mismatch or max message size exceeded.</span></span>|<span data-ttu-id="82746-154">Jeśli obecny zawiera więcej informacji na temat określonego błędu protokołu.</span><span class="sxs-lookup"><span data-stu-id="82746-154">If present provides more information about the specific protocol error.</span></span> <span data-ttu-id="82746-155">Na przykład <xref:System.ServiceModel.QuotaExceededException> jest wewnętrzny wyjątek, gdy przyczyną błędu jest przekroczenie MaxReceivedMessageSize.</span><span class="sxs-lookup"><span data-stu-id="82746-155">For example, <xref:System.ServiceModel.QuotaExceededException> is the inner exception when the error cause is exceeding MaxReceivedMessageSize.</span></span>|<span data-ttu-id="82746-156">Odzyskiwanie: Upewnij się, że ustawienia nadawcy i odebranego protokołu są zgodne.</span><span class="sxs-lookup"><span data-stu-id="82746-156">Recovery: Ensure sender and received protocol settings match.</span></span> <span data-ttu-id="82746-157">Jednym ze sposobów, aby to zrobić, jest ponowne zaimportowanie metadanych punktu końcowego usługi (zasady) i użycie wygenerowanego powiązania do ponownego wygenerowania kanału.</span><span class="sxs-lookup"><span data-stu-id="82746-157">One way to do this is to re-import the service endpoint's metadata (policy) and use the generated binding to recreate the channel.</span></span>|  
|<xref:System.ServiceModel.ServerTooBusyException>|<span data-ttu-id="82746-158">Zdalny punkt końcowy nasłuchuje, ale nie jest przygotowany do przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="82746-158">The remote endpoint is listening but is not prepared to process messages.</span></span>|<span data-ttu-id="82746-159">Jeśli jest obecny, wewnętrzny wyjątek zawiera szczegóły błędu PROTOKOŁU SOAP lub na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="82746-159">If present, the inner Exception provides the SOAP fault or transport-level error details.</span></span>|<span data-ttu-id="82746-160">Odzyskiwanie: Poczekaj i ponów próbę wykonania operacji później.</span><span class="sxs-lookup"><span data-stu-id="82746-160">Recovery: Wait and retry the operation later.</span></span>|  
|<xref:System.TimeoutException>|<span data-ttu-id="82746-161">Operacja nie została ukończona w okresie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="82746-161">The operation failed to complete within the timeout period.</span></span>|<span data-ttu-id="82746-162">Może podać szczegółowe informacje na temat limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="82746-162">May provide details about the timeout.</span></span>|<span data-ttu-id="82746-163">Poczekaj i ponów próbę wykonania operacji później.</span><span class="sxs-lookup"><span data-stu-id="82746-163">Wait and retry the operation later.</span></span>|  
  
 <span data-ttu-id="82746-164">Zdefiniuj nowy typ wyjątku tylko wtedy, gdy ten typ odpowiada określonej strategii odzyskiwania różni się od wszystkich istniejących typów wyjątków.</span><span class="sxs-lookup"><span data-stu-id="82746-164">Define a new exception type only if that type corresponds to a specific recovery strategy different from all of the existing exception types.</span></span> <span data-ttu-id="82746-165">Jeśli zdefiniujesz nowy typ wyjątku, <xref:System.ServiceModel.CommunicationException> musi on pochodzić z lub jednej z jego klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="82746-165">If you do define a new exception type, it must derive from <xref:System.ServiceModel.CommunicationException> or one of its derived classes.</span></span>  
  
### <a name="exception-messages"></a><span data-ttu-id="82746-166">Komunikaty o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="82746-166">Exception Messages</span></span>  
 <span data-ttu-id="82746-167">Komunikaty o wyjątkach są skierowane do użytkownika, a nie do programu, więc powinny one dostarczyć wystarczających informacji, aby pomóc użytkownikowi zrozumieć i rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="82746-167">Exception messages are targeted at the user not the program so they should provide sufficient information to help the user understand and solve the problem.</span></span> <span data-ttu-id="82746-168">Trzy istotne części dobrego komunikatu o wyjątku to:</span><span class="sxs-lookup"><span data-stu-id="82746-168">The three essential parts of a good exception message are:</span></span>  
  
 <span data-ttu-id="82746-169">co miało miejsce.</span><span class="sxs-lookup"><span data-stu-id="82746-169">What happened.</span></span> <span data-ttu-id="82746-170">Podaj jasny opis problemu przy użyciu terminów, które odnoszą się do środowiska użytkownika.</span><span class="sxs-lookup"><span data-stu-id="82746-170">Provide a clear description of the problem using terms that relate to the user's experience.</span></span> <span data-ttu-id="82746-171">Na przykład zły komunikat o wyjątku będzie "Nieprawidłowa sekcja konfiguracji".</span><span class="sxs-lookup"><span data-stu-id="82746-171">For example, a bad exception message would be "Invalid configuration section".</span></span> <span data-ttu-id="82746-172">Pozostawia to użytkownika zastanawiasz się, która sekcja konfiguracji jest niepoprawna i dlaczego jest niepoprawna.</span><span class="sxs-lookup"><span data-stu-id="82746-172">This leaves the user wondering which configuration section is incorrect and why it is incorrect.</span></span> <span data-ttu-id="82746-173">Ulepszony komunikat będzie "Nieprawidłowa sekcja \<konfiguracji customBinding>".</span><span class="sxs-lookup"><span data-stu-id="82746-173">An improved message would be "Invalid configuration section \<customBinding>".</span></span> <span data-ttu-id="82746-174">Jeszcze lepszy komunikat będzie "Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport".</span><span class="sxs-lookup"><span data-stu-id="82746-174">An even better message would be "Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span> <span data-ttu-id="82746-175">Jest to bardzo specyficzny komunikat przy użyciu terminów i nazw, które użytkownik może łatwo zidentyfikować w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82746-175">This is a very specific message using terms and names that the user can easily identify in the application's configuration file.</span></span> <span data-ttu-id="82746-176">Jednak nadal brakuje kilku kluczowych składników.</span><span class="sxs-lookup"><span data-stu-id="82746-176">However, there are still a few key components missing.</span></span>  
  
 <span data-ttu-id="82746-177">Znaczenie błędu.</span><span class="sxs-lookup"><span data-stu-id="82746-177">The significance of the error.</span></span> <span data-ttu-id="82746-178">O ile komunikat wyraźnie nie określa, co oznacza błąd, użytkownik może się zastanawiać, czy jest to błąd krytyczny lub czy można go zignorować.</span><span class="sxs-lookup"><span data-stu-id="82746-178">Unless the message states clearly what the error means, the user is likely to wonder whether it is a fatal error or if it can be ignored.</span></span> <span data-ttu-id="82746-179">Ogólnie rzecz biorąc komunikaty powinny prowadzić ze znaczeniem lub znaczeniem błędu.</span><span class="sxs-lookup"><span data-stu-id="82746-179">In general, messages should lead with the meaning or significance of the error.</span></span> <span data-ttu-id="82746-180">Aby poprawić poprzedni przykład, komunikat może być "ServiceHost nie można otworzyć z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport".</span><span class="sxs-lookup"><span data-stu-id="82746-180">To improve the previous example, the message could be "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport".</span></span>  
  
 <span data-ttu-id="82746-181">Jak użytkownik powinien rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="82746-181">How the user should correct the problem.</span></span> <span data-ttu-id="82746-182">Najważniejszą częścią wiadomości jest pomoc użytkownikowi w rozwiązaniu problemu.</span><span class="sxs-lookup"><span data-stu-id="82746-182">The most important part of the message is helping the user fix the problem.</span></span> <span data-ttu-id="82746-183">Komunikat powinien zawierać pewne wskazówki lub wskazówki dotyczące tego, co należy sprawdzić lub naprawić, aby rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="82746-183">The message should include some guidance or hints about what to check or fix to remedy the problem.</span></span> <span data-ttu-id="82746-184">Na przykład "ServiceHost nie można otworzyć z powodu błędu konfiguracji: Nie można dodać transportu o nazwie myTransport do powiązania o nazwie myBinding, ponieważ powiązanie ma już transport o nazwie myTransport.</span><span class="sxs-lookup"><span data-stu-id="82746-184">For example, "ServiceHost failed to Open due to a configuration error: Cannot add the transport named myTransport to the binding named myBinding because the binding already has a transport named myTransport.</span></span> <span data-ttu-id="82746-185">Upewnij się, że w oprawie znajduje się tylko jeden transport".</span><span class="sxs-lookup"><span data-stu-id="82746-185">Please ensure there is only one transport in the binding".</span></span>  
  
## <a name="communicating-faults"></a><span data-ttu-id="82746-186">Informowanie o błędach</span><span class="sxs-lookup"><span data-stu-id="82746-186">Communicating Faults</span></span>  
 <span data-ttu-id="82746-187">ZARÓWNO mydło 1.1, jak i MYDŁO 1.2 definiują specyficzną strukturę usterek.</span><span class="sxs-lookup"><span data-stu-id="82746-187">SOAP 1.1 and SOAP 1.2 both define a specific structure for faults.</span></span> <span data-ttu-id="82746-188">Istnieją pewne różnice między tymi dwoma specyfikacjami, ale ogólnie rzecz biorąc, Message i MessageFault typy są używane do tworzenia i zużywają błędy.</span><span class="sxs-lookup"><span data-stu-id="82746-188">There are some differences between the two specifications but in general, the Message and MessageFault types are used to create and consume faults.</span></span>  
  
 <span data-ttu-id="82746-189">![Obsługa wyjątków i usterek](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2SaultComparisonc")</span><span class="sxs-lookup"><span data-stu-id="82746-189">![Handling exceptions and faults](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2FaultComparisonc")</span></span>  
<span data-ttu-id="82746-190">Usterka SOAP 1.2 (po lewej) i BŁĄD SOAP 1.1 (po prawej).</span><span class="sxs-lookup"><span data-stu-id="82746-190">SOAP 1.2 Fault (left) and SOAP 1.1 Fault (right).</span></span> <span data-ttu-id="82746-191">Należy zauważyć, że w soap 1.1 tylko fault element jest obszar nazw kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="82746-191">Note that in SOAP 1.1 only the Fault element is namespace qualified.</span></span>  
  
 <span data-ttu-id="82746-192">Protokół SOAP definiuje komunikat o błędzie jako komunikat zawierający tylko `<env:Fault>`element błędu (element, którego nazwą jest) jako element podrzędny `<env:Body>`.</span><span class="sxs-lookup"><span data-stu-id="82746-192">SOAP defines a fault message as a message that contains only a fault element (an element whose name is `<env:Fault>`) as a child of `<env:Body>`.</span></span> <span data-ttu-id="82746-193">Zawartość elementu usterki różni się nieznacznie między MYDŁEM 1.1 a MYDŁEM 1.2, jak pokazano na rysunku 1.</span><span class="sxs-lookup"><span data-stu-id="82746-193">The contents of the fault element differ slightly between SOAP 1.1 and SOAP 1.2 as shown in figure 1.</span></span> <span data-ttu-id="82746-194">Jednak <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> klasa normalizuje te różnice w jeden model obiektu:</span><span class="sxs-lookup"><span data-stu-id="82746-194">However, the <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> class normalizes these differences into one object model:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-195">Właściwość `Code` odpowiada `env:Code` (lub `faultCode` w SOAP 1.1) i identyfikuje typ usterki.</span><span class="sxs-lookup"><span data-stu-id="82746-195">The `Code` property corresponds to the `env:Code` (or `faultCode` in SOAP 1.1) and identifies the type of the fault.</span></span> <span data-ttu-id="82746-196">PROTOKÓŁ SOAP 1.2 definiuje pięć `faultCode` dopuszczalnych wartości dla (na przykład `Subcode` Nadawca i Odbiorca) i definiuje element, który może zawierać dowolną wartość podkodu.</span><span class="sxs-lookup"><span data-stu-id="82746-196">SOAP 1.2 defines five allowable values for `faultCode` (for example, Sender and Receiver) and defines a `Subcode` element which can contain any subcode value.</span></span> <span data-ttu-id="82746-197">(Lista dopuszczalnych kodów usterek i ich znaczenie znajduje się w [specyfikacji protokołu SOAP 1.2).](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) SOAP 1.1 ma nieco inny mechanizm: `faultCode` definiuje cztery wartości (na przykład klient i serwer), które można rozszerzyć, definiując całkowicie nowe lub `faultCodes`za pomocą notacji kropkowej, aby utworzyć bardziej szczegółowe , na przykład Client.Authentication.</span><span class="sxs-lookup"><span data-stu-id="82746-197">(See the [SOAP 1.2 specification](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) for the list of allowable fault codes and their meaning.) SOAP 1.1 has a slightly different mechanism: It defines four `faultCode` values (for example, Client and Server) that can be extended either by defining entirely new ones or by using the dot notation to create more specific `faultCodes`, for example, Client.Authentication.</span></span>  
  
 <span data-ttu-id="82746-198">Podczas korzystania z messagefault do programowania błędów, FaultCode.Name i FaultCode.Namespace mapuje do nazwy i `env:Code` obszaru nazw protokołu SOAP `faultCode`1.2 lub SOAP 1.1 .</span><span class="sxs-lookup"><span data-stu-id="82746-198">When you use MessageFault to program faults, the FaultCode.Name and FaultCode.Namespace maps to the name and namespace of the SOAP 1.2 `env:Code` or the SOAP 1.1 `faultCode`.</span></span> <span data-ttu-id="82746-199">FaultCode.SubCode mapuje `env:Subcode` do protokołu SOAP 1.2 i jest zerowy dla protokołu SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="82746-199">The FaultCode.SubCode maps to `env:Subcode` for SOAP 1.2 and is null for SOAP 1.1.</span></span>  
  
 <span data-ttu-id="82746-200">Należy utworzyć nowe podkody błędów (lub nowe kody usterek, jeśli używasz protokołu SOAP 1.1), jeśli programowo rozróżnia się usterkę.</span><span class="sxs-lookup"><span data-stu-id="82746-200">You should create new fault subcodes (or new fault codes if using SOAP 1.1) if it is interesting to programmatically distinguish a fault.</span></span> <span data-ttu-id="82746-201">Jest to analogiczne do tworzenia nowego typu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="82746-201">This is analogous to creating a new exception type.</span></span> <span data-ttu-id="82746-202">Należy unikać używania notacji kropkowej z kodami usterek SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="82746-202">You should avoid using the dot notation with SOAP 1.1 fault codes.</span></span> <span data-ttu-id="82746-203">(Profil [podstawowy WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) również zniechęca do używania notacji dot kodu błędu).</span><span class="sxs-lookup"><span data-stu-id="82746-203">(The [WS-I Basic Profile](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) also discourages the use of the fault code dot notation.)</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-204">Właściwość `Reason` odpowiada `env:Reason` (lub `faultString` w SOAP 1.1) czytelny dla człowieka opis stanu błędu analogiczne do komunikatu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="82746-204">The `Reason` property corresponds to the `env:Reason` (or `faultString` in SOAP 1.1) a human-readable description of the error condition analogous to an exception's message.</span></span> <span data-ttu-id="82746-205">Klasa `FaultReason` (i `env:Reason/faultString`SOAP) ma wbudowaną obsługę wielu tłumaczeń w interesie globalizacji.</span><span class="sxs-lookup"><span data-stu-id="82746-205">The `FaultReason` class (and SOAP `env:Reason/faultString`) has built-in support for having multiple translations in the interest of globalization.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-206">Zawartość szczegółów usterki są widoczne na MessageFault `GetDetail` \<przy użyciu różnych `GetReaderAtDetailContents`metod, w tym T> i ().</span><span class="sxs-lookup"><span data-stu-id="82746-206">The fault detail contents are exposed on MessageFault using various methods including the `GetDetail`\<T> and `GetReaderAtDetailContents`().</span></span> <span data-ttu-id="82746-207">Szczegóły usterki jest nieprzezroczysty element do przenoszenia dodatkowych szczegółów na temat usterki.</span><span class="sxs-lookup"><span data-stu-id="82746-207">The fault detail is an opaque element for carrying additional detail about the fault.</span></span> <span data-ttu-id="82746-208">Jest to przydatne, jeśli istnieje kilka dowolnych szczegółów strukturalnych, które chcesz przeprowadzić z błędem.</span><span class="sxs-lookup"><span data-stu-id="82746-208">This is useful if there is some arbitrary structured detail that you want to carry with the fault.</span></span>  
  
### <a name="generating-faults"></a><span data-ttu-id="82746-209">Generowanie błędów</span><span class="sxs-lookup"><span data-stu-id="82746-209">Generating Faults</span></span>  
 <span data-ttu-id="82746-210">W tej sekcji opisano proces generowania błędu w odpowiedzi na warunek błędu wykryty w kanale lub we właściwości wiadomości utworzonej przez kanał.</span><span class="sxs-lookup"><span data-stu-id="82746-210">This section explains the process of generating a fault in response to an error condition detected in a channel or in a message property created by the channel.</span></span> <span data-ttu-id="82746-211">Typowym przykładem jest wysłanie z powrotem błędu w odpowiedzi na komunikat żądania, który zawiera nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="82746-211">A typical example is sending back a fault in response to a request message that contains invalid data.</span></span>  
  
 <span data-ttu-id="82746-212">Podczas generowania błędu kanał niestandardowy nie powinien wysyłać usterki bezpośrednio, a raczej powinien zgłosić wyjątek i pozwolić warstwie powyżej zdecydować, czy przekonwertować ten wyjątek na błąd i jak go wysłać.</span><span class="sxs-lookup"><span data-stu-id="82746-212">When generating a fault, the custom channel should not send the fault directly, rather, it should throw an exception and let the layer above decide whether to convert that exception to a fault and how to send it.</span></span> <span data-ttu-id="82746-213">Aby pomóc w tej konwersji, `FaultConverter` kanał powinien zapewnić implementację, która może konwertować wyjątek zgłaszany przez kanał niestandardowy na odpowiedni błąd.</span><span class="sxs-lookup"><span data-stu-id="82746-213">To aid in this conversion, the channel should provide a `FaultConverter` implementation that can convert the exception thrown by the custom channel to the appropriate fault.</span></span> <span data-ttu-id="82746-214">`FaultConverter`jest zdefiniowany jako:</span><span class="sxs-lookup"><span data-stu-id="82746-214">`FaultConverter` is defined as:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-215">Każdy kanał, który generuje niestandardowe błędy, musi `FaultConverter` `GetProperty<FaultConverter>`zaimplementować i zwrócić go z wywołania do .</span><span class="sxs-lookup"><span data-stu-id="82746-215">Each channel that generates custom faults must implement `FaultConverter` and return it from a call to `GetProperty<FaultConverter>`.</span></span> <span data-ttu-id="82746-216">Implementacja `OnTryCreateFaultMessage` niestandardowa musi przekonwertować wyjątek na błąd `FaultConverter`lub delegować do kanału wewnętrznego .</span><span class="sxs-lookup"><span data-stu-id="82746-216">The custom `OnTryCreateFaultMessage` implementation must either convert the exception to a fault or delegate to the inner channel's `FaultConverter`.</span></span> <span data-ttu-id="82746-217">Jeśli kanał jest transportem, musi przekonwertować wyjątek lub `FaultConverter` delegować `FaultConverter` do kodera lub domyślnie podany w WCF .</span><span class="sxs-lookup"><span data-stu-id="82746-217">If the channel is a transport it must either convert the exception or delegate to the encoder's `FaultConverter` or the default `FaultConverter` provided in WCF .</span></span> <span data-ttu-id="82746-218">Domyślnie `FaultConverter` konwertuje błędy odpowiadające komunikatom o błędach określonym przez WS-Addressing i SOAP.</span><span class="sxs-lookup"><span data-stu-id="82746-218">The default `FaultConverter` converts errors corresponding to fault messages specified by WS-Addressing and SOAP.</span></span> <span data-ttu-id="82746-219">Oto przykład `OnTryCreateFaultMessage` implementacji.</span><span class="sxs-lookup"><span data-stu-id="82746-219">Here is an example `OnTryCreateFaultMessage` implementation.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-220">Implikacją tego wzorca jest to, że wyjątki generowane między warstwami dla warunków błędów, które wymagają błędów, muszą zawierać wystarczającą ilość informacji dla odpowiedniego generatora usterek, aby utworzyć poprawny błąd.</span><span class="sxs-lookup"><span data-stu-id="82746-220">An implication of this pattern is that exceptions thrown between layers for error conditions that require faults must contain enough information for the corresponding fault generator to create the correct fault.</span></span> <span data-ttu-id="82746-221">Jako autor kanału niestandardowego można zdefiniować typy wyjątków, które odpowiadają różnym warunkom błędów, jeśli takie wyjątki jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="82746-221">As a custom channel author, you may define exception types that correspond to different fault conditions if such exceptions do not already exist.</span></span> <span data-ttu-id="82746-222">Należy zauważyć, że wyjątki przechodzące przez warstwy kanału powinny komunikować się warunek błędu, a nie nieprzezroczyste dane błędów.</span><span class="sxs-lookup"><span data-stu-id="82746-222">Note that exceptions traversing channel layers should communicate the error condition rather than opaque fault data.</span></span>  
  
### <a name="fault-categories"></a><span data-ttu-id="82746-223">Kategorie usterek</span><span class="sxs-lookup"><span data-stu-id="82746-223">Fault Categories</span></span>  
 <span data-ttu-id="82746-224">Zasadniczo istnieją trzy kategorie usterek:</span><span class="sxs-lookup"><span data-stu-id="82746-224">There are generally three categories of faults:</span></span>  
  
1. <span data-ttu-id="82746-225">Błędy, które są wszechobecne w całym stosie.</span><span class="sxs-lookup"><span data-stu-id="82746-225">Faults that are pervasive throughout the entire stack.</span></span> <span data-ttu-id="82746-226">Te błędy mogą wystąpić w dowolnej warstwie w stosie kanału, na przykład InvalidCardinalityAddressingException.</span><span class="sxs-lookup"><span data-stu-id="82746-226">These faults could be encountered at any layer in the channel stack, for example InvalidCardinalityAddressingException.</span></span>  
  
2. <span data-ttu-id="82746-227">Błędy, które można napotkać w dowolnym miejscu powyżej określonej warstwy w stosie, na przykład niektóre błędy, które odnoszą się do transakcji przepływanych lub ról zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="82746-227">Faults that can be encountered anywhere above a certain layer in the stack for example some errors that pertain to a flowed transaction or to security roles.</span></span>  
  
3. <span data-ttu-id="82746-228">Błędy, które są skierowane do pojedynczej warstwy w stosie, na przykład błędy, takie jak błędy numerów sekwencyjnych WS-RM.</span><span class="sxs-lookup"><span data-stu-id="82746-228">Faults that are directed at a single layer in the stack, for example errors like WS-RM sequence number faults.</span></span>  
  
 <span data-ttu-id="82746-229">Kategorii 1.</span><span class="sxs-lookup"><span data-stu-id="82746-229">Category 1.</span></span> <span data-ttu-id="82746-230">Usterki są zazwyczaj WS-Adresowanie i błędy PROTOKOŁU SOAP.</span><span class="sxs-lookup"><span data-stu-id="82746-230">Faults are generally WS-Addressing and SOAP faults.</span></span> <span data-ttu-id="82746-231">Klasa `FaultConverter` podstawowa dostarczana przez WCF konwertuje błędy odpowiadające komunikatom o błędach określonym przez WS-Addressing i SOAP, dzięki czemu nie trzeba samodzielnie obsługiwać konwersji tych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="82746-231">The base `FaultConverter` class provided by WCF converts errors corresponding to fault messages specified by WS-Addressing and SOAP so you do not have to handle conversion of these exceptions yourself.</span></span>  
  
 <span data-ttu-id="82746-232">Kategorii 2.</span><span class="sxs-lookup"><span data-stu-id="82746-232">Category 2.</span></span> <span data-ttu-id="82746-233">Błędy występują, gdy warstwa dodaje właściwość do wiadomości, która nie zużywa całkowicie informacji o wiadomości, które odnoszą się do tej warstwy.</span><span class="sxs-lookup"><span data-stu-id="82746-233">Faults occur when a layer adds a property to the message that does not completely consume message information that pertains to that layer.</span></span> <span data-ttu-id="82746-234">Błędy mogą być wykryte później, gdy wyższa warstwa prosi właściwość message do przetwarzania informacji o wiadomościach dalej.</span><span class="sxs-lookup"><span data-stu-id="82746-234">Errors may be detected later when a higher layer asks the message property to process message information further.</span></span> <span data-ttu-id="82746-235">Takie kanały `GetProperty` powinny implementować określony wcześniej, aby umożliwić wyższej warstwie odesłanie prawidłowego błędu.</span><span class="sxs-lookup"><span data-stu-id="82746-235">Such channels should implement the `GetProperty` specified previously to enable the higher layer to send back the correct fault.</span></span> <span data-ttu-id="82746-236">Przykładem tego jest TransactionMessageProperty.</span><span class="sxs-lookup"><span data-stu-id="82746-236">An example of this is the TransactionMessageProperty.</span></span> <span data-ttu-id="82746-237">Ta właściwość jest dodawana do wiadomości bez pełnej weryfikacji wszystkich danych w nagłówku (może to obejmować skontaktowanie się z koordynatorem transakcji rozproszonych (DTC).</span><span class="sxs-lookup"><span data-stu-id="82746-237">This property is added to the message without fully validating all the data in the header (doing so may involve contacting the distributed transaction coordinator (DTC).</span></span>  
  
 <span data-ttu-id="82746-238">Kategorii 3.</span><span class="sxs-lookup"><span data-stu-id="82746-238">Category 3.</span></span> <span data-ttu-id="82746-239">Usterki są generowane i wysyłane tylko przez jedną warstwę w procesorze.</span><span class="sxs-lookup"><span data-stu-id="82746-239">Faults are only generated and sent by a single layer in the processor.</span></span> <span data-ttu-id="82746-240">W związku z tym wszystkie wyjątki są zawarte w warstwie.</span><span class="sxs-lookup"><span data-stu-id="82746-240">Therefore all the exceptions are contained within the layer.</span></span> <span data-ttu-id="82746-241">Aby poprawić spójność między kanałami i ułatwić konserwację, kanał niestandardowy powinien używać wzorca określonego wcześniej do generowania komunikatów o błędach nawet w przypadku błędów wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="82746-241">To improve consistency among channels and ease maintenance, your custom channel should use the pattern specified previously to generate fault messages even for internal faults.</span></span>  
  
### <a name="interpreting-received-faults"></a><span data-ttu-id="82746-242">Interpretowanie odebranych błędów</span><span class="sxs-lookup"><span data-stu-id="82746-242">Interpreting Received Faults</span></span>  
 <span data-ttu-id="82746-243">Ta sekcja zawiera wskazówki dotyczące generowania odpowiedniego wyjątku podczas odbierania komunikatu o błędzie.</span><span class="sxs-lookup"><span data-stu-id="82746-243">This section provides guidance for generating the appropriate exception when receiving a fault message.</span></span> <span data-ttu-id="82746-244">Drzewo decyzyjne do przetwarzania wiadomości w każdej warstwie stosu jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="82746-244">The decision tree for processing a message at every layer in the stack is as follows:</span></span>  
  
1. <span data-ttu-id="82746-245">Jeśli warstwa uzna wiadomość za nieprawidłową, warstwa powinna wykonać przetwarzanie "nieprawidłowej wiadomości".</span><span class="sxs-lookup"><span data-stu-id="82746-245">If the layer considers the message to be invalid, the layer should do its 'invalid message' processing.</span></span> <span data-ttu-id="82746-246">Takie przetwarzanie jest specyficzne dla warstwy, ale może obejmować upuszczenie wiadomości, śledzenie lub zgłaszanie wyjątku, który zostanie przekonwertowany na błąd.</span><span class="sxs-lookup"><span data-stu-id="82746-246">Such processing is specific to the layer but could include dropping the message, tracing, or throwing an exception that gets converted to a fault.</span></span> <span data-ttu-id="82746-247">Przykłady obejmują zabezpieczenia odbieranie wiadomości, która nie jest poprawnie zabezpieczona, lub RM odbieranie wiadomości ze złym numerem sekwencyjnym.</span><span class="sxs-lookup"><span data-stu-id="82746-247">Examples include security receiving a message that is not secured properly, or RM receiving a message with a bad sequence number.</span></span>  
  
2. <span data-ttu-id="82746-248">W przeciwnym razie jeśli komunikat jest komunikatem o błędzie, który ma zastosowanie w szczególności do warstwy, a wiadomość nie ma znaczenia poza interakcją warstwy, warstwa powinna obsługiwać warunek błędu.</span><span class="sxs-lookup"><span data-stu-id="82746-248">Otherwise, if the message is a fault message that applies specifically to the layer, and the message is not meaningful outside the layer's interaction, the layer should handle the error condition.</span></span> <span data-ttu-id="82746-249">Przykładem tego jest błąd odmowy sekwencji RM, który jest bez znaczenia dla warstw powyżej kanału RM i który implikuje błąd kanału RM i wyrzucanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="82746-249">An example of this is an RM Sequence Refused fault that is meaningless to layers above the RM channel and that implies faulting the RM channel and throwing from pending operations.</span></span>  
  
3. <span data-ttu-id="82746-250">W przeciwnym razie wiadomość powinna zostać zwrócona z request() lub receive().</span><span class="sxs-lookup"><span data-stu-id="82746-250">Otherwise, the message should be returned from Request() or Receive().</span></span> <span data-ttu-id="82746-251">Obejmuje to przypadki, w których warstwa rozpoznaje błąd, ale błąd tylko wskazuje, że żądanie nie powiodło się i nie oznacza błąd kanału i wyrzucanie z oczekujących operacji.</span><span class="sxs-lookup"><span data-stu-id="82746-251">This includes cases where the layer recognizes the fault, but the fault just indicates that a request failed and does not imply faulting the channel and throwing from pending operations.</span></span> <span data-ttu-id="82746-252">Aby poprawić użyteczność w takim przypadku, `GetProperty<FaultConverter>` warstwa `FaultConverter` powinna zaimplementować i zwrócić klasę `OnTryCreateException`pochodną, która może przekonwertować błąd na wyjątek przez zastąpienie .</span><span class="sxs-lookup"><span data-stu-id="82746-252">To improve usability in such a case, the layer should implement `GetProperty<FaultConverter>` and return a `FaultConverter` derived class that can convert the fault to an exception by overriding `OnTryCreateException`.</span></span>  
  
 <span data-ttu-id="82746-253">Następujący model obiektu obsługuje konwertowanie komunikatów na wyjątki:</span><span class="sxs-lookup"><span data-stu-id="82746-253">The following object model supports converting messages to exceptions:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-254">Warstwa kanału `GetProperty<FaultConverter>` można zaimplementować do obsługi konwersji komunikatów o błędach do wyjątków.</span><span class="sxs-lookup"><span data-stu-id="82746-254">A channel layer can implement `GetProperty<FaultConverter>` to support converting fault messages to exceptions.</span></span> <span data-ttu-id="82746-255">Aby to zrobić, `OnTryCreateException` należy zastąpić i sprawdzić komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="82746-255">To do so, override `OnTryCreateException` and inspect the fault message.</span></span> <span data-ttu-id="82746-256">Jeśli zostanie rozpoznana, wykonaj konwersję, poproś kanał wewnętrzny o jej przekonwertowanie.</span><span class="sxs-lookup"><span data-stu-id="82746-256">If recognized, do the conversion, otherwise ask the inner channel to convert it.</span></span> <span data-ttu-id="82746-257">Kanały transportu `FaultConverter.GetDefaultFaultConverter` należy delegować do uzyskania domyślnego soap/WS-Addressing FaultConverter.</span><span class="sxs-lookup"><span data-stu-id="82746-257">Transport channels should delegate to `FaultConverter.GetDefaultFaultConverter` to get the default SOAP/WS-Addressing FaultConverter.</span></span>  
  
 <span data-ttu-id="82746-258">Typowa implementacja wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="82746-258">A typical implementation looks like this:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="82746-259">W przypadku określonych warunków błędów, które mają różne scenariusze odzyskiwania, należy rozważyć zdefiniowanie klasy pochodnej `ProtocolException`.</span><span class="sxs-lookup"><span data-stu-id="82746-259">For specific fault conditions that have distinct recovery scenarios, consider defining a derived class of `ProtocolException`.</span></span>  
  
### <a name="mustunderstand-processing"></a><span data-ttu-id="82746-260">Przetwarzanie MustUnderstand</span><span class="sxs-lookup"><span data-stu-id="82746-260">MustUnderstand Processing</span></span>  
 <span data-ttu-id="82746-261">PROTOKÓŁ SOAP definiuje ogólną usterkę sygnalizacji, że wymagany nagłówek nie został zrozumiany przez odbiornik.</span><span class="sxs-lookup"><span data-stu-id="82746-261">SOAP defines a general fault for signaling that a required header was not understood by the receiver.</span></span> <span data-ttu-id="82746-262">Ten błąd jest `mustUnderstand` znany jako usterka.</span><span class="sxs-lookup"><span data-stu-id="82746-262">This fault is known as the `mustUnderstand` fault.</span></span> <span data-ttu-id="82746-263">W WCF kanały `mustUnderstand` niestandardowe nigdy nie generują błędów.</span><span class="sxs-lookup"><span data-stu-id="82746-263">In WCF, custom channels never generate `mustUnderstand` faults.</span></span> <span data-ttu-id="82746-264">Zamiast tego WCF Dispatcher, który znajduje się w górnej części stosu komunikacji WCF, sprawdza, czy wszystkie nagłówki, które zostały oznaczone jako MustUnderstand= true zostały zrozumiane przez podstawowy stos.</span><span class="sxs-lookup"><span data-stu-id="82746-264">Instead, the WCF Dispatcher, which is located at the top of the WCF communication stack, checks to see that all headers that were marked as MustUnderstand=true were understood by the underlying stack.</span></span> <span data-ttu-id="82746-265">Jeśli którekolwiek nie zostały `mustUnderstand` zrozumiane, błąd jest generowany w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="82746-265">If any were not understood, a `mustUnderstand` fault is generated at that point.</span></span> <span data-ttu-id="82746-266">(Użytkownik może wyłączyć to `mustUnderstand` przetwarzanie i aplikacja odbierać wszystkie nagłówki wiadomości.</span><span class="sxs-lookup"><span data-stu-id="82746-266">(The user can choose to turn off this `mustUnderstand` processing and have the application receive all message headers.</span></span> <span data-ttu-id="82746-267">W takim przypadku aplikacja jest `mustUnderstand` odpowiedzialna za przetwarzanie.) Wygenerowany błąd zawiera nierozdumiony nagłówek, który zawiera nazwy wszystkich nagłówków z MustUnderstand = true, które nie zostały zrozumiane.</span><span class="sxs-lookup"><span data-stu-id="82746-267">In that case the application is responsible for performing `mustUnderstand` processing.) The generated fault includes a NotUnderstood header that contains the names of all headers with MustUnderstand=true that were not understood.</span></span>  
  
 <span data-ttu-id="82746-268">Jeśli kanał protokołu wysyła niestandardowy nagłówek z MustUnderstand = true i odbiera `mustUnderstand` błąd, należy dowiedzieć się, czy ten błąd jest z powodu nagłówka, który wysłał.</span><span class="sxs-lookup"><span data-stu-id="82746-268">If your protocol channel sends a custom header with MustUnderstand=true and receives a `mustUnderstand` fault, it must figure out whether that fault is due to the header it sent.</span></span> <span data-ttu-id="82746-269">Istnieją dwa elementy `MessageFault` członkowskie w klasie, które są przydatne do tego:</span><span class="sxs-lookup"><span data-stu-id="82746-269">There are two members on the `MessageFault` class that are useful for this:</span></span>  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 <span data-ttu-id="82746-270">`IsMustUnderstandFault`zwraca, `true` jeśli usterka jest wadą. `mustUnderstand`</span><span class="sxs-lookup"><span data-stu-id="82746-270">`IsMustUnderstandFault` returns `true` if the fault is a `mustUnderstand` fault.</span></span> <span data-ttu-id="82746-271">`WasHeaderNotUnderstood`zwraca, `true` jeśli nagłówek o określonej nazwie i obszarze nazw jest uwzględniony w usterce jako nagłówek NotUnderstood.</span><span class="sxs-lookup"><span data-stu-id="82746-271">`WasHeaderNotUnderstood` returns `true` if the header with the specified name and namespace is included in the fault as a NotUnderstood header.</span></span>  <span data-ttu-id="82746-272">W przeciwnym `false`razie zwraca .</span><span class="sxs-lookup"><span data-stu-id="82746-272">Otherwise, it returns `false`.</span></span>  
  
 <span data-ttu-id="82746-273">Jeśli kanał emituje nagłówek, który jest oznaczony MustUnderstand = true, a następnie tej `mustUnderstand` warstwy należy również zaimplementować wzorzec interfejsu API generowania wyjątków i należy przekonwertować błędy spowodowane przez ten nagłówek do bardziej użyteczny wyjątek, jak opisano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="82746-273">If a channel emits a header that is marked MustUnderstand = true, then that layer should also implement the Exception Generation API pattern and should convert `mustUnderstand` faults caused by that header to a more useful exception as described previously.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="82746-274">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="82746-274">Tracing</span></span>  
 <span data-ttu-id="82746-275">.NET Framework zapewnia mechanizm śledzenia wykonywania programu jako sposób na pomoc w diagnozowaniu aplikacji produkcyjnych lub sporadyczne problemy, gdzie nie jest możliwe po prostu dołączyć debugera i krok po kroku przez kod.</span><span class="sxs-lookup"><span data-stu-id="82746-275">The .NET Framework provides a mechanism to trace program execution as a way to aid diagnosing production applications or intermittent problems where it is not possible to just attach a debugger and step through the code.</span></span> <span data-ttu-id="82746-276">Podstawowe składniki tego mechanizmu <xref:System.Diagnostics?displayProperty=nameWithType> znajdują się w przestrzeni nazw i składają się z:</span><span class="sxs-lookup"><span data-stu-id="82746-276">The core components of this mechanism are in the <xref:System.Diagnostics?displayProperty=nameWithType> namespace and consist of:</span></span>  
  
- <span data-ttu-id="82746-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, który jest źródłem informacji śledzenia, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>które mają być napisane, który jest abstrakcyjną klasą podstawową dla konkretnych słuchaczy, które otrzymują informacje, które mają być śledzone z <xref:System.Diagnostics.TraceSource> i wyjście go do miejsca docelowego specyficzne dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="82746-277"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, which is the source of trace information to be written, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, which is an abstract base class for concrete listeners that receive the information to be traced from the <xref:System.Diagnostics.TraceSource> and output it to a listener-specific destination.</span></span> <span data-ttu-id="82746-278">Na przykład <xref:System.Diagnostics.XmlWriterTraceListener> dane wyjściowe śledzenia informacji do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="82746-278">For example, <xref:System.Diagnostics.XmlWriterTraceListener> outputs trace information to an XML file.</span></span> <span data-ttu-id="82746-279">Na koniec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, który pozwala użytkownikowi aplikacji kontrolować szczegółowość śledzenia i jest zazwyczaj określony w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="82746-279">Finally, <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, which lets the application user control the tracing verbosity and is typically specified in configuration.</span></span>  
  
- <span data-ttu-id="82746-280">Oprócz podstawowych składników można użyć [narzędzia Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) do wyświetlania i wyszukiwania śladów WCF.</span><span class="sxs-lookup"><span data-stu-id="82746-280">In addition to the core components, you can use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) to view and search WCF traces.</span></span> <span data-ttu-id="82746-281">Narzędzie zostało zaprojektowane specjalnie dla plików śledzenia generowanych przez <xref:System.Diagnostics.XmlWriterTraceListener>WCF i wypisywane za pomocą .</span><span class="sxs-lookup"><span data-stu-id="82746-281">The tool is designed specifically for trace files generated by WCF and written out using <xref:System.Diagnostics.XmlWriterTraceListener>.</span></span> <span data-ttu-id="82746-282">Na poniższej ilustracji przedstawiono różne składniki zaangażowane w śledzenie.</span><span class="sxs-lookup"><span data-stu-id="82746-282">The following figure shows the various components involved in tracing.</span></span>  
  
 <span data-ttu-id="82746-283">![Obsługa wyjątków i usterek](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span><span class="sxs-lookup"><span data-stu-id="82746-283">![Handling exceptions and faults](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")</span></span>  
  
### <a name="tracing-from-a-custom-channel"></a><span data-ttu-id="82746-284">Śledzenie z kanału niestandardowego</span><span class="sxs-lookup"><span data-stu-id="82746-284">Tracing from a Custom Channel</span></span>  
 <span data-ttu-id="82746-285">Kanały niestandardowe powinny zapisywać komunikaty śledzenia, aby pomóc w diagnozowaniu problemów, gdy nie jest możliwe dołączenie debugera do uruchomionej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82746-285">Custom channels should write out trace messages to assist in diagnosing problems when it is not possible to attach a debugger to the running application.</span></span> <span data-ttu-id="82746-286">Obejmuje to dwa zadania wysokiego poziomu: tworzenie wystąpienia <xref:System.Diagnostics.TraceSource> i wywoływanie jego metod do zapisu śladów.</span><span class="sxs-lookup"><span data-stu-id="82746-286">This involves two high level tasks: Instantiating a <xref:System.Diagnostics.TraceSource> and calling its methods to write traces.</span></span>  
  
 <span data-ttu-id="82746-287">Podczas tworzenia wystąpienia <xref:System.Diagnostics.TraceSource>, określony ciąg staje się nazwą tego źródła.</span><span class="sxs-lookup"><span data-stu-id="82746-287">When instantiating a <xref:System.Diagnostics.TraceSource>, the string you specify becomes the name of that source.</span></span> <span data-ttu-id="82746-288">Ta nazwa jest używana do konfigurowania (włącz/wyłącz/ustaw poziom śledzenia) źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-288">This name is used to configure (enable/disable/set tracing level) the trace source.</span></span> <span data-ttu-id="82746-289">Pojawia się również w danych wyjściowych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-289">It also appears in the trace output itself.</span></span> <span data-ttu-id="82746-290">Kanały niestandardowe powinny używać unikatowej nazwy źródła, aby pomóc czytelnikom danych wyjściowych śledzenia zrozumieć, skąd pochodzą informacje śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-290">Custom channels should use a unique source name to help readers of the trace output understand where the trace information comes from.</span></span> <span data-ttu-id="82746-291">Przy użyciu nazwy zestawu, który zapisuje informacje jako nazwę źródła śledzenia jest powszechną praktyką.</span><span class="sxs-lookup"><span data-stu-id="82746-291">Using the name of the assembly that is writing the information as the name of the trace source is the common practice.</span></span> <span data-ttu-id="82746-292">Na przykład WCF używa System.ServiceModel jako źródła śledzenia informacji zapisanych z System.ServiceModel zestawu.</span><span class="sxs-lookup"><span data-stu-id="82746-292">For example, WCF uses System.ServiceModel as the trace source for information written from the System.ServiceModel assembly.</span></span>  
  
 <span data-ttu-id="82746-293">Gdy masz źródło śledzenia, można <xref:System.Diagnostics.TraceSource.TraceData%2A> <xref:System.Diagnostics.TraceSource.TraceEvent%2A>wywołać <xref:System.Diagnostics.TraceSource.TraceInformation%2A> jego , lub metody zapisu śledzenia wpisów do odbiorników śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-293">Once you have a trace source, you call its <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, or <xref:System.Diagnostics.TraceSource.TraceInformation%2A> methods to write trace entries to the trace listeners.</span></span> <span data-ttu-id="82746-294">Dla każdego wpisu śledzenia, który piszesz, należy sklasyfikować <xref:System.Diagnostics.TraceEventType>typ zdarzenia jako jeden z typów zdarzeń zdefiniowanych w .</span><span class="sxs-lookup"><span data-stu-id="82746-294">For each trace entry you write, you need to classify the type of event as one of the event types defined in <xref:System.Diagnostics.TraceEventType>.</span></span> <span data-ttu-id="82746-295">Ta klasyfikacja i ustawienie poziomu śledzenia w konfiguracji określają, czy wpis śledzenia jest wyprowadzany do odbiornika.</span><span class="sxs-lookup"><span data-stu-id="82746-295">This classification and the trace level setting in configuration determine whether the trace entry is output to the listener.</span></span> <span data-ttu-id="82746-296">Na przykład ustawienie poziomu śledzenia `Warning` w `Warning` `Error` konfiguracji, aby umożliwiać zapisanie wpisów śledzenia i `Critical` śledzenia, ale blokuje wpisy informacje i pełne.</span><span class="sxs-lookup"><span data-stu-id="82746-296">For example, setting the trace level in configuration to `Warning` allows `Warning`, `Error` and `Critical` trace entries to be written but blocks Information and Verbose entries.</span></span> <span data-ttu-id="82746-297">Oto przykład tworzenia wystąpienia źródła śledzenia i wypisywanie wpisu na poziomie informacji:</span><span class="sxs-lookup"><span data-stu-id="82746-297">Here is an example of instantiating a trace source and writing out an entry at Information level:</span></span>  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="82746-298">Zdecydowanie zaleca się określenie nazwy źródła śledzenia, która jest unikatowa dla kanału niestandardowego, aby ułatwić czytnikom danych wyjściowych zrozumienie, skąd pochodzi dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="82746-298">It is highly recommended that you specify a trace source name that is unique to your custom channel to help trace output readers understand where the output came from.</span></span>  
  
#### <a name="integrating-with-the-trace-viewer"></a><span data-ttu-id="82746-299">Integracja z przeglądarką śledzenia</span><span class="sxs-lookup"><span data-stu-id="82746-299">Integrating with the Trace Viewer</span></span>  
 <span data-ttu-id="82746-300">Ślady generowane przez kanał mogą być dane wyjściowe w formacie czytelnym dla [narzędzia Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) przy użyciu <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako odbiornik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-300">Traces generated by your channel can be output in a format readable by the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) by using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> as the trace listener.</span></span> <span data-ttu-id="82746-301">To nie jest coś, co ty, jako deweloper kanału, musisz zrobić.</span><span class="sxs-lookup"><span data-stu-id="82746-301">This is not something you, as the channel developer, need to do.</span></span> <span data-ttu-id="82746-302">Jest to raczej użytkownik aplikacji (lub osoba, która rozwiązuje problemy z aplikacją), która musi skonfigurować ten odbiornik śledzenia w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82746-302">Rather, it is the application user (or the person troubleshooting the application) that needs to configure this trace listener in the application's configuration file.</span></span> <span data-ttu-id="82746-303">Na przykład następujące wyjścia konfiguracyjne <xref:System.ServiceModel?displayProperty=nameWithType> śledzą `Microsoft.Samples.Udp` informacje zarówno `TraceEventsFile.e2e`z i do pliku o nazwie:</span><span class="sxs-lookup"><span data-stu-id="82746-303">For example, the following configuration outputs trace information from both <xref:System.ServiceModel?displayProperty=nameWithType> and `Microsoft.Samples.Udp` to the file named `TraceEventsFile.e2e`:</span></span>  
  
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
  
#### <a name="tracing-structured-data"></a><span data-ttu-id="82746-304">Śledzenie danych strukturalnych</span><span class="sxs-lookup"><span data-stu-id="82746-304">Tracing Structured Data</span></span>  
 <span data-ttu-id="82746-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>ma <xref:System.Diagnostics.TraceSource.TraceData%2A> metodę, która przyjmuje jeden lub więcej obiektów, które mają być uwzględnione we wpisie śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-305"><xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> has a <xref:System.Diagnostics.TraceSource.TraceData%2A> method that takes one or more objects that are to be included in the trace entry.</span></span> <span data-ttu-id="82746-306">Ogólnie rzecz <xref:System.Object.ToString%2A?displayProperty=nameWithType> biorąc metoda jest wywoływana na każdy obiekt i wynikowy ciąg jest zapisywany jako część wpisu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="82746-306">In general, the <xref:System.Object.ToString%2A?displayProperty=nameWithType> method is called on each object and the resulting string is written as part of the trace entry.</span></span> <span data-ttu-id="82746-307">Podczas <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> korzystania z śledzenia danych wyjściowych, można przekazać <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako obiekt danych do <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span><span class="sxs-lookup"><span data-stu-id="82746-307">When using <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> to output traces, you can pass an <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> as the data object to <xref:System.Diagnostics.TraceSource.TraceData%2A>.</span></span> <span data-ttu-id="82746-308">Wynikowy wpis śledzenia zawiera kod XML dostarczony przez plik <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82746-308">The resulting trace entry includes the XML provided by the <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82746-309">Oto przykładowy wpis z danymi aplikacji XML:</span><span class="sxs-lookup"><span data-stu-id="82746-309">Here is an example entry with XML application data:</span></span>  
  
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
  
 <span data-ttu-id="82746-310">Przeglądarka śledzenia WCF rozumie schemat `TraceRecord` elementu pokazano wcześniej i wyodrębnia dane z jego elementów podrzędnych i wyświetla je w formacie tabelarycznym.</span><span class="sxs-lookup"><span data-stu-id="82746-310">The WCF trace viewer understands the schema of the `TraceRecord` element shown previously and extracts the data from its child elements and displays it in a tabular format.</span></span> <span data-ttu-id="82746-311">Kanał powinien używać tego schematu podczas śledzenia danych aplikacji strukturalnych, aby pomóc użytkownikom Svctraceviewer.exe odczytać dane.</span><span class="sxs-lookup"><span data-stu-id="82746-311">Your channel should use this schema when tracing structured application data to help Svctraceviewer.exe users read the data.</span></span>

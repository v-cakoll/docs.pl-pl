---
title: Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
ms.openlocfilehash: e506908299109f94be6d190017b381fe7b4ee044
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032993"
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="35c18-102">Informacje o prywatności dotyczące architektury WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="35c18-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="35c18-103">Firma Microsoft jest zaangażowana w ochronę prywatności użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="35c18-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="35c18-104">Podczas tworzenia aplikacji przy użyciu funkcji Windows Communication Foundation (WCF), wersja 3.0, aplikacja może mieć wpływ na prywatność użytkowników końcowych.</span><span class="sxs-lookup"><span data-stu-id="35c18-104">When you build an application using Windows Communication Foundation (WCF), version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="35c18-105">Na przykład aplikacja jawnie może zbierać informacje kontaktowe użytkownika, lub może zażądać lub wysyłanie informacji przez Internet do witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="35c18-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="35c18-106">Technologii firmy Microsoft w przypadku osadzenia w aplikacji, technologia ta może mieć własną zachowanie, które mogą mieć wpływ na prywatność.</span><span class="sxs-lookup"><span data-stu-id="35c18-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> <span data-ttu-id="35c18-107">Usługi WCF nie wysyła żadnych informacji do firmy Microsoft z aplikacji, chyba że użytkownik lub użytkownik końcowy chce wysłać ją do nas.</span><span class="sxs-lookup"><span data-stu-id="35c18-107">WCF does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="35c18-108">Usługi WCF w skrócie</span><span class="sxs-lookup"><span data-stu-id="35c18-108">WCF in Brief</span></span>  
 <span data-ttu-id="35c18-109">Usługi WCF jest platforma obsługi komunikatów rozproszonych przy użyciu programu Microsoft .NET Framework, która umożliwia deweloperom tworzenie aplikacji rozproszonych.</span><span class="sxs-lookup"><span data-stu-id="35c18-109">WCF is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="35c18-110">Komunikaty przekazywane między dwiema aplikacjami zawierają informacje, nagłówek i treść.</span><span class="sxs-lookup"><span data-stu-id="35c18-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="35c18-111">Może zawierać nagłówki, routing komunikatów, informacje o zabezpieczeniach, transakcji i dłużej w zależności od usług używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="35c18-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="35c18-112">Komunikaty są zazwyczaj domyślne szyfrowanie przekazywanego materiału.</span><span class="sxs-lookup"><span data-stu-id="35c18-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="35c18-113">Jedynym wyjątek polega na użyciu `BasicHttpBinding`, który został zaprojektowany do użytku z niezabezpieczonych, starszej wersji usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="35c18-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="35c18-114">Projektant aplikacji odpowiedzialność za ostatecznego projektu.</span><span class="sxs-lookup"><span data-stu-id="35c18-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="35c18-115">Komunikaty w treści protokołu SOAP zawierają dane specyficzne dla aplikacji; Jednak te dane, takie jak zdefiniowane przez aplikację informacje osobiste mogą być chronione za pomocą funkcji szyfrowania lub poufności WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using WCF encryption or confidentiality features.</span></span> <span data-ttu-id="35c18-116">W poniższych sekcjach opisano funkcje, które mogłoby to wpłynąć na zachowania.</span><span class="sxs-lookup"><span data-stu-id="35c18-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="35c18-117">Obsługa wiadomości</span><span class="sxs-lookup"><span data-stu-id="35c18-117">Messaging</span></span>  
 <span data-ttu-id="35c18-118">Każdy komunikat WCF ma nagłówek adres, który określa miejsce docelowe wiadomości i gdzie odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="35c18-118">Each WCF message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="35c18-119">Składnik adresu adresu punktu końcowego jest jednolite zasobów identyfikator (URI), który identyfikuje punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="35c18-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="35c18-120">Adres może być adresu sieciowego lub adres logiczny.</span><span class="sxs-lookup"><span data-stu-id="35c18-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="35c18-121">Adres może zawierać nazwy komputera (nazwa hosta, w pełni kwalifikowana nazwa domeny) i adres IP.</span><span class="sxs-lookup"><span data-stu-id="35c18-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="35c18-122">Adres punktu końcowego może również zawierać unikatowy identyfikator globalny (GUID) lub zbiór identyfikatorów GUID do adresowania tymczasowe umożliwia brakowi rozróżnienia każdego z adresów.</span><span class="sxs-lookup"><span data-stu-id="35c18-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="35c18-123">Każdy komunikat zawiera identyfikator komunikatu, który jest identyfikatorem GUID.</span><span class="sxs-lookup"><span data-stu-id="35c18-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="35c18-124">Ta funkcja postępuje zgodnie ze standardowym odwołanie WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="35c18-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="35c18-125">Warstwa obsługi komunikatów usługi WCF nie zapisuje żadnych danych osobowych do komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="35c18-125">The WCF messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="35c18-126">Jednak go może propagację informacje osobiste, na poziomie sieci jeśli deweloper usługi został utworzony, to usługa, która udostępnia takie informacje (np. przez przy użyciu nazwy osoby w nazwy punktu końcowego lub w tym informacje osobiste w sieci Web punktu końcowego Usługi języka opisu, ale nie wymaga klientom dostęp do pliku WSDL przy użyciu protokołu https).</span><span class="sxs-lookup"><span data-stu-id="35c18-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="35c18-127">Ponadto jeśli deweloper działa [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzie względem punktu końcowego, który udostępnia informacje osobiste, dane wyjściowe narzędzia firmy mogą zawierać te informacje, i jest zapisywany plik wyjściowy lokalny dysk twardy.</span><span class="sxs-lookup"><span data-stu-id="35c18-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="35c18-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="35c18-128">Hosting</span></span>  
 <span data-ttu-id="35c18-129">Hostingu funkcji w programie WCF umożliwia aplikacjom, które można uruchomić na żądanie lub włączanie udostępniania portów między wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="35c18-129">The hosting feature in WCF allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="35c18-130">Aplikacja usługi WCF, mogą być hostowane w Internet Information Services (IIS), podobnie jak [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="35c18-130">An WCF application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="35c18-131">Hostingu nie ujawnia żadnych konkretnych informacji o sieci i nie przechowuje danych na maszynie.</span><span class="sxs-lookup"><span data-stu-id="35c18-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="35c18-132">Zabezpieczenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="35c18-132">Message Security</span></span>  
 <span data-ttu-id="35c18-133">Zabezpieczenia programu WCF zapewnia funkcje zabezpieczeń dla aplikacji do obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35c18-133">WCF security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="35c18-134">Dostępne funkcje zabezpieczeń obejmują uwierzytelnianie i autoryzację.</span><span class="sxs-lookup"><span data-stu-id="35c18-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="35c18-135">Uwierzytelnianie jest wykonywane przez przekazywanie poświadczeń między klientami i usługami.</span><span class="sxs-lookup"><span data-stu-id="35c18-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="35c18-136">Uwierzytelnianie można za pomocą zabezpieczeń na poziomie transportu lub za pośrednictwem protokołu SOAP wiadomości zabezpieczenia na poziomie, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="35c18-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
- <span data-ttu-id="35c18-137">W ramach zabezpieczeń komunikatów protokołu SOAP uwierzytelnianie będzie przeprowadzane przy użyciu poświadczeń, takie jak nazwy użytkownika i hasła, certyfikaty X.509, bilety protokołu Kerberos i tokeny SAML, które mogą zawierać informacje osobiste, w zależności od wystawcy.</span><span class="sxs-lookup"><span data-stu-id="35c18-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
- <span data-ttu-id="35c18-138">Za pomocą zabezpieczeń transportu, uwierzytelnianie odbywa się za pośrednictwem tradycyjnych transportu mechanizmów uwierzytelniania, takich jak schematy uwierzytelniania HTTP (Basic, Digest, Negotiate, zintegrowanej autoryzacji Windows, NTLM, None i anonimowych) i uwierzytelniania formularzy.</span><span class="sxs-lookup"><span data-stu-id="35c18-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="35c18-139">Uwierzytelnianie może spowodować bezpiecznej sesji między komunikujące się punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="35c18-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="35c18-140">Sesja jest identyfikowana przez identyfikator GUID, który trwa okres istnienia sesji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="35c18-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="35c18-141">W poniższej tabeli przedstawiono, jakie są przechowywane i gdzie.</span><span class="sxs-lookup"><span data-stu-id="35c18-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="35c18-142">Dane</span><span class="sxs-lookup"><span data-stu-id="35c18-142">Data</span></span>|<span data-ttu-id="35c18-143">Magazyn</span><span class="sxs-lookup"><span data-stu-id="35c18-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="35c18-144">Prezentacja poświadczenia, takie jak nazwa użytkownika, certyfikatów X.509, tokenów protokołu Kerberos i odwołania do poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="35c18-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="35c18-145">Standardowa Windows poświadczeń mechanizmami zarządzania, takich jak Sklep Windows certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="35c18-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="35c18-146">Członkostwo w informacje o użytkowniku, takie jak nazwy użytkowników i hasła.</span><span class="sxs-lookup"><span data-stu-id="35c18-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] <span data-ttu-id="35c18-147">dostawcy członkostwa.</span><span class="sxs-lookup"><span data-stu-id="35c18-147">membership providers.</span></span>|  
|<span data-ttu-id="35c18-148">Informacje identyfikacyjne dotyczące usługi używany do uwierzytelniania usługi dla klientów.</span><span class="sxs-lookup"><span data-stu-id="35c18-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="35c18-149">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="35c18-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="35c18-150">Informacje o wywołującym.</span><span class="sxs-lookup"><span data-stu-id="35c18-150">Caller information.</span></span>|<span data-ttu-id="35c18-151">Dzienniki inspekcji.</span><span class="sxs-lookup"><span data-stu-id="35c18-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="35c18-152">Inspekcja</span><span class="sxs-lookup"><span data-stu-id="35c18-152">Auditing</span></span>  
 <span data-ttu-id="35c18-153">Inspekcja rejestruje sukcesów i niepowodzeń zdarzenia uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="35c18-154">Rekordy inspekcji zawierają następujące dane: identyfikator URI, identyfikator URI akcji oraz identyfikator obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="35c18-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="35c18-155">Inspekcja również są rejestrowane po administrator Modyfikuje konfigurację rejestrowania komunikatów (Włączanie on lub off), ponieważ rejestrowanie komunikatów mogą rejestrować dane specyficzne dla aplikacji w nagłówki i treść.</span><span class="sxs-lookup"><span data-stu-id="35c18-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="35c18-156">Aby uzyskać [!INCLUDE[wxp](../../../includes/wxp-md.md)], rekord jest rejestrowane w dzienniku zdarzeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="35c18-157">Aby uzyskać [!INCLUDE[wv](../../../includes/wv-md.md)] i [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], rekord jest rejestrowane w dzienniku zdarzeń zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="35c18-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="35c18-158">Transakcje</span><span class="sxs-lookup"><span data-stu-id="35c18-158">Transactions</span></span>  
 <span data-ttu-id="35c18-159">Funkcja transakcji udostępnia transakcyjne usługi aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-159">The transactions feature provides transactional services to a WCF application.</span></span>  
  
 <span data-ttu-id="35c18-160">Nagłówki transakcji używanych w propagacji transakcji może zawierać identyfikatory transakcji lub identyfikatorów rejestracji, które są identyfikatory GUID.</span><span class="sxs-lookup"><span data-stu-id="35c18-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="35c18-161">Funkcja transakcji używa transakcji Koordynator MSDTC (Microsoft Distributed) Menedżera transakcji (składnik Windows) do zarządzania stanem transakcji.</span><span class="sxs-lookup"><span data-stu-id="35c18-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="35c18-162">Domyślnie komunikacja między menedżerami transakcje są szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="35c18-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="35c18-163">Menedżerowie transakcji mogą rejestrować się odwołania do endpoint, identyfikatory transakcji i identyfikatorów rejestracji, w ramach stanu trwałego.</span><span class="sxs-lookup"><span data-stu-id="35c18-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="35c18-164">Okres istnienia tego stanu jest określana przez okres istnienia pliku dziennika Menedżera transakcji.</span><span class="sxs-lookup"><span data-stu-id="35c18-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="35c18-165">Usługa MSDTC jest właścicielem i przechowuje ten dziennik.</span><span class="sxs-lookup"><span data-stu-id="35c18-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="35c18-166">Funkcja transakcji implementuje standardów WS koordynacji i WS-Atomic Transaction.</span><span class="sxs-lookup"><span data-stu-id="35c18-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="35c18-167">Niezawodne sesje</span><span class="sxs-lookup"><span data-stu-id="35c18-167">Reliable Sessions</span></span>  
 <span data-ttu-id="35c18-168">Niezawodne sesje w programie WCF zapewniają przesyłanie wiadomości, gdy transportu lub pośredniczący błędy występują.</span><span class="sxs-lookup"><span data-stu-id="35c18-168">Reliable sessions in WCF provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="35c18-169">Zapewniają one dokładnie — raz przesyłanie komunikatów, nawet wtedy, gdy transportu źródłowego odłącza (np. połączenia protokołu TCP w sieci bezprzewodowej) lub utraci komunikat (serwer proxy HTTP porzucenie wiadomości wychodzące lub przychodzące).</span><span class="sxs-lookup"><span data-stu-id="35c18-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="35c18-170">Niezawodne sesje także odzyskać komunikat zmiany kolejności (co może się zdarzyć w przypadku routing wielościeżkowego), jednoczesnym zapewnieniu właściwej kolejności, w jakiej zostały wysłane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35c18-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="35c18-171">Niezawodne sesje są implementowane przy użyciu protokołu WS-ReliableMessaging (WS-RM).</span><span class="sxs-lookup"><span data-stu-id="35c18-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="35c18-172">Dodają WS-RM nagłówki, które zawierają informacje o sesji, który jest używany do identyfikowania wszystkie komunikaty skojarzone z określonym niezawodnej sesji.</span><span class="sxs-lookup"><span data-stu-id="35c18-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="35c18-173">Każda sesja WS-RM ma identyfikator, który jest identyfikatorem GUID.</span><span class="sxs-lookup"><span data-stu-id="35c18-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="35c18-174">Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="35c18-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="35c18-175">Queued Channels</span><span class="sxs-lookup"><span data-stu-id="35c18-175">Queued Channels</span></span>  
 <span data-ttu-id="35c18-176">Kolejki przechowywanie komunikatów w aplikacji wysyłającej w imieniu aplikacji odbierającej i później przekazuje te komunikaty odbierający aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="35c18-177">Łatwiej jest zapewnić przesyłanie wiadomości z aplikacji wysyłającej aplikacje odbierające, gdy na przykład aplikacja odbierająca jest przejściowy.</span><span class="sxs-lookup"><span data-stu-id="35c18-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> <span data-ttu-id="35c18-178">Usługi WCF zapewnia obsługę usługi kolejkowania wiadomości przy użyciu Microsoft usługi kolejkowania komunikatów (MSMQ) jako transportu.</span><span class="sxs-lookup"><span data-stu-id="35c18-178">WCF provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="35c18-179">Funkcja kanały umieszczonych w kolejce nie dodaje nagłówki do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35c18-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="35c18-180">Zamiast tego tworzy komunikatów usługi kolejkowania komunikatów za pomocą odpowiedni zestaw właściwości komunikatów usługi kolejkowania komunikatów i wywołuje metody usługi kolejkowania komunikatów, aby przełączyć komunikat do kolejki usługi kolejkowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="35c18-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="35c18-181">Usługa kolejkowania komunikatów jest opcjonalnym składnikiem, który jest dostarczany z programem Windows.</span><span class="sxs-lookup"><span data-stu-id="35c18-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="35c18-182">Żadne informacje nie są przechowywane na komputerze użytkownika końcowego przez funkcję kanały umieszczonych w kolejce, ponieważ używa ona usługi kolejkowania komunikatów jako infrastruktura do kolejkowania.</span><span class="sxs-lookup"><span data-stu-id="35c18-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="35c18-183">Integracja modelu COM+</span><span class="sxs-lookup"><span data-stu-id="35c18-183">COM+ Integration</span></span>  
 <span data-ttu-id="35c18-184">Ta funkcja jest zawijany istniejących funkcji COM i COM +, do tworzenia usług, które są zgodne z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with WCF services.</span></span> <span data-ttu-id="35c18-185">Ta funkcja nie używa określone nagłówki i nie zachowuje danych na komputerze użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="35c18-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="35c18-186">COM monikera</span><span class="sxs-lookup"><span data-stu-id="35c18-186">COM Service Moniker</span></span>  
 <span data-ttu-id="35c18-187">Zapewnia to niezarządzanych otoki standardowe klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-187">This provides an unmanaged wrapper to a standard WCF client.</span></span> <span data-ttu-id="35c18-188">Ta funkcja nie ma określonych nagłówków na potrzeby przesyłu ani jest zachować dane na maszynie.</span><span class="sxs-lookup"><span data-stu-id="35c18-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="35c18-189">Kanał elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="35c18-189">Peer Channel</span></span>  
 <span data-ttu-id="35c18-190">Kanał elementu równorzędnego umożliwia tworzenie wielostronnej aplikacji przy użyciu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-190">A peer channel enables development of multiparty applications using WCF.</span></span> <span data-ttu-id="35c18-191">Komunikaty wielostronnej występuje w kontekście siatki.</span><span class="sxs-lookup"><span data-stu-id="35c18-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="35c18-192">Oczek są identyfikowane przez nazwę, która dołączyć do węzłów.</span><span class="sxs-lookup"><span data-stu-id="35c18-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="35c18-193">Każdy węzeł w kanał elementu równorzędnego tworzy odbiornika TCP w porcie określonych przez użytkownika i ustanawia połączenie z innymi węzłami w siatce w celu zapewnienia odporności.</span><span class="sxs-lookup"><span data-stu-id="35c18-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="35c18-194">Aby połączyć z innych węzłów w siatce, węzły wymiany niektóre dane, w tym adres odbiornika i adresy IP na komputerze, z innych węzłów w siatce.</span><span class="sxs-lookup"><span data-stu-id="35c18-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="35c18-195">Komunikaty wysyłane wokół w siatce może zawierać informacje o zabezpieczeniach, które odnoszą się do nadawcy, aby zapobiec fałszowanie wiadomości i manipulowania.</span><span class="sxs-lookup"><span data-stu-id="35c18-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="35c18-196">Żadne informacje osobiste nie są przechowywane na komputerze użytkownika końcowego.</span><span class="sxs-lookup"><span data-stu-id="35c18-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="35c18-197">Profesjonalne środowisko IT</span><span class="sxs-lookup"><span data-stu-id="35c18-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="35c18-198">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="35c18-198">Tracing</span></span>  
 <span data-ttu-id="35c18-199">Funkcję diagnostyki, infrastruktura WCF rejestruje komunikaty, które przechodzą przez transportu i warstwy modelu usług i działania oraz zdarzeń związanych z tych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="35c18-199">The diagnostics feature of the WCF infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="35c18-200">Ta funkcja jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="35c18-200">This feature is turned off by default.</span></span> <span data-ttu-id="35c18-201">Jest włączona, przy użyciu pliku konfiguracji aplikacji i zachowanie śledzenia może być modyfikowany, przy użyciu dostawcy WMI usługi WCF w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="35c18-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the WCF WMI provider at run time.</span></span> <span data-ttu-id="35c18-202">Po włączeniu Infrastruktura śledzenia emituje śledzenia diagnostycznego, który zawiera komunikaty, działań i przetwarzanie zdarzeń do odbiorników skonfigurowanych.</span><span class="sxs-lookup"><span data-stu-id="35c18-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="35c18-203">Format i lokalizację danych wyjściowych są określane przez opcje konfiguracji odbiornika administratora, ale zazwyczaj jest sformatowany plik XML.</span><span class="sxs-lookup"><span data-stu-id="35c18-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="35c18-204">Administrator jest odpowiedzialny za ustawiania listy kontroli dostępu (ACL) plików śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35c18-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="35c18-205">W szczególności gdy hostowany przez System Windows Activation (WAS), administrator powinien upewnij się, że pliki nie są obsługiwane z publicznego katalogu wirtualnego, jeśli nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="35c18-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="35c18-206">Istnieją dwa rodzaje śledzenia: Rejestrowanie komunikatów i Model usługi diagnostyczne śledzenia, opisane w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="35c18-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="35c18-207">Każdy typ jest skonfigurowana za pośrednictwem źródła śledzenia: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> i <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="35c18-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="35c18-208">Oba te źródła śledzenia rejestrowania przechwytywania danych, które są lokalne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="35c18-209">Rejestrowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="35c18-209">Message Logging</span></span>  
 <span data-ttu-id="35c18-210">Rejestrowanie źródła śledzenia komunikatów (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) umożliwia administratorom komunikaty dziennika z tego przepływu za pośrednictwem systemu.</span><span class="sxs-lookup"><span data-stu-id="35c18-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="35c18-211">Za pomocą konfiguracji użytkownik może zdecydować o dziennika całej wiadomości lub tylko nagłówki komunikatu, czy mają być rejestrowane w modelu warstwy transportu i/lub usługę i czy mają zostać dołączone źle sformułowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="35c18-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="35c18-212">Ponadto użytkownik może skonfigurować filtrowanie, aby ograniczyć zakres komunikatów są rejestrowane.</span><span class="sxs-lookup"><span data-stu-id="35c18-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="35c18-213">Domyślnie rejestrowanie komunikatów jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="35c18-213">By default, message logging is disabled.</span></span> <span data-ttu-id="35c18-214">Administratorem komputera lokalnego można zapobiec włączenie komunikat logowania administratora dodatku poziomu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="35c18-215">Rejestrowanie komunikatów zaszyfrowany i odszyfrowany</span><span class="sxs-lookup"><span data-stu-id="35c18-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="35c18-216">Komunikaty są rejestrowane, szyfrowane lub odszyfrować, zgodnie z opisem w następujących warunkach.</span><span class="sxs-lookup"><span data-stu-id="35c18-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="35c18-217">Rejestrowanie transportu</span><span class="sxs-lookup"><span data-stu-id="35c18-217">Transport Logging</span></span>  
 <span data-ttu-id="35c18-218">Rejestruje komunikaty odbieranych i wysyłanych na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="35c18-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="35c18-219">Te komunikaty zawierają wszystkie nagłówki i może być zaszyfrowany przed wysłaniem przesyłania i podczas jego odebrania.</span><span class="sxs-lookup"><span data-stu-id="35c18-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="35c18-220">Jeśli komunikaty są szyfrowane przed wysłaniem przesyłania, a po ich odebraniu są rejestrowane są również szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="35c18-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="35c18-221">Wyjątkiem jest, gdy protokół zabezpieczeń jest używana (https): są następnie rejestrowane odszyfrowywany przed wysłaniem i po odbierane, nawet jeśli są one zaszyfrowane na łączu.</span><span class="sxs-lookup"><span data-stu-id="35c18-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="35c18-222">Rejestrowanie usługi</span><span class="sxs-lookup"><span data-stu-id="35c18-222">Service Logging</span></span>  
 <span data-ttu-id="35c18-223">Rejestruje komunikaty odebrania lub wysłania na poziomie modelu usługi, po kanału nagłówka zostało wykonane przetwarzanie, tuż przed i po wprowadzeniu kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="35c18-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="35c18-224">Komunikaty zarejestrowane na tym poziomie są odszyfrowywane, nawet jeśli były one chronione i szyfrowane w sieci.</span><span class="sxs-lookup"><span data-stu-id="35c18-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="35c18-225">Rejestrowanie komunikatów źle sformułowany</span><span class="sxs-lookup"><span data-stu-id="35c18-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="35c18-226">Rejestruje komunikaty infrastruktura WCF nie może zrozumieć i przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="35c18-226">Logs messages that the WCF infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="35c18-227">Komunikaty są rejestrowane jako — oznacza to zaszyfrowane, czy nie</span><span class="sxs-lookup"><span data-stu-id="35c18-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="35c18-228">Gdy komunikaty są rejestrowane formie odszyfrowany lub niezaszyfrowanym domyślnie WCF usuwa kluczy zabezpieczeń i potencjalnie dane osobowe z komunikatów przed ich zalogowaniem.</span><span class="sxs-lookup"><span data-stu-id="35c18-228">When messages are logged in decrypted or unencrypted form, by default WCF removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="35c18-229">W kolejnych sekcjach opisano, jakie informacje są usuwane i kiedy.</span><span class="sxs-lookup"><span data-stu-id="35c18-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="35c18-230">Administrator maszyny i jednocześnie wdrażania aplikacji należy wykonać określone akcje konfiguracji, aby zmienić domyślne zachowanie logowania kluczy i potencjalnie dane osobowe.</span><span class="sxs-lookup"><span data-stu-id="35c18-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="35c18-231">Informacje — usunięte z nagłówków komunikatu podczas logowania się odszyfrować niezaszyfrowanej wiadomości</span><span class="sxs-lookup"><span data-stu-id="35c18-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="35c18-232">Gdy komunikaty są rejestrowane w odszyfrować niezaszyfrowanej postaci kluczy zabezpieczeń i potencjalnie dane osobowe są usuwane domyślnie na podstawie nagłówków wiadomości oraz treść wiadomości przed ich zarejestrowaniu.</span><span class="sxs-lookup"><span data-stu-id="35c18-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="35c18-233">Na poniższej liście przedstawiono, jakie WCF uwzględnia kluczy i potencjalnie dane osobowe.</span><span class="sxs-lookup"><span data-stu-id="35c18-233">The following list shows what WCF considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="35c18-234">Klucze, które są usuwane:</span><span class="sxs-lookup"><span data-stu-id="35c18-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="35c18-235">\- Aby uzyskać xmlns:wst = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="35c18-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="35c18-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="35c18-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="35c18-237">Wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="35c18-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="35c18-238">\- Aby uzyskać xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="35c18-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="35c18-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="35c18-239">wsse:Password</span></span>  
  
 <span data-ttu-id="35c18-240">wsse:nonce</span><span class="sxs-lookup"><span data-stu-id="35c18-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="35c18-241">Informacje osobiste potencjalnie, który zostanie usunięty:</span><span class="sxs-lookup"><span data-stu-id="35c18-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="35c18-242">\- Aby uzyskać xmlns:wsse = "http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" i xmlns:wsse = "http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="35c18-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="35c18-243">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="35c18-243">wsse:Username</span></span>  
  
 <span data-ttu-id="35c18-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="35c18-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="35c18-245">\- Aby uzyskać xmlns:saml = "urn: oasis: nazwy: tc: SAML:1.0:assertion" elementy pogrubione (poniżej) są usuwane:</span><span class="sxs-lookup"><span data-stu-id="35c18-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="35c18-246">\<potwierdzenie</span><span class="sxs-lookup"><span data-stu-id="35c18-246">\<Assertion</span></span>  
  
 <span data-ttu-id="35c18-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="35c18-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="35c18-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="35c18-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="35c18-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="35c18-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="35c18-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="35c18-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="35c18-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="35c18-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="35c18-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span><span class="sxs-lookup"><span data-stu-id="35c18-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="35c18-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="35c18-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="35c18-254">\<Audience>[uri]\</Audience>+</span><span class="sxs-lookup"><span data-stu-id="35c18-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="35c18-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="35c18-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="35c18-256">\<DoNotCacheCondition />\*</span><span class="sxs-lookup"><span data-stu-id="35c18-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="35c18-257"><\!--abstrakcji typu podstawowego</span><span class="sxs-lookup"><span data-stu-id="35c18-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="35c18-258">\<Warunek / > \*</span><span class="sxs-lookup"><span data-stu-id="35c18-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="35c18-259">\</ Warunki >?</span><span class="sxs-lookup"><span data-stu-id="35c18-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="35c18-260">\<Advice></span><span class="sxs-lookup"><span data-stu-id="35c18-260">\<Advice></span></span>  
  
 <span data-ttu-id="35c18-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="35c18-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="35c18-262">\<Potwierdzenie > [asercji]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="35c18-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="35c18-263">[any] \*</span><span class="sxs-lookup"><span data-stu-id="35c18-263">[any]\*</span></span>  
  
 <span data-ttu-id="35c18-264">\</ Porady dotyczące >?</span><span class="sxs-lookup"><span data-stu-id="35c18-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="35c18-265"><\!--Abstrakcyjne typy podstawowe</span><span class="sxs-lookup"><span data-stu-id="35c18-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="35c18-266">\<Instrukcja / > \*</span><span class="sxs-lookup"><span data-stu-id="35c18-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="35c18-267">\<SubjectStatement></span><span class="sxs-lookup"><span data-stu-id="35c18-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="35c18-268">\<Temat ></span><span class="sxs-lookup"><span data-stu-id="35c18-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="35c18-269">\<SubjectConfirmation></span><span class="sxs-lookup"><span data-stu-id="35c18-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="35c18-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="35c18-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="35c18-271">\<SubjectConfirmationData > [any]\</SubjectConfirmationData >?</span><span class="sxs-lookup"><span data-stu-id="35c18-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="35c18-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="35c18-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="35c18-273">\</SubjectConfirmation>?</span><span class="sxs-lookup"><span data-stu-id="35c18-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="35c18-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="35c18-274">\</Subject></span></span>  
  
 <span data-ttu-id="35c18-275">\</SubjectStatement>\*</span><span class="sxs-lookup"><span data-stu-id="35c18-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="35c18-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="35c18-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="35c18-277">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="35c18-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="35c18-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="35c18-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="35c18-279">[Tematu]</span><span class="sxs-lookup"><span data-stu-id="35c18-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="35c18-280"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="35c18-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="35c18-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="35c18-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="35c18-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="35c18-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="35c18-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="35c18-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="35c18-284">\</AuthenticationStatement>\*</span><span class="sxs-lookup"><span data-stu-id="35c18-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="35c18-285">\<AttributeStatement></span><span class="sxs-lookup"><span data-stu-id="35c18-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="35c18-286">[Tematu]</span><span class="sxs-lookup"><span data-stu-id="35c18-286">[Subject]</span></span>  
  
 <span data-ttu-id="35c18-287">\<Atrybut</span><span class="sxs-lookup"><span data-stu-id="35c18-287">\<Attribute</span></span>  
  
 <span data-ttu-id="35c18-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="35c18-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="35c18-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="35c18-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="35c18-290">\</Attribute>+</span><span class="sxs-lookup"><span data-stu-id="35c18-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="35c18-291">\</AttributeStatement>\*</span><span class="sxs-lookup"><span data-stu-id="35c18-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="35c18-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="35c18-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="35c18-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="35c18-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="35c18-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="35c18-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="35c18-295">[Tematu]</span><span class="sxs-lookup"><span data-stu-id="35c18-295">[Subject]</span></span>  
  
 <span data-ttu-id="35c18-296">\<Action Namespace="[uri]">[string]\</Action>+</span><span class="sxs-lookup"><span data-stu-id="35c18-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="35c18-297">\<Dowód ></span><span class="sxs-lookup"><span data-stu-id="35c18-297">\<Evidence></span></span>  
  
 <span data-ttu-id="35c18-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="35c18-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="35c18-299">\<Potwierdzenie > [asercji]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="35c18-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="35c18-300">\</ Dowód >?</span><span class="sxs-lookup"><span data-stu-id="35c18-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="35c18-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="35c18-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="35c18-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="35c18-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="35c18-303">Informacje — usunięte z treści wiadomości, podczas logowania się odszyfrować niezaszyfrowanej wiadomości</span><span class="sxs-lookup"><span data-stu-id="35c18-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="35c18-304">Jak opisano wcześniej, klucze usuwa WCF i znane potencjalnie osobowych z nagłówków komunikatu rejestrowane komunikaty odszyfrować niezaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="35c18-304">As previously described, WCF removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="35c18-305">Ponadto WCF usuwa klucze i znanych potencjalnie dane osobowe z treści wiadomości elementy treści i działań na poniższej liście, które opisują komunikaty zabezpieczeń związane z wymiany kluczy.</span><span class="sxs-lookup"><span data-stu-id="35c18-305">In addition, WCF removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="35c18-306">Dla następujących przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="35c18-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="35c18-307">xmlns:WST = "http://schemas.xmlsoap.org/ws/2004/04/trust" i xmlns:wst = "http://schemas.xmlsoap.org/ws/2005/02/trust" (na przykład, jeśli brak dostępnych akcji)</span><span class="sxs-lookup"><span data-stu-id="35c18-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="35c18-308">Informacje są usuwane dla tych elementów treści, które obejmują wymiany kluczy:</span><span class="sxs-lookup"><span data-stu-id="35c18-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="35c18-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="35c18-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="35c18-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="35c18-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="35c18-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="35c18-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="35c18-312">Informacje są również usuwane dla każdego z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="35c18-312">Information is also removed for each of the following Actions:</span></span>  
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend`
  
- `http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend`
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="35c18-313">Informacje nie zostaną usunięte z nagłówków specyficzne dla aplikacji i danych treści</span><span class="sxs-lookup"><span data-stu-id="35c18-313">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 <span data-ttu-id="35c18-314">Usługi WCF nie śledzi informacje osobiste w nagłówkach specyficzne dla aplikacji (na przykład ciągów zapytań) lub dane treści (na przykład numer karty kredytowej).</span><span class="sxs-lookup"><span data-stu-id="35c18-314">WCF does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="35c18-315">Jeśli rejestrowanie komunikatów jest włączona, informacje osobiste w nagłówkach specyficzne dla aplikacji i treść informacji mogą być widoczne w dziennikach.</span><span class="sxs-lookup"><span data-stu-id="35c18-315">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="35c18-316">Ponownie narzędzia do wdrażania aplikacji jest odpowiedzialna za ustawienie listy kontroli dostępu dla plików dziennika i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35c18-316">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="35c18-317">Może on także wyłączyć rejestrowanie, jeśli użytkownik nie chce, aby te informacje mają być wyświetlane lub może on filtrować te informacje w plikach dziennika po jej zarejestrowaniu.</span><span class="sxs-lookup"><span data-stu-id="35c18-317">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="35c18-318">Śledzenie modelu usług</span><span class="sxs-lookup"><span data-stu-id="35c18-318">Service Model Tracing</span></span>  
 <span data-ttu-id="35c18-319">Źródło śladu Model usługi (<xref:System.ServiceModel>) umożliwia śledzenie działań i zdarzenia związane z przetwarzania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="35c18-319">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="35c18-320">Ta funkcja korzysta z funkcji diagnostycznych systemu .NET Framework z <xref:System.Diagnostics>.</span><span class="sxs-lookup"><span data-stu-id="35c18-320">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="35c18-321">Podobnie jak w przypadku <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> właściwości, lokalizację i jego listy ACL są konfigurowanych przez użytkownika za pomocą plików konfiguracji aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="35c18-321">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="35c18-322">Podobnie jak w przypadku rejestrowania komunikatów lokalizacja pliku jest zawsze konfigurowane podczas administrator włącza śledzenie; w związku z tym administrator steruje listy ACL.</span><span class="sxs-lookup"><span data-stu-id="35c18-322">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="35c18-323">Ślady zawierają nagłówki wiadomości, gdy komunikat jest w zakresie.</span><span class="sxs-lookup"><span data-stu-id="35c18-323">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="35c18-324">Zastosuj te same zasady stosowania ukrywanie potencjalnie osobowe w nagłówkach wiadomości w poprzedniej sekcji: wcześniej zidentyfikować dane osobowe są usuwane domyślnie z nagłówków w śladach.</span><span class="sxs-lookup"><span data-stu-id="35c18-324">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="35c18-325">Administrator maszyny i wdrażania aplikacji należy zmodyfikować konfigurację rejestrowania potencjalnie dane osobowe.</span><span class="sxs-lookup"><span data-stu-id="35c18-325">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="35c18-326">Jednak informacji osobistych znajdujących się w nagłówkach specyficzne dla aplikacji jest rejestrowane w śladach.</span><span class="sxs-lookup"><span data-stu-id="35c18-326">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="35c18-327">Narzędzia do wdrażania aplikacji jest odpowiedzialna za ustawienie listy kontroli dostępu dla plików konfiguracji i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="35c18-327">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="35c18-328">On również wyłączyć śledzenie Jeśli użytkownik nie chce, aby te informacje mają być wyświetlane lub on można odfiltrować te informacje z plików śledzenia, po ich zarejestrowaniem.</span><span class="sxs-lookup"><span data-stu-id="35c18-328">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="35c18-329">W ramach modelu ServiceModel śledzenia, unikatowe identyfikatory (nazywane identyfikatory aktywności i zazwyczaj identyfikator GUID) łączenie różnych działań jako wiadomość odbywa się za pośrednictwem różnych części infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="35c18-329">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="35c18-330">Obiekty nasłuchujące śledzenia niestandardowe</span><span class="sxs-lookup"><span data-stu-id="35c18-330">Custom Trace Listeners</span></span>  
 <span data-ttu-id="35c18-331">Dla obu komunikatu rejestrowania i śledzenia można skonfigurować odbiornik śledzenia niestandardowego, który można wysłać danych śledzenia i wiadomości na łączu (na przykład do zdalnej bazy danych).</span><span class="sxs-lookup"><span data-stu-id="35c18-331">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="35c18-332">Narzędzia do wdrażania aplikacji jest odpowiedzialny za konfigurowanie niestandardowe odbiorniki lub umożliwienie użytkownikom to zrobić.</span><span class="sxs-lookup"><span data-stu-id="35c18-332">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="35c18-333">Jest on również odpowiedzialny za wszelkie informacje osobiste, które zostały ujawnione w lokalizacji zdalnej i prawidłowo zastosowania list ACL do tej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-333">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="35c18-334">Inne funkcje dla specjalistów IT</span><span class="sxs-lookup"><span data-stu-id="35c18-334">Other features for IT Professionals</span></span>  
 <span data-ttu-id="35c18-335">Usługi WCF jest dostawca WMI, która udostępnia informacje o konfiguracji infrastruktury usług WCF za pomocą usługi WMI (dostarczane z programem Windows).</span><span class="sxs-lookup"><span data-stu-id="35c18-335">WCF has a WMI provider that exposes the WCF infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="35c18-336">Domyślnie interfejs usługi WMI są dostępne dla administratorów.</span><span class="sxs-lookup"><span data-stu-id="35c18-336">By default, the WMI interface is available to administrators.</span></span>  
  
 <span data-ttu-id="35c18-337">Mechanizm konfiguracji .NET Framework korzysta z konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-337">WCF configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="35c18-338">Pliki konfiguracji są przechowywane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="35c18-338">The configuration files are stored on the machine.</span></span> <span data-ttu-id="35c18-339">Deweloper aplikacji i administrator tworzyć pliki konfiguracji i listy ACL dla każdego wymagania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35c18-339">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="35c18-340">Plik konfiguracji może zawierać adresy punktów końcowych i łącza do certyfikatów w magazynie certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="35c18-340">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="35c18-341">Certyfikaty mogą służyć do zapewnienia danych aplikacji, aby skonfigurować różne właściwości funkcje używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="35c18-341">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="35c18-342">Usługi WCF również korzysta z funkcji zrzutu procesu .NET Framework, wywołując <xref:System.Environment.FailFast%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="35c18-342">WCF also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="35c18-343">IT Pro Tools</span><span class="sxs-lookup"><span data-stu-id="35c18-343">IT Pro Tools</span></span>  
 <span data-ttu-id="35c18-344">Usługi WCF zapewnia również następujące IT profesjonalne narzędzia, które są dostępne w zestawie Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="35c18-344">WCF also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="35c18-345">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="35c18-345">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="35c18-346">Przeglądarka wyświetla pliki śledzenia WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-346">The viewer displays WCF trace files.</span></span> <span data-ttu-id="35c18-347">Podgląd pokazuje wszelkie informacje zawarte w śladów.</span><span class="sxs-lookup"><span data-stu-id="35c18-347">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="35c18-348">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="35c18-348">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="35c18-349">Edytor zezwala użytkownikowi na tworzenie i edytowanie plików konfiguracyjnych WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-349">The editor allows the user to create and edit WCF configuration files.</span></span> <span data-ttu-id="35c18-350">Edytor pokazuje dowolne informacje są zawarte w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35c18-350">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="35c18-351">Tego samego zadania można wykonywać za pomocą edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="35c18-351">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="35c18-352">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="35c18-352">ServiceModel_Reg</span></span>  
 <span data-ttu-id="35c18-353">To narzędzie umożliwia użytkownikowi zarządzanie ServiceModel instaluje na komputerze.</span><span class="sxs-lookup"><span data-stu-id="35c18-353">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="35c18-354">Narzędzie wyświetla komunikaty o stanie w oknie konsoli, gdy go, w procesie, mogą być wyświetlane informacje o konfiguracji instalacji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-354">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the WCF installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="35c18-355">WSATConfig.exe i WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="35c18-355">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="35c18-356">Te narzędzia umożliwiają specjalistom IT Konfigurowanie obsługi sieci w usłudze interoperacyjne WS-AtomicTransaction programu WCF.</span><span class="sxs-lookup"><span data-stu-id="35c18-356">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in WCF.</span></span> <span data-ttu-id="35c18-357">Narzędzia, wyświetlaj i Zezwalaj użytkownikowi na zmianę wartości najczęściej używanych ustawień WS-AtomicTransaction przechowywane w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="35c18-357">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="35c18-358">Funkcje ogólne</span><span class="sxs-lookup"><span data-stu-id="35c18-358">Cross-cutting Features</span></span>  
 <span data-ttu-id="35c18-359">Następujące funkcje są kompleksowymi.</span><span class="sxs-lookup"><span data-stu-id="35c18-359">The following features are cross-cutting.</span></span> <span data-ttu-id="35c18-360">Oznacza to mogą być złożone z żadnym z powyższych funkcji.</span><span class="sxs-lookup"><span data-stu-id="35c18-360">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="35c18-361">Struktura usługi</span><span class="sxs-lookup"><span data-stu-id="35c18-361">Service Framework</span></span>  
 <span data-ttu-id="35c18-362">Nagłówki może zawierać Identyfikatora wystąpienia, który jest identyfikatorem GUID, który kojarzy wiadomość z wystąpieniem klasy CLR.</span><span class="sxs-lookup"><span data-stu-id="35c18-362">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="35c18-363">Web Services Description Language (WSDL) zawiera definicję portu.</span><span class="sxs-lookup"><span data-stu-id="35c18-363">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="35c18-364">Każdy port ma adres punktu końcowego i powiązania, który reprezentuje usług używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="35c18-364">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="35c18-365">Udostępnianie WSDL można wyłączyć za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="35c18-365">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="35c18-366">Żadne informacje nie są przechowywane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="35c18-366">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c18-367">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35c18-367">See also</span></span>

- [<span data-ttu-id="35c18-368">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="35c18-368">Windows Communication Foundation</span></span>](index.md)
- [<span data-ttu-id="35c18-369">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="35c18-369">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)

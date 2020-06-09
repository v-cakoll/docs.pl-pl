---
title: Federacja
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: c31c2612b595e627b0c4c2d7fbb3a359b19ee704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595495"
---
# <a name="federation"></a><span data-ttu-id="de16e-102">Federacja</span><span class="sxs-lookup"><span data-stu-id="de16e-102">Federation</span></span>
<span data-ttu-id="de16e-103">Ten temat zawiera krótkie omówienie koncepcji zabezpieczeń federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="de16e-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="de16e-104">Opisano w nim również obsługę Windows Communication Foundation (WCF) na potrzeby wdrażania federacyjnych architektur zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="de16e-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="de16e-105">Aby zapoznać się z przykładową aplikacją, która demonstruje Federacji, zobacz [przykład Federacji](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="de16e-105">For a sample application that demonstrates federation, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="de16e-106">Definicja zabezpieczeń federacyjnych</span><span class="sxs-lookup"><span data-stu-id="de16e-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="de16e-107">Zabezpieczenia federacyjne umożliwiają czyste rozdzielenie między usługą dostępną przez klienta a związanymi z nimi procedurami uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="de16e-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="de16e-108">Zabezpieczenia federacyjne umożliwiają również współpracę między wieloma systemami, sieciami i organizacjami w różnych obszarach zaufania.</span><span class="sxs-lookup"><span data-stu-id="de16e-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="de16e-109">Funkcja WCF zapewnia obsługę kompilowania i wdrażania systemów rozproszonych, które wykorzystują zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="de16e-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="de16e-110">Elementy architektury zabezpieczeń federacyjnych</span><span class="sxs-lookup"><span data-stu-id="de16e-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="de16e-111">Architektura zabezpieczeń federacyjnych ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="de16e-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="de16e-112">Element</span><span class="sxs-lookup"><span data-stu-id="de16e-112">Element</span></span>|<span data-ttu-id="de16e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="de16e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de16e-114">Domena/obszar</span><span class="sxs-lookup"><span data-stu-id="de16e-114">Domain/realm</span></span>|<span data-ttu-id="de16e-115">Pojedyncza jednostka administrowania zabezpieczeniami lub zaufania.</span><span class="sxs-lookup"><span data-stu-id="de16e-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="de16e-116">Typowa domena może obejmować jedną organizację.</span><span class="sxs-lookup"><span data-stu-id="de16e-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="de16e-117">Federacja</span><span class="sxs-lookup"><span data-stu-id="de16e-117">Federation</span></span>|<span data-ttu-id="de16e-118">Kolekcja domen, które mają ustanowioną relację zaufania.</span><span class="sxs-lookup"><span data-stu-id="de16e-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="de16e-119">Poziom zaufania może się różnić — zwykle obejmuje uwierzytelnianie i niemal zawsze autoryzację.</span><span class="sxs-lookup"><span data-stu-id="de16e-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="de16e-120">Typowa federacja może obejmować kilka organizacji, które mają ustanowioną relację zaufania na potrzeby dostępu współdzielonego do zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="de16e-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="de16e-121">Usługa tokenu zabezpieczającego (STS)</span><span class="sxs-lookup"><span data-stu-id="de16e-121">Security Token Service (STS)</span></span>|<span data-ttu-id="de16e-122">Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że wykonuje potwierdzenia oparte na zasobie, że ufa, aby whomever je z zaufaniem.</span><span class="sxs-lookup"><span data-stu-id="de16e-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="de16e-123">Stanowi to podstawę zaufania między domenami.</span><span class="sxs-lookup"><span data-stu-id="de16e-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="de16e-124">Przykładowy scenariusz</span><span class="sxs-lookup"><span data-stu-id="de16e-124">Example Scenario</span></span>  
 <span data-ttu-id="de16e-125">Na poniższej ilustracji przedstawiono przykład zabezpieczeń federacyjnych:</span><span class="sxs-lookup"><span data-stu-id="de16e-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagram przedstawiający typowy scenariusz zabezpieczeń federacyjnych.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="de16e-127">Ten scenariusz obejmuje dwie organizacje: a i B. organizacja B ma zasób sieci Web (usługę sieci Web), który niektórzy użytkownicy w organizacji znalazły wartość cenną.</span><span class="sxs-lookup"><span data-stu-id="de16e-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de16e-128">Ta sekcja używa zamiennie postanowień dotyczących *zasobów*, *usług*i *usług sieci Web* .</span><span class="sxs-lookup"><span data-stu-id="de16e-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="de16e-129">Zazwyczaj organizacja B wymaga, aby przed uzyskaniem dostępu do usługi użytkownik z organizacji A zapewniał pewną prawidłową formę uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="de16e-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="de16e-130">Ponadto organizacja może również wymagać, aby użytkownik miał uprawnienia dostępu do określonego zasobu.</span><span class="sxs-lookup"><span data-stu-id="de16e-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="de16e-131">Jednym ze sposobów rozwiązania tego problemu i umożliwienie użytkownikom w organizacji A uzyskiwania dostępu do zasobu w organizacji B jest następująca:</span><span class="sxs-lookup"><span data-stu-id="de16e-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="de16e-132">Użytkownicy z organizacji A rejestrują swoje poświadczenia (nazwa użytkownika i hasło) w organizacji B.</span><span class="sxs-lookup"><span data-stu-id="de16e-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="de16e-133">Podczas uzyskiwania dostępu do zasobów użytkownicy z organizacji składają swoje poświadczenia do organizacji B i są uwierzytelniani przed uzyskaniem dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="de16e-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="de16e-134">Takie podejście ma trzy znaczące wady:</span><span class="sxs-lookup"><span data-stu-id="de16e-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="de16e-135">Organizacja B musi zarządzać poświadczeniami użytkowników z organizacji A poza zarządzaniem poświadczeniami użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="de16e-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="de16e-136">Użytkownicy w organizacji muszą zachować dodatkowy zestaw poświadczeń (czyli zapamiętać dodatkową nazwę użytkownika i hasło) od poświadczeń, z których zazwyczaj korzystają, aby uzyskać dostęp do zasobów w organizacji A. Zwykle jest to zalecane w przypadku używania tej samej nazwy użytkownika i hasła w wielu lokacjach usług, co jest słabym środkiem bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="de16e-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="de16e-137">Architektura nie jest skalowana, ponieważ coraz więcej organizacji postrzega zasób w organizacji B jako część wartości.</span><span class="sxs-lookup"><span data-stu-id="de16e-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="de16e-138">Alternatywne podejście, które dotyczy wyżej wspomnianych wad, ma na celu zastosowanie zabezpieczeń federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="de16e-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="de16e-139">W tym podejściu organizacje A i B ustanawiają relację zaufania i korzystają z usługi tokenu zabezpieczającego (STS) w celu umożliwienia brokera ustanowionego zaufania.</span><span class="sxs-lookup"><span data-stu-id="de16e-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="de16e-140">W federacyjnej architekturze zabezpieczeń Użytkownicy z organizacji wiedzą, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, która musi przedstawić prawidłowy token zabezpieczający z STS w organizacji B, który uwierzytelnia i autoryzuje dostęp do określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="de16e-141">Podczas kontaktowania się z usługą STS B użytkownicy otrzymują kolejny poziom pośredni z zasad skojarzonych z usługą STS.</span><span class="sxs-lookup"><span data-stu-id="de16e-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="de16e-142">Muszą one przedstawić prawidłowy token zabezpieczający od usługi STS A (czyli obszaru zaufania klienta) przed wystawieniem im tokenu zabezpieczającego przez usługę STS B.</span><span class="sxs-lookup"><span data-stu-id="de16e-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="de16e-143">Jest to współrzut relacji zaufania ustanowiony między obiema organizacjami i oznacza, że organizacja B nie musi zarządzać tożsamościami użytkowników z organizacji A. W przypadku usługi STS B zazwyczaj ma wartość null `issuerAddress` i `issuerMetadataAddress` .</span><span class="sxs-lookup"><span data-stu-id="de16e-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="de16e-144">Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie lokalnego wystawcy](how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="de16e-144">For more information, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="de16e-145">W takim przypadku klient korzysta z zasad lokalnych w celu zlokalizowania usługi STS A. Ta konfiguracja jest nazywana *Federacją obszaru głównego* i skalowalna, ponieważ usługa STS B nie musi obsługiwać informacji o usłudze STS A.</span><span class="sxs-lookup"><span data-stu-id="de16e-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="de16e-146">Użytkownicy mogą następnie skontaktować się z usługą STS w organizacji A i uzyskać token zabezpieczający przez przedstawienie poświadczeń uwierzytelniania, które zwykle są używane do uzyskania dostępu do dowolnego innego zasobu w organizacji A. Pozwala to również uniknąć problemów użytkowników, którzy muszą zachować wiele zestawów poświadczeń lub użyć tego samego zestawu poświadczeń w wielu lokacjach usług.</span><span class="sxs-lookup"><span data-stu-id="de16e-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="de16e-147">Gdy użytkownicy uzyskają token zabezpieczający od usługi STS A, przedstawią token do usługi STS B. organizacja B wykonuje autoryzację żądań użytkowników i wystawia token zabezpieczający użytkownikom ze swojego własnego zestawu tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="de16e-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="de16e-148">Użytkownicy mogą następnie przedstawić swój token dla zasobu w organizacji B i uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="de16e-149">Obsługa zabezpieczeń federacyjnych w programie WCF</span><span class="sxs-lookup"><span data-stu-id="de16e-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="de16e-150">Funkcja WCF oferuje gotoweą obsługę wdrażania federacyjnych architektur zabezpieczeń za pomocą programu [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="de16e-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="de16e-151">[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Element zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które wiąże się z użyciem protokołu HTTP jako podstawowego mechanizmu transportu dla stylu komunikacji żądanie-odpowiedź, wykorzystując tekst i XML jako format sieci do kodowania.</span><span class="sxs-lookup"><span data-stu-id="de16e-151">The [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="de16e-152">Korzystanie z programu [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnym scenariuszu zabezpieczeń można rozdzielić na dwie niezależne fazy logiczne, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="de16e-152">The use of [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="de16e-153">Faza 1: faza projektowania</span><span class="sxs-lookup"><span data-stu-id="de16e-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="de16e-154">W fazie projektowania klient używa narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , aby przeczytać zasady ujawniane przez punkt końcowy usługi i zebrać wymagania dotyczące uwierzytelniania i autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="de16e-155">Odpowiednie serwery proxy są konstruowane w celu utworzenia na kliencie następującego wzorca komunikacji z zabezpieczeniami federacyjnymi:</span><span class="sxs-lookup"><span data-stu-id="de16e-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="de16e-156">Uzyskaj token zabezpieczający z usługi STS w obszarze zaufania klienta.</span><span class="sxs-lookup"><span data-stu-id="de16e-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="de16e-157">Zaprezentowanie tokenu w usłudze STS w obszarze zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="de16e-158">Uzyskaj token zabezpieczający z programu STS w obszarze zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="de16e-159">Zaprezentowanie tokenu usłudze w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="de16e-160">Faza 2: faza czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="de16e-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="de16e-161">Podczas fazy czasu wykonywania klient tworzy wystąpienie obiektu klasy klienta WCF i wykonuje wywołanie przy użyciu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="de16e-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="de16e-162">Podstawowa struktura programu WCF obsługuje wyżej wymienione kroki we wzorcu komunikacji z zabezpieczeniami federacyjnymi i umożliwia klientowi bezproblemowe korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="de16e-163">Przykładowa implementacja przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="de16e-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="de16e-164">Na poniższej ilustracji przedstawiono przykładową implementację architektury zabezpieczeń federacyjnych przy użyciu natywnej pomocy technicznej z programu WCF.</span><span class="sxs-lookup"><span data-stu-id="de16e-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagram przedstawiający przykładową implementację zabezpieczeń Federacji.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="de16e-166">Przykładowa usługa</span><span class="sxs-lookup"><span data-stu-id="de16e-166">Example MyService</span></span>  
 <span data-ttu-id="de16e-167">Usługa `MyService` ujawnia pojedynczy punkt końcowy za pomocą `MyServiceEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="de16e-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="de16e-168">Na poniższej ilustracji przedstawiono adres, powiązanie i kontrakt skojarzone z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="de16e-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagram przedstawiający szczegóły dotyczące programu ServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="de16e-170">Punkt końcowy usługi `MyServiceEndpoint` używa [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu potwierdzeń zabezpieczeń (SAML) z `accessAuthorized` twierdzeniem wystawionym przez usługę STS B. Ta wartość jest deklaratywnie określona w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="de16e-171">Należy zauważyć delikatny wgląd w oświadczenia wymagane przez `MyService` .</span><span class="sxs-lookup"><span data-stu-id="de16e-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="de16e-172">Drugi rysunek wskazuje, że `MyService` wymaga tokenu SAML z tym elementem `accessAuthorized` .</span><span class="sxs-lookup"><span data-stu-id="de16e-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="de16e-173">Aby dokładniej określić typ, który `MyService` wymaga.</span><span class="sxs-lookup"><span data-stu-id="de16e-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="de16e-174">W pełni kwalifikowana nazwa tego typu jest `http://tempuri.org:accessAuthorized` (wraz ze skojarzoną przestrzenią nazw), która jest używana w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="de16e-175">Wartość tego żądania wskazuje obecność tego żądania i zakłada się, że jest ono ustawiane `true` przez usługę STS B.</span><span class="sxs-lookup"><span data-stu-id="de16e-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="de16e-176">W czasie wykonywania te zasady są wymuszane przez `MyServiceOperationRequirement` klasę, która jest implementowana w ramach programu `MyService` .</span><span class="sxs-lookup"><span data-stu-id="de16e-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="de16e-177">USŁUGA STS B</span><span class="sxs-lookup"><span data-stu-id="de16e-177">STS B</span></span>  
 <span data-ttu-id="de16e-178">Na poniższej ilustracji przedstawiono usługę STS B. Jak wspomniano wcześniej, usługa tokenu zabezpieczającego (STS) jest również usługą sieci Web i może mieć skojarzone punkty końcowe, zasady i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="de16e-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagram przedstawiający usługę tokenów zabezpieczających B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="de16e-180">Usługa STS B udostępnia jeden punkt końcowy o nazwie, `STSEndpoint` którego można użyć do żądania tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="de16e-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="de16e-181">W odniesieniu do usługi STS B są wystawiane tokeny SAML `accessAuthorized` , które mogą być prezentowane w `MyService` lokacji usługi w celu uzyskania dostępu do usług.</span><span class="sxs-lookup"><span data-stu-id="de16e-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="de16e-182">Jednak usługa STS B wymaga, aby użytkownicy zaprezentować prawidłowy token SAML wystawiony przez usługę STS A, która zawiera ten element `userAuthenticated` .</span><span class="sxs-lookup"><span data-stu-id="de16e-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="de16e-183">Ta wartość jest deklaratywnie określona w konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="de16e-183">This is declaratively specified in the STS configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="de16e-184">Ponownie jest to `userAuthenticated` Typ zgłoszenia wymagany przez usługę STS B. W pełni kwalifikowana nazwa tego typu jest `http://tempuri.org:userAuthenticated` (wraz ze skojarzoną przestrzenią nazw), która jest używana w pliku konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="de16e-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="de16e-185">Wartość tego żądania wskazuje obecność tego żądania i przyjmuje się, że jest ono ustawiane `true` przez usługę STS a.</span><span class="sxs-lookup"><span data-stu-id="de16e-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="de16e-186">W czasie wykonywania `STS_B_OperationRequirement` Klasa wymusza te zasady, które są implementowane w ramach usługi STS B.</span><span class="sxs-lookup"><span data-stu-id="de16e-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="de16e-187">Jeśli sprawdzanie dostępu jest jasne, usługa STS B wystawia token języka SAML w ramach tego `accessAuthorized` żądania.</span><span class="sxs-lookup"><span data-stu-id="de16e-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="de16e-188">USŁUGA STS A</span><span class="sxs-lookup"><span data-stu-id="de16e-188">STS A</span></span>  
 <span data-ttu-id="de16e-189">Na poniższej ilustracji przedstawiono usługę STS A.</span><span class="sxs-lookup"><span data-stu-id="de16e-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="de16e-190">![Federacja](media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="de16e-190">![Federation](media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="de16e-191">Podobnie jak w przypadku usługi STS B, usługa STS A jest również usługą sieci Web, która wystawia tokeny zabezpieczające i udostępnia w tym celu pojedynczy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="de16e-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="de16e-192">Jednak używa innego powiązania ( `wsHttpBinding` ) i wymaga, aby użytkownicy zaprezentować prawidłowy program CardSpace z `emailAddress` zastrzeżeniem.</span><span class="sxs-lookup"><span data-stu-id="de16e-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="de16e-193">W odpowiedzi powoduje wystawianie tokenów SAML z `userAuthenticated` wnioskiem.</span><span class="sxs-lookup"><span data-stu-id="de16e-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="de16e-194">Ta wartość jest deklaratywnie określona w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-194">This is declaratively specified in the service configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"
                       storeName="My" />  
       </identity>  
    </endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="de16e-195">W czasie wykonywania `STS_A_OperationRequirement` Klasa wymusza te zasady, które są implementowane w ramach usługi STS A.</span><span class="sxs-lookup"><span data-stu-id="de16e-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="de16e-196">Jeśli dostęp to `true` , usługa STS wystawia token języka SAML przy użyciu `userAuthenticated` żądania.</span><span class="sxs-lookup"><span data-stu-id="de16e-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="de16e-197">Klient w organizacji A</span><span class="sxs-lookup"><span data-stu-id="de16e-197">Client at Organization A</span></span>  
 <span data-ttu-id="de16e-198">Na poniższej ilustracji przedstawiono klienta w organizacji A wraz z krokami związanymi z wykonywaniem `MyService` wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="de16e-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="de16e-199">Pozostałe składniki funkcjonalne są również dołączone do kompletności.</span><span class="sxs-lookup"><span data-stu-id="de16e-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagram przedstawiający kroki wywołania usługi WebService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="de16e-201">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="de16e-201">Summary</span></span>  
 <span data-ttu-id="de16e-202">Zabezpieczenia federacyjne zapewniają czyste dział odpowiedzialności i ułatwiają tworzenie bezpiecznych, skalowalnych architektur usług.</span><span class="sxs-lookup"><span data-stu-id="de16e-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="de16e-203">Jako platforma do kompilowania i wdrażania aplikacji rozproszonych, WCF zapewnia natywną obsługę implementowania zabezpieczeń federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="de16e-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de16e-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de16e-204">See also</span></span>

- [<span data-ttu-id="de16e-205">Bezpieczeństwo</span><span class="sxs-lookup"><span data-stu-id="de16e-205">Security</span></span>](security.md)

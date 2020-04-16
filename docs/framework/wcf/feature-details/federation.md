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
ms.openlocfilehash: 9616a5afb88e46bb5d69f1cd253c854cc1684d9f
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464181"
---
# <a name="federation"></a><span data-ttu-id="d534c-102">Federacja</span><span class="sxs-lookup"><span data-stu-id="d534c-102">Federation</span></span>
<span data-ttu-id="d534c-103">Ten temat zawiera krótki przegląd pojęcia zabezpieczeń federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="d534c-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="d534c-104">Opisano w nim również obsługę programu Windows Communication Foundation (WCF) w zakresie wdrażania architektur zabezpieczeń federacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d534c-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="d534c-105">Aby zapoznać się z przykładową aplikacją, która demonstruje federację, zobacz [Próbka federacyjne](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="d534c-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="d534c-106">Definicja zabezpieczeń federacyjnej</span><span class="sxs-lookup"><span data-stu-id="d534c-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="d534c-107">Zabezpieczenia federacyjne umożliwiają czystą separację między usługą, do która klient uzyskuje dostęp, a skojarzonymi procedurami uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="d534c-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="d534c-108">Zabezpieczenia federacyjne umożliwiają również współpracę między wieloma systemami, sieciami i organizacjami w różnych domenach zaufania.</span><span class="sxs-lookup"><span data-stu-id="d534c-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="d534c-109">WCF zapewnia obsługę tworzenia i wdrażania systemów rozproszonych, które wykorzystują zabezpieczenia federacyjne.</span><span class="sxs-lookup"><span data-stu-id="d534c-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="d534c-110">Elementy architektury zabezpieczeń federacyjnej</span><span class="sxs-lookup"><span data-stu-id="d534c-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="d534c-111">Architektura zabezpieczeń federacyjnej ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d534c-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="d534c-112">Element</span><span class="sxs-lookup"><span data-stu-id="d534c-112">Element</span></span>|<span data-ttu-id="d534c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d534c-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d534c-114">Domena/królestwo</span><span class="sxs-lookup"><span data-stu-id="d534c-114">Domain/realm</span></span>|<span data-ttu-id="d534c-115">Pojedyncza jednostka administracji zabezpieczeń lub zaufania.</span><span class="sxs-lookup"><span data-stu-id="d534c-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="d534c-116">Typowa domena może obejmować jedną organizację.</span><span class="sxs-lookup"><span data-stu-id="d534c-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="d534c-117">Federacja</span><span class="sxs-lookup"><span data-stu-id="d534c-117">Federation</span></span>|<span data-ttu-id="d534c-118">Kolekcja domen, które nawiązały zaufanie.</span><span class="sxs-lookup"><span data-stu-id="d534c-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="d534c-119">Poziom zaufania może się różnić — zwykle obejmuje uwierzytelnianie i niemal zawsze autoryzację.</span><span class="sxs-lookup"><span data-stu-id="d534c-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="d534c-120">Typowa federacja może obejmować kilka organizacji, które mają ustanowioną relację zaufania na potrzeby dostępu współdzielonego do zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="d534c-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="d534c-121">Usługa tokenu zabezpieczającego (STS)</span><span class="sxs-lookup"><span data-stu-id="d534c-121">Security Token Service (STS)</span></span>|<span data-ttu-id="d534c-122">Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że sprawia, że twierdzenia oparte na dowodach, że ufa, kto mu ufa.</span><span class="sxs-lookup"><span data-stu-id="d534c-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="d534c-123">Stanowi to podstawę brokerowania zaufania między domenami.</span><span class="sxs-lookup"><span data-stu-id="d534c-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="d534c-124">Przykładowy scenariusz</span><span class="sxs-lookup"><span data-stu-id="d534c-124">Example Scenario</span></span>  
 <span data-ttu-id="d534c-125">Na poniższej ilustracji przedstawiono przykład zabezpieczeń federacyjnych:</span><span class="sxs-lookup"><span data-stu-id="d534c-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagram przedstawiający typowy scenariusz zabezpieczeń federacyjnej.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="d534c-127">Ten scenariusz obejmuje dwie organizacje: A i B. Organizacja B ma zasób sieci Web (usługa sieci Web), który niektórzy użytkownicy w organizacji A uważają za wartościowy.</span><span class="sxs-lookup"><span data-stu-id="d534c-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d534c-128">W tej sekcji użyto *warunków zasób*, *usługa*i usługa *sieci Web* zamiennie.</span><span class="sxs-lookup"><span data-stu-id="d534c-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="d534c-129">Zazwyczaj organizacja B wymaga, aby użytkownik z organizacji A dostarczył prawidłową formę uwierzytelniania przed dostępem do usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="d534c-130">Ponadto organizacja może również wymagać, aby użytkownik był upoważniony do uzyskania dostępu do określonego zasobu, o których mowa.</span><span class="sxs-lookup"><span data-stu-id="d534c-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="d534c-131">Jednym ze sposobów rozwiązania tego problemu i umożliwienia użytkownikom w organizacji A dostępu do zasobu w organizacji B jest następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d534c-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="d534c-132">Użytkownicy z organizacji A rejestrują swoje poświadczenia (nazwę użytkownika i hasło) w organizacji B.</span><span class="sxs-lookup"><span data-stu-id="d534c-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="d534c-133">Podczas dostępu do zasobów użytkownicy z organizacji A prezentują swoje poświadczenia w organizacji B i są uwierzytelnieni przed dostępem do zasobu.</span><span class="sxs-lookup"><span data-stu-id="d534c-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="d534c-134">Takie podejście ma trzy istotne wady:</span><span class="sxs-lookup"><span data-stu-id="d534c-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="d534c-135">Organizacja B musi zarządzać poświadczeniami dla użytkowników z organizacji A oprócz zarządzania poświadczeniami użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="d534c-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="d534c-136">Użytkownicy w organizacji A muszą zachować dodatkowy zestaw poświadczeń (czyli zapamiętać dodatkową nazwę użytkownika i hasło) oprócz poświadczeń, których zwykle używają do uzyskiwania dostępu do zasobów w organizacji A. Zazwyczaj zachęca to do stosowania tej samej nazwy użytkownika i hasła w wielu witrynach serwisowych, co jest słabym środkiem bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="d534c-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="d534c-137">Architektura nie skaluje się, ponieważ więcej organizacji postrzega zasób w organizacji B jako o pewnej wartości.</span><span class="sxs-lookup"><span data-stu-id="d534c-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="d534c-138">Alternatywnym podejściem, które rozwiązuje wspomniane wcześniej wady, jest stosowanie zabezpieczeń federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="d534c-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="d534c-139">W tym podejściu organizacje A i B ustanawiają relację zaufania i wykorzystują usługę tokenu zabezpieczeń (STS), aby umożliwić pośrednictwo w ustalonym zaufaniu.</span><span class="sxs-lookup"><span data-stu-id="d534c-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="d534c-140">W architekturze zabezpieczeń federacyjnego użytkownicy z organizacji A wiedzą, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, muszą przedstawić prawidłowy token zabezpieczający z usługi STS w organizacji B, która uwierzytelnia i autoryzuje ich dostęp do określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="d534c-141">Po skontaktowaniu się z STS B użytkownicy otrzymują inny poziom pośredni z zasad skojarzonych z STS.</span><span class="sxs-lookup"><span data-stu-id="d534c-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="d534c-142">Muszą przedstawić prawidłowy token zabezpieczający z STS A (czyli sfery zaufania klienta), zanim usługa STS B może wydać im token zabezpieczający.</span><span class="sxs-lookup"><span data-stu-id="d534c-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="d534c-143">Jest to następstwo relacji zaufania ustanowionej między dwiema organizacjami i oznacza, że organizacja B nie musi zarządzać tożsamościami użytkowników z organizacji A. W praktyce STS B zazwyczaj `issuerAddress` `issuerMetadataAddress`ma wartość null i .</span><span class="sxs-lookup"><span data-stu-id="d534c-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="d534c-144">Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie wystawcy lokalnego](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="d534c-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="d534c-145">W takim przypadku klient konsultuje się z zasadami lokalnymi w celu zlokalizowania usługi STS A. Ta konfiguracja jest nazywana *federacją obszaru macierzystego* i jest skalowana lepiej, ponieważ STS B nie musi obsługiwać informacji o STS A.</span><span class="sxs-lookup"><span data-stu-id="d534c-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="d534c-146">Następnie użytkownicy kontaktują się z STS w organizacji A i uzyskują token zabezpieczający, przedstawiając poświadczenia uwierzytelniania, których zwykle używają do uzyskiwania dostępu do innych zasobów w organizacji A. To również łagodzi problem użytkowników konieczności obsługi wielu zestawów poświadczeń lub przy użyciu tego samego zestawu poświadczeń w wielu lokacjach usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="d534c-147">Gdy użytkownicy uzyskują token zabezpieczający z STS A, przedstawiają token do STS B. Organizacja B przystępuje do wykonywania autoryzacji żądań użytkowników i wystawia token zabezpieczający dla użytkowników z własnego zestawu tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d534c-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="d534c-148">Użytkownicy mogą następnie przedstawić swój token do zasobu w organizacji B i uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="d534c-149">Wsparcie dla federacyjnego bezpieczeństwa w WCF</span><span class="sxs-lookup"><span data-stu-id="d534c-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="d534c-150">WCF zapewnia "pod klucz" obsługę wdrażania architektur zabezpieczeń federacyjnych za pośrednictwem [ \<>wsFederationHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d534c-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="d534c-151">Element [ \<>wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) zapewnia bezpieczne, niezawodne, interoperacyjne powiązanie, które pociąga za sobą użycie protokołu HTTP jako mechanizmu transportu bazowego dla stylu komunikacji żądanie-odpowiedź, wykorzystując tekst i XML jako format przewodowy do kodowania.</span><span class="sxs-lookup"><span data-stu-id="d534c-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="d534c-152">Użycie [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w scenariuszu zabezpieczeń federacyjnych można oddzielić na dwie logicznie niezależne fazy, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d534c-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="d534c-153">Faza 1: Faza projektowania</span><span class="sxs-lookup"><span data-stu-id="d534c-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="d534c-154">W fazie projektowania klient używa [Narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do odczytu zasad udostępnianych przez punkt końcowy usługi oraz do zbierania wymagań dotyczących uwierzytelniania i autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="d534c-155">Odpowiednie serwery proxy są skonstruowane w celu utworzenia następującego wzorca komunikacji zabezpieczeń federacyjnego na kliencie:</span><span class="sxs-lookup"><span data-stu-id="d534c-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="d534c-156">Uzyskaj token zabezpieczający z usługi STS w dziedzinie zaufania klienta.</span><span class="sxs-lookup"><span data-stu-id="d534c-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="d534c-157">Przedstaw token do STS w sferze zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="d534c-158">Uzyskaj token zabezpieczający z STS w dziedzinie zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="d534c-159">Przedstaw token do usługi, aby uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="d534c-160">Faza 2: Faza czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="d534c-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="d534c-161">Podczas fazy wykonywania klienta tworzy wystąpienia obiektu klasy klienta WCF i wykonuje wywołanie przy użyciu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="d534c-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="d534c-162">Podstawowa struktura WCF obsługuje wcześniej wymienionych kroków w federacyjnej komunikacji zabezpieczeń wzorca i umożliwia klientowi bezproblemowe korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="d534c-163">Przykładowa implementacja przy użyciu WCF</span><span class="sxs-lookup"><span data-stu-id="d534c-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="d534c-164">Na poniższej ilustracji przedstawiono przykładową implementację architektury zabezpieczeń federacyjnych przy użyciu natywnej obsługi z WCF.</span><span class="sxs-lookup"><span data-stu-id="d534c-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagram przedstawiający przykładową implementację zabezpieczeń federacji.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="d534c-166">Przykład MyService</span><span class="sxs-lookup"><span data-stu-id="d534c-166">Example MyService</span></span>  
 <span data-ttu-id="d534c-167">Usługa `MyService` udostępnia pojedynczy punkt końcowy `MyServiceEndpoint`za pośrednictwem .</span><span class="sxs-lookup"><span data-stu-id="d534c-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="d534c-168">Na poniższej ilustracji przedstawiono adres, powiązanie i umowy skojarzone z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="d534c-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagram przedstawiający szczegóły MyServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="d534c-170">Punkt `MyServiceEndpoint` końcowy usługi używa [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu języka znaczników oświadczeń zabezpieczeń (SAML) z oświadczeniem wystawionym `accessAuthorized` przez STS B. Jest to deklaratywnie określone w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
> <span data-ttu-id="d534c-171">Subtelny punkt należy zwrócić uwagę na `MyService`roszczenia wymagane przez .</span><span class="sxs-lookup"><span data-stu-id="d534c-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="d534c-172">Druga liczba wskazuje, `MyService` że wymaga tokenu `accessAuthorized` SAML z oświadczeniem.</span><span class="sxs-lookup"><span data-stu-id="d534c-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="d534c-173">Aby być bardziej precyzyjne, określa `MyService` typ oświadczenia, który wymaga.</span><span class="sxs-lookup"><span data-stu-id="d534c-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="d534c-174">W pełni kwalifikowana nazwa tego `http://tempuri.org:accessAuthorized` typu oświadczenia jest (wraz ze skojarzonym obszarem nazw), który jest używany w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="d534c-175">Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i zakłada `true` się, że jest ona ustawiona przez STS B.</span><span class="sxs-lookup"><span data-stu-id="d534c-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="d534c-176">W czasie wykonywania ta zasada jest `MyServiceOperationRequirement` wymuszana przez klasę, która jest implementowana jako część `MyService`.</span><span class="sxs-lookup"><span data-stu-id="d534c-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="d534c-177">STS B</span><span class="sxs-lookup"><span data-stu-id="d534c-177">STS B</span></span>  
 <span data-ttu-id="d534c-178">Na poniższej ilustracji przedstawiono STS B. Jak wspomniano wcześniej, usługa tokenu zabezpieczającego (STS) jest również usługą sieci Web i może mieć skojarzone z nią punkty końcowe, zasady i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d534c-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagram przedstawiający usługę tokenu zabezpieczającego B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="d534c-180">STS B udostępnia pojedynczy punkt `STSEndpoint` końcowy, wywoływane, które mogą być używane do żądania tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d534c-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="d534c-181">W szczególności STS B wystawia tokeny `accessAuthorized` SAML z oświadczenia, `MyService` które mogą być prezentowane w witrynie usługi dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="d534c-182">Jednak STS B wymaga od użytkowników przedstawienia prawidłowego tokenu SAML `userAuthenticated` wystawionego przez STS A, który zawiera oświadczenie.</span><span class="sxs-lookup"><span data-stu-id="d534c-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="d534c-183">Jest to deklaratywnie określone w konfiguracji STS.</span><span class="sxs-lookup"><span data-stu-id="d534c-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
> <span data-ttu-id="d534c-184">`userAuthenticated` Ponownie, oświadczenie jest typem oświadczenia, który jest wymagany przez STS B. W pełni kwalifikowana nazwa tego `http://tempuri.org:userAuthenticated` typu oświadczenia jest (wraz ze skojarzonym obszarem nazw), która jest używana w pliku konfiguracyjnym STS.</span><span class="sxs-lookup"><span data-stu-id="d534c-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="d534c-185">Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i zakłada `true` się, że jest ustawiona przez STS A.</span><span class="sxs-lookup"><span data-stu-id="d534c-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="d534c-186">W czasie wykonywania `STS_B_OperationRequirement` klasa wymusza tę zasadę, która jest implementowana jako część STS B.</span><span class="sxs-lookup"><span data-stu-id="d534c-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="d534c-187">Jeśli sprawdzanie dostępu jest jasne, STS B wystawia `accessAuthorized` token SAML z oświadczeniem.</span><span class="sxs-lookup"><span data-stu-id="d534c-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="d534c-188">STS A</span><span class="sxs-lookup"><span data-stu-id="d534c-188">STS A</span></span>  
 <span data-ttu-id="d534c-189">Na poniższej ilustracji przedstawiono STS A.</span><span class="sxs-lookup"><span data-stu-id="d534c-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="d534c-190">![Federacja](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="d534c-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="d534c-191">Podobnie jak STS B, STS A jest również usługą sieci Web, która wystawia tokeny zabezpieczające i udostępnia w tym celu pojedynczy punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="d534c-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="d534c-192">Używa jednak innego powiązania (`wsHttpBinding`) i wymaga od użytkowników przedstawienia `emailAddress` ważnego CardSpace z roszczeniem.</span><span class="sxs-lookup"><span data-stu-id="d534c-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid CardSpace with an `emailAddress` claim.</span></span> <span data-ttu-id="d534c-193">W odpowiedzi wydaje tokeny SAML `userAuthenticated` z roszczeniem.</span><span class="sxs-lookup"><span data-stu-id="d534c-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="d534c-194">Jest to deklaratywnie określone w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="d534c-195">W czasie wykonywania `STS_A_OperationRequirement` klasa wymusza tę zasadę, która jest implementowana jako część STS A.</span><span class="sxs-lookup"><span data-stu-id="d534c-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="d534c-196">Jeśli dostęp `true`jest , STS A wystawia `userAuthenticated` token SAML z oświadczeniem.</span><span class="sxs-lookup"><span data-stu-id="d534c-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="d534c-197">Client w: Organization A</span><span class="sxs-lookup"><span data-stu-id="d534c-197">Client at Organization A</span></span>  
 <span data-ttu-id="d534c-198">Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z kroki związane z wykonywaniem `MyService` wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="d534c-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="d534c-199">Pozostałe elementy funkcjonalne są również dołączone do kompletności.</span><span class="sxs-lookup"><span data-stu-id="d534c-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagram przedstawiający kroki w wywołaniu usługi MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="d534c-201">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="d534c-201">Summary</span></span>  
 <span data-ttu-id="d534c-202">Zabezpieczenia federacyjne zapewniają czysty podział odpowiedzialności i pomagają w tworzeniu bezpiecznych, skalowalnych architektur usług.</span><span class="sxs-lookup"><span data-stu-id="d534c-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="d534c-203">Jako platforma do tworzenia i wdrażania aplikacji rozproszonych WCF zapewnia natywną obsługę wdrażania zabezpieczeń federacyjnych.</span><span class="sxs-lookup"><span data-stu-id="d534c-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d534c-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d534c-204">See also</span></span>

- [<span data-ttu-id="d534c-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="d534c-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

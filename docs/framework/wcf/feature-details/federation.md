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
ms.openlocfilehash: 376448502b7b9c7002213be5c3437849a3868166
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425034"
---
# <a name="federation"></a><span data-ttu-id="884d2-102">Federacja</span><span class="sxs-lookup"><span data-stu-id="884d2-102">Federation</span></span>
<span data-ttu-id="884d2-103">Ten temat zawiera krótkie omówienie koncepcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="884d2-104">Omówiono także obsługę usług Windows Communication Foundation (WCF) wdrażanie architektury zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="884d2-105">Dla przykładowej aplikacji, która pokazuje federacyjnego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="884d2-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="884d2-106">Definicja zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="884d2-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="884d2-107">Zabezpieczeń umożliwia czystą separacji między klient uzyskuje dostęp do usługi i skojarzone procedury uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="884d2-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="884d2-108">Zabezpieczeń również umożliwia współpracę między wiele systemów, sieci i organizacje w obszarach różnych zaufania.</span><span class="sxs-lookup"><span data-stu-id="884d2-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="884d2-109">Usługi WCF zapewnia obsługę tworzenia i wdrażania systemów rozproszonych, korzystających z federacyjnego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="884d2-110">Elementy architektury zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="884d2-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="884d2-111">Architektura zabezpieczeń ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="884d2-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="884d2-112">Element</span><span class="sxs-lookup"><span data-stu-id="884d2-112">Element</span></span>|<span data-ttu-id="884d2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="884d2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="884d2-114">Domena/obszaru</span><span class="sxs-lookup"><span data-stu-id="884d2-114">Domain/realm</span></span>|<span data-ttu-id="884d2-115">Pojedynczą jednostką administrowanie zabezpieczeniami lub relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="884d2-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="884d2-116">Typowe domeny może zawierać jednej organizacji.</span><span class="sxs-lookup"><span data-stu-id="884d2-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="884d2-117">Federacja</span><span class="sxs-lookup"><span data-stu-id="884d2-117">Federation</span></span>|<span data-ttu-id="884d2-118">Kolekcja domenach z ustalonymi zaufania.</span><span class="sxs-lookup"><span data-stu-id="884d2-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="884d2-119">Poziom zaufania, mogą się różnić, ale zazwyczaj obejmują uwierzytelnianie i prawie zawsze zawiera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="884d2-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="884d2-120">Typowe Federacji mogą obejmować wiele organizacji z ustalonymi zaufania w celu zapewnienia dostępu współdzielonego z zestawem zasobów.</span><span class="sxs-lookup"><span data-stu-id="884d2-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="884d2-121">Usługa tokenu zabezpieczającego (STS)</span><span class="sxs-lookup"><span data-stu-id="884d2-121">Security Token Service (STS)</span></span>|<span data-ttu-id="884d2-122">Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że to sprawia, że potwierdzenia na podstawie dowodów, której ufa do każdego, kto jest w relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="884d2-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="884d2-123">Stanowi to podstawę przekazywania zaufania między domenami.</span><span class="sxs-lookup"><span data-stu-id="884d2-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="884d2-124">Przykładowy scenariusz</span><span class="sxs-lookup"><span data-stu-id="884d2-124">Example Scenario</span></span>  
 <span data-ttu-id="884d2-125">Na poniższej ilustracji przedstawiono przykład zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="884d2-125">The following illustration shows an example of federated security:</span></span>  
  
 ![Diagram przedstawiający Scenariusz typowe zabezpieczeń.](./media/federation/typical-federated-security-scenario.gif)  
  
 <span data-ttu-id="884d2-127">Ten scenariusz obejmuje dwie organizacje: A i B. organizacji B ma zasób sieci Web (usługa sieci Web), który niektórzy użytkownicy w organizacji, A znaleźć wartościowe.</span><span class="sxs-lookup"><span data-stu-id="884d2-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="884d2-128">Ta sekcja używa warunki *zasobów*, *usługi*, i *usługi sieci Web* zamiennie.</span><span class="sxs-lookup"><span data-stu-id="884d2-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="884d2-129">Zazwyczaj organizacji B wymaga, czy użytkownik z organizacji, A zapewniają pewną formę prawidłowe uwierzytelniania przed uzyskaniem dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="884d2-130">Ponadto organizacja może również wymagać, czy użytkownika można autoryzowany dostęp do określonego zasobu w danym.</span><span class="sxs-lookup"><span data-stu-id="884d2-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="884d2-131">Jednym ze sposobów, aby rozwiązać ten problem i umożliwić użytkownikom w organizacji, A dostęp do zasobów w organizacji B jest następująca:</span><span class="sxs-lookup"><span data-stu-id="884d2-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
- <span data-ttu-id="884d2-132">Użytkownicy z organizacji, A Zarejestruj swoje poświadczenia (nazwę użytkownika i hasło) w organizacji B.</span><span class="sxs-lookup"><span data-stu-id="884d2-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
- <span data-ttu-id="884d2-133">Podczas uzyskiwania dostępu do zasobów użytkownicy z organizacji, A przedstawienia poświadczeń dla organizacji B i uwierzytelnieniu się przed uzyskaniem dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="884d2-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="884d2-134">Takie podejście ma trzy istotne wady:</span><span class="sxs-lookup"><span data-stu-id="884d2-134">This approach has three significant drawbacks:</span></span>  
  
- <span data-ttu-id="884d2-135">Organizacja B ma zarządzania poświadczeniami dla użytkowników z organizacji, A oprócz zarządzania poświadczeń użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="884d2-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
- <span data-ttu-id="884d2-136">Użytkownicy w organizacji, A trzeba utrzymywać dodatkowy zestaw poświadczeń (oznacza to, należy pamiętać, nazwę dodatkowego użytkownika i hasło) oprócz poświadczenia są zwykle są używane do uzyskania dostępu do zasobów organizacji A. To zwykle zachęca praktyka przy użyciu tej samej nazwy użytkownika i hasła w wielu lokacjach usługi, który jest miarą słabe zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
- <span data-ttu-id="884d2-137">Architektura nie skalowanie więcej organizacji dostrzegana zasobów w organizacji B jako jedna z wartości.</span><span class="sxs-lookup"><span data-stu-id="884d2-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="884d2-138">Podejście alternatywne adresy wady wspomniano wcześniej, jest mogą wykorzystać zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="884d2-139">W tym podejściu organizacji, A i B, ustanawiania relacji zaufania i stosować Usługa tokenu zabezpieczającego (STS) umożliwiające pośrednictwo o ustanowioną relację zaufania.</span><span class="sxs-lookup"><span data-stu-id="884d2-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="884d2-140">W przypadku architektury zabezpieczeń użytkowników z organizacji A poinformować, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, który muszą prezentować tokenu zabezpieczającego prawidłowy z usługi STS w organizacji B, która je uwierzytelnia i autoryzuje dostępu do określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="884d2-141">Na skontaktowanie się z B usługi STS, użytkownicy będą otrzymywać kolejny poziom pośredni z zasad skojarzonych z usługi STS.</span><span class="sxs-lookup"><span data-stu-id="884d2-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="884d2-142">Podmioty zabezpieczeń muszą prezentować tokenu z STS A (czyli obszaru zaufania klienta) przed B Usługa STS może wystawiać je tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="884d2-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="884d2-143">To jest następstwem relacji zaufania między dwiema organizacjami i oznacza organizacji B nie ma zarządzania tożsamością użytkowników z organizacji A. W praktyce STS B zwykle ma wartość null `issuerAddress` i `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="884d2-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="884d2-144">Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="884d2-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="884d2-145">W takim przypadku klient konsultacje dotyczące zasad lokalnych, aby zlokalizować usługi STS A. Ta konfiguracja jest nazywana *home obszaru Federacji* i lepsze skalowanie, ponieważ nie ma usługi STS B do obsługi informacji na temat usługi STS A.</span><span class="sxs-lookup"><span data-stu-id="884d2-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="884d2-146">Następnie skontaktuj się z usługą STS w organizacji, A użytkownicy i uzyskania tokenu zabezpieczającego z uwzględnieniem poświadczenia uwierzytelniania, które są zwykle są używane do uzyskiwania dostępu do innych zasobów organizacji A. Eliminuje to również problem użytkowników muszą obsługiwać wiele zestawów poświadczeń lub w wielu lokacjach usługi przy użyciu tego samego zestawu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="884d2-147">Gdy użytkownicy uzyskują tokenu zabezpieczającego z A usługą STS, ich obecny token do usługi STS B. organizacji B rozpoczynające się przeprowadzić autoryzację żądań użytkowników i wystawia token zabezpieczający do użytkowników z swój własny zestaw tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="884d2-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="884d2-148">Użytkowników można prezentować swoje tokenu do zasobu w organizacji B i uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="884d2-149">Obsługa zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="884d2-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="884d2-150">Usługi WCF zapewnia gotową do użycia obsługę wdrażania architektury zabezpieczeń za pomocą [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="884d2-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="884d2-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które pociąga za sobą korzystanie z protokołu HTTP jako podstawowy mechanizm transportu dla stylu komunikacji "żądanie-odpowiedź" wprowadzenie tekstu i XML jako format kodowania o komunikacji sieciowej.</span><span class="sxs-lookup"><span data-stu-id="884d2-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="884d2-152">Korzystanie z [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnego zabezpieczenia scenariusza może być odłączona na dwie fazy logicznie niezależny od, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="884d2-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="884d2-153">Faza 1: Fazy projektowania</span><span class="sxs-lookup"><span data-stu-id="884d2-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="884d2-154">W fazie projektowania, klient używa [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można odczytać zasad uwidacznia punkt końcowy usługi oraz w celu zbierania wymagania dotyczące uwierzytelniania i autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="884d2-155">Odpowiednie serwery proxy, tak aby można było utworzyć następujący wzorzec komunikacji zabezpieczeń po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="884d2-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
- <span data-ttu-id="884d2-156">Uzyskiwanie tokenu zabezpieczającego z usługi STS w obszarze zaufania klienta.</span><span class="sxs-lookup"><span data-stu-id="884d2-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
- <span data-ttu-id="884d2-157">Przedstawia token usługi STS w obszarze relacji zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-157">Present the token to the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="884d2-158">Uzyskiwanie tokenu zabezpieczającego z usługi STS w obszarze relacji zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
- <span data-ttu-id="884d2-159">Przedstawia token do usługi w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="884d2-160">Faza 2: Fazy czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="884d2-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="884d2-161">Podczas fazy czasu wykonywania klient tworzy obiekt klasy klienta WCF i nawiązuje połączenie za pomocą klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="884d2-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="884d2-162">Podstawowej struktury usług WCF obsługuje opisanych powyżej kroków we wzorcu z federacyjnego zabezpieczenia komunikacji i umożliwia klientowi bezproblemowe korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="884d2-163">Przykład implementacji przy użyciu usługi WCF</span><span class="sxs-lookup"><span data-stu-id="884d2-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="884d2-164">Poniższa ilustracja przedstawia przykład implementacji architektury federacyjnego zabezpieczenia dzięki obsłudze natywnych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="884d2-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 ![Diagram przedstawiający przykładową implementację zabezpieczeń federacji.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a><span data-ttu-id="884d2-166">Przykład Moja_usługa</span><span class="sxs-lookup"><span data-stu-id="884d2-166">Example MyService</span></span>  
 <span data-ttu-id="884d2-167">Usługa `MyService` udostępnia pojedynczego punktu końcowego za pośrednictwem `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="884d2-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="884d2-168">Na poniższej ilustracji przedstawiono adres, powiązania i umowy związane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="884d2-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 ![Diagram przedstawiający szczegóły MyServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 <span data-ttu-id="884d2-170">Punkt końcowy usługi `MyServiceEndpoint` używa [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu zabezpieczeń potwierdzenia Markup Language (SAML) z `accessAuthorized` oświadczenia wydane przez usługi STS B. Jest to deklaratywne określony w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
>  <span data-ttu-id="884d2-171">Punkt subtelne należy zauważyć, dotyczących oświadczeń wymaganych przez `MyService`.</span><span class="sxs-lookup"><span data-stu-id="884d2-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="884d2-172">Druga liczba wskazuje, że `MyService` wymaga tokenu SAML z `accessAuthorized` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="884d2-173">Aby zapewnić bardziej precyzyjne, określa typ oświadczenia, które `MyService` wymaga.</span><span class="sxs-lookup"><span data-stu-id="884d2-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="884d2-174">W pełni kwalifikowaną nazwą tego typu oświadczenia jest `http://tempuri.org:accessAuthorized` (oraz skojarzony przestrzeni nazw), która zostanie użyta w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-174">The fully-qualified name of this claim type is `http://tempuri.org:accessAuthorized` (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="884d2-175">Wartość tego oświadczenia wskazuje obecność tego oświadczenia i założono, że można ustawić `true` przez usługę STS B.</span><span class="sxs-lookup"><span data-stu-id="884d2-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="884d2-176">W czasie wykonywania, ta zasada jest wymuszana przez `MyServiceOperationRequirement` klasę, która jest wdrażany jako część `MyService`.</span><span class="sxs-lookup"><span data-stu-id="884d2-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="884d2-177">STS B</span><span class="sxs-lookup"><span data-stu-id="884d2-177">STS B</span></span>  
 <span data-ttu-id="884d2-178">Na poniższej ilustracji przedstawiono B. usługi STS Jak wspomniano wcześniej, Usługa tokenu zabezpieczającego (STS) jest również usługa sieci Web i może mieć jego skojarzone punkty końcowe, zasad i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="884d2-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 ![Diagram przedstawiający usługę tokenu zabezpieczającego B.](./media/federation/myservice-security-token-service-b.gif)  
  
 <span data-ttu-id="884d2-180">STS B uwidacznia pojedynczego punktu końcowego wywołanego `STSEndpoint` służy do żądania tokenów zabezpieczających, które można.</span><span class="sxs-lookup"><span data-stu-id="884d2-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="884d2-181">W szczególności STS B wystawia tokeny SAML za pomocą `accessAuthorized` oświadczenia, które mogą być przedstawiane na `MyService` lokacji usługi do uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="884d2-182">Jednak Usługa STS B wymaga od użytkowników przedstawić prawidłowy token SAML wystawione przez usługę STS A, który zawiera `userAuthenticated` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="884d2-183">Jest to deklaratywne określona w konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="884d2-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
>  <span data-ttu-id="884d2-184">Ponownie `userAuthenticated` oświadczeń jest typ oświadczenia, która jest wymagana przez usługę STS B. W pełni kwalifikowaną nazwą tego typu oświadczenia jest `http://tempuri.org:userAuthenticated` (oraz skojarzony przestrzeni nazw), która zostanie użyta w pliku konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="884d2-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is `http://tempuri.org:userAuthenticated` (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="884d2-185">Wartość tego oświadczenia wskazuje obecność tego oświadczenia i założono, że można ustawić `true` przez usługę STS A.</span><span class="sxs-lookup"><span data-stu-id="884d2-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="884d2-186">W czasie wykonywania `STS_B_OperationRequirement` klasy wymusza tę zasadę, która została wdrożona jako część usługi STS B.</span><span class="sxs-lookup"><span data-stu-id="884d2-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="884d2-187">Jeżeli sprawdzanie dostępu nie zostanie zaznaczone, STS B wystawia token SAML z `accessAuthorized` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="884d2-188">USŁUGA STS A</span><span class="sxs-lookup"><span data-stu-id="884d2-188">STS A</span></span>  
 <span data-ttu-id="884d2-189">Na poniższej ilustracji przedstawiono A. usługi STS</span><span class="sxs-lookup"><span data-stu-id="884d2-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="884d2-190">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="884d2-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="884d2-191">Podobnie jak B usługi STS, A Usługa STS jest również usługa sieci Web, który wystawia tokeny zabezpieczające i udostępnia pojedyncze punkty końcowe w tym celu.</span><span class="sxs-lookup"><span data-stu-id="884d2-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="884d2-192">Jednak używa różnych powiązania (`wsHttpBinding`) i wymaga od użytkowników przedstawić prawidłowy [!INCLUDE[infocard](../../../../includes/infocard-md.md)] z `emailAddress` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="884d2-193">W odpowiedzi, wystawia tokeny SAML za pomocą `userAuthenticated` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="884d2-194">Jest to deklaratywne określony w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-194">This is declaratively specified in the service configuration.</span></span>  
  
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
    <endpoint>  
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
  
 <span data-ttu-id="884d2-195">W czasie wykonywania `STS_A_OperationRequirement` klasy wymusza tę zasadę, która została wdrożona jako część usługi STS A.</span><span class="sxs-lookup"><span data-stu-id="884d2-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="884d2-196">Jeśli dostęp jest `true`, A Usługa STS wystawia token SAML z `userAuthenticated` oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="884d2-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="884d2-197">Klient w organizacji, A</span><span class="sxs-lookup"><span data-stu-id="884d2-197">Client at Organization A</span></span>  
 <span data-ttu-id="884d2-198">Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z etapy w tworzeniu `MyService` wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="884d2-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="884d2-199">Funkcjonalności innych składników dostępne są również aby informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="884d2-199">The other functional components are also included for completeness.</span></span>  
  
 ![Diagram przedstawiający kroki w wywołaniu usługi Moja_usługa.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a><span data-ttu-id="884d2-201">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="884d2-201">Summary</span></span>  
 <span data-ttu-id="884d2-202">Federacyjnego zabezpieczenia zapewnia czyste podział odpowiedzialności i pomaga w tworzeniu architektur bezpiecznego, skalowalnego usług.</span><span class="sxs-lookup"><span data-stu-id="884d2-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="884d2-203">Platforma do kompilowania i wdrażania aplikacji rozproszonych WCF zapewnia macierzystą obsługę dotyczące implementowania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="884d2-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="884d2-204">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="884d2-204">See also</span></span>

- [<span data-ttu-id="884d2-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="884d2-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

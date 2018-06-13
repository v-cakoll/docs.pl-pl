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
ms.openlocfilehash: d69de8c01a23eff5314220a10a51f6487080df41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496766"
---
# <a name="federation"></a><span data-ttu-id="aa540-102">Federacja</span><span class="sxs-lookup"><span data-stu-id="aa540-102">Federation</span></span>
<span data-ttu-id="aa540-103">Ten temat zawiera krótki przegląd koncepcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-103">This topic provides a brief overview of the concept of federated security.</span></span> <span data-ttu-id="aa540-104">Omówiono także obsługa wdrażania architektury zabezpieczeń systemu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aa540-104">It also describes Windows Communication Foundation (WCF) support for deploying federated security architectures.</span></span> <span data-ttu-id="aa540-105">Przykładową aplikację prezentującą federacyjnego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="aa540-105">For a sample application that demonstrates federation, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="definition-of-federated-security"></a><span data-ttu-id="aa540-106">Definicja zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="aa540-106">Definition of Federated Security</span></span>  
 <span data-ttu-id="aa540-107">Zabezpieczeń umożliwia czyste rozdzielenie klient uzyskuje dostęp do usługi i skojarzone procedury uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="aa540-107">Federated security allows for clean separation between the service a client is accessing and the associated authentication and authorization procedures.</span></span> <span data-ttu-id="aa540-108">Zabezpieczeń umożliwia także współpracy w wielu systemów, sieci i organizacji w obszarach różnych zaufania.</span><span class="sxs-lookup"><span data-stu-id="aa540-108">Federated security also enables collaboration across multiple systems, networks, and organizations in different trust realms.</span></span>  
  
 <span data-ttu-id="aa540-109">WCF umożliwia tworzenie i wdrażanie systemów rozproszonych, korzystających z federacyjnego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="aa540-109">WCF provides support for building and deploying distributed systems that employ federated security.</span></span>  
  
### <a name="elements-of-a-federated-security-architecture"></a><span data-ttu-id="aa540-110">Elementy architektury zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="aa540-110">Elements of a Federated Security Architecture</span></span>  
 <span data-ttu-id="aa540-111">Architektura zabezpieczeń ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="aa540-111">The federated security architecture has three key elements, as described in the following table.</span></span>  
  
|<span data-ttu-id="aa540-112">Element</span><span class="sxs-lookup"><span data-stu-id="aa540-112">Element</span></span>|<span data-ttu-id="aa540-113">Opis</span><span class="sxs-lookup"><span data-stu-id="aa540-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa540-114">Domena/obszaru</span><span class="sxs-lookup"><span data-stu-id="aa540-114">Domain/realm</span></span>|<span data-ttu-id="aa540-115">Pojedynczą jednostkę administrowania zabezpieczeniami lub relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="aa540-115">A single unit of security administration or trust.</span></span> <span data-ttu-id="aa540-116">Typowe domeny mogą obejmować pojedynczej organizacji.</span><span class="sxs-lookup"><span data-stu-id="aa540-116">A typical domain might include a single organization.</span></span>|  
|<span data-ttu-id="aa540-117">Federacja</span><span class="sxs-lookup"><span data-stu-id="aa540-117">Federation</span></span>|<span data-ttu-id="aa540-118">Kolekcja domen, które zostało ustanowione zaufania.</span><span class="sxs-lookup"><span data-stu-id="aa540-118">A collection of domains that have established trust.</span></span> <span data-ttu-id="aa540-119">Poziom zaufania może się różnić, ale zwykle obejmuje uwierzytelniania i prawie zawsze zawiera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="aa540-119">The level of trust may vary, but typically includes authentication and almost always includes authorization.</span></span> <span data-ttu-id="aa540-120">Typowy Federacji może obejmować wiele organizacji, które zostało ustanowione zaufania, aby uzyskać dostęp do zestawu zasobów.</span><span class="sxs-lookup"><span data-stu-id="aa540-120">A typical federation might include a number of organizations that have established trust for shared access to a set of resources.</span></span>|  
|<span data-ttu-id="aa540-121">Usługa tokenu zabezpieczającego (STS)</span><span class="sxs-lookup"><span data-stu-id="aa540-121">Security Token Service (STS)</span></span>|<span data-ttu-id="aa540-122">Usługi sieci Web, która wystawia tokeny zabezpieczające; oznacza to ułatwia potwierdzenia oparte na dowód, któremu ufa do każdego, kto w relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="aa540-122">A Web service that issues security tokens; that is, it makes assertions based on evidence that it trusts, to whomever trusts it.</span></span> <span data-ttu-id="aa540-123">Ten proces jest podstawą przekazywania zaufania między domenami.</span><span class="sxs-lookup"><span data-stu-id="aa540-123">This forms the basis of trust brokering between domains.</span></span>|  
  
### <a name="example-scenario"></a><span data-ttu-id="aa540-124">Przykładowy scenariusz</span><span class="sxs-lookup"><span data-stu-id="aa540-124">Example Scenario</span></span>  
 <span data-ttu-id="aa540-125">Na poniższej ilustracji przedstawiono przykład zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-125">The following illustration shows an example of federated security.</span></span>  
  
 <span data-ttu-id="aa540-126">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span><span class="sxs-lookup"><span data-stu-id="aa540-126">![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")</span></span>  
  
 <span data-ttu-id="aa540-127">Taki scenariusz obejmuje dwie organizacje: A i B organizacji B. zawiera zasobu sieci Web (usługa sieci Web) niektórzy użytkownicy w organizacji A znaleźć cenne.</span><span class="sxs-lookup"><span data-stu-id="aa540-127">This scenario includes two organizations: A and B. Organization B has a Web resource (a Web service) that some users in organization A find valuable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa540-128">Ta sekcja używa warunki *zasobów*, *usługi*, i *usługi sieci Web* zamiennie.</span><span class="sxs-lookup"><span data-stu-id="aa540-128">This section uses the terms *resource*, *service*, and *Web service* interchangeably.</span></span>  
  
 <span data-ttu-id="aa540-129">Zazwyczaj organizacji B wymaga użytkownik z organizacji A podania niektórych prawidłowy formy uwierzytelniania przed uzyskaniem dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-129">Typically, organization B requires that a user from organization A provide some valid form of authentication before accessing the service.</span></span> <span data-ttu-id="aa540-130">Ponadto organizacja może również wymagać, użytkownik mieć możliwość dostępu do określonego zasobu w.</span><span class="sxs-lookup"><span data-stu-id="aa540-130">In addition, the organization may also require that the user be authorized to access the specific resource in question.</span></span> <span data-ttu-id="aa540-131">Jednym ze sposobów rozwiązania tego problemu i umożliwienie użytkownikom w organizacji, A dostęp do zasobu w organizacji B wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="aa540-131">One way to address this problem and enable users in organization A to access the resource in organization B is as follows:</span></span>  
  
-   <span data-ttu-id="aa540-132">Użytkownicy z organizacji, A zarejestrować poświadczeń (nazwy użytkownika i hasło) z organizacją B.</span><span class="sxs-lookup"><span data-stu-id="aa540-132">Users from organization A register their credentials (a user name and password) with organization B.</span></span>  
  
-   <span data-ttu-id="aa540-133">Podczas dostępu do zasobów użytkownicy z organizacji A prezentować swoje poświadczenia dla organizacji B oraz uwierzytelniania przed uzyskaniem dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="aa540-133">During the resource access, users from organization A present their credentials to organization B and are authenticated before accessing the resource.</span></span>  
  
 <span data-ttu-id="aa540-134">Takie podejście ma trzy znaczących wady:</span><span class="sxs-lookup"><span data-stu-id="aa540-134">This approach has three significant drawbacks:</span></span>  
  
-   <span data-ttu-id="aa540-135">Organizacja B ma zarządzać poświadczenia dla użytkowników z organizacji, A oprócz zarządzania poświadczeń użytkowników lokalnych.</span><span class="sxs-lookup"><span data-stu-id="aa540-135">Organization B has to manage the credentials for users from organization A in addition to managing the credentials of its local users.</span></span>  
  
-   <span data-ttu-id="aa540-136">Użytkownicy w organizacji A należy obsługiwać dodatkowy zestaw poświadczeń (oznacza to, należy pamiętać o nazwę dodatkowe użytkownika i hasło) oprócz poświadczenia używają zwykle uzyskują dostęp do zasobów w organizacji A. To zwykle zachęca do rozwiązania przy użyciu tej samej nazwy użytkownika i hasła w wielu lokacjach usługi, która jest słaby zabezpieczenie.</span><span class="sxs-lookup"><span data-stu-id="aa540-136">Users in organization A need to maintain an additional set of credentials (that is, remember an additional user name and password) apart from the credentials they normally use to gain access to resources within organization A. This usually encourages the practice of using the same user name and password at multiple service sites, which is a weak security measure.</span></span>  
  
-   <span data-ttu-id="aa540-137">Architektura nie działa zgodnie z organizacji więcej postrzegać zasobów w organizacji B jako pewnej wartości.</span><span class="sxs-lookup"><span data-stu-id="aa540-137">The architecture does not scale as more organizations perceive the resource at organization B as being of some value.</span></span>  
  
 <span data-ttu-id="aa540-138">Alternatywne podejście, które dotyczy wady opisane powyżej, jest fragmentów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-138">An alternative approach, which addresses the previously mentioned drawbacks, is to employ federated security.</span></span> <span data-ttu-id="aa540-139">W takie podejście organizacji, A i B ustanawiania relacji zaufania i stosować zabezpieczeń tokenu usługi (STS) umożliwia utrzymywanie właściwych ustanowić relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="aa540-139">In this approach, organizations A and B establish a trust relationship and employ Security Token Service (STS) to enable brokering of the established trust.</span></span>  
  
 <span data-ttu-id="aa540-140">W architekturze zabezpieczeń użytkownicy z organizacji A pamiętać, że jeśli chcą, aby uzyskać dostęp do usługi sieci Web w organizacji B, który muszą prezentować tokenu zabezpieczającego prawidłowe z STS w organizacji B, który uwierzytelnia i autoryzuje dostępu do określonej usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-140">In a federated security architecture, users from organization A know that if they want to access the Web service in organization B that they must present a valid security token from the STS at organization B, which authenticates and authorizes their access to the specific service.</span></span>  
  
 <span data-ttu-id="aa540-141">Na skontaktowanie się z STS B, użytkownicy otrzymują inny poziom pośredników od zasady skojarzone z usługi STS.</span><span class="sxs-lookup"><span data-stu-id="aa540-141">On contacting the STS B, the users receive another level of indirection from the policy associated with the STS.</span></span> <span data-ttu-id="aa540-142">Podmioty zabezpieczeń muszą prezentować tokenu z STS A (to znaczy obszar zaufania klienta), przed STS B mogą wystawiać ich tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="aa540-142">They must present a valid security token from the STS A (that is, the client trust realm) before the STS B can issue them a security token.</span></span> <span data-ttu-id="aa540-143">To jest następstwem relacji zaufania między dwiema organizacjami i oznacza organizacji B nie musi zarządzać tożsamościami użytkowników z organizacji A. W praktyce STS B zazwyczaj ma wartość null `issuerAddress` i `issuerMetadataAddress`.</span><span class="sxs-lookup"><span data-stu-id="aa540-143">This is a corollary of the trust relationship established between the two organizations and implies that organization B does not have to manage identities for users from organization A. In practice, STS B typically has a null `issuerAddress` and `issuerMetadataAddress`.</span></span> <span data-ttu-id="aa540-144">Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span><span class="sxs-lookup"><span data-stu-id="aa540-144">For more information, see [How to: Configure a Local Issuer](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md).</span></span> <span data-ttu-id="aa540-145">W takim przypadku klient sprawdza zasad lokalnych można znaleźć usługi STS A. Ta konfiguracja jest nazywana *home federacyjnego obszaru* i lepiej skaluje ponieważ STS B nie ma do przechowywania informacji o STS A.</span><span class="sxs-lookup"><span data-stu-id="aa540-145">In that case, the client consults a local policy to locate STS A. This configuration is called *home realm federation* and it scales better because STS B does not have to maintain information about STS A.</span></span>  
  
 <span data-ttu-id="aa540-146">Następnie skontaktuj się z STS w organizacji, A użytkownicy i uzyskania tokenu zabezpieczającego z uwzględnieniem poświadczenia uwierzytelniania, które zazwyczaj używają do uzyskiwania dostępu do innych zasobów organizacji A. Eliminuje to również problem użytkownicy muszą obsługiwać wiele zestawów poświadczeń lub w wielu lokacjach usługi przy użyciu tego samego zestawu poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-146">The users then contact the STS at organization A and obtain a security token by presenting authentication credentials that they normally use to gain access to any other resource within organization A. This also alleviates the problem of users having to maintain multiple sets of credentials or using the same set of credentials at multiple service sites.</span></span>  
  
 <span data-ttu-id="aa540-147">Gdy użytkownicy uzyskują tokenu zabezpieczającego z STS A, ich obecny token do usługi STS B. organizacji B będzie kontynuowane do wykonania autoryzację żądań użytkowników i wystawia token zabezpieczający dla użytkowników z własny zestaw tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="aa540-147">Once the users obtain a security token from the STS A, they present the token to the STS B. Organization B proceeds to perform authorization of the users' requests and issues a security token to the users from its own set of security tokens.</span></span> <span data-ttu-id="aa540-148">Użytkownicy można prezentować swoje token do zasobu w organizacji B i uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-148">The users can then present their token to the resource at organization B and access the service.</span></span>  
  
## <a name="support-for-federated-security-in-wcf"></a><span data-ttu-id="aa540-149">Obsługa zabezpieczeń w programie WCF</span><span class="sxs-lookup"><span data-stu-id="aa540-149">Support for Federated Security in WCF</span></span>  
 <span data-ttu-id="aa540-150">Usługi WCF zapewnia obsługę gotowe do wdrożenia architektury zabezpieczeń za pomocą [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aa540-150">WCF provides turnkey support for deploying federated security architectures through the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="aa540-151">[ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które powoduje użycie protokołu HTTP jako podstawowy mechanizm transportu dla stylu komunikacji "żądanie-odpowiedź" wykorzystujące tekst i kodu XML, ponieważ format kodowania danych przesyłanych w sieci.</span><span class="sxs-lookup"><span data-stu-id="aa540-151">The [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element provides for a secure, reliable, interoperable binding that entails the use of HTTP as the underlying transport mechanism for request-reply communication style, employing text and XML as the wire format for encoding.</span></span>  
  
 <span data-ttu-id="aa540-152">Korzystanie z [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnego zabezpieczenia scenariusz może być odłączona na dwa etapy logicznie niezależny, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="aa540-152">The use of [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) in a federated security scenario can be decoupled into two logically independent phases, as described in the following sections.</span></span>  
  
### <a name="phase-1-design-phase"></a><span data-ttu-id="aa540-153">Faza 1: Faza projektowania</span><span class="sxs-lookup"><span data-stu-id="aa540-153">Phase 1: Design Phase</span></span>  
 <span data-ttu-id="aa540-154">W fazie projektowania, klient używa [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) odczytać zasad udostępnia punkt końcowy usługi i gromadzić wymagania usługi uwierzytelniania i autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="aa540-154">During the design phase, the client uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to read the policy the service endpoint exposes and to collect the service's authentication and authorization requirements.</span></span> <span data-ttu-id="aa540-155">Odpowiednie serwery proxy, tak aby utworzyć następującego wzorca komunikacji zabezpieczeń po stronie klienta:</span><span class="sxs-lookup"><span data-stu-id="aa540-155">The appropriate proxies are constructed to create the following federated security communication pattern at the client:</span></span>  
  
-   <span data-ttu-id="aa540-156">Uzyskania tokenu zabezpieczającego z STS w obszarze zaufania klienta.</span><span class="sxs-lookup"><span data-stu-id="aa540-156">Obtain a security token from the STS in the client trust realm.</span></span>  
  
-   <span data-ttu-id="aa540-157">Przedstawia tokenu Zabezpieczającego w obszarze zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-157">Present the token to the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="aa540-158">Uzyskania tokenu zabezpieczającego z STS w obszarze zaufania usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-158">Obtain a security token from the STS in the service trust realm.</span></span>  
  
-   <span data-ttu-id="aa540-159">Przedstawia token do usługi, aby uzyskać dostęp do usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-159">Present the token to the service to access the service.</span></span>  
  
### <a name="phase-2-run-time-phase"></a><span data-ttu-id="aa540-160">Faza 2: Faza środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="aa540-160">Phase 2: Run-Time Phase</span></span>  
 <span data-ttu-id="aa540-161">Podczas fazy środowiska wykonawczego klient tworzy obiekt klasy klienta WCF i nawiązuje połączenie za pomocą klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="aa540-161">During the run-time phase, the client instantiates an object of the WCF client class and makes a call using the WCF client.</span></span> <span data-ttu-id="aa540-162">Zakresie podstawowej struktury WCF obsługuje opisane powyżej kroki we wzorcu federacyjnego zabezpieczenia komunikacji i umożliwia klientowi bezproblemowo korzystanie z usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-162">The underlying framework of WCF handles the previously mentioned steps in the federated security communication pattern and enables the client to seamlessly consume the service.</span></span>  
  
## <a name="sample-implementation-using-wcf"></a><span data-ttu-id="aa540-163">Przykładowe zastosowanie przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="aa540-163">Sample Implementation Using WCF</span></span>  
 <span data-ttu-id="aa540-164">Na poniższej ilustracji przedstawiono przykładowe zastosowanie dla architektury zabezpieczeń przy użyciu natywnej obsługi z WCF.</span><span class="sxs-lookup"><span data-stu-id="aa540-164">The following illustration shows a sample implementation for a federated security architecture using native support from WCF.</span></span>  
  
 <span data-ttu-id="aa540-165">![Federacyjna zabezpieczeń w programie WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span><span class="sxs-lookup"><span data-stu-id="aa540-165">![Federation security in WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")</span></span>  
  
### <a name="example-myservice"></a><span data-ttu-id="aa540-166">Przykład Moja_usługa</span><span class="sxs-lookup"><span data-stu-id="aa540-166">Example MyService</span></span>  
 <span data-ttu-id="aa540-167">Usługa `MyService` udostępnia jeden punkt końcowy za pośrednictwem `MyServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="aa540-167">The service `MyService` exposes a single endpoint through `MyServiceEndpoint`.</span></span> <span data-ttu-id="aa540-168">Na poniższej ilustracji przedstawiono address, binding i kontrakt skojarzony z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="aa540-168">The following illustration shows the address, binding, and contract associated with the endpoint.</span></span>  
  
 <span data-ttu-id="aa540-169">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/myservice.gif "Moja_usługa")</span><span class="sxs-lookup"><span data-stu-id="aa540-169">![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")</span></span>  
  
 <span data-ttu-id="aa540-170">Punkt końcowy usługi `MyServiceEndpoint` używa [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu zabezpieczeń potwierdzenia Markup Language (SAML) z `accessAuthorized` oświadczenia wydane przez usługę STS B. Jest to deklaratywnie określone w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-170">The service endpoint `MyServiceEndpoint` uses the [\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and requires a valid Security Assertions Markup Language (SAML) token with an `accessAuthorized` claim issued by STS B. This is declaratively specified in the service configuration.</span></span>  
  
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
>  <span data-ttu-id="aa540-171">Niewielkie punktu należy zauważyć, dotyczących oświadczeń wymagane przez `MyService`.</span><span class="sxs-lookup"><span data-stu-id="aa540-171">A subtle point should be noted about the claims required by `MyService`.</span></span> <span data-ttu-id="aa540-172">Druga liczba wskazuje, że `MyService` wymaga tokenu SAML z `accessAuthorized` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-172">The second figure indicates that `MyService` requires a SAML token with the `accessAuthorized` claim.</span></span> <span data-ttu-id="aa540-173">Mówiąc ściślej, określa typ oświadczenia, które `MyService` wymaga.</span><span class="sxs-lookup"><span data-stu-id="aa540-173">To be more precise, this specifies the claim type that `MyService` requires.</span></span> <span data-ttu-id="aa540-174">Jest w pełni kwalifikowaną nazwę tego typu oświadczenia http://tempuri.org:accessAuthorized (wraz z skojarzona przestrzeń nazw), która jest używana w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-174">The fully-qualified name of this claim type is http://tempuri.org:accessAuthorized (along with the associated namespace), which is used in the service configuration file.</span></span> <span data-ttu-id="aa540-175">Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i przyjęto, że można ustawić `true` przez usługę STS B.</span><span class="sxs-lookup"><span data-stu-id="aa540-175">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS B.</span></span>  
  
 <span data-ttu-id="aa540-176">W czasie wykonywania, te zasady są wymuszane przez `MyServiceOperationRequirement` klasy, która jest zaimplementowany jako część `MyService`.</span><span class="sxs-lookup"><span data-stu-id="aa540-176">At runtime, this policy is enforced by the `MyServiceOperationRequirement` class that is implemented as part of the `MyService`.</span></span>  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a><span data-ttu-id="aa540-177">STS B</span><span class="sxs-lookup"><span data-stu-id="aa540-177">STS B</span></span>  
 <span data-ttu-id="aa540-178">Na poniższej ilustracji przedstawiono STS B. Jak wspomniano wcześniej, Usługa tokenu zabezpieczającego (STS) jest również usługi sieci Web i może mieć jego skojarzone punkty końcowe, zasad i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="aa540-178">The following illustration shows the STS B. As stated earlier, a security token service (STS) is also a Web service and can have its associated endpoints, policy, and so on.</span></span>  
  
 <span data-ttu-id="aa540-179">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span><span class="sxs-lookup"><span data-stu-id="aa540-179">![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")</span></span>  
  
 <span data-ttu-id="aa540-180">STS B udostępnia jeden punkt końcowy o nazwie `STSEndpoint` które może być używany do żądania tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="aa540-180">STS B exposes a single endpoint, called `STSEndpoint` that can be use to request security tokens.</span></span> <span data-ttu-id="aa540-181">W szczególności STS B wystawia tokeny SAML z `accessAuthorized` oświadczenia, które mogą być przedstawiane w `MyService` lokacji usługi do uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-181">Specifically, STS B issues SAML tokens with the `accessAuthorized` claim, which can be presented at the `MyService` service site for accessing the service.</span></span> <span data-ttu-id="aa540-182">Jednak STS B wymaga od użytkowników istnieje prawidłowy token SAML wystawione przez usługi STS A, który zawiera `userAuthenticated` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-182">However, STS B requires users to present a valid SAML token issued by STS A that contains the `userAuthenticated` claim.</span></span> <span data-ttu-id="aa540-183">Jest to deklaratywnie określony w konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="aa540-183">This is declaratively specified in the STS configuration.</span></span>  
  
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
>  <span data-ttu-id="aa540-184">Ponownie `userAuthenticated` oświadczenia jest typ oświadczenia, który jest wymagany przez usługę STS B. Jest w pełni kwalifikowaną nazwę tego typu oświadczenia http://tempuri.org:userAuthenticated (wraz z skojarzona przestrzeń nazw), która jest używana w pliku konfiguracji usługi STS.</span><span class="sxs-lookup"><span data-stu-id="aa540-184">Again, the `userAuthenticated` claim is the claim type that is required by STS B. The fully-qualified name of this claim type is http://tempuri.org:userAuthenticated (along with the associated namespace), which is used in the STS configuration file.</span></span> <span data-ttu-id="aa540-185">Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i przyjęto, że można ustawić `true` przez usługę STS A.</span><span class="sxs-lookup"><span data-stu-id="aa540-185">The value of this claim indicates the presence of this claim and is assumed to be set to `true` by STS A.</span></span>  
  
 <span data-ttu-id="aa540-186">W czasie wykonywania `STS_B_OperationRequirement` klasy wymusza tych zasad, które zostało zaimplementowane jako część usługi STS B.</span><span class="sxs-lookup"><span data-stu-id="aa540-186">At runtime, the `STS_B_OperationRequirement` class enforces this policy, which is implemented as part of STS B.</span></span>  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 <span data-ttu-id="aa540-187">Jeśli dostęp do wyboru jest wyczyszczone, STS B wystawia token SAML z `accessAuthorized` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-187">If the access check is clear, STS B issues a SAML token with the `accessAuthorized` claim.</span></span>  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a><span data-ttu-id="aa540-188">STS A</span><span class="sxs-lookup"><span data-stu-id="aa540-188">STS A</span></span>  
 <span data-ttu-id="aa540-189">Na poniższej ilustracji przedstawiono STS A.</span><span class="sxs-lookup"><span data-stu-id="aa540-189">The following illustration shows the STS A.</span></span>  
  
 <span data-ttu-id="aa540-190">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span><span class="sxs-lookup"><span data-stu-id="aa540-190">![Federation](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")</span></span>  
  
 <span data-ttu-id="aa540-191">Podobnie STS B, A usługi STS jest również usługa sieci Web, która wystawia tokeny zabezpieczające i udostępnia jeden punkt końcowy do tego celu.</span><span class="sxs-lookup"><span data-stu-id="aa540-191">Similar to the STS B, the STS A is also a Web service that issues security tokens and exposes a single endpoint for this purpose.</span></span> <span data-ttu-id="aa540-192">Jednak używa inne powiązanie (`wsHttpBinding`) i wymaga od użytkowników istnieje prawidłowy [!INCLUDE[infocard](../../../../includes/infocard-md.md)] z `emailAddress` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-192">However, it uses a different binding (`wsHttpBinding`) and requires users to present a valid [!INCLUDE[infocard](../../../../includes/infocard-md.md)] with an `emailAddress` claim.</span></span> <span data-ttu-id="aa540-193">W odpowiedzi, wystawia tokeny SAML z `userAuthenticated` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-193">In response, it issues SAML tokens with the `userAuthenticated` claim.</span></span> <span data-ttu-id="aa540-194">Jest to deklaratywnie określone w konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-194">This is declaratively specified in the service configuration.</span></span>  
  
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
  
 <span data-ttu-id="aa540-195">W czasie wykonywania `STS_A_OperationRequirement` klasy wymusza tych zasad, które zostało zaimplementowane jako część usługi STS A.</span><span class="sxs-lookup"><span data-stu-id="aa540-195">At runtime, the `STS_A_OperationRequirement` class enforces this policy, which is implemented as part of STS A.</span></span>  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 <span data-ttu-id="aa540-196">Jeśli dostęp jest `true`, A usługi STS wystawia token SAML z `userAuthenticated` oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-196">If the access is `true`, STS A issues a SAML token with `userAuthenticated` claim.</span></span>  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a><span data-ttu-id="aa540-197">Klient w organizacji A</span><span class="sxs-lookup"><span data-stu-id="aa540-197">Client at Organization A</span></span>  
 <span data-ttu-id="aa540-198">Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z kroki do wykonania w tworzeniu `MyService` do działu obsługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-198">The following illustration shows the client at organization A, along with the steps involved in making a `MyService` service call.</span></span> <span data-ttu-id="aa540-199">Inne składniki funkcjonalności uwzględniono również informacje były kompletne.</span><span class="sxs-lookup"><span data-stu-id="aa540-199">The other functional components are also included for completeness.</span></span>  
  
 <span data-ttu-id="aa540-200">![Federacyjna](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span><span class="sxs-lookup"><span data-stu-id="aa540-200">![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="aa540-201">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="aa540-201">Summary</span></span>  
 <span data-ttu-id="aa540-202">Zabezpieczeń zawiera jasny podział odpowiedzialności i ułatwia tworzenie architektur bezpiecznego, skalowalnego usługi.</span><span class="sxs-lookup"><span data-stu-id="aa540-202">Federated security provides a clean division of responsibility and helps to build secure, scalable service architectures.</span></span> <span data-ttu-id="aa540-203">Jako platformę umożliwiającą tworzenie i wdrażanie aplikacji rozproszonych WCF zapewnia macierzystą obsługę wdrażania zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="aa540-203">As a platform for building and deploying distributed applications, WCF provides native support for implementing federated security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa540-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa540-204">See Also</span></span>  
 [<span data-ttu-id="aa540-205">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="aa540-205">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)

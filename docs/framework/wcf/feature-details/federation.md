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
ms.openlocfilehash: f05d4a9348c12a29dc3cd7b93334ab1134eeb1a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709393"
---
# <a name="federation"></a>Federacja
Ten temat zawiera krótkie omówienie koncepcji zabezpieczeń. Omówiono także obsługę usług Windows Communication Foundation (WCF) wdrażanie architektury zabezpieczeń. Dla przykładowej aplikacji, która pokazuje federacyjnego, zobacz [Federacja — przykład](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definicja zabezpieczeń  
 Zabezpieczeń umożliwia czystą separacji między klient uzyskuje dostęp do usługi i skojarzone procedury uwierzytelniania i autoryzacji. Zabezpieczeń również umożliwia współpracę między wiele systemów, sieci i organizacje w obszarach różnych zaufania.  
  
 Usługi WCF zapewnia obsługę tworzenia i wdrażania systemów rozproszonych, korzystających z federacyjnego zabezpieczenia.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementy architektury zabezpieczeń  
 Architektura zabezpieczeń ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|Domena/obszaru|Pojedynczą jednostką administrowanie zabezpieczeniami lub relacji zaufania. Typowe domeny może zawierać jednej organizacji.|  
|Federacja|Kolekcja domenach z ustalonymi zaufania. Poziom zaufania, mogą się różnić, ale zazwyczaj obejmują uwierzytelnianie i prawie zawsze zawiera autoryzacji. Typowe Federacji mogą obejmować wiele organizacji z ustalonymi zaufania w celu zapewnienia dostępu współdzielonego z zestawem zasobów.|  
|Usługa tokenu zabezpieczającego (STS)|Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że to sprawia, że potwierdzenia na podstawie dowodów, której ufa do każdego, kto jest w relacji zaufania. Stanowi to podstawę przekazywania zaufania między domenami.|  
  
### <a name="example-scenario"></a>Przykładowy scenariusz  
 Na poniższej ilustracji przedstawiono przykład federacyjnego zabezpieczenia.  
  
 ![Federation](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Ten scenariusz obejmuje dwie organizacje: A i B. organizacji B ma zasób sieci Web (usługa sieci Web), który niektórzy użytkownicy w organizacji, A znaleźć wartościowe.  
  
> [!NOTE]
>  Ta sekcja używa warunki *zasobów*, *usługi*, i *usługi sieci Web* zamiennie.  
  
 Zazwyczaj organizacji B wymaga, czy użytkownik z organizacji, A zapewniają pewną formę prawidłowe uwierzytelniania przed uzyskaniem dostępu do usługi. Ponadto organizacja może również wymagać, czy użytkownika można autoryzowany dostęp do określonego zasobu w danym. Jednym ze sposobów, aby rozwiązać ten problem i umożliwić użytkownikom w organizacji, A dostęp do zasobów w organizacji B jest następująca:  
  
-   Użytkownicy z organizacji, A Zarejestruj swoje poświadczenia (nazwę użytkownika i hasło) w organizacji B.  
  
-   Podczas uzyskiwania dostępu do zasobów użytkownicy z organizacji, A przedstawienia poświadczeń dla organizacji B i uwierzytelnieniu się przed uzyskaniem dostępu do zasobu.  
  
 Takie podejście ma trzy istotne wady:  
  
-   Organizacja B ma zarządzania poświadczeniami dla użytkowników z organizacji, A oprócz zarządzania poświadczeń użytkowników lokalnych.  
  
-   Użytkownicy w organizacji, A trzeba utrzymywać dodatkowy zestaw poświadczeń (oznacza to, należy pamiętać, nazwę dodatkowego użytkownika i hasło) oprócz poświadczenia są zwykle są używane do uzyskania dostępu do zasobów organizacji A. To zwykle zachęca praktyka przy użyciu tej samej nazwy użytkownika i hasła w wielu lokacjach usługi, który jest miarą słabe zabezpieczeń.  
  
-   Architektura nie skalowanie więcej organizacji dostrzegana zasobów w organizacji B jako jedna z wartości.  
  
 Podejście alternatywne adresy wady wspomniano wcześniej, jest mogą wykorzystać zabezpieczeń. W tym podejściu organizacji, A i B, ustanawiania relacji zaufania i stosować Usługa tokenu zabezpieczającego (STS) umożliwiające pośrednictwo o ustanowioną relację zaufania.  
  
 W przypadku architektury zabezpieczeń użytkowników z organizacji A poinformować, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, który muszą prezentować tokenu zabezpieczającego prawidłowy z usługi STS w organizacji B, która je uwierzytelnia i autoryzuje dostępu do określonej usługi.  
  
 Na skontaktowanie się z B usługi STS, użytkownicy będą otrzymywać kolejny poziom pośredni z zasad skojarzonych z usługi STS. Podmioty zabezpieczeń muszą prezentować tokenu z STS A (czyli obszaru zaufania klienta) przed B Usługa STS może wystawiać je tokenu zabezpieczającego. To jest następstwem relacji zaufania między dwiema organizacjami i oznacza organizacji B nie ma zarządzania tożsamością użytkowników z organizacji A. W praktyce STS B zwykle ma wartość null `issuerAddress` i `issuerMetadataAddress`. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). W takim przypadku klient konsultacje dotyczące zasad lokalnych, aby zlokalizować usługi STS A. Ta konfiguracja jest nazywana *home obszaru Federacji* i lepsze skalowanie, ponieważ nie ma usługi STS B do obsługi informacji na temat usługi STS A.  
  
 Następnie skontaktuj się z usługą STS w organizacji, A użytkownicy i uzyskania tokenu zabezpieczającego z uwzględnieniem poświadczenia uwierzytelniania, które są zwykle są używane do uzyskiwania dostępu do innych zasobów organizacji A. Eliminuje to również problem użytkowników muszą obsługiwać wiele zestawów poświadczeń lub w wielu lokacjach usługi przy użyciu tego samego zestawu poświadczeń.  
  
 Gdy użytkownicy uzyskują tokenu zabezpieczającego z A usługą STS, ich obecny token do usługi STS B. organizacji B rozpoczynające się przeprowadzić autoryzację żądań użytkowników i wystawia token zabezpieczający do użytkowników z swój własny zestaw tokenów zabezpieczających. Użytkowników można prezentować swoje tokenu do zasobu w organizacji B i uzyskać dostęp do usługi.  
  
## <a name="support-for-federated-security-in-wcf"></a>Obsługa zabezpieczeń w programie WCF  
 Usługi WCF zapewnia gotową do użycia obsługę wdrażania architektury zabezpieczeń za pomocą [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które pociąga za sobą korzystanie z protokołu HTTP jako podstawowy mechanizm transportu dla stylu komunikacji "żądanie-odpowiedź" wprowadzenie tekstu i XML jako format kodowania o komunikacji sieciowej.  
  
 Korzystanie z [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnego zabezpieczenia scenariusza może być odłączona na dwie fazy logicznie niezależny od, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="phase-1-design-phase"></a>Faza 1: Fazy projektowania  
 W fazie projektowania, klient używa [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można odczytać zasad uwidacznia punkt końcowy usługi oraz w celu zbierania wymagania dotyczące uwierzytelniania i autoryzacji usługi. Odpowiednie serwery proxy, tak aby można było utworzyć następujący wzorzec komunikacji zabezpieczeń po stronie klienta:  
  
-   Uzyskiwanie tokenu zabezpieczającego z usługi STS w obszarze zaufania klienta.  
  
-   Przedstawia token usługi STS w obszarze relacji zaufania usługi.  
  
-   Uzyskiwanie tokenu zabezpieczającego z usługi STS w obszarze relacji zaufania usługi.  
  
-   Przedstawia token do usługi w celu uzyskania dostępu do usługi.  
  
### <a name="phase-2-run-time-phase"></a>Faza 2: Fazy czasu wykonywania  
 Podczas fazy czasu wykonywania klient tworzy obiekt klasy klienta WCF i nawiązuje połączenie za pomocą klienta WCF. Podstawowej struktury usług WCF obsługuje opisanych powyżej kroków we wzorcu z federacyjnego zabezpieczenia komunikacji i umożliwia klientowi bezproblemowe korzystanie z usługi.  
  
## <a name="sample-implementation-using-wcf"></a>Przykład implementacji przy użyciu usługi WCF  
 Poniższa ilustracja przedstawia przykład implementacji architektury federacyjnego zabezpieczenia dzięki obsłudze natywnych z usługi WCF.  
  
 ![Zabezpieczenia federacji w programie WCF](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Przykład Moja_usługa  
 Usługa `MyService` udostępnia pojedynczego punktu końcowego za pośrednictwem `MyServiceEndpoint`. Na poniższej ilustracji przedstawiono adres, powiązania i umowy związane z punktem końcowym.  
  
 ![Federation](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")  
  
 Punkt końcowy usługi `MyServiceEndpoint` używa [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu zabezpieczeń potwierdzenia Markup Language (SAML) z `accessAuthorized` oświadczenia wydane przez usługi STS B. Jest to deklaratywne określony w konfiguracji usługi.  
  
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
>  Punkt subtelne należy zauważyć, dotyczących oświadczeń wymaganych przez `MyService`. Druga liczba wskazuje, że `MyService` wymaga tokenu SAML z `accessAuthorized` oświadczenia. Aby zapewnić bardziej precyzyjne, określa typ oświadczenia, które `MyService` wymaga. W pełni kwalifikowaną nazwą tego typu oświadczenia jest `http://tempuri.org:accessAuthorized` (oraz skojarzony przestrzeni nazw), która zostanie użyta w pliku konfiguracji usługi. Wartość tego oświadczenia wskazuje obecność tego oświadczenia i założono, że można ustawić `true` przez usługę STS B.  
  
 W czasie wykonywania, ta zasada jest wymuszana przez `MyServiceOperationRequirement` klasę, która jest wdrażany jako część `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Na poniższej ilustracji przedstawiono B. usługi STS Jak wspomniano wcześniej, Usługa tokenu zabezpieczającego (STS) jest również usługa sieci Web i może mieć jego skojarzone punkty końcowe, zasad i tak dalej.  
  
 ![Federation](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B uwidacznia pojedynczego punktu końcowego wywołanego `STSEndpoint` służy do żądania tokenów zabezpieczających, które można. W szczególności STS B wystawia tokeny SAML za pomocą `accessAuthorized` oświadczenia, które mogą być przedstawiane na `MyService` lokacji usługi do uzyskiwania dostępu do usługi. Jednak Usługa STS B wymaga od użytkowników przedstawić prawidłowy token SAML wystawione przez usługę STS A, który zawiera `userAuthenticated` oświadczenia. Jest to deklaratywne określona w konfiguracji usługi STS.  
  
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
>  Ponownie `userAuthenticated` oświadczeń jest typ oświadczenia, która jest wymagana przez usługę STS B. W pełni kwalifikowaną nazwą tego typu oświadczenia jest `http://tempuri.org:userAuthenticated` (oraz skojarzony przestrzeni nazw), która zostanie użyta w pliku konfiguracji usługi STS. Wartość tego oświadczenia wskazuje obecność tego oświadczenia i założono, że można ustawić `true` przez usługę STS A.  
  
 W czasie wykonywania `STS_B_OperationRequirement` klasy wymusza tę zasadę, która została wdrożona jako część usługi STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Jeżeli sprawdzanie dostępu nie zostanie zaznaczone, STS B wystawia token SAML z `accessAuthorized` oświadczenia.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>USŁUGA STS A  
 Na poniższej ilustracji przedstawiono A. usługi STS  
  
 ![Federacyjna](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobnie jak B usługi STS, A Usługa STS jest również usługa sieci Web, który wystawia tokeny zabezpieczające i udostępnia pojedyncze punkty końcowe w tym celu. Jednak używa różnych powiązania (`wsHttpBinding`) i wymaga od użytkowników przedstawić prawidłowy [!INCLUDE[infocard](../../../../includes/infocard-md.md)] z `emailAddress` oświadczenia. W odpowiedzi, wystawia tokeny SAML za pomocą `userAuthenticated` oświadczenia. Jest to deklaratywne określony w konfiguracji usługi.  
  
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
  
 W czasie wykonywania `STS_A_OperationRequirement` klasy wymusza tę zasadę, która została wdrożona jako część usługi STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Jeśli dostęp jest `true`, A Usługa STS wystawia token SAML z `userAuthenticated` oświadczenia.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient w organizacji, A  
 Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z etapy w tworzeniu `MyService` wywołania usługi. Funkcjonalności innych składników dostępne są również aby informacje były kompletne.  
  
 ![Federation](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Podsumowanie  
 Federacyjnego zabezpieczenia zapewnia czyste podział odpowiedzialności i pomaga w tworzeniu architektur bezpiecznego, skalowalnego usług. Platforma do kompilowania i wdrażania aplikacji rozproszonych WCF zapewnia macierzystą obsługę dotyczące implementowania zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)

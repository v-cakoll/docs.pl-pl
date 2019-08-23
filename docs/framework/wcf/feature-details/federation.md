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
ms.openlocfilehash: 2331e484f22be7e3154a4cff981ee320a9b143a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948161"
---
# <a name="federation"></a>Federacja
Ten temat zawiera krótkie omówienie koncepcji zabezpieczeń federacyjnych. Opisano w nim również obsługę Windows Communication Foundation (WCF) na potrzeby wdrażania federacyjnych architektur zabezpieczeń. Aby zapoznać się z przykładową aplikacją, która demonstruje Federacji, zobacz [przykład Federacji](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definicja zabezpieczeń federacyjnych  
 Zabezpieczenia federacyjne umożliwiają czyste rozdzielenie między usługą dostępną przez klienta a związanymi z nimi procedurami uwierzytelniania i autoryzacji. Zabezpieczenia federacyjne umożliwiają również współpracę między wieloma systemami, sieciami i organizacjami w różnych obszarach zaufania.  
  
 Funkcja WCF zapewnia obsługę kompilowania i wdrażania systemów rozproszonych, które wykorzystują zabezpieczenia federacyjne.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementy architektury zabezpieczeń federacyjnych  
 Architektura zabezpieczeń federacyjnych ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|Domena/obszar|Pojedyncza jednostka administrowania zabezpieczeniami lub zaufania. Typowa domena może obejmować jedną organizację.|  
|Federacja|Kolekcja domen, które mają ustanowioną relację zaufania. Poziom zaufania może się różnić, ale zazwyczaj obejmuje uwierzytelnianie i prawie zawsze obejmuje autoryzację. Typowa Federacja może obejmować wiele organizacji, które ustanowiły zaufanie dostępu współdzielonego do zestawu zasobów.|  
|Usługa tokenu zabezpieczającego (STS)|Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że wykonuje potwierdzenia oparte na zasobie, że ufa, aby whomever je z zaufaniem. Stanowi to podstawę zaufania między domenami.|  
  
### <a name="example-scenario"></a>Przykładowy scenariusz  
 Na poniższej ilustracji przedstawiono przykład zabezpieczeń federacyjnych:  
  
 ![Diagram przedstawiający typowy scenariusz zabezpieczeń federacyjnych.](./media/federation/typical-federated-security-scenario.gif)  
  
 Ten scenariusz obejmuje dwie organizacje: A i B. organizacja B ma zasób sieci Web (usługę sieci Web), który niektórzy użytkownicy w organizacji znalazły wartość cenną.  
  
> [!NOTE]
> Ta sekcja używa zamiennie postanowień dotyczących *zasobów*, *usług*i *usług sieci Web* .  
  
 Zazwyczaj organizacja B wymaga, aby przed uzyskaniem dostępu do usługi użytkownik z organizacji A zapewniał pewną prawidłową formę uwierzytelniania. Ponadto organizacja może również wymagać, aby użytkownik miał uprawnienia dostępu do określonego zasobu. Jednym ze sposobów rozwiązania tego problemu i umożliwienie użytkownikom w organizacji A uzyskiwania dostępu do zasobu w organizacji B jest następująca:  
  
- Użytkownicy z organizacji A rejestrują swoje poświadczenia (nazwa użytkownika i hasło) w organizacji B.  
  
- Podczas uzyskiwania dostępu do zasobów użytkownicy z organizacji składają swoje poświadczenia do organizacji B i są uwierzytelniani przed uzyskaniem dostępu do zasobu.  
  
 Takie podejście ma trzy znaczące wady:  
  
- Organizacja B musi zarządzać poświadczeniami użytkowników z organizacji A poza zarządzaniem poświadczeniami użytkowników lokalnych.  
  
- Użytkownicy w organizacji muszą zachować dodatkowy zestaw poświadczeń (czyli zapamiętać dodatkową nazwę użytkownika i hasło) od poświadczeń, z których zazwyczaj korzystają, aby uzyskać dostęp do zasobów w organizacji A. Zwykle jest to zalecane w przypadku używania tej samej nazwy użytkownika i hasła w wielu lokacjach usług, co jest słabym środkiem bezpieczeństwa.  
  
- Architektura nie jest skalowana, ponieważ coraz więcej organizacji postrzega zasób w organizacji B jako część wartości.  
  
 Alternatywne podejście, które dotyczy wyżej wspomnianych wad, ma na celu zastosowanie zabezpieczeń federacyjnych. W tym podejściu organizacje A i B ustanawiają relację zaufania i korzystają z usługi tokenu zabezpieczającego (STS) w celu umożliwienia brokera ustanowionego zaufania.  
  
 W federacyjnej architekturze zabezpieczeń Użytkownicy z organizacji wiedzą, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, która musi przedstawić prawidłowy token zabezpieczający z STS w organizacji B, który uwierzytelnia i autoryzuje dostęp do określona usługa.  
  
 Podczas kontaktowania się z usługą STS B użytkownicy otrzymują kolejny poziom pośredni z zasad skojarzonych z usługą STS. Muszą one przedstawić prawidłowy token zabezpieczający od usługi STS A (czyli obszaru zaufania klienta) przed wystawieniem im tokenu zabezpieczającego przez usługę STS B. Jest to współrzut relacji zaufania ustanowiony między obiema organizacjami i oznacza, że organizacja B nie musi zarządzać tożsamościami użytkowników z organizacji A. W przypadku usługi STS B zazwyczaj ma wartość null `issuerAddress` i `issuerMetadataAddress`. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie lokalnego wystawcy](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). W takim przypadku klient korzysta z zasad lokalnych w celu zlokalizowania usługi STS A. Ta konfiguracja jest nazywana *Federacją obszaru głównego* i skalowalna, ponieważ usługa STS B nie musi obsługiwać informacji o usłudze STS A.  
  
 Użytkownicy mogą następnie skontaktować się z usługą STS w organizacji A i uzyskać token zabezpieczający przez przedstawienie poświadczeń uwierzytelniania, które zwykle są używane do uzyskania dostępu do dowolnego innego zasobu w organizacji A. Pozwala to również uniknąć problemów użytkowników, którzy muszą zachować wiele zestawów poświadczeń lub użyć tego samego zestawu poświadczeń w wielu lokacjach usług.  
  
 Gdy użytkownicy uzyskają token zabezpieczający od usługi STS A, przedstawią token do usługi STS B. organizacja B wykonuje autoryzację żądań użytkowników i wystawia token zabezpieczający użytkownikom ze swojego własnego zestawu tokenów zabezpieczających. Użytkownicy mogą następnie przedstawić swój token dla zasobu w organizacji B i uzyskać dostęp do usługi.  
  
## <a name="support-for-federated-security-in-wcf"></a>Obsługa zabezpieczeń federacyjnych w programie WCF  
 Funkcja WCF oferuje gotoweą obsługę wdrażania federacyjnych architektur zabezpieczeń za pomocą [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Element [WSFederationHttpBinding > zapewnia bezpieczne, niezawodne i interoperacyjne powiązanie, które wiąże się z użyciem protokołu HTTP jako podstawowego mechanizmu transportu dla stylu komunikacji żądanie-odpowiedź, używając tekstu i XML jako \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Format sieci do kodowania.  
  
 Korzystanie z [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w federacyjnym scenariuszu zabezpieczeń można rozdzielić na dwie niezależne od siebie fazy, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="phase-1-design-phase"></a>Faza 1: Faza projektowania  
 W fazie projektowania klient używa narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby przeczytać zasady ujawniane przez punkt końcowy usługi i zebrać wymagania dotyczące uwierzytelniania i autoryzacji usługi. Odpowiednie serwery proxy są konstruowane w celu utworzenia na kliencie następującego wzorca komunikacji z zabezpieczeniami federacyjnymi:  
  
- Uzyskaj token zabezpieczający z usługi STS w obszarze zaufania klienta.  
  
- Zaprezentowanie tokenu w usłudze STS w obszarze zaufania usługi.  
  
- Uzyskaj token zabezpieczający z programu STS w obszarze zaufania usługi.  
  
- Zaprezentowanie tokenu usłudze w celu uzyskania dostępu do usługi.  
  
### <a name="phase-2-run-time-phase"></a>Faza 2: Faza czasu wykonywania  
 Podczas fazy czasu wykonywania klient tworzy wystąpienie obiektu klasy klienta WCF i wykonuje wywołanie przy użyciu klienta WCF. Podstawowa struktura programu WCF obsługuje wyżej wymienione kroki we wzorcu komunikacji z zabezpieczeniami federacyjnymi i umożliwia klientowi bezproblemowe korzystanie z usługi.  
  
## <a name="sample-implementation-using-wcf"></a>Przykładowa implementacja przy użyciu programu WCF  
 Na poniższej ilustracji przedstawiono przykładową implementację architektury zabezpieczeń federacyjnych przy użyciu natywnej pomocy technicznej z programu WCF.  
  
 ![Diagram przedstawiający przykładową implementację zabezpieczeń Federacji.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Przykładowa usługa  
 Usługa `MyService` ujawnia pojedynczy punkt końcowy za pomocą `MyServiceEndpoint`. Na poniższej ilustracji przedstawiono adres, powiązanie i kontrakt skojarzone z punktem końcowym.  
  
 ![Diagram przedstawiający szczegóły dotyczące programu ServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 Punkt końcowy `MyServiceEndpoint` usługi `accessAuthorized` [ \<używa > WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu potwierdzeń zabezpieczeń (SAML) z twierdzeniem wystawionym przez usługę STS B. Ta wartość jest deklaratywnie określona w konfiguracji usługi.  
  
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
> Należy zauważyć delikatny wgląd w oświadczenia wymagane przez `MyService`. Drugi rysunek wskazuje, że `MyService` wymaga tokenu SAML z tym `accessAuthorized` elementem. Aby dokładniej określić typ, który `MyService` wymaga. W pełni kwalifikowana nazwa tego typu jest `http://tempuri.org:accessAuthorized` (wraz ze skojarzoną przestrzenią nazw), która jest używana w pliku konfiguracji usługi. Wartość tego żądania wskazuje obecność tego żądania i zakłada się, że jest ono ustawiane `true` przez usługę STS B.  
  
 W czasie wykonywania te zasady są wymuszane przez `MyServiceOperationRequirement` klasę, która jest implementowana w ramach `MyService`programu.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>USŁUGA STS B  
 Na poniższej ilustracji przedstawiono usługę STS B. Jak wspomniano wcześniej, usługa tokenu zabezpieczającego (STS) jest również usługą sieci Web i może mieć skojarzone punkty końcowe, zasady i tak dalej.  
  
 ![Diagram przedstawiający usługę tokenów zabezpieczających B.](./media/federation/myservice-security-token-service-b.gif)  
  
 Usługa STS B udostępnia jeden punkt końcowy o `STSEndpoint` nazwie, którego można użyć do żądania tokenów zabezpieczających. W odniesieniu do usługi STS B są `accessAuthorized` wystawiane tokeny SAML, które `MyService` mogą być prezentowane w lokacji usługi w celu uzyskania dostępu do usług. Jednak usługa STS B wymaga, aby użytkownicy zaprezentować prawidłowy token SAML wystawiony przez usługę `userAuthenticated` STS a, która zawiera ten element. Ta wartość jest deklaratywnie określona w konfiguracji usługi STS.  
  
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
> `userAuthenticated` Ponownie jest to typ zgłoszenia wymagany przez usługę STS B. W pełni kwalifikowana nazwa tego typu jest `http://tempuri.org:userAuthenticated` (wraz ze skojarzoną przestrzenią nazw), która jest używana w pliku konfiguracji usługi STS. Wartość tego żądania wskazuje obecność tego żądania i przyjmuje się, że jest ono ustawiane `true` przez usługę STS a.  
  
 W czasie wykonywania `STS_B_OperationRequirement` Klasa wymusza te zasady, które są implementowane w ramach usługi STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Jeśli sprawdzanie dostępu jest jasne, usługa STS B wystawia token języka SAML `accessAuthorized` w ramach tego żądania.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>USŁUGA STS A  
 Na poniższej ilustracji przedstawiono usługę STS A.  
  
 ![Federacja federacyjna](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobnie jak w przypadku usługi STS B, usługa STS A jest również usługą sieci Web, która wystawia tokeny zabezpieczające i udostępnia w tym celu pojedynczy punkt końcowy. Jednak używa innego powiązania (`wsHttpBinding`) i wymaga, aby użytkownicy zaprezentować prawidłowy `emailAddress` program CardSpace z zastrzeżeniem. W odpowiedzi powoduje wystawianie tokenów SAML `userAuthenticated` z wnioskiem. Ta wartość jest deklaratywnie określona w konfiguracji usługi.  
  
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
  
 W czasie wykonywania `STS_A_OperationRequirement` Klasa wymusza te zasady, które są implementowane w ramach usługi STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Jeśli dostęp to `true`, usługa STS wystawia token języka SAML `userAuthenticated` przy użyciu żądania.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Klient w organizacji A  
 Na poniższej ilustracji przedstawiono klienta w organizacji A wraz z krokami związanymi z wykonywaniem `MyService` wywołania usługi. Pozostałe składniki funkcjonalne są również dołączone do kompletności.  
  
 ![Diagram przedstawiający kroki wywołania usługi WebService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Podsumowanie  
 Zabezpieczenia federacyjne zapewniają czyste dział odpowiedzialności i ułatwiają tworzenie bezpiecznych, skalowalnych architektur usług. Jako platforma do kompilowania i wdrażania aplikacji rozproszonych, WCF zapewnia natywną obsługę implementowania zabezpieczeń federacyjnych.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)

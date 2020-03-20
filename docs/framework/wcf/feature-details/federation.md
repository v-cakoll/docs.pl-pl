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
ms.openlocfilehash: 86c679af77f2b7b1960e7489e0e6e61b811e1bad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185222"
---
# <a name="federation"></a>Federacja
Ten temat zawiera krótki przegląd pojęcia zabezpieczeń federacyjnej. Opisano w nim również obsługę programu Windows Communication Foundation (WCF) w zakresie wdrażania architektur zabezpieczeń federacyjnego. Aby zapoznać się z przykładową aplikacją, która demonstruje federację, zobacz [Próbka federacyjne](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Definicja zabezpieczeń federacyjnej  
 Zabezpieczenia federacyjne umożliwiają czystą separację między usługą, do która klient uzyskuje dostęp, a skojarzonymi procedurami uwierzytelniania i autoryzacji. Zabezpieczenia federacyjne umożliwiają również współpracę między wieloma systemami, sieciami i organizacjami w różnych domenach zaufania.  
  
 WCF zapewnia obsługę tworzenia i wdrażania systemów rozproszonych, które wykorzystują zabezpieczenia federacyjne.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Elementy architektury zabezpieczeń federacyjnej  
 Architektura zabezpieczeń federacyjnej ma trzy kluczowe elementy, zgodnie z opisem w poniższej tabeli.  
  
|Element|Opis|  
|-------------|-----------------|  
|Domena/królestwo|Pojedyncza jednostka administracji zabezpieczeń lub zaufania. Typowa domena może obejmować jedną organizację.|  
|Federacja|Kolekcja domen, które nawiązały zaufanie. Poziom zaufania może się różnić — zwykle obejmuje uwierzytelnianie i niemal zawsze autoryzację. Typowa federacja może obejmować kilka organizacji, które mają ustanowioną relację zaufania na potrzeby dostępu współdzielonego do zestawu zasobów.|  
|Usługa tokenu zabezpieczającego (STS)|Usługa sieci Web, która wystawia tokeny zabezpieczające; oznacza to, że sprawia, że twierdzenia oparte na dowodach, że ufa, kto mu ufa. Stanowi to podstawę brokerowania zaufania między domenami.|  
  
### <a name="example-scenario"></a>Przykładowy scenariusz  
 Na poniższej ilustracji przedstawiono przykład zabezpieczeń federacyjnych:  
  
 ![Diagram przedstawiający typowy scenariusz zabezpieczeń federacyjnej.](./media/federation/typical-federated-security-scenario.gif)  
  
 Ten scenariusz obejmuje dwie organizacje: A i B. Organizacja B ma zasób sieci Web (usługa sieci Web), który niektórzy użytkownicy w organizacji A uważają za wartościowy.  
  
> [!NOTE]
> W tej sekcji użyto *warunków zasób*, *usługa*i usługa *sieci Web* zamiennie.  
  
 Zazwyczaj organizacja B wymaga, aby użytkownik z organizacji A dostarczył prawidłową formę uwierzytelniania przed dostępem do usługi. Ponadto organizacja może również wymagać, aby użytkownik był upoważniony do uzyskania dostępu do określonego zasobu, o których mowa. Jednym ze sposobów rozwiązania tego problemu i umożliwienia użytkownikom w organizacji A dostępu do zasobu w organizacji B jest następujący sposób:  
  
- Użytkownicy z organizacji A rejestrują swoje poświadczenia (nazwę użytkownika i hasło) w organizacji B.  
  
- Podczas dostępu do zasobów użytkownicy z organizacji A prezentują swoje poświadczenia w organizacji B i są uwierzytelnieni przed dostępem do zasobu.  
  
 Takie podejście ma trzy istotne wady:  
  
- Organizacja B musi zarządzać poświadczeniami dla użytkowników z organizacji A oprócz zarządzania poświadczeniami użytkowników lokalnych.  
  
- Użytkownicy w organizacji A muszą zachować dodatkowy zestaw poświadczeń (czyli zapamiętać dodatkową nazwę użytkownika i hasło) oprócz poświadczeń, których zwykle używają do uzyskiwania dostępu do zasobów w organizacji A. Zazwyczaj zachęca to do stosowania tej samej nazwy użytkownika i hasła w wielu witrynach serwisowych, co jest słabym środkiem bezpieczeństwa.  
  
- Architektura nie skaluje się, ponieważ więcej organizacji postrzega zasób w organizacji B jako o pewnej wartości.  
  
 Alternatywnym podejściem, które rozwiązuje wspomniane wcześniej wady, jest stosowanie zabezpieczeń federacyjnej. W tym podejściu organizacje A i B ustanawiają relację zaufania i wykorzystują usługę tokenu zabezpieczeń (STS), aby umożliwić pośrednictwo w ustalonym zaufaniu.  
  
 W architekturze zabezpieczeń federacyjnego użytkownicy z organizacji A wiedzą, że jeśli chcą uzyskać dostęp do usługi sieci Web w organizacji B, muszą przedstawić prawidłowy token zabezpieczający z STS w organizacji B, który uwierzytelnia i zezwala na ich dostęp do konkretnej usługi.  
  
 Po skontaktowaniu się z STS B użytkownicy otrzymują inny poziom pośredni z zasad skojarzonych z STS. Muszą przedstawić prawidłowy token zabezpieczający z STS A (czyli sfery zaufania klienta), zanim usługa STS B może wydać im token zabezpieczający. Jest to następstwo relacji zaufania ustanowionej między dwiema organizacjami i oznacza, że organizacja B nie musi zarządzać tożsamościami użytkowników z organizacji A. W praktyce STS B zazwyczaj `issuerAddress` `issuerMetadataAddress`ma wartość null i . Aby uzyskać więcej informacji, zobacz [Jak: Konfigurowanie wystawcy lokalnego](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). W takim przypadku klient konsultuje się z zasadami lokalnymi w celu zlokalizowania usługi STS A. Ta konfiguracja jest nazywana *federacją obszaru macierzystego* i jest skalowana lepiej, ponieważ STS B nie musi obsługiwać informacji o STS A.  
  
 Następnie użytkownicy kontaktują się z STS w organizacji A i uzyskują token zabezpieczający, przedstawiając poświadczenia uwierzytelniania, których zwykle używają do uzyskiwania dostępu do innych zasobów w organizacji A. To również łagodzi problem użytkowników konieczności obsługi wielu zestawów poświadczeń lub przy użyciu tego samego zestawu poświadczeń w wielu lokacjach usługi.  
  
 Gdy użytkownicy uzyskują token zabezpieczający z STS A, przedstawiają token do STS B. Organizacja B przystępuje do wykonywania autoryzacji żądań użytkowników i wystawia token zabezpieczający dla użytkowników z własnego zestawu tokenów zabezpieczających. Użytkownicy mogą następnie przedstawić swój token do zasobu w organizacji B i uzyskać dostęp do usługi.  
  
## <a name="support-for-federated-security-in-wcf"></a>Wsparcie dla federacyjnego bezpieczeństwa w WCF  
 WCF zapewnia "pod klucz" obsługę wdrażania architektur zabezpieczeń federacyjnych za pośrednictwem [ \<>wsFederationHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Element [ \<>wsFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) zapewnia bezpieczne, niezawodne, interoperacyjne powiązanie, które pociąga za sobą użycie protokołu HTTP jako mechanizmu transportu bazowego dla stylu komunikacji żądanie-odpowiedź, wykorzystując tekst i XML jako format przewodowy do kodowania.  
  
 Użycie [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) w scenariuszu zabezpieczeń federacyjnych można oddzielić na dwie logicznie niezależne fazy, zgodnie z opisem w poniższych sekcjach.  
  
### <a name="phase-1-design-phase"></a>Faza 1: Faza projektowania  
 W fazie projektowania klient używa [Narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do odczytu zasad udostępnianych przez punkt końcowy usługi oraz do zbierania wymagań dotyczących uwierzytelniania i autoryzacji usługi. Odpowiednie serwery proxy są skonstruowane w celu utworzenia następującego wzorca komunikacji zabezpieczeń federacyjnego na kliencie:  
  
- Uzyskaj token zabezpieczający z usługi STS w dziedzinie zaufania klienta.  
  
- Przedstaw token do STS w sferze zaufania usługi.  
  
- Uzyskaj token zabezpieczający z STS w dziedzinie zaufania usługi.  
  
- Przedstaw token do usługi, aby uzyskać dostęp do usługi.  
  
### <a name="phase-2-run-time-phase"></a>Faza 2: Faza czasu wykonywania  
 Podczas fazy wykonywania klienta tworzy wystąpienia obiektu klasy klienta WCF i wykonuje wywołanie przy użyciu klienta WCF. Podstawowa struktura WCF obsługuje wcześniej wymienionych kroków w federacyjnej komunikacji zabezpieczeń wzorca i umożliwia klientowi bezproblemowe korzystanie z usługi.  
  
## <a name="sample-implementation-using-wcf"></a>Przykładowa implementacja przy użyciu WCF  
 Na poniższej ilustracji przedstawiono przykładową implementację architektury zabezpieczeń federacyjnych przy użyciu natywnej obsługi z WCF.  
  
 ![Diagram przedstawiający przykładową implementację zabezpieczeń federacji.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Przykład MyService  
 Usługa `MyService` udostępnia pojedynczy punkt końcowy `MyServiceEndpoint`za pośrednictwem . Na poniższej ilustracji przedstawiono adres, powiązanie i umowy skojarzone z punktem końcowym.  
  
 ![Diagram przedstawiający szczegóły MyServiceEndpoint.](./media/federation/myserviceendpoint-details.gif)  
  
 Punkt `MyServiceEndpoint` końcowy usługi używa [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) i wymaga prawidłowego tokenu języka znaczników oświadczeń zabezpieczeń (SAML) z oświadczeniem wystawionym `accessAuthorized` przez STS B. Jest to deklaratywnie określone w konfiguracji usługi.  
  
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
> Subtelny punkt należy zwrócić uwagę na `MyService`roszczenia wymagane przez . Druga liczba wskazuje, `MyService` że wymaga tokenu `accessAuthorized` SAML z oświadczeniem. Aby być bardziej precyzyjne, określa `MyService` typ oświadczenia, który wymaga. W pełni kwalifikowana nazwa tego `http://tempuri.org:accessAuthorized` typu oświadczenia jest (wraz ze skojarzonym obszarem nazw), który jest używany w pliku konfiguracji usługi. Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i zakłada `true` się, że jest ona ustawiona przez STS B.  
  
 W czasie wykonywania ta zasada jest `MyServiceOperationRequirement` wymuszana przez klasę, która jest implementowana jako część `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Na poniższej ilustracji przedstawiono STS B. Jak wspomniano wcześniej, usługa tokenu zabezpieczającego (STS) jest również usługą sieci Web i może mieć skojarzone z nią punkty końcowe, zasady i tak dalej.  
  
 ![Diagram przedstawiający usługę tokenu zabezpieczającego B.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B udostępnia pojedynczy punkt `STSEndpoint` końcowy, wywoływane, które mogą być używane do żądania tokenów zabezpieczających. W szczególności STS B wystawia tokeny `accessAuthorized` SAML z oświadczenia, `MyService` które mogą być prezentowane w witrynie usługi dostępu do usługi. Jednak STS B wymaga od użytkowników przedstawienia prawidłowego tokenu SAML `userAuthenticated` wystawionego przez STS A, który zawiera oświadczenie. Jest to deklaratywnie określone w konfiguracji STS.  
  
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
> `userAuthenticated` Ponownie, oświadczenie jest typem oświadczenia, który jest wymagany przez STS B. W pełni kwalifikowana nazwa tego `http://tempuri.org:userAuthenticated` typu oświadczenia jest (wraz ze skojarzonym obszarem nazw), która jest używana w pliku konfiguracyjnym STS. Wartość tego oświadczenia wskazuje na obecność tego oświadczenia i zakłada `true` się, że jest ustawiona przez STS A.  
  
 W czasie wykonywania `STS_B_OperationRequirement` klasa wymusza tę zasadę, która jest implementowana jako część STS B.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Jeśli sprawdzanie dostępu jest jasne, STS B wystawia `accessAuthorized` token SAML z oświadczeniem.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Na poniższej ilustracji przedstawiono STS A.  
  
 ![Federacja](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 Podobnie jak STS B, STS A jest również usługą sieci Web, która wystawia tokeny zabezpieczające i udostępnia w tym celu pojedynczy punkt końcowy. Używa jednak innego powiązania (`wsHttpBinding`) i wymaga od użytkowników przedstawienia `emailAddress` ważnego CardSpace z roszczeniem. W odpowiedzi wydaje tokeny SAML `userAuthenticated` z roszczeniem. Jest to deklaratywnie określone w konfiguracji usługi.  
  
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
  
 W czasie wykonywania `STS_A_OperationRequirement` klasa wymusza tę zasadę, która jest implementowana jako część STS A.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Jeśli dostęp `true`jest , STS A wystawia `userAuthenticated` token SAML z oświadczeniem.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Client w: Organization A  
 Na poniższej ilustracji przedstawiono klienta w organizacji A, wraz z kroki związane z wykonywaniem `MyService` wywołania usługi. Pozostałe elementy funkcjonalne są również dołączone do kompletności.  
  
 ![Diagram przedstawiający kroki w wywołaniu usługi MyService.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Podsumowanie  
 Zabezpieczenia federacyjne zapewniają czysty podział odpowiedzialności i pomagają w tworzeniu bezpiecznych, skalowalnych architektur usług. Jako platforma do tworzenia i wdrażania aplikacji rozproszonych WCF zapewnia natywną obsługę wdrażania zabezpieczeń federacyjnych.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
